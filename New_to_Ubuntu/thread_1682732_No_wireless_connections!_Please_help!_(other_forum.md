---
title: "No wireless connections! Please help! (other forums don't make sense)"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Halo0125 on 2011-02-06
I have looked up countless forums and nothing is answering my question to the slightest degree. I have an HP G62-455DX running Ubuntu 10.10. When I go to connect to the internet wirelessly, NO CONNECTIONS SHOW AT ALL! Not just my connection, none. It shows nothing. My only options are "Wired Network disconnected VPN Connections >" NOTHING! I don't understand how to get a driver for my wireless card, or how to even see if its seeing my wireless card! I've had countless computers and a laptop run ubuntu, and have never ever had this problem! Somebody please help!

---

### Post by jd2012 on 2011-02-06
Hi, open a terminal window (Applications > Accessories > Terminal) and type

```

sudo ifconfig

```Post the output, and:

```

sudo lshw -C network

```Post the output.

---

### Post by Halo0125 on 2011-02-06
I don't understand what you mean. I typed in the commands and what not, and a bunch of stuff comes up, and I don't know what to do with any of it...

---

### Post by firebird_1979 on 2011-02-06
> **Halo0125 said:**
> I don't understand what you mean. I typed in the commands and what not, and a bunch of stuff comes up, and I don't know what to do with any of it...

He was asking you to open Terminal, and execute those commands. Then copy and paste the output those commands give you back here. So we can see what's going on with your system.

---

### Post by bkratz on 2011-02-06
He/she wants you to copy/paste the results back in your response.

---

### Post by Halo0125 on 2011-02-06
halo0125@synesthesia:~$ sudo ifconfig 
[sudo] password for halo0125: 
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:8d:a0:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB) 

halo0125@synesthesia:~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Network controller 
       product: RaLink 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:d3400000-d340ffff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth0 
       version: 02 
       serial: 98:4b:e1:8d:a0:b8 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:42 ioport:2000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff 
halo0125@synesthesia:~$

---

### Post by Harker86 on 2011-02-06
I'm new to all this but I had this problem myself, but mine was more stupid, I forgot to turn my wireless switch on (most new laptops have a switch on the keyboard or on the side of the laptop)

---

### Post by Halo0125 on 2011-02-06
I don't have a switch. My function 12 key has i wifi symbol on it, and an orange light, and i've pressed it and nothing happens. Also, before I loaded ubuntu I had windows 7 and didn't have to press it or anything for the wifi to work.

---

### Post by Halo0125 on 2011-02-06
Ps, i got the orange light to go blue... still nothing :(

---

### Post by Harker86 on 2011-02-06
well blue is good as it means its on so you no the card works hardware side, so like you suggested its a driver problem, I'm running 10.10 and it automatically installed the right drivers for my laptop (also a HP)

---

### Post by Jetso on 2011-02-06
Could you please post the output of ```
sudo lspci
```? That would help us identify your wireless card.

---

### Post by Halo0125 on 2011-02-06
Certainly:


halo0125@synesthesia:~$ sudo lspci
[sudo] password for halo0125: 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: RaLink Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
halo0125@synesthesia:~$

---

### Post by jd2012 on 2011-02-06
It seems your not the only one with this problem..

[http://ubuntuforums.org/showthread.php?t=1680039](http://ubuntuforums.org/showthread.php?t=1680039)

But perhaps this thread might shed some light?

[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

Didnt read much just kinda skimmed...

---

### Post by Halo0125 on 2011-02-06
I have no idea which one to download though...

---

### Post by jd2012 on 2011-02-06
> **Halo0125 said:**
> I have no idea which one to download though...

[U][http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Top selection, the one with 5390 in the filename ([/U][RT5390PCIe]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTNNVFl4TkRrMk1TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUTFNemt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D"))
[U]

[/U][]("http://www.filedropper.com/20101217rt5390linuxstav2404wifibtcombodpo")

---

### Post by Halo0125 on 2011-02-06
Okay i'm getting a little closer...i'm at the point is says run command "make" where do i do that at?

---

### Post by jd2012 on 2011-02-06
> **Halo0125 said:**
> Okay i'm getting a little closer...i'm at the point is says run command "make" where do i do that at?


In the terminal window, if you cd'd to the driver directory, and followed all the previous instructions.

*Edit* After you cd to the dir just type "make" without quotations, and hit enter.

---

### Post by Halo0125 on 2011-02-06
Please assume i'm 100 percent incompetent because I essentially am.
i put it in the terminal, and it said something along the lines of no target specified...If I cd'd to the driver directory-I don't know what that means.

---

### Post by Mbroadstone on 2011-02-06
You have a realtek 8101/8102 wireless card and you need to install a driver.  Go to the terminal and put in the following commands.  You need to be connected via you wired connection in order to download these files (I assume your wired connection works, just like mine did)
 
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

 
Now bear in mind that this will work until you update Ubuntu.  If it doesn't work the first time it will if you use a fresh install.  I am still working on the update problem, or I should say, I am hoping that someone else will post a solution (I am a total newbie).  If you find a fix for this update issue please let me know, I'll do the same if someone answers it in my thread.
 
Mbroadstone

---

### Post by jd2012 on 2011-02-06
Yes plz post back if the above solution works.

---

### Post by Halo0125 on 2011-02-06
after it was done and i unplugged my wire, it still isn't working... so i just re-install ubuntu and put it in again?

---

### Post by jd2012 on 2011-02-06
Try unplugging the wire, rebooting THEN see if the driver update worked.

If that doesnt work (If it was me) I would proceed to follow the instructions on the forum I posted.

THEN if THAT doesnt work, you could always try booting from live cd and see if things work there.

If all that fails, then perhaps maybe someone else more experienced can shed some light.

---

### Post by Halo0125 on 2011-02-06
Well I rebooted, which prompted me with updates... still no wifi though... I don't understand the instructions for the other forum. I got to the part where it said type make as a command, and when i did that, it said target not specified and there was no makefile.

---

### Post by Halo0125 on 2011-02-07
*sigh* I've tried several things and nothing is working, it's always something with Ubuntu. I don't see why people give windows a bad name. My windows buggs out so much less than my linux usually does.

---

### Post by Jetso on 2011-02-07
Okay so if you can, do a clean install. That will help alot. Now get the file that jd2012 told you about. In the terminal ( Applications > Accesories >Terminal) type ```
unzip <filename here>.zip 
``` Replace the <> with the name of the file you downloaded. Then type```
cd <filename here>
``` Once again, replacing <> with the filename. Then do ```
sudo make
``` and ```
sudo make install
``` I think that will work. 

A example: ```
unzip driverfile.zip
cd driverfile
sudo make
sudo make install
```

---

### Post by Halo0125 on 2011-02-08
I have no idea which file you're talking about. Are you talking about the whole zipped folder?

---

### Post by Halo0125 on 2011-02-08
NVM...it just says no such file. I give up.

---

### Post by Jetso on 2011-02-09
Okay, I downloaded the file, so I know what to do. 

1.) Re-download the whole file. Make sure it goes to your downloads folder.
2.) Open Terminal
3.) ```
 cd Downloads 
```
4.) ```
unzip 2010_1217_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.zip 

```
5.) ```
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/
 
```
6.)```
make
```
7.)```
make install
```

---

### Post by Halo0125 on 2011-02-09
I get an error when I try make install

---

### Post by Halo0125 on 2011-02-09
make: *** [install] Error 2
halo0125@halo0125-laptop:~/Downloads/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO$

---

### Post by Dojan on 2011-02-16
Try doing exactly what he said, but when you have just opened the terminal, before you go on an do the other stuff, write:

```
sudo su 
```
and then enter your password at the prompt.

hope it helps...

---

