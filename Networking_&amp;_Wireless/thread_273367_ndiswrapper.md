---
title: "ndiswrapper"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by ckonrad on 2006-10-07
I have ndiswrapper installed and it seems pretty easy to use, but where do i get the .INF driver file? I downloaded my wireless driver from many different places on the internet and there is never an .INF file, they are always .EXE and ndiswrapper never sees any .INF files with those downloads.

Thanks

---

### Post by wieman01 on 2006-10-08
The .EXE is a zip file and contains all the relevant files including .INF. Just do...
> unzip [COLOR="Red"]your_file.exe[/COLOR]
...and you should be able to see all the files you need.

When you deploy the Windows driver using "ndiswrapper" please make sure that all driver files (not only .INF) are in one directory. Otherwise the installation will fail. Seen this a million times before, that's why I am mentioning it here.

---

### Post by ckonrad on 2006-10-08
> **wieman01 said:**
> The .EXE is a zip file and contains all the relevant files including .INF. Just do...

...and you should be able to see all the files you need.

When you deploy the Windows driver using "ndiswrapper" please make sure that all driver files (not only .INF) are in one directory. Otherwise the installation will fail. Seen this a million times before, that's why I am mentioning it here.


Thanks for the info but i tried that, it doesnt work. 

End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of sp29332.exe or
        sp29332.exe.zip, and cannot find sp29332.exe.ZIP, period.

I think my best bet would be to get one of those Belkin wireless cards with the ralink opensource chipsets, they are only like $40

---

### Post by wieman01 on 2006-10-08
Then try to open it with Windows. Perhaps it contains another .EXE archive.

---

### Post by ckonrad on 2006-10-08
> **wieman01 said:**
> Then try to open it with Windows. Perhaps it contains another .EXE archive.


Ok, that worked, it took me awhile to figure out how to unzip the exe i basically had to install it a windows system to get it to unzip.

I have the driver installed on ubuntu, but i still cant get the wireless to work, what am i missing?

thanks

---

### Post by Titus A Duxass on 2006-10-08
What have you done so far?
What does ndiswrapper -l give you?
Have you put ndiswrapper in /etc/modules?

We need more information!

---

### Post by ckonrad on 2006-10-08
> **Titus A Duxass said:**
> What have you done so far?
What does ndiswrapper -l give you?
Have you put ndiswrapper in /etc/modules?

We need more information!

ndiswrapper -l shows

ckonrad@ckonrad-laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

i dont have an etc/modules directory, there is no modules file

i do have an etc/network file that shows the interfaces....i understand most of what needs to go into that file from what it says on this wiki [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu) but i dont understand what to put for wireless_nick

thanks

---

### Post by Titus A Duxass on 2006-10-08
Okay so your drivers are loaded okay.
You do have modules file, just that you cannot see with the gui.  Go into a terminal and do "sudo nano /etc/modules" and add ndiswrapper to the bottom of the file.

Ignore wireless_nick, it's the nickname for your wireless (if you have one).

Try turning off all security at first, get the card up and running then add security.

Make sure you have disable any other network cards (on-board), I do this through BIOS.

---

### Post by wieman01 on 2006-10-08
If "ndiswrapper -l" does not complain, your driver should be alright by now. Can you post the output of the following commands please?
> ifconfig
> iwconfig
> iwlist wlan0 scan
> sudo gedit /etc/network/interfaces
Then please also tell us a bit more about your configuration e.g. DHCP, Static Leases, WEP or WPA, etc.

---

### Post by ckonrad on 2006-10-08
> **wieman01 said:**
> If "ndiswrapper -l" does not complain, your driver should be alright by now. Can you post the output of the following commands please?

Then please also tell us a bit more about your configuration e.g. DHCP, Static Leases, WEP or WPA, etc.

ckonrad@ckonrad-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:C9:F0:9B
          inet addr:192.168.2.58  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fec9:f09b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6332579 (6.0 MiB)  TX bytes:524269 (511.9 KiB)
          Interrupt:209 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

ckonrad@ckonrad-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ckonrad@ckonrad-laptop:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

ckonrad@ckonrad-laptop:~$ sudo gedit /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhc

I just use wireless wherever, so i would like to setup dynamic ip, i do use wireless at home with a key.

---

### Post by Titus A Duxass on 2006-10-08
Try disabling eth0 through BIOS.

Your interfaces file looks okay, but your wireless card is not coming to life.

Do you have an lights flashing on the card?

---

### Post by wieman01 on 2006-10-08
Ok, can you try this please:
> iwlist eth1 scan
Apparenly your wireless card has been recognized... Not sure if you need "ndiswrapper" at all. "wlan0" is reserved for "ndiswrapper" and "eth1" (next to others) for the native driver(s).

---

### Post by ckonrad on 2006-10-08
> **wieman01 said:**
> Ok, can you try this please:

Apparenly your wireless card has been recognized... Not sure if you need "ndiswrapper" at all. "wlan0" is reserved for "ndiswrapper" and "eth1" (next to others) for the native driver(s).

no LED light
ckonrad@ckonrad-laptop:~$ iwlist eth1 scan
eth1      No scan results

i cant figure out how to save the changes to /etc/modules, i choose Y to save the changes but it never does.

---

### Post by Titus A Duxass on 2006-10-08
How are you editing the file with pico or nano or what?

With pico or nano simply Ctrl+X and then confirm savings with Y.

---

### Post by ckonrad on 2006-10-08
> **Titus A Duxass said:**
> How are you editing the file with pico or nano or what?

With pico or nano simply Ctrl+X and then confirm savings with Y.

yeah that is exactly what i am doing, but it never saves my change e.g everytime i open it up the ndiswrapper i added to the bottom is gone.

##never mind i got it to save, you have to also press enter to get back to the regular terminal still looks like no wireless though.

---

### Post by Titus A Duxass on 2006-10-08
Are you doing a cold start or just reboot?

As a last resort power down and switch power off, remove wireless card, power back up, power down but do not remove the power connection, replace card, reboot.  I have to do this when I have disconnected the power lead from my pc.

---

### Post by ckonrad on 2006-10-08
> **Titus A Duxass said:**
> Are you doing a cold start or just reboot?

As a last resort power down and switch power off, remove wireless card, power back up, power down but do not remove the power connection, replace card, reboot.  I have to do this when I have disconnected the power lead from my pc.

i cant remove my wireless its attached to the motherboard i'm not using a card. I'll restart my system and see if that does anything though.

---

### Post by ckonrad on 2006-10-08
> **ckonrad said:**
> i cant remove my wireless its attached to the motherboard i'm not using a card. I'll restart my system and see if that does anything though.

well after i restarted my internet didnt work at all not even the ethernet i was using before....i dont know i think i am going to scratch this ndiswrapper idea it doesnt seem like a very elegant solution. I'll just go pick up one of those wireless adapters that work out of the box with ubuntu and hopefully i wont have any issues with it. 

Thanks for all the help.

---

