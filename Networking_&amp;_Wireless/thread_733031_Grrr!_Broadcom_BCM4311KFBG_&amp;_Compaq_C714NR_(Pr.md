---
title: "Grrr! Broadcom BCM4311KFBG &amp; Compaq C714NR (Presario C700)"
date: 2008-03-23
forum: Networking &amp; Wireless
---

### Post by luvit on 2008-03-23
I've spent my 3day weekend trying to get the following to work on Gutsy Gibbon:

Broadcom BCM4311KFBG
Compaq Presario C714NR (Presario C700)

I'm sorry I waited until now to write for help... I have searched and searched the forum and tried several solutions that were rather unique to each other for the above hardware combination... results varied greatly... but never discovered/connected to to my non-hidden, non-encrypted WiFi AP...**[COLOR="Red"] PLEASE HELP[/COLOR]**. ;) I so wish for a solution before Monday morning.

---

### Post by kevdog on 2008-03-23
Try this wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

And then get back to me if it doesn't work.

---

### Post by luvit on 2008-03-23
> **kevdog said:**
> Try this wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

And then get back to me if it doesn't work.

Thank you for a quick response. I did try that wiki twice... each attempt after a clean install of Gutsy 64bit.

I am running Gutsy 64bit and that wiki described to choose step 2a for my model of PC... my WiFi light does change from orange to blue (success) but i cannot get it to connect to APs with a manual config nor does it detect APs in the roaming config.

I followed those directions to a tee and the install looked successful without errors... do you believe I could just be missing some obvious or assumed knowledge? Could it be that I'm running the 64bit version of Gutsy?

---

### Post by kevdog on 2008-03-23
Im pegging it on the 64 bit install since I think you need a 64 bit windows driver.  Do you have a windows 64 bit xp driver or can you get one?

---

### Post by luvit on 2008-03-23
I will try to search for a 64bit driver... I assume 64bit **[COLOR="Blue"]XP[/COLOR]** driver... not Vista
While I search I will do another clean install of 64bit Gutsy since I experiment after each  failed attempt...  unless someone tells me 64bit is overrated... ;) (on my dual core intel)

---

### Post by luvit on 2008-03-23
> **luvit said:**
> ...  unless someone tells me 64bit is overrated... ;) (on my dual core intel)

[_[COLOR="Blue"]This thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=707046") [COLOR="Red"]has helped me decide to revert back to 32bit... maybe I'll have instant success! I'll try now.[/COLOR]

> **fragos said:**
> You won't notice a difference in speed.  Some libraries and plugins are only available in 32 bit which will make 64 bit more difficult to set up.  32 bit does have a memory addressing limit of 4GB but you aren't likely to be able to use that much memory anyway on the Desktop.  When I bought my 1st 64 bit machine I felt obligated to run 64 bit but I was wrong and got over it.

---

### Post by kevdog on 2008-03-23
You definitely do not need to do another install -- that is for certain.

---

### Post by luvit on 2008-03-23
I installed 32-bit ubuntu and failed on the above instructions for Feisty.
I have insured i am following the right step 2 by: [COLOR="Blue"]$ lspci -n | grep '14e4:43'[/COLOR]

I'm so lame ;)
I have tried a ton of other directions when i had 64bit installed... I will try those while I am currently on 32bit.
I'll hang around the board while I test all the other solutions on 32bit.
...in hopes of someone posting the silver bullet in this thread. ;)

---

### Post by kevdog on 2008-03-23
Just post 

lspci -nn | grep Network

---

### Post by luvit on 2008-03-23
[COLOR="Blue"]$ lspci -nn | grep Network

01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)[/COLOR]

---

### Post by kevdog on 2008-03-23
Ok great,  

get your windows driver from the following:

(Note: If you get "Couldn't find package cabextract" after line one, then [WWW] enable the "universe" repository. Then, re-run line one.)

(Also note: These download sites are flaky. Try wget [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe) if the listed wget doesn't work.)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)
cabextract sp34152.exe

---

### Post by luvit on 2008-03-23
ok. I completed those two steps. without errors ;)

I finished easter dinner so my replies should be much faster since I don't have to sneak out.

---

### Post by kevdog on 2008-03-23
Ok its pretty easy after this.

Can you tell me after you ran the cabextract command what you are left with.  A directory with the bcmwl5.inf and sys files or just the files?  I didnt cabextract the files on my machine (I did along time ago).

---

### Post by luvit on 2008-03-23
Thank you for this help. Here is the output.

[COLOR="Blue"]$ cabextract sp34152.exe
Extracting cabinet: sp34152.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp34152.cva

All done, no errors.
[/COLOR]

---

### Post by kevdog on 2008-03-23
Ok, so what ever directory all those files live in, you want to change into the name of the directory:

cd <name of directory>

Hold on -- you have ndiswrapper installed?
If so can you post

ndiswrapper -v

---

### Post by lswest on 2008-03-23
then you should just need to do:
```
sudo apt-get install ndiswrapper
cd [pathtofiles]
sudo ndiswrapper -i bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo echo "ndiswrapper" >> /etc/modules
sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist

``` then reboot.  The card should work then.

---

### Post by luvit on 2008-03-23
[COLOR="Blue"]$ ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586[/COLOR]

---

### Post by lswest on 2008-03-23
since you've already got an ndiswrapper installed, you can try my instructions from the second line onwards.

---

### Post by kevdog on 2008-03-23
Ok you are all good 

cd <directory where those files are>

Look I really was going to write out all the steps for you but Im going to point you to my other post that Ive explained this in thorough detail -- the reason -- because it has a lot of troubleshooting tips in case something goes wrong -- most people are not going to give you that.

I assumed in the tutorial all the bcmwl5 files where in a directory called driver.  It really isnt important, just  change into whatever directory your files are in and pick up the instructions from that point on.  And it doesnt matter your ndiswrapper v is 1.45.  It should work:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by luvit on 2008-03-23
thanks. i'd also like kevdog to chime in on if this is the direction he was heading.

---

### Post by kevdog on 2008-03-23
Basically those instructions are 100% accurate, however just take a look at my thread in case something goes wrong or you want to verify installation steps along the way.

---

### Post by lswest on 2008-03-23
you might be better off following his instructions, since they're more thorough, my method is a quick cobbling together that i did ages ago when i installed drivers for the same chipset in my HP laptop.   Good luck ^^

Oh, thanks kevdog ^^ Nice to know my memory served correctly ^^  By the way, nice How-To!

---

### Post by luvit on 2008-03-23
It shows installed, but it still won't show nearby APs or connect to an AP by manual mode.

---

### Post by kevdog on 2008-03-23
Ok so list the following

iwlist scan
lshw -C network

Also try an unencrypted network first if you can - no WEP,WPA or MAC filtering.

---

### Post by luvit on 2008-03-23
this is a non-hidden non-encrypted AP

[COLOR="Blue"]$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results[/COLOR]

[COLOR="DarkRed"]$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:8a:78:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:80:6d:53
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.226 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
[/COLOR]

---

### Post by kevdog on 2008-03-23
Its not picking up any networks, you sure you have any networks nearby??

Also type dmesg at the command line to confirm you are not seeing any errors related to wlan0 or ndiswrapper.

Can you also post ifconfig

---

### Post by luvit on 2008-03-23
> Its not picking up any networks, you sure you have any networks nearby??
lulz.... yes. my windows PCs are on it. unhidden with no encryption

[COLOR="Blue"]$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1B:38:80:6D:53  
          inet addr:192.168.0.226  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe80:6d53/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9251376 (8.8 MB)  TX bytes:2002207 (1.9 MB)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:1A:73:8A:78:B0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Memory:91300000-91304000 [/COLOR]

[HTML]$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f4d6000 (usable)
[    0.000000]  BIOS-e820: 000000007f4d6000 - 000000007f4e1000 (reserved)
[    0.000000]  BIOS-e820: 000000007f4e1000 - 000000007f52d000 (usable)
[    0.000000]  BIOS-e820: 000000007f52d000 - 000000007f530000 (reserved)
[    0.000000]  BIOS-e820: 000000007f530000 - 000000007f5bb000 (usable)
[    0.000000]  BIOS-e820: 000000007f5bb000 - 000000007f5bf000 (reserved)
[    0.000000]  BIOS-e820: 000000007f5bf000 - 000000007f67a000 (usable)
[    0.000000]  BIOS-e820: 000000007f67a000 - 000000007f6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6bf000 - 000000007f700000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f700000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 1142MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe270
[    0.000000] Entering add_active_range(0, 0, 521850) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   521850
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   521850
[    0.000000] On node 0 totalpages: 521850
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2284 pages used for memmap
[    0.000000]   HighMem zone: 290190 pages, LIFO batch:31
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE020 checksum 0
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7F6FE120, 0064 (r1 HPQOEM SLIC-MPC        1       1000013)
[    0.000000] ACPI: FACP 7F6FD000, 00F4 (r4 HP     SPARTAN         1 LOHR        0)
[    0.000000] ACPI: DSDT 7F6F5000, 7E50 (r1 HP     SPARTAN         1 LOHR        0)
[    0.000000] ACPI: FACS 7F67F000, 0040
[    0.000000] ACPI: APIC 7F6F4000, 0068 (r2 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: HPET 7F6F3000, 0038 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: MCFG 7F6F2000, 003C (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: ASF! 7F6F1000, 00A5 (r32 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: SLIC 7F6F0000, 0176 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: BOOT 7F6EF000, 0028 (r1 HPQOEM SLIC-MPC        1 LOHR        0)
[    0.000000] ACPI: SSDT 7F6EE000, 04C4 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 517774
[    0.000000] Kernel command line: root=UUID=50b8e3a1-aa1f-4a14-8e6d-2090539b4085 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1463.163 MHz processor.
[   27.533491] Console: colour VGA+ 80x25
[   27.533847] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.534193] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.639078] Memory: 2058040k/2087400k available (2015k kernel code, 28100k reserved, 915k data, 364k init, 1169824k highmem)
[   27.639088] virtual kernel memory layout:
[   27.639090]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   27.639091]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.639092]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.639094]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.639095]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   27.639096]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   27.639098]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   27.639101] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.639148] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   27.639319] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   27.639325] hpet0: 3 64-bit timers, 14318180 Hz
[   27.720240] Calibrating delay using timer specific routine.. 2929.49 BogoMIPS (lpj=5858996)
[   27.720268] Security Framework v1.0.0 initialized
[   27.720275] SELinux:  Disabled at boot.
[   27.720291] Mount-cache hash table entries: 512
[   27.720448] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   27.720456] monitor/mwait feature present.
[   27.720458] using mwait in idle threads.
[   27.720463] CPU: L1 I cache: 32K, L1 D cache: 32K
[   27.720466] CPU: L2 cache: 1024K
[   27.720469] CPU: Physical Processor ID: 0
[   27.720471] CPU: Processor Core ID: 0
[   27.720473] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   27.720485] Compat vDSO mapped to ffffe000.
[   27.720501] Checking 'hlt' instruction... OK.
[   27.736350] SMP alternatives: switching to UP code
[   27.736858] Early unpacking initramfs... done
[   28.111255] ACPI: Core revision 20070126
[   28.111316] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.164148] CPU0: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz stepping 0d
[   28.164167] SMP alternatives: switching to SMP code
[   28.164271] Booting processor 1/1 eip 3000
[   28.174396] Initializing CPU#1
[   28.251523] Calibrating delay using timer specific routine.. 2926.04 BogoMIPS (lpj=5852085)
[   28.251530] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001
[   28.251535] monitor/mwait feature present.
[   28.251538] CPU: L1 I cache: 32K, L1 D cache: 32K
[   28.251541] CPU: L2 cache: 1024K
[   28.251543] CPU: Physical Processor ID: 0
[   28.251545] CPU: Processor Core ID: 1
[   28.251547] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001
[   28.252050] CPU1: Intel(R) Pentium(R) Dual  CPU  T2310  @ 1.46GHz stepping 0d
[   28.252075] Total of 2 processors activated (5855.54 BogoMIPS).
[   28.252272] ENABLING IO-APIC IRQs
[   28.252484] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.399427] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   28.419419] Brought up 2 CPUs
[   28.567460] migration_cost=58
[   28.567600] Booting paravirtualized kernel on bare hardware
[   28.567692] Time: 22:47:58  Date: 02/23/108
[   28.567713] NET: Registered protocol family 16
[   28.567808] EISA bus registered
[   28.567813] ACPI: bus type pci registered
[   28.568866] PCI: Using configuration type 1
[   28.568868] Setting up standard PCI resources
[   28.573957] ACPI: EC: Look up EC in DSDT
[   28.595978] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   28.620405] ACPI: System BIOS is requesting _OSI(Linux)
[   28.620408] ACPI: Please test with "acpi_osi=!Linux"
[   28.620410] Please send dmidecode to linux-acpi@vger.kernel.org
[   28.622701] ACPI: Interpreter enabled
[   28.622705] ACPI: (supports S0 S3 S4 S5)
[   28.622760] ACPI: Using IOAPIC for interrupt routing
[   28.744132] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   28.744191] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.744207] PCI: Probing PCI hardware (bus 00)
[   28.745625] PCI: Transparent bridge - 0000:00:1e.0
[   28.745682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.746093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   28.746227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   28.753227] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   28.753360] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   28.753491] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   28.753619] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   28.753749] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[   28.753878] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[   28.754006] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[   28.754135] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   28.754280] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.754292] pnp: PnP ACPI init
[   28.754304] ACPI: bus type pnp registered
[   28.808589] pnp: PnP ACPI: found 9 devices
[   28.808593] ACPI: ACPI bus type pnp unregistered
[   28.808597] PnPBIOS: Disabled by ACPI PNP
[   28.808653] PCI: Using ACPI for IRQ routing
[   28.808656] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.808825] NET: Registered protocol family 8
[   28.808827] NET: Registered protocol family 20
[   28.808887] pnp: 00:01: ioport range 0x164e-0x164f has been reserved
[   28.808891] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   28.808895] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   28.808899] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   28.808903] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   28.810776] Time: tsc clocksource has been installed.
[   28.810793] Switched to high resolution mode on CPU 0
[   28.810883] Switched to high resolution mode on CPU 1
[   28.839204] PCI: Bridge: 0000:00:1c.0
[   28.839208]   IO window: 2000-2fff
[   28.839216]   MEM window: 91300000-923fffff
[   28.839221]   PREFETCH window: 90000000-90ffffff
[   28.839228] PCI: Bridge: 0000:00:1e.0
[   28.839232]   IO window: 1000-1fff
[   28.839239]   MEM window: 91200000-912fffff
[   28.839244]   PREFETCH window: disabled.
[   28.839280] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 18 (level, low) -> IRQ 16
[   28.839288] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   28.839305] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   28.839318] NET: Registered protocol family 2
[   28.890654] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.890742] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   28.891873] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.892349] TCP: Hash tables configured (established 131072 bind 65536)
[   28.892352] TCP reno registered
[   28.906784] checking if image is initramfs... it is
[   29.645057] Freeing initrd memory: 7043k freed
[   29.645201] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[   29.645203] Simple Boot Flag at 0x44 set to 0x1
[   29.645744] audit: initializing netlink socket (disabled)
[   29.645765] audit(1206312478.500:1): initialized
[   29.645869] highmem bounce pool size: 64 pages
[   29.647948] VFS: Disk quotas dquot_6.5.1
[   29.648006] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.648106] io scheduler noop registered
[   29.648109] io scheduler anticipatory registered
[   29.648111] io scheduler deadline registered
[   29.648126] io scheduler cfq registered (default)
[   29.648144] Boot video device is 0000:00:02.0
[   29.648404] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   29.648472] assign_interrupt_mode Found MSI capability
[   29.648476] Allocate Port Service[0000:00:1c.0:pcie00]
[   29.648521] Allocate Port Service[0000:00:1c.0:pcie02]
[   29.648701] isapnp: Scanning for PnP cards...
[   30.002459] isapnp: No Plug & Play device found
[   30.026219] Real Time Clock Driver v1.12ac
[   30.026445] hpet_resources: 0xfed00000 is busy
[   30.026493] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.027729] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.027865] input: Macintosh mouse button emulation as /class/input/input0
[   30.027949] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   30.064839] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.064846] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.065031] mice: PS/2 mouse device common for all mice
[   30.066704] EISA: Probing bus 0 at eisa.0
[   30.066713] Cannot allocate resource for EISA slot 1
[   30.066715] Cannot allocate resource for EISA slot 2
[   30.066718] Cannot allocate resource for EISA slot 3
[   30.066745] EISA: Detected 0 cards.
[   30.066872] TCP cubic registered
[   30.066889] NET: Registered protocol family 1
[   30.066914] Using IPI No-Shortcut mode
[   30.067081]   Magic number: 0:281:806
[   30.067165]   hash matches device ptys0
[   30.067403] Freeing unused kernel memory: 364k freed
[   30.085448] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.299043] AppArmor: AppArmor initialized<5>audit(1206312480.000:2):  type=1505 info="AppArmor initialized" pid=1217
[   31.306078] fuse init (API version 7.8)
[   31.311324] Failure registering capabilities with primary security module.
[   31.345388] ACPI: SSDT 7F67EC90, 01EA (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[   31.345657] ACPI: SSDT 7F67D610, 05D7 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[   31.346048] Monitor-Mwait will be used to enter C-1 state
[   31.346052] Monitor-Mwait will be used to enter C-2 state
[   31.346055] Monitor-Mwait will be used to enter C-3 state
[   31.346060] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   31.346066] ACPI: Processor [CPU0] (supports 8 throttling states)
[   31.346339] ACPI: SSDT 7F67EF10, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[   31.346585] ACPI: SSDT 7F680D10, 0083 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[   31.347012] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   31.347018] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.540000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.544000] Time: hpet clocksource has been installed.
[    3.548000] ACPI: Thermal Zone [TZ01] (55 C)
[    4.064000] usbcore: registered new interface driver usbfs
[    4.064000] usbcore: registered new interface driver hub
[    4.064000] usbcore: registered new device driver usb
[    4.064000] USB Universal Host Controller Interface driver v3.0
[    4.064000] ACPI: PCI Interrupt 0000:00:1d.0[D] -> GSI 21 (level, low) -> IRQ 17
[    4.064000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.064000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.064000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.064000] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00003080
[    4.064000] usb usb1: configuration #1 chosen from 1 choice
[    4.064000] hub 1-0:1.0: USB hub found
[    4.064000] hub 1-0:1.0: 2 ports detected
[    4.084000] SCSI subsystem initialized
[    4.108000] libata version 2.21 loaded.
[    4.168000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 18
[    4.168000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.168000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.168000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.168000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[    4.168000] usb usb2: configuration #1 chosen from 1 choice
[    4.168000] hub 2-0:1.0: USB hub found
[    4.168000] hub 2-0:1.0: 2 ports detected
[    4.188000] 8139too Fast Ethernet driver 0.9.28
[    4.272000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 19 (level, low) -> IRQ 19
[    4.272000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.272000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.272000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.272000] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00003040
[    4.272000] usb usb3: configuration #1 chosen from 1 choice
[    4.272000] hub 3-0:1.0: USB hub found
[    4.272000] hub 3-0:1.0: 2 ports detected
[    4.376000] ahci 0000:00:1f.2: version 2.2
[    4.376000] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 17 (level, low) -> IRQ 20
[    4.376000] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match
[    4.500000] Clocksource tsc unstable (delta = -231044517 ns)
[    5.384000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    5.384000] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    5.384000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.384000] scsi0 : ahci
[    5.384000] ata1: SATA max UDMA/133 cmd 0xf880a100 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.872000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.872000] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7BP, max UDMA/100
[    5.872000] ata1.00: 234441648 sectors, multi 16: LBA48 
[    5.872000] ata1.00: configured for UDMA/100
[    5.872000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    5.872000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    5.872000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    5.872000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.872000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    5.872000] ehci_hcd 0000:00:1d.7: debug port 1
[    5.872000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    5.872000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0x92404800
[    5.876000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.876000] usb usb4: configuration #1 chosen from 1 choice
[    5.876000] hub 4-0:1.0: USB hub found
[    5.876000] hub 4-0:1.0: 6 ports detected
[    5.880000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.880000] sd 0:0:0:0: [sda] Write Protect is off
[    5.880000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.880000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.880000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.880000] sd 0:0:0:0: [sda] Write Protect is off
[    5.880000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.880000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.880000]  sda:<6>ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 22
[    5.980000] PCI: Setting latency timer of device 0000:02:01.0 to 64
[    5.980000] eth0: RealTek RTL8139 at 0xf886c000, 00:1b:38:80:6d:53, IRQ 22
[    5.980000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    5.980000] ata_piix 0000:00:1f.1: version 2.11
[    5.980000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[    5.980000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    5.980000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.984000] scsi1 : ata_piix
[    5.984000] scsi2 : ata_piix
[    5.984000] ata2: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000130a0 irq 14
[    5.984000] ata3: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000130a8 irq 15
[    6.284000]  sda1 sda2 < sda5 >
[    6.304000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.308000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.328000] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[    6.512000] Attempting manual resume
[    6.516000] swsusp: Resume From Partition 8:5
[    6.516000] PM: Checking swsusp image.
[    6.516000] PM: Resume from disk failed.
[    6.516000] ata2.00: configured for MWDMA2
[    6.560000] kjournald starting.  Commit interval 5 seconds
[    6.560000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.688000] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  HS02 PQ: 0 ANSI: 5
[    6.688000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   14.076000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.192000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.192000] agpgart: Detected an Intel 965GM Chipset.
[   14.196000] agpgart: Detected 7676K stolen memory.
[   14.208000] agpgart: AGP aperture is 256M @ 0x80000000
[   14.280000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.520000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.520000] Uniform CD-ROM driver Revision: 3.20
[   14.520000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.716000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   14.716000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   14.896000] input: PS/2 Mouse as /class/input/input2
[   14.932000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   15.244000] lp: driver loaded but no devices found
[   15.288000] ndiswrapper version 1.45 loaded (smp=yes)
[   15.372000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   15.372000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
[   15.372000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.376000] ndiswrapper: using IRQ 22
[   15.732000] wlan0: ethernet device 00:1a:73:8a:78:b0 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   15.732000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   15.732000] usbcore: registered new interface driver ndiswrapper
[   15.800000] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
[   16.040000] hda_intel: azx_get_response timeout, switching to polling mode...
[   16.364000] EXT3 FS on sda1, internal journal
[   17.680000] No dock devices found.
[   17.784000] ACPI: Battery Slot [BAT0] (battery present)
[   17.804000] input: Power Button (FF) as /class/input/input4
[   17.804000] ACPI: Power Button (FF) [PWRF]
[   17.804000] input: Power Button (CM) as /class/input/input5
[   17.804000] ACPI: Power Button (CM) [PWRB]
[   17.804000] input: Lid Switch as /class/input/input6
[   17.804000] ACPI: Lid Switch [LID0]
[   17.804000] input: Sleep Button (CM) as /class/input/input7
[   17.804000] ACPI: Sleep Button (CM) [SLPB]
[   17.984000] ACPI: AC Adapter [AC] (on-line)
[   18.004000] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   19.384000] ppdev: user-space parallel port driver
[   19.600000] audit(1206312496.461:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4780 profile="/usr/sbin/cupsd"
[   19.644000] apm: BIOS not found.
[   19.740000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   19.956000] Failure registering capabilities with primary security module.
[   20.220000] Bluetooth: Core ver 2.11
[   20.220000] NET: Registered protocol family 31
[   20.220000] Bluetooth: HCI device and connection manager initialized
[   20.220000] Bluetooth: HCI socket layer initialized
[   20.232000] Bluetooth: L2CAP ver 2.8
[   20.232000] Bluetooth: L2CAP socket layer initialized
[   20.312000] Bluetooth: RFCOMM socket layer initialized
[   20.312000] Bluetooth: RFCOMM TTY layer initialized
[   20.312000] Bluetooth: RFCOMM ver 1.8
[   25.072000] NET: Registered protocol family 17
[   25.316000] [drm] Initialized drm 1.1.0 20060810
[   25.316000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 22
[   25.316000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   27.576000] NET: Registered protocol family 10
[   27.576000] lo: Disabled Privacy Extensions
[   27.576000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.516000] eth0: no IPv6 routers present
[/HTML]

---

### Post by kevdog on 2008-03-23
Ahhh

Do the following

sudo ifconfig eth0 down <---- Takes down the wired NIC
sudo ifconfig wlan0 up <------- Bring up the wireless device

then check with
iwlist scan

Cant run wired and wireless at the same time unless you manually configure each device.

---

### Post by luvit on 2008-03-23
vvv see below post vvv

---

### Post by luvit on 2008-03-23
[B][COLOR="Red"]I posted too soon:
I'm now posting from Wireless ;)[/COLOR][/B]

[COLOR="Blue"]$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:84:39:A2
                    ESSID:"bocera"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0[/COLOR]

---

### Post by kevdog on 2008-03-23
Ok it seems you connected with network manager (or manually - it doesnt really matter)!

---

### Post by luvit on 2008-03-23
I'm giving you many thanks, kevdog.
I'm going to reboot to see if it sticks and then try on a 64bit system... I may be a glutton for punishment. lulz.

---

### Post by lswest on 2008-03-24
if you follow the same steps it should work, just remember to use a 64x driver for the card.

---

### Post by Terminating.proprietary on 2008-03-24
OK, I have a Broadcom card and I am using 64 bit. It isn't automatically working under a 32 bit install either. I have done some research and it appears ndiswrapper might not even support  card is this really possible. Is is possible that there is just no support at this time or should I be looking around for some wacky workaround?

---

### Post by luvit on 2008-04-01
For clarity, I solved my wireless issue on my Compaq C700 / C714NR per kevdog's directions.




**I followed this thread precisely:**
[[COLOR="Blue"]_https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

**But I substituted the following commands:**
sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
cabextract sp34152.exe

I have used this quite a few times with immediate success.;)

---

