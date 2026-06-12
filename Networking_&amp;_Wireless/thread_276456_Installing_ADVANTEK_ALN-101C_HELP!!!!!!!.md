---
title: "Installing ADVANTEK ALN-101C HELP!!!!!!!"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by vzlan82 on 2006-10-12
Hello!

I installed Dapper Drake a few days ago. My network card is the Advantek ALN-101C, and I can't install the driver! I know there is a sundance driver preinstalled on the linux kernel but it won't work with this card. I've been reading a post here about that, and a few about installing it on other linux distributions but none of them have been very helpful. First, I can't even compile the driver on the cd (which is for kernel 2.4. And I can't find more actual drivers either. The result of the compilation is the following:




francisco@Francisco-desktop:~/Desktop/Linux$ make all
gcc -D__KERNEL__ -DMODULE -O -Wall -Wstrict-prototypes -I/usr/include -DUSE_IO_O PS  -D_COMPAT_WITH_OLD_KERNEL   -c -o sundance_main.o sundance_main.c
In file included from /usr/include/linux/capability.h:16,
                 from /usr/include/linux/sched.h:6,
                 from /usr/include/linux/module.h:9,
                 from sundance_main.c:168:
/usr/include/linux/types.h:4:23: error: sys/types.h: No such file or directory
In file included from /usr/include/linux/posix_types.h:47,
                 from /usr/include/linux/types.h:5,
                 from /usr/include/linux/capability.h:16,
                 from /usr/include/linux/sched.h:6,
                 from /usr/include/linux/module.h:9,
                 from sundance_main.c:168:
/usr/lib/gcc/i486-linux-gnu/4.0.3/include/asm/posix_types.h:13:22: error: featur es.h: No such file or directory
In file included from /usr/include/asm/page.h:11,
                 from /usr/include/linux/sched.h:12,
                 from /usr/include/linux/module.h:9,
                 from sundance_main.c:168:
/usr/include/asm-i386/page.h:4:20: error: unistd.h: No such file or directory
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from sundance_main.c:168:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h >. This time I will do it for you."
/usr/include/linux/signal.h:4:20: error: signal.h: No such file or directory
In file included from /usr/include/linux/module.h:9,
                 from sundance_main.c:168:
/usr/include/linux/sched.h:77:22: error: sys/time.h: No such file or directory
In file included from sundance_main.c:168:
/usr/include/linux/module.h:41: error: field â€˜attrâ€™ has incomplete type
/usr/include/linux/module.h:49: error: field â€˜kobjâ€™ has incomplete type
sundance_main.c:170:26: error: linux/string.h: No such file or directory
sundance_main.c:171:25: error: linux/timer.h: No such file or directory
sundance_main.c:174:24: error: linux/slab.h: No such file or directory
In file included from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/linux/irq.h:17:27: error: linux/cpumask.h: No such file or director y
In file included from /usr/include/asm/irq.h:11,
                 from /usr/include/linux/irq.h:19,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/asm-i386/irq.h:15:25: error: irq_vectors.h: No such file or directo ry
/usr/include/asm-i386/irq.h:16:29: error: asm/thread_info.h: No such file or dir ectory
In file included from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/linux/irq.h:47: error: syntax error before â€˜cpumask_tâ€™
/usr/include/linux/irq.h:67: error: syntax error before â€˜spinlock_tâ€™
/usr/include/linux/irq.h:68: error: â€˜CONFIG_X86_L1_CACHE_SHIFTâ€™ undeclared here (not in a function)
/usr/include/linux/irq.h:68: error: requested alignment is not a constant
/usr/include/linux/irq.h:70: error: syntax error before â€˜irq_descâ€™
/usr/include/linux/irq.h:70: error: â€˜NR_IRQSâ€™ undeclared here (not in a function )
In file included from /usr/include/asm/hw_irq.h:11,
                 from /usr/include/linux/irq.h:72,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/asm-i386/hw_irq.h:15:27: error: linux/profile.h: No such file or di rectory
/usr/include/asm-i386/hw_irq.h:18:26: error: asm/sections.h: No such file or dir ectory
In file included from /usr/include/asm/hw_irq.h:11,
                 from /usr/include/linux/irq.h:72,
                 from /usr/include/asm-i386/hardirq.h:5,
                 from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/asm-i386/hw_irq.h:27: error: â€˜NR_IRQ_VECTORSâ€™ undeclared here (not in a function)
In file included from /usr/include/asm/hardirq.h:11,
                 from /usr/include/linux/interrupt.h:9,
                 from sundance_main.c:175:
/usr/include/asm-i386/hardirq.h:12: error: requested alignment is not a constant
In file included from sundance_main.c:175:
/usr/include/linux/interrupt.h:36: error: syntax error before â€˜cpumask_tâ€™
/usr/include/linux/interrupt.h:42: error: syntax error before â€˜}â€™ token
/usr/include/linux/interrupt.h:61: error: syntax error before â€˜cliâ€™
/usr/include/linux/interrupt.h:65: error: syntax error before â€˜stiâ€™
/usr/include/linux/interrupt.h:69: error: syntax error before â€˜save_flagsâ€™
/usr/include/linux/interrupt.h: In function â€˜save_flagsâ€™:
/usr/include/linux/interrupt.h:71: error: syntax error before â€˜unsignedâ€™
/usr/include/linux/interrupt.h: At top level:
/usr/include/linux/interrupt.h:74: error: syntax error before â€˜restore_flagsâ€™
/usr/include/linux/interrupt.h: In function â€˜restore_flagsâ€™:
/usr/include/linux/interrupt.h:76: error: syntax error before â€˜unsignedâ€™
/usr/include/linux/interrupt.h: At top level:
/usr/include/linux/interrupt.h:79: error: syntax error before â€˜save_and_cliâ€™
In file included from /usr/include/linux/netdevice.h:28,
                 from sundance_main.c:177:
/usr/include/linux/if.h:22:59: error: sys/socket.h: No such file or directory
In file included from /usr/include/linux/netdevice.h:28,
                 from sundance_main.c:177:
/usr/include/linux/if.h:144: error: field â€˜ifru_addrâ€™ has incomplete type
/usr/include/linux/if.h:145: error: field â€˜ifru_dstaddrâ€™ has incomplete type
/usr/include/linux/if.h:146: error: field â€˜ifru_broadaddrâ€™ has incomplete type
/usr/include/linux/if.h:147: error: field â€˜ifru_netmaskâ€™ has incomplete type
/usr/include/linux/if.h:148: error: field â€˜ifru_hwaddrâ€™ has incomplete type
In file included from sundance_main.c:177:
/usr/include/linux/netdevice.h:33:20: error: endian.h: No such file or directory
/usr/include/linux/netdevice.h:34:22: error: byteswap.h: No such file or directo ry
sundance_main.c:178:31: error: linux/etherdevice.h: No such file or directory
In file included from sundance_main.c:179:
/usr/include/linux/skbuff.h:24:26: error: net/checksum.h: No such file or direct ory
In file included from sundance_main.c:179:
/usr/include/linux/skbuff.h:115: error: syntax error before â€˜spinlock_tâ€™
/usr/include/linux/skbuff.h:140: error: variable-size type declared outside of a ny function
sundance_main.c:181:25: error: asm/uaccess.h: No such file or directory
In file included from /usr/include/asm/processor.h:11,
                 from sundance_main.c:182:
/usr/include/asm-i386/processor.h:21:24: error: asm/percpu.h: No such file or di rectory
In file included from /usr/include/asm/processor.h:11,
                 from sundance_main.c:182:
/usr/include/asm-i386/processor.h:68: error: requested alignment is not a consta nt
/usr/include/asm-i386/processor.h:89: error: syntax error before â€˜init_tssâ€™
In file included from /usr/include/asm/io.h:11,
                 from sundance_main.c:184:
/usr/include/asm-i386/io.h:1:2: warning: #warning "You should include <sys/io.h> . This time I will do it for you."
/usr/include/asm-i386/io.h:2:20: error: sys/io.h: No such file or directory
sundance_main.c:185:25: error: linux/delay.h: No such file or directory
In file included from /usr/include/linux/spinlock.h:1,
                 from sundance_main.c:186:
/usr/include/linux/err_kernel_only.h:1:2: error: #error Kernel only header inclu ded in userspace
In file included from sundance_main.c:192:
crc32.h:34: error: syntax error before â€˜ether_crcâ€™
crc32.h:35: warning: return type defaults to â€˜intâ€™
In file included from sundance_main.c:193:
ethtool.h:18: error: syntax error before â€˜u32â€™
ethtool.h:18: warning: no semicolon at end of struct or union
ethtool.h:19: warning: type defaults to â€˜intâ€™ in declaration of â€˜supportedâ€™
ethtool.h:19: warning: data definition has no type or storage class
ethtool.h:20: error: syntax error before â€˜advertisingâ€™
ethtool.h:20: warning: type defaults to â€˜intâ€™ in declaration of â€˜advertisingâ€™
ethtool.h:20: warning: data definition has no type or storage class
ethtool.h:21: error: syntax error before â€˜speedâ€™
ethtool.h:21: warning: type defaults to â€˜intâ€™ in declaration of â€˜speedâ€™
ethtool.h:21: warning: data definition has no type or storage class
ethtool.h:22: error: syntax error before â€˜duplexâ€™
ethtool.h:22: warning: type defaults to â€˜intâ€™ in declaration of â€˜duplexâ€™
ethtool.h:22: warning: data definition has no type or storage class
ethtool.h:23: error: syntax error before â€˜portâ€™
ethtool.h:23: warning: type defaults to â€˜intâ€™ in declaration of â€˜portâ€™
ethtool.h:23: warning: data definition has no type or storage class
ethtool.h:24: error: syntax error before â€˜phy_addressâ€™
ethtool.h:24: warning: type defaults to â€˜intâ€™ in declaration of â€˜phy_addressâ€™
ethtool.h:24: warning: data definition has no type or storage class
ethtool.h:25: error: syntax error before â€˜transceiverâ€™
ethtool.h:25: warning: type defaults to â€˜intâ€™ in declaration of â€˜transceiverâ€™
ethtool.h:25: warning: data definition has no type or storage class
ethtool.h:26: error: syntax error before â€˜autonegâ€™
ethtool.h:26: warning: type defaults to â€˜intâ€™ in declaration of â€˜autonegâ€™
ethtool.h:26: warning: data definition has no type or storage class
ethtool.h:27: error: syntax error before â€˜maxtxpktâ€™
ethtool.h:27: warning: type defaults to â€˜intâ€™ in declaration of â€˜maxtxpktâ€™
ethtool.h:27: warning: data definition has no type or storage class
ethtool.h:28: error: syntax error before â€˜maxrxpktâ€™
ethtool.h:28: warning: type defaults to â€˜intâ€™ in declaration of â€˜maxrxpktâ€™
ethtool.h:28: warning: data definition has no type or storage class
ethtool.h:29: error: syntax error before â€˜reservedâ€™
ethtool.h:29: warning: type defaults to â€˜intâ€™ in declaration of â€˜reservedâ€™
ethtool.h:29: warning: data definition has no type or storage class
ethtool.h:30: error: syntax error before â€˜}â€™ token
ethtool.h:35: error: syntax error before â€˜u32â€™
ethtool.h:35: warning: no semicolon at end of struct or union
ethtool.h:43: error: syntax error before â€˜testinfo_lenâ€™
ethtool.h:43: warning: type defaults to â€˜intâ€™ in declaration of â€˜testinfo_lenâ€™
ethtool.h:43: warning: data definition has no type or storage class
ethtool.h:44: error: syntax error before â€˜eedump_lenâ€™
ethtool.h:44: warning: type defaults to â€˜intâ€™ in declaration of â€˜eedump_lenâ€™
ethtool.h:44: warning: data definition has no type or storage class
ethtool.h:45: error: syntax error before â€˜regdump_lenâ€™
ethtool.h:45: warning: type defaults to â€˜intâ€™ in declaration of â€˜regdump_lenâ€™
ethtool.h:45: warning: data definition has no type or storage class
ethtool.h:51: error: syntax error before â€˜u32â€™
ethtool.h:51: warning: no semicolon at end of struct or union
ethtool.h:52: warning: type defaults to â€˜intâ€™ in declaration of â€˜supportedâ€™
ethtool.h:52: warning: data definition has no type or storage class
ethtool.h:53: error: syntax error before â€˜woloptsâ€™
ethtool.h:53: warning: type defaults to â€˜intâ€™ in declaration of â€˜woloptsâ€™
ethtool.h:53: warning: data definition has no type or storage class
ethtool.h:54: error: syntax error before â€˜sopassâ€™
ethtool.h:54: warning: type defaults to â€˜intâ€™ in declaration of â€˜sopassâ€™
ethtool.h:54: warning: data definition has no type or storage class
ethtool.h:55: error: syntax error before â€˜}â€™ token
ethtool.h:59: error: syntax error before â€˜u32â€™
ethtool.h:59: warning: no semicolon at end of struct or union
ethtool.h:60: warning: type defaults to â€˜intâ€™ in declaration of â€˜dataâ€™
ethtool.h:60: warning: data definition has no type or storage class
ethtool.h:65: error: syntax error before â€˜u32â€™
ethtool.h:65: warning: no semicolon at end of struct or union
ethtool.h:66: warning: type defaults to â€˜intâ€™ in declaration of â€˜versionâ€™
ethtool.h:66: error: conflicting types for â€˜versionâ€™
ethtool.h:37: error: previous declaration of â€˜versionâ€™ was here
ethtool.h:66: warning: data definition has no type or storage class
ethtool.h:67: error: syntax error before â€˜lenâ€™
ethtool.h:67: warning: type defaults to â€˜intâ€™ in declaration of â€˜lenâ€™
ethtool.h:67: warning: data definition has no type or storage class
ethtool.h:68: error: syntax error before â€˜dataâ€™
ethtool.h:68: warning: type defaults to â€˜intâ€™ in declaration of â€˜dataâ€™
ethtool.h:68: error: conflicting types for â€˜dataâ€™
ethtool.h:60: error: previous declaration of â€˜dataâ€™ was here
ethtool.h:68: warning: data definition has no type or storage class
ethtool.h:69: error: syntax error before â€˜}â€™ token
ethtool.h:73: error: syntax error before â€˜u32â€™
ethtool.h:73: warning: no semicolon at end of struct or union
ethtool.h:74: warning: type defaults to â€˜intâ€™ in declaration of â€˜magicâ€™
ethtool.h:74: warning: data definition has no type or storage class
ethtool.h:75: error: syntax error before â€˜offsetâ€™
ethtool.h:75: warning: type defaults to â€˜intâ€™ in declaration of â€˜offsetâ€™
ethtool.h:75: warning: data definition has no type or storage class
ethtool.h:76: error: syntax error before â€˜lenâ€™
ethtool.h:76: warning: type defaults to â€˜intâ€™ in declaration of â€˜lenâ€™
ethtool.h:76: warning: data definition has no type or storage class
ethtool.h:77: error: syntax error before â€˜dataâ€™
ethtool.h:77: warning: type defaults to â€˜intâ€™ in declaration of â€˜dataâ€™
ethtool.h:77: error: conflicting types for â€˜dataâ€™
ethtool.h:60: error: previous declaration of â€˜dataâ€™ was here
ethtool.h:77: warning: data definition has no type or storage class
ethtool.h:78: error: syntax error before â€˜}â€™ token
ethtool.h:82: error: syntax error before â€˜u32â€™
ethtool.h:82: warning: no semicolon at end of struct or union
ethtool.h:88: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_coalesce_use csâ€™
ethtool.h:88: warning: data definition has no type or storage class
ethtool.h:96: error: syntax error before â€˜rx_max_coalesced_framesâ€™
ethtool.h:96: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_max_coalesce d_framesâ€™
ethtool.h:96: warning: data definition has no type or storage class
ethtool.h:103: error: syntax error before â€˜rx_coalesce_usecs_irqâ€™
ethtool.h:103: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_coalesce_us ecs_irqâ€™
ethtool.h:103: warning: data definition has no type or storage class
ethtool.h:104: error: syntax error before â€˜rx_max_coalesced_frames_irqâ€™
ethtool.h:104: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_max_coalesc ed_frames_irqâ€™
ethtool.h:104: warning: data definition has no type or storage class
ethtool.h:110: error: syntax error before â€˜tx_coalesce_usecsâ€™
ethtool.h:110: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_coalesce_us ecsâ€™
ethtool.h:110: warning: data definition has no type or storage class
ethtool.h:118: error: syntax error before â€˜tx_max_coalesced_framesâ€™
ethtool.h:118: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_max_coalesc ed_framesâ€™
ethtool.h:118: warning: data definition has no type or storage class
ethtool.h:125: error: syntax error before â€˜tx_coalesce_usecs_irqâ€™
ethtool.h:125: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_coalesce_us ecs_irqâ€™
ethtool.h:125: warning: data definition has no type or storage class
ethtool.h:126: error: syntax error before â€˜tx_max_coalesced_frames_irqâ€™
ethtool.h:126: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_max_coalesc ed_frames_irqâ€™
ethtool.h:126: warning: data definition has no type or storage class
ethtool.h:133: error: syntax error before â€˜stats_block_coalesce_usecsâ€™
ethtool.h:133: warning: type defaults to â€˜intâ€™ in declaration of â€˜stats_block_co alesce_usecsâ€™
ethtool.h:133: warning: data definition has no type or storage class
ethtool.h:142: error: syntax error before â€˜use_adaptive_rx_coalesceâ€™
ethtool.h:142: warning: type defaults to â€˜intâ€™ in declaration of â€˜use_adaptive_r x_coalesceâ€™
ethtool.h:142: warning: data definition has no type or storage class
ethtool.h:143: error: syntax error before â€˜use_adaptive_tx_coalesceâ€™
ethtool.h:143: warning: type defaults to â€˜intâ€™ in declaration of â€˜use_adaptive_t x_coalesceâ€™
ethtool.h:143: warning: data definition has no type or storage class
ethtool.h:149: error: syntax error before â€˜pkt_rate_lowâ€™
ethtool.h:149: warning: type defaults to â€˜intâ€™ in declaration of â€˜pkt_rate_lowâ€™
ethtool.h:149: warning: data definition has no type or storage class
ethtool.h:150: error: syntax error before â€˜rx_coalesce_usecs_lowâ€™
ethtool.h:150: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_coalesce_us ecs_lowâ€™
ethtool.h:150: warning: data definition has no type or storage class
ethtool.h:151: error: syntax error before â€˜rx_max_coalesced_frames_lowâ€™
ethtool.h:151: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_max_coalesc ed_frames_lowâ€™
ethtool.h:151: warning: data definition has no type or storage class
ethtool.h:152: error: syntax error before â€˜tx_coalesce_usecs_lowâ€™
ethtool.h:152: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_coalesce_us ecs_lowâ€™
ethtool.h:152: warning: data definition has no type or storage class
ethtool.h:153: error: syntax error before â€˜tx_max_coalesced_frames_lowâ€™
ethtool.h:153: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_max_coalesc ed_frames_lowâ€™
ethtool.h:153: warning: data definition has no type or storage class
ethtool.h:164: error: syntax error before â€˜pkt_rate_highâ€™
ethtool.h:164: warning: type defaults to â€˜intâ€™ in declaration of â€˜pkt_rate_highâ€™
ethtool.h:164: warning: data definition has no type or storage class
ethtool.h:165: error: syntax error before â€˜rx_coalesce_usecs_highâ€™
ethtool.h:165: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_coalesce_us ecs_highâ€™
ethtool.h:165: warning: data definition has no type or storage class
ethtool.h:166: error: syntax error before â€˜rx_max_coalesced_frames_highâ€™
ethtool.h:166: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_max_coalesc ed_frames_highâ€™
ethtool.h:166: warning: data definition has no type or storage class
ethtool.h:167: error: syntax error before â€˜tx_coalesce_usecs_highâ€™
ethtool.h:167: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_coalesce_us ecs_highâ€™
ethtool.h:167: warning: data definition has no type or storage class
ethtool.h:168: error: syntax error before â€˜tx_max_coalesced_frames_highâ€™
ethtool.h:168: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_max_coalesc ed_frames_highâ€™
ethtool.h:168: warning: data definition has no type or storage class
ethtool.h:173: error: syntax error before â€˜rate_sample_intervalâ€™
ethtool.h:173: warning: type defaults to â€˜intâ€™ in declaration of â€˜rate_sample_in tervalâ€™
ethtool.h:173: warning: data definition has no type or storage class
ethtool.h:178: error: syntax error before â€˜u32â€™
ethtool.h:178: warning: no semicolon at end of struct or union
ethtool.h:184: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_max_pending â€™
ethtool.h:184: warning: data definition has no type or storage class
ethtool.h:185: error: syntax error before â€˜rx_mini_max_pendingâ€™
ethtool.h:185: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_mini_max_pe ndingâ€™
ethtool.h:185: warning: data definition has no type or storage class
ethtool.h:186: error: syntax error before â€˜rx_jumbo_max_pendingâ€™
ethtool.h:186: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_jumbo_max_p endingâ€™
ethtool.h:186: warning: data definition has no type or storage class
ethtool.h:187: error: syntax error before â€˜tx_max_pendingâ€™
ethtool.h:187: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_max_pending â€™
ethtool.h:187: warning: data definition has no type or storage class
ethtool.h:192: error: syntax error before â€˜rx_pendingâ€™
ethtool.h:192: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_pendingâ€™
ethtool.h:192: warning: data definition has no type or storage class
ethtool.h:193: error: syntax error before â€˜rx_mini_pendingâ€™
ethtool.h:193: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_mini_pendin gâ€™
ethtool.h:193: warning: data definition has no type or storage class
ethtool.h:194: error: syntax error before â€˜rx_jumbo_pendingâ€™
ethtool.h:194: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_jumbo_pendi ngâ€™
ethtool.h:194: warning: data definition has no type or storage class
ethtool.h:195: error: syntax error before â€˜tx_pendingâ€™
ethtool.h:195: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_pendingâ€™
ethtool.h:195: warning: data definition has no type or storage class
ethtool.h:200: error: syntax error before â€˜u32â€™
ethtool.h:200: warning: no semicolon at end of struct or union
ethtool.h:212: warning: type defaults to â€˜intâ€™ in declaration of â€˜autonegâ€™
ethtool.h:212: warning: data definition has no type or storage class
ethtool.h:213: error: syntax error before â€˜rx_pauseâ€™
ethtool.h:213: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_pauseâ€™
ethtool.h:213: warning: data definition has no type or storage class
ethtool.h:214: error: syntax error before â€˜tx_pauseâ€™
ethtool.h:214: warning: type defaults to â€˜intâ€™ in declaration of â€˜tx_pauseâ€™
ethtool.h:214: warning: data definition has no type or storage class
ethtool.h:225: error: syntax error before â€˜u32â€™
ethtool.h:225: warning: no semicolon at end of struct or union
ethtool.h:226: warning: type defaults to â€˜intâ€™ in declaration of â€˜string_setâ€™
ethtool.h:226: warning: data definition has no type or storage class
ethtool.h:227: error: syntax error before â€˜lenâ€™
ethtool.h:227: warning: type defaults to â€˜intâ€™ in declaration of â€˜lenâ€™
ethtool.h:227: warning: data definition has no type or storage class
ethtool.h:228: error: syntax error before â€˜dataâ€™
ethtool.h:228: warning: type defaults to â€˜intâ€™ in declaration of â€˜dataâ€™
ethtool.h:228: error: conflicting types for â€˜dataâ€™
ethtool.h:60: error: previous declaration of â€˜dataâ€™ was here
ethtool.h:228: warning: data definition has no type or storage class
ethtool.h:229: error: syntax error before â€˜}â€™ token
ethtool.h:238: error: syntax error before â€˜u32â€™
ethtool.h:238: warning: no semicolon at end of struct or union
ethtool.h:239: warning: type defaults to â€˜intâ€™ in declaration of â€˜flagsâ€™
ethtool.h:239: warning: data definition has no type or storage class
ethtool.h:240: error: syntax error before â€˜reservedâ€™
ethtool.h:240: warning: type defaults to â€˜intâ€™ in declaration of â€˜reservedâ€™
ethtool.h:240: error: conflicting types for â€˜reservedâ€™
ethtool.h:29: error: previous declaration of â€˜reservedâ€™ was here
ethtool.h:240: warning: data definition has no type or storage class
ethtool.h:241: error: syntax error before â€˜lenâ€™
ethtool.h:241: warning: type defaults to â€˜intâ€™ in declaration of â€˜lenâ€™
ethtool.h:241: warning: data definition has no type or storage class
ethtool.h:242: error: syntax error before â€˜dataâ€™
ethtool.h:242: warning: type defaults to â€˜intâ€™ in declaration of â€˜dataâ€™
ethtool.h:242: error: conflicting types for â€˜dataâ€™
ethtool.h:60: error: previous declaration of â€˜dataâ€™ was here
ethtool.h:242: warning: data definition has no type or storage class
ethtool.h:243: error: syntax error before â€˜}â€™ token
In file included from sundance_main.c:194:
mii.h:140: error: syntax error before â€˜u16â€™
mii.h:140: warning: no semicolon at end of struct or union
mii.h:141: warning: type defaults to â€˜intâ€™ in declaration of â€˜reg_numâ€™
mii.h:141: warning: data definition has no type or storage class
mii.h:142: error: syntax error before â€˜val_inâ€™
mii.h:142: warning: type defaults to â€˜intâ€™ in declaration of â€˜val_inâ€™
mii.h:142: warning: data definition has no type or storage class
mii.h:143: error: syntax error before â€˜val_outâ€™
mii.h:143: warning: type defaults to â€˜intâ€™ in declaration of â€˜val_outâ€™
mii.h:143: warning: data definition has no type or storage class
sundance_main.c:199: error: conflicting types for â€˜versionâ€™
ethtool.h:66: error: previous declaration of â€˜versionâ€™ was here
sundance_main.c:201: error: â€˜KERN_INFOâ€™ undeclared here (not in a function)
sundance_main.c:201: error: syntax error before string constant
sundance_main.c:295: error: array type has incomplete element type
sundance_main.c:300: error: â€˜PCI_ANY_IDâ€™ undeclared here (not in a function)
sundance_main.c:447: error: syntax error before â€˜u32â€™
sundance_main.c:447: warning: no semicolon at end of struct or union
sundance_main.c:448: warning: type defaults to â€˜intâ€™ in declaration of â€˜statusâ€™
sundance_main.c:448: warning: data definition has no type or storage class
sundance_main.c:449: error: syntax error before â€˜u32â€™
sundance_main.c:449: warning: no semicolon at end of struct or union
sundance_main.c:449: warning: type defaults to â€˜intâ€™ in declaration of â€˜fragâ€™
sundance_main.c:449: warning: data definition has no type or storage class
sundance_main.c:450: error: syntax error before â€˜}â€™ token
sundance_main.c:473: error: syntax error before â€˜dma_addr_tâ€™
sundance_main.c:473: warning: no semicolon at end of struct or union
sundance_main.c:474: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_ring_ dmaâ€™
sundance_main.c:474: warning: data definition has no type or storage class
sundance_main.c:478: error: syntax error before â€˜lockâ€™
sundance_main.c:478: warning: type defaults to â€˜intâ€™ in declaration of â€˜lockâ€™
sundance_main.c:478: warning: data definition has no type or storage class
sundance_main.c:479: error: syntax error before â€˜rx_lockâ€™
sundance_main.c:479: warning: type defaults to â€˜intâ€™ in declaration of â€˜rx_lockâ€™
sundance_main.c:479: warning: data definition has no type or storage class
sundance_main.c:487: error: syntax error before â€˜:â€™ token
sundance_main.c:488: error: syntax error before â€˜:â€™ token
sundance_main.c:489: error: syntax error before â€˜:â€™ token
sundance_main.c:490: error: conflicting types for â€˜speedâ€™
ethtool.h:21: error: previous declaration of â€˜speedâ€™ was here
sundance_main.c:496: error: syntax error before â€˜mcastlockâ€™
sundance_main.c:496: warning: type defaults to â€˜intâ€™ in declaration of â€˜mcastloc kâ€™




and a few more hundreds error lines 
I'm attaching the drivers here that were on the CD. Can anyone help me, please??? I really don't know what to do! 

Thanks!!!

---

