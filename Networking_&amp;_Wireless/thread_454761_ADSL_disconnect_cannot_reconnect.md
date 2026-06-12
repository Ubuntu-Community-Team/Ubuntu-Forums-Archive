---
title: "ADSL disconnect cannot reconnect"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by mart_in_brasil on 2007-05-25
Hi,

My ADSL sometimes disconnects; and I cannot reconnect unless I reboot.

Is there an obvious thing I should do?
Is there a way of getting more details from the connection routine as it tries to connect to identify the problem?

Some details:
I recently (last weekend) installed Ubuntu 6.06 LTS (Dapper) {because I had the CD}
{Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue Mar 13 20:49:31 UTC 2007}
I configured ADSL using the pppoe-conf accepting all the defaults.
My service is from Telefonica - 'Speedy' and the provider is Terra {this is São Paulo - Brasil}

I have tried:
adsl-stop/adsl-start but that does not seem to do anything
There is nothing 'unusual' in the system message log

My Modem is
Speedtouch 510 connected by ethernet to eth0

Thank you for your help 

Martin

lots of PC details ...

My PC is 
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Athlon(tm) XP 2000+
stepping        : 1
cpu MHz         : 1659.901
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 3321.19

AMD Athlon XP 2000+ 1.7GHz 256Kb 
512MB memory
MemTotal:       515936 kB
MemFree:        122732 kB
Buffers:          9684 kB
Cached:         188636 kB
SwapCached:          0 kB
Active:         234160 kB
Inactive:       125776 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515936 kB
LowFree:        122732 kB
SwapTotal:     2377612 kB
SwapFree:      2377612 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:         211636 kB
Slab:            16724 kB
CommitLimit:   2635580 kB
Committed_AS:   440292 kB
PageTables:       1756 kB
VmallocTotal:   507896 kB
VmallocUsed:      8652 kB
VmallocChunk:   498164 kB

Swap
/dev/hda3                               partition       2377612 0       -1

Partitions
major minor  #blocks  name

   3     0   39082680 hda
   3     1   20972826 hda1
   3     2   15727635 hda2
   3     3    2377620 hda3
  22     0   78150744 hdc
  22     1   78148161 hdc1
 253     0   20972826 dm-0
 253     1   15727635 dm-1
 253     2    2377620 dm-2
 253     3   78148161 dm-3

---

### Post by mart_in_brasil on 2007-05-26
Sorry I know the answer ...

I need to type "pon dsl-provider" not just "pon"!

I still do not know why if disconnects.
Possibly something to do with the Speed Touch 510 router.

Martin

---

