---
title: "Simple question re 'linux headers'"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by flyingsolo on 2006-11-28
I'm following this tutorial for Broadcom wireless with ndiswrapper but don't know what is required for the following:
[COLOR="Sienna"]
Step 3 - Prepare the Linux build environment

You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update 
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` 
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
[/COLOR]

What is to be entered at 'uname -r'?  My username perhaps??  In case it matters, I am using Edgy.  Hopefully this isn't over my noobish head!  Thanks.

---

### Post by FrodoB on 2006-11-28
Just copy that exact line and paste it into a terminal window and it will request the correct file for your kernel.

It is just taking the output of uname -r and putting that in the command that goes to apt-get.

---

### Post by flyingsolo on 2006-11-28
Thnks for quick reply...I had to go out to son's basketball game!  I went ahead on my own as you stated above, guessing that was what I had to do but of course am stuck at the next step:
[COLOR="Sienna"]Step 5 - Extract and install the ndiswrapper using make

Using tar extract the archived driver and change directories into the build area.

user@ubuntu:~$ tar xvzf ndiswrapper-1.28.tar.gz 
user@ubuntu:~$ cd ndiswrapper-1.28
[/COLOR]

I am using ndiswrapper 1.29 which is downloaded and extracted to the desktop.   I don't understand what it means to "...change directories into the build area."
Sorry, but I'm pretty green with this.  My broadcom is 4328 and I'm hoping to get it going with this.  (Dell inspiron 6400, core2duo)  Thanks again.

---

### Post by FrodoB on 2006-11-28
1) Open a terminal window

2) Move the file from your desktop to the current directory

     mv Desktop/ndiswrapper-1.29.tar.gz ~

3) Your ndiswrapper-1.29.tar.gz file is in your current directory, proceed with the instructions as they were given. 

You can type list short, ls to see the files

ls

---

### Post by flyingsolo on 2006-11-28
thanks frodoB for continuing help...things going well now to point of having ndiswrapper1.29 installed and am now ready to load windows drivers.  The drivers have been fetched to desktop from Dell download site.  I believe I need the bcmwl5.inf file in my case but I'm not certain.  The driver download also includes a .exe file (R140747.exe)
Because the tutorial has specific reference to an HP driver, I am a little confused at this point.  Clearly, the HP fetch isn't relevant to me and I have my necessary Windows drivers. So, the following wouldn't apply to me:
[COLOR="Sienna"]user@ubuntu:~/ndiswrapper-1.28$ sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) -O${HOME}/sp33008.exe

[/COLOR]
but when I continue with:
[COLOR="Sienna"]sudo gedit /etc/apt/sources.list[/COLOR]
I only get an empty text editor file.
More directions please!

EDIT--OK, I tried sudo gedit /etc/apt/sources.list again and now it worked.  Don't know why b/c I just re-entered the same command.  Anyway, I'll have to put this aside for tonight as it is late on the East coast.  Thanks for help so far...it's looking promising!

---

### Post by FrodoB on 2006-11-29
If you really have a bcm4311 the link that I gave you may very well work. If you want to try to get into the exe file that you downloaded you have to try all three of the tools that I suggested to see which one opens it:

cabextract

unzip

unshield

We don't know how they made the file, so we just have to try until one of them works.

---

### Post by flyingsolo on 2006-11-29
Back at it again!
I thought I was doing well when I got:
[COLOR="Sienna"]ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4328) present[/COLOR]
(that smiley face should be an "8" as in 4328}
but then iwconfig gives:

[COLOR="Sienna"][COLOR="Sienna"]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
[/COLOR][/COLOR]

So...this seems to mean my hardware is now detected and drivers are installed but still no wireless is seen with iwconfig?  I guess I don't understand this or what might now be missing.  Is there any point in running network manager now?

---

### Post by FrodoB on 2006-11-30
No something is wrong. Retrace you steps from the beginning.

What you are showing looks like you have not brought up the driver yet. 

Bring up the driver:  
 user@ubuntu:~/bcm4311$ sudo depmod -a
user@ubuntu:~/bcm4311$ sudo modprobe ndiswrapper
If you do not get any errors and your system does not immediately freeze the driver should now be loaded. Do not reboot until we have made some basic checks and installed the driver permanently.



Then run iwconfig and see if you don't get better results.

---

### Post by flyingsolo on 2006-11-30
I am guessing the problem is with the driver download.  Originally, I downloaded the XP drivers but the Dell site also has a drop down list for drivers including SUSE ES 9 or 10, Linux 8, Linux 9, Enterprise Linux 3.  Any guess whether one of these might work directly without ndiswrapper?  In the meantime, I'll proceed with the XP drivers under ndiswrapper.

EDIT--Ok, the linux downloads are for BIOS and other things, not the wireless card.

EDIT 2--Stuck again.  I've downloaded dell drivers via ftp, similar to example in tutorial, and then mkdir bcm4328 but when I move driver file to bcm4328, I get the following error:

[COLOR="Sienna"] mv R140747.EXE bcm4328
mv: cannot stat `R140747.EXE': No such file or directory
[/COLOR]
(R140747.exe is the dell name for my driver file; it is for their draft n card)  Scratching my head again!

---

### Post by FrodoB on 2006-11-30
Is it perhaps on your Desktop?

[COLOR=Sienna] mv Desktop/R140747.EXE bcm4328

You can see if it is there or not with:

ls

ls Desktop


[/COLOR]

---

### Post by flyingsolo on 2006-11-30
OK--I got the .exe file from desktop and then got the following via unzip:

[COLOR="Sienna"]:~/bcm4328$ unzip R140747.EXE
Archive:  R140747.EXE
  inflating: msvcr71.DLL             
  inflating: preflib.dll             
  inflating: README.rtf              
  inflating: setup.exe               
  inflating: setup.inx               
  inflating: Setup.ini               
  inflating: setup.iss               
  inflating: WLBCGCBPRO731.DLL       
  inflating: wltray.exe              
  inflating: wltrynt.dll             
  inflating: wltrysvc.exe            
  inflating: AMD64/atl71.dll         
  inflating: AMD64/BCMLogon64.dll    
  inflating: AMD64/bcmwlcpl64.cpl    
  inflating: AMD64/MFC71.DLL         
  inflating: AMD64/msvcp71.DLL       
  inflating: AMD64/msvcr71.DLL       
  inflating: DRIVER/bcm43xx.cat      
  inflating: DRIVER/bcm43xx64.cat    
  inflating: DRIVER/bcmwl5.inf       
  inflating: DRIVER/bcmwl5.sys       
  inflating: DRIVER/bcmwl564.sys     
  inflating: ATL71.DLL               
  inflating: bcm1xsup.dll            
  inflating: BCMLogon.dll            
  inflating: Bcmnpf64.sys            
  inflating: bcmwlcpl.cpl            
  inflating: bcmwlhlp.cab            
  inflating: bcmwlhlp.chm            
  inflating: bcmwliss.dll            
  inflating: bcmwlnpf.sys            
  inflating: bcmwlpkt.dll            
  inflating: bcmwls.ini              
  inflating: bcmwls32.exe            
  inflating: bcmwls64.exe            
  inflating: bcmwltry.exe            
  inflating: bcmwlu00.exe            
  inflating: data1.cab               
  inflating: data1.hdr               
  inflating: data2.cab               
  inflating: DellInfo.exe            
  inflating: DellInfo64.exe          
  inflating: dellinst.exe            
  inflating: ikernel.ex_             
  inflating: is.exe                  
 extracting: launcher.ini            
  inflating: layout.bin              
  inflating: MFC71.DLL               
  inflating: msvcp71.DLL             
  inflating: Version.txt     [/COLOR]
At this point, I did the sudo ndiswrapper -i bcmwl5.inf but got the reply that "driver bcmwl5 is already installed."  Still no wireless seen with iwconfig.  By the way, the list for bcmwl5 is as follows:

[COLOR="Sienna"]~/bcm4328$ ls /etc/ndiswrapper/bcmwl5
14E4:4311:1028:0007.5.conf  14E4:4320:1028:0002.5.conf
14E4:4311:1028:0008.5.conf  14E4:4320:1028:0003.5.conf
14E4:4311.5.conf            14E4:4320:1028:0004.5.conf
14E4:4312:1028:0007.5.conf  14E4:4320.5.conf
14E4:4312:1028:0008.5.conf  14E4:4324:1028:0001.5.conf
14E4:4312.5.conf            14E4:4324:1028:0002.5.conf
14E4:4318:1028:0005.5.conf  14E4:4324:1028:0003.5.conf
14E4:4318:1028:0006.5.conf  14E4:4324:1028:0004.5.conf
14E4:4318.5.conf            14E4:4324.5.conf
14E4:4319:1028:0005.5.conf  14E4:4328:1028:0009.5.conf
14E4:4319:1028:0006.5.conf  14E4:4328.5.conf
14E4:4319.5.conf            bcmwl564.sys
14E4:4320:1028:0001.5.conf  bcmwl5.inf
[/COLOR]
I think I'm one step closer but not quite there yet.  Also, according to the tutorial, I don't have to edit the files above with ndiswrapper 1.29, correct?
(FrodoB, your patience is immense!)
Edit--additionally,
~/bcm4328$ sudo depmod -a
~/bcm4328$ sudo modprobe ndiswrapper
give no errors or freezes.

---

### Post by FrodoB on 2006-11-30
You need to edit the files exactly as described. The only difference is to subsititute 1.29 every place you see 1.28 in the instructions.

What do you get from:

ndiswrapper -l

---

### Post by flyingsolo on 2006-12-01
> **FrodoB said:**
> You need to edit the files exactly as described. The only difference is to subsititute 1.29 every place you see 1.28 in the instructions.

What do you get from:

ndiswrapper -l

To answer your question:
[COLOR="Sienna"]ndiswrapper -l
installed drivers:
bcmwl5          driver installed, hardware (14E4:4328) present 
[/COLOR]
[COLOR="Black"]The reason I thought no editing was needed was because of the note in the tutorial stating that:
 On 1.29, altering config file proved to be not needed. --Teaker1s[/COLOR]
Anyway, I did the edit as per tutorial.  Also, in the config file, I didn't need to change Afterburner|1 to Afterburner|0 as it was already set to 0.  Still iwconfig shows no wireless.:(
Just to clarify, when you said replace every instance of 1.28 with 1.29, are you referring to the content of bcmwl5 perhaps? (just my guess) In other words, in the following:
[COLOR="black"][COLOR="black"][COLOR="Sienna"]14E4:4311:1028:0007.5.conf  14E4:4320:1028:0002.5.conf
14E4:4311:1028:0008.5.conf  14E4:4320:1028:0003.5.conf
14E4:4311.5.conf            14E4:4320:1028:0004.5.conf
14E4:4312:1028:0007.5.conf  14E4:4320.5.conf
14E4:4312:1028:0008.5.conf  14E4:4324:1028:0001.5.conf
14E4:4312.5.conf            14E4:4324:1028:0002.5.conf
14E4:4318:1028:0005.5.conf  14E4:4324:1028:0003.5.conf
14E4:4318:1028:0006.5.conf  14E4:4324:1028:0004.5.conf
14E4:4318.5.conf            14E4:4324.5.conf
14E4:4319:1028:0005.5.conf  14E4:4328:1028:0009.5.conf
14E4:4319:1028:0006.5.conf  14E4:4328.5.conf
14E4:4319.5.conf            bcmwl564.sys
14E4:4320:1028:0001.5.conf  bcmwl5.inf
[/COLOR][/COLOR][/COLOR]
[COLOR="Sienna"][COLOR="Black"]I would change all the instances of :1028: to :1029: ?  [/COLOR][/COLOR]

---

### Post by FrodoB on 2006-12-01
I am just saying that when the instruction says 1.28 you think 1.29 because that is the version that you are using.

What you describe sounds like ndiswrapper is not loaded as a module.  Run lsmod and see if ndiswrapper is loaded. If not depmod and and ndiswrapper -m per the instructions.

---

### Post by flyingsolo on 2006-12-01
lsmod shows ndiswrapper _is_ loaded.  I had substituted 1.29 for 1.28 throughout the tutorial.

---

### Post by FrodoB on 2006-12-01
Try doing a modprobe -m and then reboot and see what happens.  

Then what does iwconfig show?

---

### Post by flyingsolo on 2006-12-01
Well, modprobe -m only gives the following--maybe a typo error?
[COLOR="Sienna"] modprobe -m
modprobe: invalid option -- m
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
[/COLOR]
and then ndiswrapper -m gives:
[COLOR="Sienna"] ndiswrapper -m
modprobe config already contains alias directive
[/COLOR]
and still no go with iwconfig.

---

### Post by FrodoB on 2006-12-01
Sorry:

depmod -a
modprobe ndiswrapper

---

### Post by flyingsolo on 2006-12-01
Still no wireless after depmod -a and modprobe ndiswrapper.  Reboot & iwconfig-->still no wireless extensions.

---

### Post by FrodoB on 2006-12-02
Well, I am missing something. It seems like it should work. Does anyone have some ideas out there?

---

### Post by FrodoB on 2006-12-02
Can you publish the output of the dmesg command. Then we can see what ndiswrapper thinks is wrong perhaps.

---

### Post by flyingsolo on 2006-12-02
OK,here is the dmesg output:
```
 dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40 UTC 2006 (Ubuntu 2.6.17-10.33-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000007fed3400 (usable)
[17179569.184000]  BIOS-e820: 000000007fed3400 - 0000000080000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f0000000 - 00000000f4007000 (reserved)
[17179569.184000]  BIOS-e820: 00000000f4008000 - 00000000f400c000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 1150MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 523987
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 294611 pages, LIFO batch:31
[17179569.184000] DMI 2.4 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fc1d0
[17179569.184000] ACPI: RSDT (v001 DELL    M07     0x27d6091d ASL  0x00000061) @ 0x7fed39cd
[17179569.184000] ACPI: FADT (v001 DELL    M07     0x27d6091d ASL  0x00000061) @ 0x7fed4800
[17179569.184000] ACPI: HPET (v001 DELL    M07     0x00000001 ASL  0x00000061) @ 0x7fed4f00
[17179569.184000] ACPI: MADT (v001 DELL    M07     0x27d6091d ASL  0x00000047) @ 0x7fed5000
[17179569.184000] ACPI: MCFG (v016 DELL    M07     0x27d6091d ASL  0x00000061) @ 0x7fed4fc0
[17179569.184000] ACPI: SLIC (v001 DELL    M07     0x27d6091d ASL  0x00000061) @ 0x7fed509c
[17179569.184000] ACPI: BOOT (v001 DELL    M07     0x27d6091d ASL  0x00000061) @ 0x7fed4bc0
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050624) @ 0x7fed3a0d
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 INTL 0x20050624) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:15 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[17179569.184000] Processor #1 6:15 APIC version 20
[17179569.184000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=8de4d647-5823-41b6-912e-418ad5d35c80 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Console: colour VGA+ 80x25
[17179569.184000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.184000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.184000] Memory: 2067244k/2095948k available (1829k kernel code, 27400k reserved, 1038k data, 288k init, 1178444k highmem)
[17179569.184000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.184000] hpet0: at MMIO 0xfed00000 (virtual 0xf8800000), IRQs 2, 8, 0
[17179569.184000] hpet0: 3 64-bit timers, 14318180 Hz
[17179569.184000] Using HPET for base-timer
[17179569.184000] Using HPET for gettimeofday
[17179569.184000] Detected 1995.052 MHz processor.
[17179569.184000] Using hpet for high-res timesource
[17179569.268000] Calibrating delay using timer specific routine.. 3994.37 BogoMIPS (lpj=7988746)
[17179569.268000] Security Framework v1.0.0 initialized
[17179569.268000] SELinux:  Disabled at boot.
[17179569.268000] Mount-cache hash table entries: 512
[17179569.268000] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] CPU: After vendor identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[17179569.268000] monitor/mwait feature present.
[17179569.268000] using mwait in idle threads.
[17179569.268000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.268000] CPU: L2 cache: 4096K
[17179569.268000] CPU: After all inits, caps: bfebfbff 20100000 00000000 00000140 0000e3bd 00000000 00000001
[17179569.268000] CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz stepping 06
[17179569.268000] Checking 'hlt' instruction... OK.
[17179569.284000] SMP alternatives: switching to UP code
[17179569.284000] Freeing SMP alternatives: 0k freed
[17179569.284000] checking if image is initramfs... it is
[17179569.788000] Freeing initrd memory: 6628k freed
[17179569.788000] ACPI: Core revision 20060707
[17179569.804000] ACPI: Looking for DSDT ... not found!
[17179569.808000] ENABLING IO-APIC IRQs
[17179569.808000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179569.960000] NET: Registered protocol family 16
[17179569.960000] EISA bus registered
[17179569.960000] ACPI: bus type pci registered
[17179569.960000] PCI: Using MMCONFIG
[17179569.960000] Setting up standard PCI resources
[17179569.984000] ACPI: Interpreter enabled
[17179569.984000] ACPI: Using IOAPIC for interrupt routing
[17179569.984000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179569.984000] PCI: Probing PCI hardware (bus 00)
[17179569.984000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179569.996000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.2
[17179569.996000] Boot video device is 0000:01:00.0
[17179570.000000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.000000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.016000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[17179570.016000] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[17179570.016000] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[17179570.016000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[17179570.016000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179570.016000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179570.016000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179570.016000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[17179570.016000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179570.016000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179570.020000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[17179570.020000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[17179570.020000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.020000] pnp: PnP ACPI init
[17179570.048000] pnp: PnP ACPI: found 12 devices
[17179570.048000] PnPBIOS: Disabled by ACPI PNP
[17179570.048000] PCI: Using ACPI for IRQ routing
[17179570.048000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.064000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179570.064000] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[17179570.064000] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[17179570.064000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[17179570.064000] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[17179570.064000] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[17179570.064000] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[17179570.064000] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[17179570.064000] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[17179570.064000] pnp: 00:08: ioport range 0xc80-0xcff has been reserved
[17179570.064000] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[17179570.064000] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[17179570.064000] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[17179570.064000] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[17179570.064000] PCI: Bridge: 0000:00:01.0
[17179570.064000]   IO window: e000-efff
[17179570.064000]   MEM window: efd00000-efefffff
[17179570.064000]   PREFETCH window: d0000000-dfffffff
[17179570.064000] PCI: Bridge: 0000:00:1c.0
[17179570.064000]   IO window: disabled.
[17179570.064000]   MEM window: efc00000-efcfffff
[17179570.064000]   PREFETCH window: e0000000-e00fffff
[17179570.064000] PCI: Bridge: 0000:00:1c.3
[17179570.064000]   IO window: d000-dfff
[17179570.064000]   MEM window: efa00000-efbfffff
[17179570.064000]   PREFETCH window: e0100000-e03fffff
[17179570.064000] PCI: Bridge: 0000:00:1e.0
[17179570.064000]   IO window: disabled.
[17179570.064000]   MEM window: ef900000-ef9fffff
[17179570.064000]   PREFETCH window: disabled.
[17179570.064000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.064000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.064000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.064000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.064000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.064000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.064000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.064000] NET: Registered protocol family 2
[17179570.104000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.104000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179570.104000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.104000] TCP: Hash tables configured (established 262144 bind 65536)
[17179570.104000] TCP reno registered
[17179570.104000] Simple Boot Flag at 0x79 set to 0x1
[17179570.104000] audit: initializing netlink socket (disabled)
[17179570.104000] audit(1165080243.104:1): initialized
[17179570.104000] highmem bounce pool size: 64 pages
[17179570.104000] VFS: Disk quotas dquot_6.5.1
[17179570.104000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.104000] Initializing Cryptographic API
[17179570.104000] io scheduler noop registered
[17179570.104000] io scheduler anticipatory registered
[17179570.104000] io scheduler deadline registered
[17179570.104000] io scheduler cfq registered (default)
[17179570.104000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.104000] assign_interrupt_mode Found MSI capability
[17179570.104000] Allocate Port Service[0000:00:01.0:pcie00]
[17179570.104000] Allocate Port Service[0000:00:01.0:pcie03]
[17179570.104000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179570.104000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[17179570.104000] assign_interrupt_mode Found MSI capability
[17179570.104000] Allocate Port Service[0000:00:1c.0:pcie00]
[17179570.104000] Allocate Port Service[0000:00:1c.0:pcie02]
[17179570.104000] Allocate Port Service[0000:00:1c.0:pcie03]
[17179570.104000] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 177
[17179570.104000] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[17179570.104000] assign_interrupt_mode Found MSI capability
[17179570.104000] Allocate Port Service[0000:00:1c.3:pcie00]
[17179570.104000] Allocate Port Service[0000:00:1c.3:pcie02]
[17179570.104000] Allocate Port Service[0000:00:1c.3:pcie03]
[17179570.104000] isapnp: Scanning for PnP cards...
[17179570.460000] isapnp: No Plug & Play device found
[17179570.472000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.472000] mice: PS/2 mouse device common for all mice
[17179570.476000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.476000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.476000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.476000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.476000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.476000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.476000] EISA: Probing bus 0 at eisa.0
[17179570.476000] EISA: Cannot allocate resource for mainboard
[17179570.476000] Cannot allocate resource for EISA slot 1
[17179570.476000] EISA: Detected 0 cards.
[17179570.476000] TCP bic registered
[17179570.476000] NET: Registered protocol family 1
[17179570.476000] NET: Registered protocol family 8
[17179570.476000] NET: Registered protocol family 20
[17179570.476000] Using IPI Shortcut mode
[17179570.476000] ACPI: (supports S0 S3 S4 S5)
[17179570.476000] Freeing unused kernel memory: 288k freed
[17179570.484000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.536000] Capability LSM initialized
[17179571.560000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[17179571.560000] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[17179571.560000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.560000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179571.560000] ACPI: Getting cpuindex for acpiid 0x1
[17179571.564000] ACPI: Thermal Zone [THM] (55 C)
[17179571.824000] SCSI subsystem initialized
[17179571.824000] libata version 1.20 loaded.
[17179571.824000] ata_piix 0000:00:1f.2: version 1.05
[17179571.824000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 217
[17179571.824000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179571.824000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
[17179571.988000] ata1: dev 0 cfg 49:0f00 82:746b 83:7f69 84:4163 85:7469 86:3e49 87:4163 88:203f
[17179571.988000] ata1: dev 0 ATA-7, max UDMA/100, 312581808 sectors: LBA48
[17179571.996000] ata1: dev 0 configured for UDMA/100
[17179571.996000] scsi0 : ata_piix
[17179571.996000]   Vendor: ATA       Model: Hitachi HTS54161  Rev: SB4O
[17179571.996000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179571.996000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[17179572.316000] ata2: dev 0 cfg 49:0b00 82:0210 83:0000 84:0000 85:0000 86:0000 87:0000 88:0407
[17179572.316000] ata2: dev 0 ATAPI, max UDMA/33
[17179572.484000] ata2: dev 0 configured for UDMA/33
[17179572.484000] scsi1 : ata_piix
[17179572.484000]   Vendor: PHILIPS   Model: DVD+-RW SDVD8820  Rev: AD15
[17179572.484000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[17179572.500000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179572.500000] sda: Write Protect is off
[17179572.500000] sda: Mode Sense: 00 3a 00 00
[17179572.500000] SCSI device sda: drive cache: write back
[17179572.500000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[17179572.500000] sda: Write Protect is off
[17179572.500000] sda: Mode Sense: 00 3a 00 00
[17179572.500000] SCSI device sda: drive cache: write back
[17179572.500000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[17179572.552000] sd 0:0:0:0: Attached scsi disk sda
[17179572.868000] ide0: I/O resource 0x1F0-0x1F7 not free.
[17179572.868000] ide0: ports already in use, skipping probe
[17179572.868000] ide1: I/O resource 0x170-0x177 not free.
[17179572.868000] ide1: ports already in use, skipping probe
[17179572.928000] usbcore: registered new driver usbfs
[17179572.928000] usbcore: registered new driver hub
[17179572.928000] USB Universal Host Controller Interface driver v3.0
[17179572.928000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 225
[17179572.928000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179572.928000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179572.928000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179572.928000] uhci_hcd 0000:00:1d.0: irq 225, io base 0x0000bf80
[17179572.928000] usb usb1: configuration #1 chosen from 1 choice
[17179572.932000] hub 1-0:1.0: USB hub found
[17179572.932000] hub 1-0:1.0: 2 ports detected
[17179572.936000] ieee1394: Initialized config rom entry `ip1394'
[17179573.036000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 233
[17179573.036000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179573.036000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179573.036000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179573.036000] uhci_hcd 0000:00:1d.1: irq 233, io base 0x0000bf60
[17179573.036000] usb usb2: configuration #1 chosen from 1 choice
[17179573.036000] hub 2-0:1.0: USB hub found
[17179573.036000] hub 2-0:1.0: 2 ports detected
[17179573.140000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 50
[17179573.140000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179573.140000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179573.140000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179573.140000] uhci_hcd 0000:00:1d.2: irq 50, io base 0x0000bf40
[17179573.140000] usb usb3: configuration #1 chosen from 1 choice
[17179573.140000] hub 3-0:1.0: USB hub found
[17179573.140000] hub 3-0:1.0: 2 ports detected
[17179573.244000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 58
[17179573.244000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179573.244000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179573.244000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179573.244000] uhci_hcd 0000:00:1d.3: irq 58, io base 0x0000bf20
[17179573.244000] usb usb4: configuration #1 chosen from 1 choice
[17179573.244000] hub 4-0:1.0: USB hub found
[17179573.244000] hub 4-0:1.0: 2 ports detected
[17179573.348000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 225
[17179573.348000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179573.348000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179573.348000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179573.348000] ehci_hcd 0000:00:1d.7: debug port 1
[17179573.348000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179573.348000] ehci_hcd 0000:00:1d.7: irq 225, io mem 0xffa80000
[17179573.352000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179573.352000] usb usb5: configuration #1 chosen from 1 choice
[17179573.352000] hub 5-0:1.0: USB hub found
[17179573.352000] hub 5-0:1.0: 8 ports detected
[17179573.380000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179573.456000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 177
[17179573.512000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179573.596000] kjournald starting.  Commit interval 5 seconds
[17179573.596000] EXT3-fs: mounted filesystem with ordered data mode.
[17179574.136000] usb 2-1: new full speed USB device using uhci_hcd and address 3
[17179574.344000] usb 2-1: configuration #1 chosen from 1 choice
[17179574.788000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc0000af98961]
[17179585.036000] input: PC Speaker as /class/input/input1
[17179585.252000] hw_random: cannot enable RNG, aborting
[17179585.288000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179585.312000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179585.436000] Real Time Clock Driver v1.12ac
[17179585.480000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.616000] agpgart: Detected an Intel 945GM Chipset.
[17179585.636000] agpgart: AGP aperture is 256M @ 0x0
[17179585.692000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[17179585.732000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179585.808000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179585.812000]  1:0:0:0: Attached scsi generic sg1 type 5
[17179586.216000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[17179586.216000] sdhci: Copyright(c) Pierre Ossman
[17179586.216000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[17179586.216000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 66
[17179586.216000] mmc0: SDHCI at 0xef9fd400 irq 66 DMA
[17179586.244000] usbcore: registered new driver hiddev
[17179586.248000] input: Logitech Logitech USB Headset as /class/input/input3
[17179586.248000] input: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.1-1
[17179586.248000] usbcore: registered new driver usbhid
[17179586.248000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179586.256000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 233
[17179586.256000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179586.280000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[17179586.280000] Uniform CD-ROM driver Revision: 3.20
[17179586.280000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[17179586.316000] ts: Compaq touchscreen protocol output
[17179586.484000] usbcore: registered new driver snd-usb-audio
[17179586.824000] b44.c:v1.00 (Apr 7, 2006)
[17179586.824000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 217
[17179586.824000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:15:c5:be:e4:be
[17179587.952000] NET: Registered protocol family 17
[17179590.816000] lp: driver loaded but no devices found
[17179590.836000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179590.836000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179590.900000] Unable to find swap-space signature
[17179591.044000] EXT3 FS on sda4, internal journal
[17179591.220000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179591.220000] md: bitmap version 4.39
[17179591.396000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: dm-devel@redhat.com
[17179592.536000] Unable to find swap-space signature
[17179596.000000] ndiswrapper version 1.29 loaded (preempt=no,smp=no)
[17179596.152000] ndiswrapper (check_nt_hdr:159): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[17179596.152000] ndiswrapper (load_sys_files:217): couldn't prepare driver 'bcmwl5'
[17179596.152000] ndiswrapper (load_wrap_driver:119): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[17179596.152000] usbcore: registered new driver ndiswrapper
[17179597.916000] ACPI: AC Adapter [AC] (off-line)
[17179597.960000] ACPI: Battery Slot [BAT0] (battery present)
[17179597.968000] ACPI: Lid Switch [LID]
[17179597.968000] ACPI: Power Button (CM) [PBTN]
[17179597.968000] ACPI: Sleep Button (CM) [SBTN]
[17179598.072000] ibm_acpi: ec object not found
[17179598.096000] pcc_acpi: loading...
[17179598.164000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179598.168000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179598.168000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179601.208000] apm: BIOS not found.
[17179605.260000] Bluetooth: Core ver 2.8
[17179605.260000] NET: Registered protocol family 31
[17179605.260000] Bluetooth: HCI device and connection manager initialized
[17179605.260000] Bluetooth: HCI socket layer initialized
[17179605.288000] Bluetooth: L2CAP ver 2.8
[17179605.288000] Bluetooth: L2CAP socket layer initialized
[17179605.292000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
[17179605.312000] Bluetooth: RFCOMM socket layer initialized
[17179605.312000] Bluetooth: RFCOMM TTY layer initialized
[17179605.312000] Bluetooth: RFCOMM ver 1.7
[17179629.044000] NET: Registered protocol family 10
[17179629.044000] lo: Disabled Privacy Extensions
[17179629.044000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179629.044000] IPv6 over IPv4 tunneling driver
[17180316.880000] b44: eth0: Link is up at 100 Mbps, full duplex.
[17180316.880000] b44: eth0: Flow control is off for TX and off for RX.
[17180316.880000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180332.564000] eth0: no IPv6 routers present

```
Hopefully this helps (big file!).  Just an aside, I thought Edgy was dual core aware but I note my kernel is 2.6.17-10-386 and I believe dual core aware kernel is 686-smp correct?

---

### Post by FrodoB on 2006-12-02
Here is the problem, but what is the cause?

[17179596.000000] ndiswrapper version 1.29 loaded (preempt=no,smp=no)
[17179596.152000] ndiswrapper (check_nt_hdr:159): kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B
[17179596.152000] ndiswrapper (load_sys_files:217): couldn't prepare driver 'bcmwl5'
[17179596.152000] ndiswrapper (load_wrap_driver:119): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[17179596.152000] usbcore: registered new driver ndiswrapper


See: kernel is 32-bit, but Windows driver is not 32-bit;bad magic: 020B

What Windows drivers are you using? That would seem to be the issue.

---

### Post by flyingsolo on 2006-12-02
Thanks for all this help.  The windows drivers I got from Dell's site and it gives choices for XP-64 and XP.  I chose the latter, so would have assumed it was 32 bit.

---

### Post by FrodoB on 2006-12-02
I think you need to look on the ndiswrapper hardware list and see which ndis drivers are recommended.  Sometimes the latest ones do not yet work with ndiswrapper.

---

### Post by FrodoB on 2006-12-03
I could not find the device on the ndiswrapper hardware list. 

I did just find a post in Italian where someone has fixed your very problem. 

Take a look at this:
[http://translate.google.com/translate?hl=en&sl=it&u=http://www.archlinux.it/forum/viewpost.4031.html&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dbcm4328%2Bndiswrapper%26hl%3Den%26lr%3D%26sa%3DG]("http://translate.google.com/translate?hl=en&sl=it&u=http://www.archlinux.it/forum/viewpost.4031.html&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3Dbcm4328%2Bndiswrapper%26hl%3Den%26lr%3D%26sa%3DG")


The driver that they said works is here:
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

remove the existing driver with:

sudo ndiswrapper -r [COLOR=Sienna] bcmwl5

[/COLOR]
verify that it is gone:

ndiswrapper -l
[COLOR=Sienna]
[/COLOR]change into the directory where you extracted the new driver and install it:

sudo ndiswrapper -i bcmwl5.inf

Reboot and see if the output from dmesg looks better and if iwconfig shows the device now.


At least we know that someone has done it.

---

### Post by flyingsolo on 2006-12-04
Here again...I did as suggested above, removing old drivers from Dell and downloading the one you found etc and rebooting.  dmesg gives the following:
[COLOR="Sienna"][INDENT][17179762.584000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179762.604000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179762.604000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179762.628000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179762.628000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179762.632000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179762.672000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179762.672000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179762.672000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17179762.700000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179762.700000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
[17179762.700000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[/INDENT][/COLOR]
I should explain that since I last posted here, I found I was running the 386 kernel and so switched to the generic kernel to permit use of both cores on this dual core laptop.  Could that explain why dmesg shows me with ndiswrapper version 1.22 now instead of 1.29?

---

### Post by FrodoB on 2006-12-05
Yes, and I don't know whether your dual core system is going to work with ndiswrapper or not. It is best to change one thing at a time, otherwise you don't know what you really did that had an effect.

Go back to the single kernel system and the latest version of ndiswrapper and the ndis file tha the post recommended.  If we ever this this thing working you can try to go the new kernel afterwards.

---

### Post by flyingsolo on 2006-12-05
Sorry, I didn't mean to confuse things.  I reverted to the 386 kernel and removed the old driver, reinstalled the new one and have the following from dmesg (not the whole file, just the part about ndiswrapper)
[COLOR="Sienna"][17179596.452000] ndiswrapper version 1.29 loaded (preempt=no,smp=no)
[17179596.572000] ndiswrapper (load_wrap_driver:119): couldn't load driver bcmwl5; check system log for messages from 'loadndisdriver'
[17179596.572000] usbcore: registered new driver ndiswrapper[/COLOR]
and iwconfig still shows no wireless.

---

