# xBoreUp Linux Patch

A curated collection of performance and responsiveness patches for Linux `linux-7.1.y`.

## Patch List

### Network

| # | Patch | Description |
|---|-------|-------------|
| 0001 | [`net/tcp: add Google BBR v3 congestion control`](https://github.com/google/bbr/tree/v3) | Replace default CUBIC with BBR v3 for higher throughput and lower latency |
| 0002 | `net/tcp: increase TCP write buffer limit 4MB → 16MB` | Bigger TCP write buffer for high-throughput connections |
| 0003 | `net/sock: increase default socket buffer size 4x` | Raise default socket receive/send buffer across all sockets |

### Scheduler

| # | Patch | Description |
|---|-------|-------------|
| 0004 | `sched: rate-limit sched_yield to once per jiffy` | Prevent yield spam in Proton/Wine games that abuse `sched_yield()` |
| 0008 | [`sched: add BORE Scheduler`](https://github.com/firelzrd/bore-scheduler) | Burst-Oriented Response Enhancer — improves desktop interactivity |
| 0009 | [`sched: add POC Selector`](https://github.com/firelzrd/poc-selector) | Piece Of Cake task selector for the fair scheduler |
| 0013 | [`sched: add Cambyses load balancer`](https://github.com/firelzrd/cambyses) | Alternative load balancer for better multi-core task distribution |

### Memory Management

| # | Patch | Description |
|---|-------|-------------|
| 0005 | [`mm: raise default max_map_count to INT_MAX`](https://fedoraproject.org/wiki/Changes/IncreaseVmMaxMapCount) | Prevent game crashes caused by VMA exhaustion |
| 0012 | [`zram: add Immediate Recompression`](https://github.com/firelzrd/zram-ir) | Re-compress ZRAM pages immediately for better memory efficiency |
| 0015 | [`mm: add lru_marie MARIE LRU`](https://github.com/firelzrd/lru_marie) | Unified SIMD-accelerated LRU reclaim with async swap compression via `kcompmari` and hardware-accelerated PTE scanning (SSE2/AVX2/AVX-512/NEON) |
| 0016 | `lru_marie: add AVX-512F+BW+BMI2 PTE scanner for AMD Zen 5` | AVX-512 optimised PTE scanner specifically tuned for AMD Zen 5 |

### I/O

| # | Patch | Description |
|---|-------|-------------|
| 0010 | [`block: add ADIOS I/O Scheduler`](https://github.com/firelzrd/adios) | Adaptive Deadline I/O Scheduler — lower latency block I/O |

### CPU / Power

| # | Patch | Description |
|---|-------|-------------|
| 0006 | `time: reduce default timer_slack_ns 50µs → 50ns` | Tighter hrtimer coalescing window for `nanosleep`/`select`/`futex`, inherited from PID 1 |
| 0007 | `iommu: enable posted MSI by default` | Lower PCIe interrupt latency, especially for GPU |
| 0011 | [`cpuidle: add NAP Governor`](https://github.com/firelzrd/nap) | Neural Adaptive Prediction cpuidle governor for smarter power saving |
| 0014 | [`cpufreq: add Reflex Governor`](https://github.com/firelzrd/reflex) | Interactive cpufreq governor with fast frequency scaling (default as modules) |

### Build

| # | Patch | Description |
|---|-------|-------------|
| 0017 | `scripts: setlocalversion remove tag for git repo` | Cleaner kernel version string |

---

*Maintained by [Salman Wahib](https://github.com/sxlmnwb)*
