# Papers

(some papers are available in Papers repo dir)

- [Papers](#papers)
  - [Compute](#compute)
  - [Storage](#storage)
  - [Concurrency](#concurrency)
  - [Testing](#testing)

## Compute

* [Google, Borg: the next generation](https://www.cs.cmu.edu/~harchol/Papers/EuroSys20.pdf)

* [ZooKeeper: Wait-free coordination for Internet-scale systems](https://www.usenix.org/legacy/event/atc10/tech/full_papers/Hunt.pdf)
* Froid: Optimization of Imperative Programs in a Relational Database (K. Ramachandra, et al., VLDB 2017)
* Don't Hold My Data Hostage: A Case for Client Protocol Redesign (M. Raasveldt, et al., VLDB 2017)
* An Overview of Query Optimization in Relational Systems (S. Chaudhuri, PODS 1998)
* Dremel: A Decade of Interactive SQL Analysis at Web Scale (S. Melnik, et al., VLDB 2020)
* Photon: A Fast Query Engine for Lakehouse Systems (A. Behm, et al., SIGMOD 2022)

## Storage

Distributed File Systems
* [Navigating the Landscape of Distributed File Systems: Architectures, Implementations, and Considerations (arxiv 2024)](./Papers/navigating_landscape_distributed_file_system.pdf). This article provides an overview of DFS, its architecture, classification methods, design considerations, challenges, and common implementations.
* [Google File System (SOSP 2023)](https://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf). Very influential, inspired HDFS (Hadoop Distributed File System). This paper describes the distributed file system designed to run on large clusters of commodity hardware at early Google. It introduced concepts like a single master architecture (for simplicity), large chunk sizes (64MB) optimized for large sequential reads/writes typical of MapReduce workloads, replication for fault tolerance (instead of RAID), and relaxed consistency models optimized for Google's specific use cases.
* Ceph: A Scalable, High-Performance Distributed File System (OSDI 2006). Ceph introduced a fundamentally different approach compared to GFS/HDFS. Key ideas: decoupling metadata from data storage (using MDS servers), calculating data placement algorithmically using CRUSH (Controlled Replication Under Scalable Hashing) instead of relying on a central lookup table, and providing unified access to object, block, and file storage. A move towards more dynamic, self-managing, and flexible distributed storage architectures.
* [Finding a needle in Haystack: Facebook’s photo storage (OSDI 2010)](./Papers/finding_needle_in_haystack_facebook_photo_storage.pdf). This paper shows how object store design can be tailored for specific access patterns. It tackles a specific, critical object storage problem: efficiently storing and serving billions of small objects (photos) with low latency. Traditional file/object systems often struggle with metadata overhead for small files. Haystack's design optimizes for this by appending photos into large log-structured "store" files (reducing disk seeks and metadata overhead) and keeping an in-memory index mapping photo IDs to their location within these store files. Result: reduced disk I/O and latency for Facebook's photo serving workload.

Databases
* Bigtable: A Distributed Storage System for Structured Data (OSDI 2006).
* [Dynamo: Amazon’s Highly Available Key-value Store (SOSP 2007)](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf). This paper described Amazon's internal key-value store, focusing relentlessly on availability and partition tolerance, even at the cost of strong consistency. It popularized techniques like eventual consistency, vector clocks for resolving conflicts, consistent hashing for partitioning and distribution, read repair, and gossip protocols for membership and failure detection. Influential in the NoSQL movement, particularly for systems prioritizing uptime. There are informative videos i.e. [Christopher Batey - DYNAMO: the paper that changed the database world](https://www.youtube.com/watch?v=hMt9yFp0JKM)
* [The Snowflake Elastic Data Warehouse (B. Dageville, et al., SIGMOD 2016)](./Papers/Snowflake_elastic_data_warehouse.pdf). This paper details Snowflake's multi-cluster, shared-data architecture built for the cloud. A key aspect is its complete separation of storage and compute.
* Amazon Aurora: Design Considerations for High Throughput Cloud-Native Relational Databases (SIGMOD 2017). This paper describes the architecture of Amazon Aurora, focusing on how the storage layer was redesigned for the cloud. Instead of replicating full disk blocks, Aurora uses a log-structured storage service, replicating only redo log records across multiple Availability Zones. Result: reduction of network I/O, improves fault tolerance, and enables faster crash recovery.
* DuckDB: an Embeddable Analytical Database (M. Raasveldt, et al., SIGMOD 2019)
* Yellowbrick: An Elastic Data Warehouse on Kubernetes (M. Cusack, et al., CIDR 2024)
* Amazon Redshift Re-Invented (N. Armenatzoglou, et al., SIGMOD 2022). This paper describes the evolution of Amazon Redshift towards a more disaggregated, cloud-native architecture.
* [Understanding the Performance Implications of the Design Principles in Storage-Disaggregated Databases (ACM 2023)](https://dl.acm.org/doi/10.1145/3654983). This papers looks at the performance trade-offs inherent in separating compute and storage, particularly the impact of network latency and bandwidth between compute nodes and remote storage (like S3). It studies caching strategies and data skipping techniques important for making these disaggregated systems performant.

Storage Formats
* An Empirical Evaluation of Columnar Storage Formats.

## Concurrency
* [Why Events Are A Bad Idea (for high-concurrency servers)](Papers/why_events_are_a_bad_idea.pdf)
* [Learning from Mistakes — A Comprehensive Study on Real World Concurrency Bug Characteristics](https://www.cs.columbia.edu/~junfeng/08fa-e6998/sched/readings/concurrency-bugs.pdf)
* [Everything You Always Wanted to Know About Synchronization but Were Afraid to Ask (SIGOPS 2013)](https://sigops.org/s/conferences/sosp/2013/papers/p33-david.pdf)


## Testing

* SparkFuzz - searching correctness regressions in modern query engines
