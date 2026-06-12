---
title: "CPU usage is a 100%, no processes running"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by stressmonkey on 2010-07-05
My CPU usage suddenly started oscillating between 5% and 100% causing the computer to lag very badly. This problem came on suddenly--I was using the computer the night before and then the next day I was hit with the lag.

Computer info:

IBM Lenovo ThinkpadR61 with Ubuntu 10.04 Lucid Lynx
Intel Duo Core 2GHz Processor T7300
2.5GB RAM (2GB Kingston DDR2 + 512MB DDR2 not sure what brand)
Intel Graphics Media Accelerator X3100
Intel 802.11abg wireless

everything was working perfectly until the CPU usage started to spike. It's very strange, spiking every few seconds.

Here is a picture of the System Monitor and htop output:

[http://picasaweb.google.com/lh/photo/WhrjEXVlDFdWhU0rg0hDUg?feat=directlink]("http://picasaweb.google.com/lh/photo/WhrjEXVlDFdWhU0rg0hDUg?feat=directlink")

[http://picasaweb.google.com/malikb33/SystemMonitor#]("http://picasaweb.google.com/malikb33/SystemMonitor#")

so what I did was do a clean install of Lucid and update the BIOS, but the problem is still there.

I had been running the computer with just one processor turned on, but because the lag is so much from the CPU usage, I turned on the other processor. 

Here are pictures of the system monitor and htop with clean install of Lynx and updated BIOS:

[http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink]("http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink")

[http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink]("http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink")

any ideas of what the problem could be?!?!

---

### Post by -humanaut- on 2010-07-05
When your in system monitor hit view all processes and then hit CPU so the arrow is pointed down that should show you the culprit you could also use the top command from the terminal.

---

### Post by stressmonkey on 2010-07-05
in the htop picutures I posted, the processes are sorted by CPU usage. 

here is a repost:

[http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink]("http://picasaweb.google.com/lh/photo/HrOu3iBanXuEM7B1YQkbrg?feat=directlink")


if you look at the htop picture, you can see I have it sorted by CPU usage. Use the magnify feature if the picture is to small to see clearly.

---

### Post by stressmonkey on 2010-07-05
it's a strange problem, the CPU usage should only total 20% if you added the usage of the processes listed in htop, but as you can see in the picture there is 93.5% in one processor and 28.1% in the other. 

if you look at the system monitor picture:


[http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink]("http://picasaweb.google.com/lh/photo/H21jRccJ42oST5-NUibhug?feat=directlink")


you can see how they fluctuate every few seconds. It's so crazy, I have no idea what is wrong with my computer!! 


Please let me know if you need any additional information!

---

### Post by -humanaut- on 2010-07-05
Do you have your system overclocked or anything? It looks really unstable I would try underclocking it a little bit if its not O.Ced Also power supply could be an issue thats knowin to cause spikes in cpu's. Oh yeah did you add extra ram to it? If so it could be the power to the ram is causing a drop-off in the power to the cpu.

---

### Post by stressmonkey on 2010-07-05
The computer is not overclocked--I don't know how to do that...

I did add extra RAM, an upgrade from 1gb (two 512mb sticks) to 2.5gb (2gb + 512mb), but the computer was stable for about 4 months until the CPU spiking started.

I will call in to IBM and see if they can tell me anything about the power supply and if it has gone bad.

---

### Post by CharlesA on 2010-07-05
Take out that stick of 512 and see what happens.

---

### Post by -humanaut- on 2010-07-05
I'd take out the extra ram you put in. It's could be a bad stick of ram or the system simple can't handle the extra power consumption.

---

### Post by vagrale13 on 2010-07-05
Can you post result of
```
lspci -nn
sudo lshw -C cpu
uname -a
ps aux > prg.txt
```and post the content of the archive **prg.txt** where create to your */home/user* folder

---

### Post by stressmonkey on 2010-07-05
[FONT=Arial][SIZE=2]ok we might be on to something, I took out the 512mb stick and the system seemed to calm down. Here are the htop and system monitor photos with 512mb taken out:

[/SIZE][/FONT][http://picasaweb.google.com/lh/photo/j2dJrkbay_nZ3JpvN4zPTw?feat=directlink](http://picasaweb.google.com/lh/photo/j2dJrkbay_nZ3JpvN4zPTw?feat=directlink)

[http://picasaweb.google.com/lh/photo/9VsQLmBtLGX502Lwu5GxOQ?feat=directlink](http://picasaweb.google.com/lh/photo/9VsQLmBtLGX502Lwu5GxOQ?feat=directlink)
[FONT=Arial][SIZE=2]

here is what I got when I copy pasted 

[/SIZE][/FONT][FONT=Courier New][SIZE=2]lspci -nn
sudo lshw -C cpu
uname -a
ps aux > prg.txt[/SIZE][/FONT][FONT=Arial][SIZE=2]
into terminal.

wobis@wobis-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MC Gigabit Network Connection [8086:104d] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
wobis@wobis-laptop:~$ sudo lshw -C cpu
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 6
       bus info: cpu@0
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       slot: None
       size: 2001MHz
       capacity: 2001MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       size: 800MHz
       capacity: 800MHz
       capabilities: vmx ht cpufreq
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          capabilities: logical
wobis@wobis-laptop:~$ uname -a
Linux wobis-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
wobis@wobis-laptop:~$ ps aux > prg.txt^C
wobis@wobis-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MC Gigabit Network Connection [8086:104d] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b6)
wobis@wobis-laptop:~$ sudo lshw -C cpu
  *-cpu:0                 
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz
       vendor: Intel Corp.
       physical id: 6
       bus info: cpu@0
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       slot: None
       size: 2001MHz
       capacity: 2001MHz
       width: 64 bits
       clock: 200MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 64 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 64 bits
          capabilities: logical
  *-cpu:1
       physical id: 1
       bus info: cpu@1
       version: 6.15.11
       serial: 0000-06FB-0000-0000-0000-0000
       size: 800MHz
       capacity: 800MHz
       capabilities: vmx ht cpufreq
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          capabilities: logical
wobis@wobis-laptop:~$ uname -a
Linux wobis-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
wobis@wobis-laptop:~$ ps aux > prg.txt


-------------------------------------------------------



I tried talking to IBM support but my warranty is expired and they were of no help.

Do you think that the 512mb stick of RAM was the problem?  Someone also send me this bug report:

[/SIZE][/FONT][FONT=Arial][SIZE=2][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396)


where people are mentioning what seems to be a very similar problem that I had[/SIZE][/FONT].

---

### Post by stressmonkey on 2010-07-05
[FONT=Arial][SIZE=2]sorry [vagrale13]("http://ubuntuforums.org/member.php?u=952139"), I did not notice your comment to post the .txt file until after I made my reply.  Here is the txt file:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2772  1616 ?        Ss   14:32   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    14:32   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    14:32   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    14:32   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    14:32   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    14:32   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    14:32   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    14:32   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    14:32   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    14:32   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    14:32   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    14:32   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    14:32   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    14:32   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    14:32   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    14:32   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    14:32   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    14:32   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    14:32   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    14:32   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    14:32   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    14:32   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    14:32   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    14:32   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    14:32   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    14:32   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    14:32   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    14:32   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    14:32   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    14:32   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    14:32   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    14:32   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    14:32   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   14:32   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    14:32   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    14:32   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    14:32   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    14:32   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    14:32   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    14:32   0:00 [pciehpd]
root        54  0.0  0.0      0     0 ?        S    14:32   0:00 [scsi_eh_0]
root        55  0.0  0.0      0     0 ?        S    14:32   0:00 [scsi_eh_1]
root        56  0.0  0.0      0     0 ?        S    14:32   0:00 [kstriped]
root        57  0.0  0.0      0     0 ?        S    14:32   0:00 [kmpathd/0]
root        58  0.0  0.0      0     0 ?        S    14:32   0:00 [kmpathd/1]
root        59  0.0  0.0      0     0 ?        S    14:32   0:00 [kmpath_handlerd]
root        60  0.0  0.0      0     0 ?        S    14:32   0:00 [ksnapd]
root        61  0.0  0.0      0     0 ?        S    14:32   0:00 [kondemand/0]
root        62  0.0  0.0      0     0 ?        S    14:32   0:00 [kondemand/1]
root        63  0.0  0.0      0     0 ?        S    14:32   0:00 [kconservative/0]
root        64  0.0  0.0      0     0 ?        S    14:32   0:00 [kconservative/1]
root       313  0.0  0.0      0     0 ?        S    14:32   0:00 [jbd2/sda1-8]
root       314  0.0  0.0      0     0 ?        S    14:32   0:00 [ext4-dio-unwrit]
root       315  0.0  0.0      0     0 ?        S    14:32   0:00 [ext4-dio-unwrit]
root       348  0.0  0.0      0     0 ?        S    14:32   0:00 [flush-8:0]
root       374  0.0  0.0   2312   924 ?        S    14:32   0:00 upstart-udev-bridge --daemon
root       377  0.0  0.0   2552   976 ?        S<s  14:32   0:00 udevd --daemon
root       625  0.0  0.0      0     0 ?        S    14:32   0:00 [kpsmoused]
root       629  0.0  0.0      0     0 ?        S    14:32   0:00 [bluetooth]
root       645  0.0  0.0      0     0 ?        S    14:32   0:00 [i915]
root       671  0.0  0.0      0     0 ?        S    14:32   0:00 [pccardd]
root       672  0.0  0.0      0     0 ?        S    14:32   0:00 [iwl3945]
root       673  0.0  0.0      0     0 ?        S    14:32   0:00 [phy0]
root       706  0.0  0.0      0     0 ?        S    14:32   0:00 [ktpacpid]
syslog     770  0.0  0.0  34572  1544 ?        Sl   14:32   0:00 rsyslogd -c4
root       844  0.0  0.0      0     0 ?        S    14:32   0:00 [hd-audio0]
root       846  0.0  0.0   1788   560 tty4     Ss+  14:32   0:00 /sbin/getty -8 38400 tty4
root       850  0.0  0.0   1788   568 tty5     Ss+  14:32   0:00 /sbin/getty -8 38400 tty5
root       857  0.0  0.0   1788   564 tty2     Ss+  14:32   0:00 /sbin/getty -8 38400 tty2
root       858  0.0  0.0   1788   564 tty3     Ss+  14:32   0:00 /sbin/getty -8 38400 tty3
root       862  0.0  0.0   1788   564 tty6     Ss+  14:32   0:00 /sbin/getty -8 38400 tty6
root       865  0.0  0.0   2044   892 ?        Ss   14:32   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       894  0.0  0.0   2372   904 ?        Ss   14:32   0:00 cron
daemon     895  0.0  0.0   2244   428 ?        Ss   14:32   0:00 atd
102        896  0.0  0.0   3240  1584 ?        Ss   14:32   0:00 dbus-daemon --system --fork
root       898  0.0  0.0   4048  1880 ?        S<s  14:32   0:00 /usr/sbin/bluetoothd --udev
root       906  0.0  0.2  18996  4124 ?        Ssl  14:32   0:00 NetworkManager
root       908  0.0  0.1  18776  3256 ?        Ssl  14:32   0:00 gdm-binary
avahi      912  0.0  0.0   2924  1536 ?        S    14:32   0:00 avahi-daemon: running [wobis-laptop.local]
avahi      913  0.0  0.0   2924   548 ?        Ss   14:32   0:00 avahi-daemon: chroot helper
root       915  0.0  0.1   4164  2308 ?        S    14:32   0:00 /usr/sbin/modem-manager
root       945  0.0  0.0      0     0 ?        S<   14:32   0:00 [krfcommd]
root       961  0.0  0.1  20584  3248 ?        Sl   14:32   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1026  0.0  0.1  20496  3780 ?        Sl   14:32   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root      1038  0.0  0.1   6696  2532 ?        Ss   14:32   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1043  0.0  0.1   4824  2360 ?        S    14:32   0:00 /sbin/wpa_supplicant -u -s
root      1103 13.9  1.4  55852 29740 tty7     Ds+  14:32   2:13 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-Eozz2h/database -nolisten tcp vt7
root      1150  0.0  0.0   1788   564 tty1     Ss+  14:32   0:00 /sbin/getty -8 38400 tty1
gdm       1170  0.0  0.0   3380   776 ?        S    14:32   0:00 /usr/bin/dbus-launch --exit-with-session
root      1190  0.0  0.1   5560  2944 ?        S    14:32   0:00 /usr/lib/upower/upowerd
rtkit     1193  0.0  0.0  22904  1212 ?        SNl  14:32   0:00 /usr/lib/rtkit/rtkit-daemon
root      1197  0.0  0.1   6424  3912 ?        S    14:32   0:00 /usr/lib/policykit-1/polkitd
gdm       1242  0.0  0.1  17248  3748 ?        Ss   14:32   0:00 /usr/bin/gnome-screensaver
root      1257  0.0  0.1  18808  3060 ?        Sl   14:33   0:00 /usr/lib/gdm/gdm-session-worker
wobis     1263  0.0  0.1  23980  2464 ?        Sl   14:33   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
wobis     1281  0.0  0.3  25892  6748 ?        Ssl  14:33   0:00 gnome-session
wobis     1315  0.0  0.0   3280   356 ?        Ss   14:33   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
wobis     1318  0.0  0.0   3380   772 ?        S    14:33   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
wobis     1319  0.0  0.0   3320  1484 ?        Ss   14:33   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
wobis     1322  0.0  0.2   7584  4320 ?        S    14:33   0:00 /usr/lib/libgconf2-4/gconfd-2
wobis     1329  0.0  0.4  88976  9192 ?        Ss   14:33   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
wobis     1331  0.0  0.1   6508  2312 ?        S    14:33   0:00 /usr/lib/gvfs/gvfsd
wobis     1336  0.0  0.1  30276  2656 ?        Ssl  14:33   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/wobis/.gvfs
wobis     1342  0.0  0.4  35048  9760 ?        S    14:33   0:00 bluetooth-applet
wobis     1343  0.1  0.6  54264 13660 ?        S    14:33   0:01 nm-applet --sm-disable
wobis     1346  0.0  0.2  94280  4688 ?        S<sl 14:33   0:00 /usr/bin/pulseaudio --start --log-target=syslog
wobis     1347  0.0  0.4  35736  9852 ?        S    14:33   0:00 gnome-power-manager
wobis     1348  1.1  1.2  85876 25924 ?        R    14:33   0:11 /usr/bin/compiz
wobis     1349  0.0  0.9  89008 19168 ?        S    14:33   0:00 nautilus
wobis     1351  0.4  0.8  44520 17012 ?        S    14:33   0:04 gnome-panel
wobis     1352  0.0  0.2  18528  6100 ?        S    14:33   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
wobis     1371  0.0  0.1  10748  2988 ?        S    14:33   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
wobis     1374  0.0  0.1  17792  2944 ?        Ss   14:33   0:00 /usr/bin/gnome-screensaver
wobis     1377  0.0  0.0   1828   516 ?        Ss   14:33   0:00 /bin/sh -c /usr/bin/compiz-decorator
wobis     1378  0.0  0.1   6820  3008 ?        S    14:33   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
wobis     1379  0.0  0.4  20376  9832 ?        S    14:33   0:00 /usr/bin/gtk-window-decorator
wobis     1382  0.0  0.0   3816  1072 ?        S    14:33   0:00 syndaemon -i 0.5 -k
wobis     1384  0.0  0.1   7756  3208 ?        S    14:33   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1386  0.0  0.1  15632  3044 ?        Sl   14:33   0:00 /usr/lib/udisks/udisks-daemon
root      1387  0.0  0.0   5176   880 ?        S    14:33   0:00 udisks-daemon: polling /dev/sr0
wobis     1389  0.0  0.1  41932  3568 ?        Ssl  14:33   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
wobis     1392  0.0  0.1   7256  2392 ?        S    14:33   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
wobis     1394  0.0  0.1  16948  2360 ?        Sl   14:33   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
wobis     1405  0.2  0.6  40616 13260 ?        S    14:33   0:02 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
wobis     1406  0.0  0.5  39212 11080 ?        S    14:33   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=24
wobis     1411  0.0  0.6  49616 13004 ?        Sl   14:33   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=21
wobis     1412  0.0  0.6  32060 13392 ?        S    14:33   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=30
wobis     1414  0.0  0.6  49536 12636 ?        S    14:33   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=36
wobis     1417  0.0  0.4  23116  9028 ?        S    14:33   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=42
wobis     1422  0.0  0.0   6180  1968 ?        S    14:33   0:00 /usr/lib/gvfs/gvfsd-metadata
wobis     1423  0.0  0.2  24300  4280 ?        S    14:33   0:00 /usr/lib/indicator-application/indicator-application-service
wobis     1427  0.0  0.2  18840  4900 ?        S    14:33   0:00 /usr/lib/indicator-me/indicator-me-service
wobis     1428  0.0  0.2  17500  4328 ?        S    14:33   0:00 /usr/lib/indicator-messages/indicator-messages-service
wobis     1432  0.0  0.2  18100  4792 ?        S    14:33   0:00 /usr/lib/indicator-session/indicator-session-service
wobis     1433  0.0  0.2  85072  4564 ?        S    14:33   0:00 /usr/lib/indicator-sound/indicator-sound-service
wobis     1436  0.0  0.1   6376  2396 ?        S    14:33   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
wobis     1438  0.1  0.5  37220 12060 ?        S    14:33   0:01 /usr/lib/notify-osd/notify-osd
wobis     1446  0.0  0.6  38504 12920 ?        S    14:33   0:00 palimpsest
wobis     1447  0.0  0.3  18912  7196 ?        S    14:33   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
wobis     1450  0.4  0.6  47516 13812 ?        Sl   14:33   0:03 gnome-terminal
wobis     1451  0.0  0.0   1984   716 ?        S    14:33   0:00 gnome-pty-helper
wobis     1452  0.0  0.1   5792  3176 pts/0    Ss   14:33   0:00 bash
wobis     1469  1.7  0.0   2648  1356 pts/0    S+   14:33   0:15 htop
wobis     1470  0.0  0.7  31464 15224 ?        S    14:33   0:00 python /usr/share/system-config-printer/applet.py
wobis     1471  0.0  0.5  34612 10992 ?        Sl   14:33   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
wobis     1484  0.0  0.5  36936 11556 ?        S    14:34   0:00 update-notifier
wobis     1534  0.0  0.0   1828   560 ?        S    14:34   0:00 /bin/sh /usr/lib/firefox-3.6.6/firefox
wobis     1539  0.0  0.0   1828   568 ?        S    14:34   0:00 /bin/sh /usr/lib/firefox-3.6.6/run-mozilla.sh /usr/lib/firefox-3.6.6/firefox-bin
wobis     1543  5.4  3.5 238348 71904 ?        Sl   14:34   0:47 /usr/lib/firefox-3.6.6/firefox-bin
wobis     1579 12.6  0.8  44328 17932 ?        S    14:34   1:48 gnome-system-monitor
wobis     1587  0.0  0.5  38756 10524 ?        S    14:36   0:00 /usr/lib/gnome-power-manager/gnome-inhibit-applet --oaf-activate-iid=OAFIID:GNOME_InhibitApplet_Factory --oaf-ior-fd=32
wobis     1592  0.0  0.1   5792  3180 pts/1    Ss   14:37   0:00 bash
root      1612  0.0  0.0   2748  1088 ?        S<   14:37   0:00 udevd --daemon
root      1613  0.0  0.0   2748  1016 ?        S<   14:37   0:00 udevd --daemon
root      1632  0.0  0.0   2228   992 ?        S    14:38   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp3/dhclient-b2bdbc09-5e79-4127-9a8f-7c6e2c152b7f-wlan0.lease -cf /var/run/nm-dhclient-wlan0.conf wlan0
wobis     1728  0.0  0.1   9552  3532 ?        S    14:41   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
108       1731  0.0  0.2  16796  4344 ?        Ssl  14:41   0:00 /usr/sbin/hald
root      1732  0.0  0.0   3528  1288 ?        S    14:41   0:00 hald-runner
root      1756  0.0  0.0   3604  1244 ?        S    14:41   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event1 /dev/input/event7 /dev/input/event2 /dev/input/event0 /dev/input/event5
root      1758  0.0  0.0   3604  1228 ?        S    14:41   0:00 /usr/lib/hal/hald-addon-rfkill-killswitch
root      1759  0.0  0.0   3604  1236 ?        S    14:41   0:00 /usr/lib/hal/hald-addon-leds
root      1767  0.0  0.0   3600  1192 ?        S    14:41   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      1772  0.0  0.0   3608  1236 ?        S    14:41   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1773  0.0  0.0   3616  1224 ?        S    14:41   0:00 /usr/lib/hal/hald-addon-cpufreq
108       1774  0.0  0.0   3416  1168 ?        S    14:41   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
wobis     1921  0.0  0.0   2712  1068 pts/1    R+   14:48   0:00 ps aux
[/SIZE][/FONT]

---

### Post by stressmonkey on 2010-07-05
[SIZE=2][FONT=Arial]here is the htop and System Monitor with the 512mb stick back in:

[/FONT][/SIZE][http://picasaweb.google.com/lh/photo/yDwlSxuRwxscOmYKORxxIA?feat=directlink](http://picasaweb.google.com/lh/photo/yDwlSxuRwxscOmYKORxxIA?feat=directlink)

[http://picasaweb.google.com/lh/photo/SK2W7d5vbA-hEpASqae5Rg?feat=directlink](http://picasaweb.google.com/lh/photo/SK2W7d5vbA-hEpASqae5Rg?feat=directlink)[SIZE=2][FONT=Arial]


and I loaded the** pgr.txt** file with the 512mb back in as an **attachment**.


there seems to be little difference in the system from having the 512mb stick removed and then putting it back in.

However, I did notice in the bug report that one of the users removed the battery for a minute and then started the computer back up and it solved the problem for her. ( you can find the posting at #32 of the bug report [/FONT][/SIZE][FONT=Arial][SIZE=2][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396)  )[/SIZE][/FONT]

[SIZE=2][FONT=Arial]Do you guys think that solved the problem? Or was it like you were mentioning--that the RAM stick is bad?


[/FONT][/SIZE]
[SIZE=2][FONT=Arial]


[/FONT][/SIZE]

---

### Post by stressmonkey on 2010-07-05
[FONT=Arial][SIZE=2]I guess this post can be marked as SOLVED, because everything is back to normal with my computer.  

I think what happened was that one of the updates triggered something in my computer to use a ton of CPU usage. What was strange about it was that there was no process listed in 'htop' or system monitor that was eating so much processor power.  When I took my battery out of the laptop to remove the 512mb memory stick, the problem went away. 

I reinstalled the 512mb stick and now everything is running smooth, so it was not the RAM that was causing the issue.

Reading the debugging report  [/SIZE][/FONT][FONT=Arial][SIZE=2]

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/537396)

at post #33, a user was experiencing similar problems with a sudden CPU spiking and 100% usage, and he took his battery out for 1 minute, and that fixed the problem.  So if you have this problem, I guess the best bet is to do likewise.

Thanks a lot for the help everyone. This was my first time using the forum and I appreciate it very much! 


[/SIZE][/FONT]

---

### Post by -humanaut- on 2010-07-06
Strange that is was the battery.

---

### Post by rablack on 2010-07-16
I'm using 10.04 on a Dell Latitude X1. This "fix" has solved my problem too. It makes absolutely no sense, but I took my battery out, left the laptop unplugged for ten minutes (just to be sure) and when I switched it on, the strange 100% CPU with no process  issue was gone!

---

