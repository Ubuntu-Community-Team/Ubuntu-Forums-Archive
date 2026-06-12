---
title: "Seriously fed up! What is wrong with.. EVERYTHING?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Lucypie on 2011-08-02
Whoo hoo. Got Ubuntu and windows 7 installed. Already ****ed up again. What the HECK is wrong with me or ubuntu? I can't load firefox. Infact, I uninstalled and reinstalled. I had to get Midori just to get my internet browser back. I get errors galore when loading sudo nautilus, I reuploaded my home folder and now everytime I log in  I get errors. I'm SCARED to restart my system. I just installed GIMP and its better than ever. What the crap am I going to do? DId the installation eff up or is it just my computer? Would i be better off just sucking it up with my errors until I can get to a hotel, download a fresh version of Ubuntu and then do everything over again, reupdate and redownload ALL my programs AGAIN? I really don't know what I am asking. Its just all messed up! My system keeps freezing when I move my normal mouse, and i have to use touchpad just to move until my other mouse unfreezes. When I go into UbuntuClassic theme, it gives me some notification applet error. Please just give me something! I am scared I am near the max of my internet. There is no way I can download anything else. I have 2 HP Factory Image Recovery disks, a driver disk, an ubuntu 11.04 disk that boots after 200000000000 years, a ubuntu 10.10 disk that won't boot, a 10.04 disk SOMEWHERE that rarely boots, and a headache from this whole ordeal...

... All because I wanted a bit more room in Ubuntu by giving it a partition of its own

Sorry if I am not helpful at all. If you need any information, I will give you ANYTHING (other than credit cards, addresses, phone numbers, ss numbers or anything else unsensible. o_O)

---

### Post by new_tolinux on 2011-08-02
First of all, grab a beer and get some sleep ;)

Then, tomorrow, just have a look on what's actually working, and what's not....

As I read what you wrote, any answer yet won't bring you any further, since you're frustrated (understandable, but always a bad thing when you try to fix something)

---

### Post by kaldor on 2011-08-02
lol :)

So when did the problems start happening? Did it ever work properly? I am a bit confused because it sounds like a fresh dual boot, yet you mention at the end, "All because I wanted a bit more room in Ubuntu by giving it a partition of its own". What do you mean by that?

This isn't the usual experience for people using Ubuntu (or any OS). Could you give us the specs of the machine? Do that by pasting here the output of *lspci -v*.

---

### Post by Lucypie on 2011-08-02
Fresh everything. Fresh Windows because Ubuntu ****ed that up, Fresh Ubuntu cause Windows ****ed that up, Fresh EVERYTHING >_<

Heres the command you asked for. I also added some more after.
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0
	Memory at d2400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 40e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 40c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at d4505c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at d4500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d3500000-d44fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2500000-d34fffff
	Prefetchable memory behind bridge: 00000000d1400000-00000000d23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 40a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 4080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 4040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d4505800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43
	I/O ports at 4108 [size=8]
	I/O ports at 411c [size=4]
	I/O ports at 4100 [size=8]
	I/O ports at 4118 [size=4]
	I/O ports at 4020 [size=32]
	Memory at d4505000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: medium devsel, IRQ 11
	Memory at d4506000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 4000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: fast devsel, IRQ 11
	Memory at d4504000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d3500000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1484
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at 2000 [size=256]
	Memory at d1410000 (64-bit, prefetchable) [size=4K]
	Memory at d1400000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1420000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

df -h
```
alyssa@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              49G  2.7G   43G   6% /
none                  1.5G  732K  1.5G   1% /dev
none                  1.5G  288K  1.5G   1% /dev/shm
none                  1.5G  132K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda6             142G  1.4G  133G   2% /home
/dev/sdc1              38G   17G   22G  44% /media/Alyssa
/dev/sdd1             1.9G   69M  1.8G   4% /media/ALY 2G
alyssa@ubuntu:~$ 

```

free -m
```
             total       used       free     shared    buffers     cached
Mem:          2955       2576        379          0        113       1040
-/+ buffers/cache:       1422       1533
Swap:         7999          0       7999

```

top

(WAITAMINUTE, I don't even have compiz installed... wtfcake?)
```
top - 19:35:26 up  4:15,  2 users,  load average: 0.04, 0.07, 0.05
Tasks: 156 total,   1 running, 154 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.5%us,  3.5%sy,  0.0%ni, 92.9%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3026136k total,  2640984k used,   385152k free,   116184k buffers
Swap:  8191996k total,       48k used,  8191948k free,  1068196k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7245 root      20   0 86292  24m  11m S    7  0.8   1:35.92 Xorg               
 8980 alyssa    20   0 91240  13m  10m S    4  0.5   0:01.06 gnome-terminal     
 7405 alyssa    20   0 74740  15m 9832 S    2  0.5   0:24.01 compiz             
 7429 alyssa    20   0 38620  10m 8456 S    0  0.4   0:01.84 unity-window-de    
 8635 alyssa    20   0  227m  64m  27m S    0  2.2   0:46.64 midori             
 9042 alyssa    20   0  2632 1156  860 R    0  0.0   0:00.04 top                
    1 root      20   0  3024 1760 1216 S    0  0.1   0:00.65 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:01.29 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns              
   15 root      20   0     0    0    0 S    0  0.0   0:00.02 sync_supers        
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        

```

uname -a
```
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

Hopefully that will help some.

---

### Post by Lucypie on 2011-08-02
Alright, I fixed the startup error (which I may have forgotten to mention) and I fixed firefox. What i had to do was go into root and fix all my /home/ files to be able to be editted by ME. Read & Write. I still plan on the next time I go to a hotel I will be redownloading ubuntu, and all DEBs associated with me. xDThanks for the help guys!

---

### Post by jtarin on 2011-08-02
> **Lucypie said:**
>  I still plan on the next time I go to a hotel I will be redownloading ubuntu, and all DEBs associated with me.If your in the US, motels in the desert along I-10 are the best.

---

### Post by EkuquoL on 2011-08-02
Install Windows 7 with VM ware... 
Microsoft jacks with indexing and many bios routines... Kinda funny really . They force software and hardware developers to pay for contracts to show microsoft how all their topology works... Just to jack up indexing and boot commands in the bios.

---

### Post by pmooney78 on 2011-08-03
It's entirely possible that your file ownership problems are caused by running sudo <graphical programname>. Sudo is meant only for (text) commands that are run in a terminal. If you're trying to run a graphical program -- firefox, nautilus, anything that pops up windows and draws to the screen instead of spitting out text on a terminal -- you should use gksudo instead (or kdesudo if you're running KDE, e.g. in Kubuntu). It doesn't always cause problems, but sometimes it will, and it sounds like you're experiencing one of those problems with your permission errors.

The Psychocats site has an excellent explanation here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

That may not explain everything, but it's entirely possible that it's a contributing factor. Hope that helps.

---

### Post by sadaruwan12 on 2011-08-03
Best thing I see for you right now get some sleep and put a fresh Ubuntu ISO to get downloaded whiles you sleep then after you wake up then burn the ISO file on to a CD then please back up you /home folder but don't back up your hidden files and folders.

'Cos those hidden folders or files 'cos if you do that your problems might come back to haunt you due to those folders contain the user references for you software you use if they have an error then it'll come back to haunt you if you pates them in to the new installed system.

Now first you install ubuntu install windows after finishing that install the ubuntu system remember to redo all the partition table and after installation finishers update the system with out doing anything else after doing that start to tinker with your system.

Please, first sleep and let your frustrations to cool down.

---

### Post by jtarin on 2011-08-03
> **sadaruwan12 said:**
> Best thing I see for you right now get some sleep 

> **sadaruwan12 said:**
> Please, first sleep and let your frustrations to cool down.Got me dozing off....ZZZZZZZZZ:-$

---

### Post by sadaruwan12 on 2011-08-03
> **jtarin said:**
> Got me dozing off....ZZZZZZZZZ:-$

No, really bro he need to cool down and look at his post's they are full of anger also the F word has poped up thats bad for his karma. ;-)

---

### Post by Lucypie on 2011-08-03
I never used the f word xD I use ****ed which I pronounce as "star'd up" xD I don't cuss, I justl ike using stars xD No worries. I'm cool now.

Pmooney- Thanks for that info. I will now be using gksudo. I always wondered what the differences were. :)
EkuquoL - I have a factory image recovery disk. I don't know how to do that stuff :/ 


The deal with a factory image recovery disk is that it doesnt let you install windows, it comes up a box and says "Please do NOT connect ANY external devices or unplug the power source. Press next to continue" It then repartitions the ENTIRE drive, no way to "partition" it yourself. It uploads files to each, formats, and installs. :/

---

### Post by Mark Phelps on 2011-08-03
> **Lucypie said:**
> The deal with a factory image recovery disk is that it doesnt let you install windows, it comes up a box and says "Please do NOT connect ANY external devices or unplug the power source. Press next to continue" It then repartitions the ENTIRE drive, no way to "partition" it yourself. It uploads files to each, formats, and installs. :/

And ... that is what it is SUPPOSED to do!

Some OEMs provide restore disks that will allow you to boot into a command line; others provide some utilities as well. But, restoring the PC to it's original "factory condition" is the main purpose of the disk.

---

### Post by linuxford on 2011-08-03
I am a noob, but I have found that sometimes newer hardware can be problematic sometimes. I would recommend getting a computer that is a couple of years old or older and that you don't have anything important on, and install ubuntu. The software low-level drivers will have had time to mature and all the main programs like internet browsing should work just fine out of the box. 

Sometimes wireless connections or specialized software can get a little sticky, but Linux is free and tons of free, powerful software. It seems to take some tinkering at times when you want to do different stuff. I personally have all linux computers at home (I have done but don't do dual-boot anymore) and have one Windows computer just to run programs that I need that Wine doesn't handle well.

---

### Post by Rasa1111 on 2011-08-03
I have all the same Ubuntu discs and they all run perfectly.
Never have/had any of those problems when installing Ubuntu either.
On many, many machines. 
Got to be you or your machine, mate. 

Good luck

---

### Post by Baniita on 2011-08-03
Here's to my unhelpfulness.

But comradership.

I'm so. Freaking. Fed up. As well.

Everything goes wrong. /Everything./

I've already encountered 6286293 problems during my ubuntu experience. I:

I'm avoiding Natty Narwhydoyoudothistome at the moment.

---

### Post by akand074 on 2011-08-03
Did you burn your discs at the slowest possible speed?

---

### Post by linuxford on 2011-08-03
> **Baniita said:**
> Here's to my unhelpfulness.

But comradership.

I'm so. Freaking. Fed up. As well.

Everything goes wrong. /Everything./

I've already encountered 6286293 problems during my ubuntu experience. I:

I'm avoiding Natty Narwhydoyoudothistome at the moment.

I've found staying a generation or two can be helpful as well. I use Lucid Lynx and not only do you still have the cool menuing rather than the IPad like interface, mine is stable and even the earlier wireless problems I had earlier on in my Linux experience are resolved and they have good support now. Previously, I had to use this thing called Ndiswrapper which seemed to be a linux software wrapper that wrapped around a windows driver, and I got it to work for this broadcom wireless device driver but took some digging and some tinkering. 

If you use the latest piece of hardware and the latest Ubuntu, you may encounter issues.

I could never afford a MAC and always used PC clones so I found this Unity system with the MAC/Ipad feel not comfortable at this point. Perhaps if I had a MAC or with use, I may like it, but I don't care for it.

---

### Post by 3rdalbum on 2011-08-03
I think you need to run a memory test - some of what you're describing sounds like bad RAM. Live CDs that "rarely" boot? Either they boot or they don't - and if they *sometimes* don't then it's probably an intermittent problem such as the RAM.

---

