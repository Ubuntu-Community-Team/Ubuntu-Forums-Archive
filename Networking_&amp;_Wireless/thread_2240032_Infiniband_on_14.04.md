---
title: "Infiniband on 14.04"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by Rio_Yokota on 2014-08-17
I have recently upgraded from 12.04 LTS to 14.04 LTS, and OpenMPI over infiniband now gives me a warning

WARNING: It appears that your OpenFabrics subsystem is configured to only
allow registering part of your physical memory.  This can cause MPI jobs to
run with erratic performance, hang, and/or crash.

Everything that I could find on google suggests to change log_num_mtt, but I cannot do this for the following reasons:
1. There is no log_num_mtt in /sys/module/mlx4_core/parameters/
2. Adding "options mlx4_core log_num_mtt=24" to /etc/modprobe.d/mlx4.conf doesn't seem to change anything
3. I am not sure how I can restart the driver because there is no "/etc/init.d/openibd" file (I've rebooted the system but it didn't do anything to create log_num_mtt)

---

### Post by Rio_Yokota on 2014-08-20
I have received the following reply on the OpenMPI forum.
----
Rio is using the kernel.org drivers that are part of Ubuntu/3.13.x and
log_num_mtt is not a parameter in those drivers. In fact log_num_mtt
has never been a parameter in the kernel.org sources (just checked the
git commit history). And it's not needed anymore either, since the
following commit (which is also part of OFED 3.12 btw; Mike, seems
Mellanox OFED is behind with this respect):
-----------------------------------------------------------
commit db5a7a65c05867cb6ff5cb6d556a0edfce631d2d
Author: Roland Dreier <roland@purestorage.com>
Date:   Mon Mar 5 10:05:28 2012 -0800


   mlx4_core: Scale size of MTT table with system RAM


   The current driver defaults to 1M MTT segments, where each segment holds
   8 MTT entries.  This limits the total memory registered to 8M * PAGE_SIZE
   which is 32GB with 4K pages.  Since systems that have much more memory
   are pretty common now (at least among systems with InfiniBand hardware),
   this limit ends up getting hit in practice quite a bit.


   Handle this by having the driver allocate at least enough MTT entries to
   cover 2 * totalram pages.


   Signed-off-by: Roland Dreier <roland@purestorage.com>
-----------------------------------------------------------


The relevant code segment (drivers/net/ethernet/mellanox/mlx4/profile.c):


-----------------------------------------------------------
       /*
        * We want to scale the number of MTTs with the size of the
        * system memory, since it makes sense to register a lot of
        * memory on a system with a lot of memory.  As a heuristic,
        * make sure we have enough MTTs to cover twice the system
        * memory (with PAGE_SIZE entries).
        *
        * This number has to be a power of two and fit into 32 bits
        * due to device limitations, so cap this at 2^31 as well.
        * That limits us to 8TB of memory registration per HCA with
        * 4KB pages, which is probably OK for the next few months.
        */
       si_meminfo(&si);
       request->num_mtt =
               roundup_pow_of_two(max_t(unsigned, request->num_mtt,
                                        min(1UL << (31 - log_mtts_per_seg),
                                            si.totalram >> (log_mtts_per_seg - 1))));
-----------------------------------------------------------


So the point here is that OpenMPI should check the mlx4 driver versions
and not output false warnings when newer drivers are used. Didn't check
whether this is fixed in the OpenMPI code repositories yet. It's not
fixed in 1.8.2rc4 anyway (static uint64_t calculate_max_reg in
ompi/mca/btl/openib/btl_openib.c). Also, the OpenMPI FAQ should be
corrected accordingly.


Rio as a note for you: You can safely ignore the warning.


Cheers,


Roland

---

