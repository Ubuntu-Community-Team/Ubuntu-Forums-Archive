---
title: "broadcom 4311  hardware drivers not recognize"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by jareddlc on 2008-05-11
ive tried so many ways to try to activate my wireless but none seem to work. i am alwasy stuck sincse hardware drivers or (restricted drivers) doesnot recognize my wifi. i installed b43fw-cutter and it downloads the correct firmware but it still doesnt appear, ive tried with ndiswrapper and nothing. any ideas?
 when i put an usb driver it works fine.

---

### Post by Jimmey on 2008-05-12
This is how I got mine working (it might not work for you)

Use the bcm43xx-fwcutter (note that it's NOT the b43-fwcutter) on the wlapsta.o driver you can download from various locations, and put the firmware files in /lib/firmware.

Restart the computer.

Then ```
sudo modprobe -r b43 && modprobe bcm43xx
```

Worked for me.

---

### Post by Ayuthia on 2008-05-12
> **jareddlc said:**
> ive tried so many ways to try to activate my wireless but none seem to work. i am alwasy stuck sincse hardware drivers or (restricted drivers) doesnot recognize my wifi. i installed b43fw-cutter and it downloads the correct firmware but it still doesnt appear, ive tried with ndiswrapper and nothing. any ideas?
 when i put an usb driver it works fine.

Can you post your lspci -nn information, your uname -r, and lshw -C network?  The rev 02 of the 4311 cards are not working in kernel 2.6.24-16 unless you use NDISwrapper.  The last portion will check to see which driver you are using.

---

### Post by jareddlc on 2008-05-13
well i used the bcm43xx and now it loads the LED light and well it shows that i wireless installed but i still cannot view the wireless or i still doesnot show up in hardware drivers, im getting near though, so i tried blacklisting b43 and removing bcm43xx from the blacklist, im going to try with ndiswrapper

---

### Post by jareddlc on 2008-05-13
so i just mest it up since i blacklisted and added a line to /etc/modules lol so now i can get the LED back on. anysuggestions and when i do get the led on it stays on only for that session why i turn off my pc it wont autoload

---

### Post by Ayuthia on 2008-05-13
> **jareddlc said:**
> so i just mest it up since i blacklisted and added a line to /etc/modules lol so now i can get the LED back on. anysuggestions and when i do get the led on it stays on only for that session why i turn off my pc it wont autoload

If you are using NDISwrapper, try this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").  Check out the section on Making it Permanent.

---

### Post by anomsuratno on 2008-05-14
Take a look at this [guide]("http://anomsuratno.wordpress.com")
It works.

---

### Post by SurferGTO on 2008-05-14
help. anyone.

> master@master-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: a2
       serial: 00:1d:72:48:08:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
master@master-laptop:~$ 


---

### Post by Ayuthia on 2008-05-14
> **SurferGTO said:**
> help. anyone.

You might try the link in post #6.  I have not seen the b43 drivers work with the BCM4310 (14e4:4315) cards.  That link has some driver options that might work for you.

---

### Post by SurferGTO on 2008-05-14
> You might try the link in post #6. I have not seen the b43 drivers work with the BCM4310 (14e4:4315) cards. That link has some driver options that might work for you

thank you very much, but ive tried that many many times (it would be step 2e) on many fresh installs both in gutsy and in hardy. I still cant get ndiswrapper to find my hardware. again i have no problems whatsoever installing or running ndiswrapper, it would appear. nor do i have a problem installing or finding the driver, or having ndiswrapper find the driver. ndiswrapper just doesnt find my hardware.

---

### Post by SurferGTO on 2008-05-14
> master@master-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: a2
       serial: 00:1d:72:48:08:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
master@master-laptop:~$ 




that is whats listed for *lswh -c network*

---

### Post by SurferGTO on 2008-05-14
the guide linked in post 6 says as a hardy bug, when lshw -c network is run, you want module listed as ndiswrapper and not ssb. mine, however says forcedeth. which sounds scary. to me anyway.

---

### Post by Jimmey on 2008-05-14
There's a bug in the network manager that means it won't report the device as working using the bcm43xx module even though it is. I had to configure my network manually using if/iwconfig.

---

### Post by Ayuthia on 2008-05-14
> **SurferGTO said:**
> the guide linked in post 6 says as a hardy bug, when lshw -c network is run, you want module listed as ndiswrapper and not ssb. mine, however says forcedeth. which sounds scary. to me anyway.

Yes.  If you cannot get it to work, you must forcedeth....  Sorry, bad joke.  Actually, that is the driver for your wired network card.  Yours is displaying UNCLAIMED which means that it currently does not have a driver.  You might want to check ndiswrapper -l to see if the driver that you are using is valid.  It should show driver (14e4:4315) present.

---

### Post by SurferGTO on 2008-05-14
haha i feel like forcing deth. upon my laptop. 

> master@master-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
master@master-laptop:~$ 



thats all it shows with ndiswrapper -l

---

### Post by SurferGTO on 2008-05-14
Great. i dont know why but i thought id try to use WICD as a network manager and see if i got any different results at all, and now i dont even have a WIRED connection. im using a verizon USB modem. 

WTF this is starting to really anger me. broadcom sucks. 150 bux to anyone in my area who can get this working in one day. argh!!

---

### Post by SurferGTO on 2008-05-14
ok i fixed it. the wired connection. still no wireless tho.

---

### Post by Ayuthia on 2008-05-14
> **SurferGTO said:**
> haha i feel like forcing deth. upon my laptop. 
> master@master-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
master@master-laptop:~$ 
thats all it shows with ndiswrapper -l
That means that it does not like the driver.  Is this the driver from step 2e (R174291.exe)?

From post 13 from this [link]("http://ubuntuforums.org/showthread.php?t=704088&page=2"), the poster states that roaming needs to be enabled in order to connect.  Of course, I don't think that this is going to solve your problem yet because we need to be able to get your wireless to see access points.  Also, they are using the driver in step 2e...

What company made your laptop?

---

### Post by SurferGTO on 2008-05-14
as far as i know yes it is the driver from step 2e. its an HP Pavilion dv2745se Notebook PC according to the product number

---

### Post by Ayuthia on 2008-05-14
> **SurferGTO said:**
> as far as i know yes it is the driver from step 2e. its an HP Pavilion dv2745se Notebook PC according to the product number
If you haven't tried this one yet, it is the XP driver for your laptop:
[ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe](ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe)

---

### Post by SurferGTO on 2008-05-14
ok, so i have that file, and i have the windows vista file, i run them using wine, and than what? still a bit of a noob here but im learnin quick.. after running them windows wireless drivers menu still doesnt have them listed....

---

