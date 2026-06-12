---
title: "ATTENTION GURU'S: Installing Windows XP Pro (Frustrating)"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by CharlesWelsh on 2009-07-11
I have searched this vigorously and found threads only with trial and errors so far. I am curious... without any maybes or trials with error... is there a way for me to do this and not have to delete my Jaunty Jackalope setup and configuration/ current installation. If not, I'm throwing my iPod away. I only want windows for iTunes. Thanks in advance. 
*This should be LOADS of fun :popcorn:

---

### Post by IHeequ5i on 2009-07-11
If your system has the horsepower, you might think about running XP in a VM when you want access to your iTunes. 

Otherwise...
Are you wanting to install XP on the same physical hard drive as your Jaunty install, or will you be installing it on a separate drive? 

Do you have an OEM CD for XP or will you be using a recovery disk?

Please post your system specs.

Also, there are no absolutes in the world of OS installs. The best we can do is tell you what we have done that has worked for us.

---

### Post by CharlesWelsh on 2009-07-11
I dunno how to even give you any of the information you just requested... I'm sorry. I am a week long user so far.

---

### Post by HermanAB on 2009-07-11
Howdy,

See the Virtualization forum.

Install Virtualbox, create a new Virtual disk and install Windows XP in that.  That way, you'll have Windows running inside a window where it belongs.  

It is much easier than it sounds!

---

### Post by sailthesea on 2009-07-11
> **CharlesWelsh said:**
> I have searched this vigorously and found threads only with trial and errors so far. I am curious... without any maybes or trials with error... is there a way for me to do this and not have to delete my Jaunty Jackalope setup and configuration/ current installation. If not, I'm throwing my iPod away. I only want windows for iTunes. Thanks in advance. 
*This should be LOADS of fun :popcorn:

 If you found your way round everything else this quickly you're doing ok
 Maybe VM your iTunes but I'd throw that iPod away and get something you can actually USE in the real world;)

---

### Post by nhasian on 2009-07-11
wait, dont Rhythmbox, Amarok, and songbird music players all support ipods?

also as Doomspark mentioned, if you need to install an additional operating system on your computer we need additional information to be able to help you.  installing an OS requires a fair amount of computer knowledge, especially when your setting up a dual boot system.

open a terminal and type:

```
df -h
```

```
sudo fdisk -l
```

```
lshw
```

and post back the results here.

---

### Post by CharlesWelsh on 2009-07-11
Okay... something is going on here... Something is wrong with my terminal and which virtualbox package do i install? Look at the screenshots... Normally my terminal says something like CJ's Laptop@... somethin like that...

terminal works now

---

### Post by CharlesWelsh on 2009-07-12
Check out this link and tell me what you think. And if so... I need help. LOL I think ill eventually get the help I need... I always do here on the Ubuntu Forums. :)

[http://ubuntuforums.org/showthread.php?t=1210746](http://ubuntuforums.org/showthread.php?t=1210746)

---

### Post by CharlesWelsh on 2009-07-12
laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  4.1G   21G  17% /
tmpfs                 241M     0  241M   0% /lib/init/rw
varrun                241M  200K  241M   1% /var/run
varlock               241M     0  241M   0% /var/lock
udev                  241M  148K  241M   1% /dev
tmpfs                 241M   76K  241M   1% /dev/shm


Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7da97da9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3492    28049458+  83  Linux
/dev/sda2            3493        3648     1253070    5  Extended
/dev/sda5            3493        3648     1253038+  82  Linux swap / Solaris



    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 495MiB
     *-cpu
          product: Mobile Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 15.2.9
          size: 350MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KiB
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-system:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-system:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-network
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:91:56:c2
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 module=yenta_socket
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
     *-network
          description: Wireless interface
          product: AR2413 802.11bg NIC
          vendor: Atheros Communications Inc.
          physical id: 0
          bus info: pci@0000:02:00.0
          logical name: wmaster0
          version: 01
          serial: 00:15:e9:5e:f0:c5
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath5k ip=192.168.0.4 latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:62:5e:95:c1:a7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



all of this nonsense to me is supposedly what you all need. enjoy ^^

---

### Post by nhasian on 2009-07-12
well if you want to go the virtualbox route, you will be happier with the version from their website as it supports USB whereas the open source version in the repos does not:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

based on the output you provided we can see you have in your computer:

Intel Celeron 2.40GHz
30.0 GB (you can forget virtualbox or dual booting at this point not enough hd space for multiple operating systems)
495MiB Ram

getting more ram and a bigger hard disk would make your ubuntu experience significantly better.

---

### Post by steveneddy on 2009-07-12
> **CharlesWelsh said:**
> Okay... something is going on here... Something is wrong with my terminal and which virtualbox package do i install? Look at the screenshots... Normally my terminal says something like CJ's Laptop@... somethin like that...

terminal works now

First of all, remember that all you have to do to Copy and Paste in Linux is to highlight what you want to copy, then go to the terminal and press the scroll button down. Highlighting will automatically copy and the scroll button press will paste. Easy - now.....

go to the virtualbox website and **install version 3.0**

[COLOR=Red][B]do not use the version in the repos
[/B][/COLOR] 
First in terminal:

```
sudo apt-get install dkms

```Look - go here:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

add one of these lines to the end of your sources.list

```
gksudo gedit /etc/apt/sources.list
```Copy and paste ONE LINE from this list. Just pick the Ubuntu version you are running:

```
[B]deb http://download.virtualbox.org/virtualbox/debian [COLOR=Red]jaunty[/COLOR] non-free
deb http://download.virtualbox.org/virtualbox/debian [COLOR=Red]intrepid[/COLOR] non-free
deb http://download.virtualbox.org/virtualbox/debian [COLOR=Red]hardy[/COLOR] non-free
deb http://download.virtualbox.org/virtualbox/debian[COLOR=Red] gutsy[/COLOR] non-free[/B]
deb http://download.virtualbox.org/virtualbox/debian dapper non-free
deb http://download.virtualbox.org/virtualbox/debian lenny non-free
deb http://download.virtualbox.org/virtualbox/debian etch non-free
deb http://download.virtualbox.org/virtualbox/debian sarge non-free
deb http://download.virtualbox.org/virtualbox/debian xandros4.0-xn non-free
```OK - now in terminal do this:

Just remember to copy and paste - OK?

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```and finally
```

apt-get install virtualbox-3.0

```and you're done

It will automatically update for you when a new version is available.

Easy peasy

---

### Post by steveneddy on 2009-07-12
Yes - I answered your post here:

[http://ubuntuforums.org/showpost.php?p=7601830&postcount=10](http://ubuntuforums.org/showpost.php?p=7601830&postcount=10)

---

### Post by ericab on 2009-07-12
CharlesWelsh

1 thread is enough dude

---

### Post by andrea000 on 2009-07-14
virtual box 3 is a great piece of software just
download the version from there website [here]("http://www.virtualbox.org/")

---

### Post by binbash on 2009-07-15
Yes it will solve your problem.

---

