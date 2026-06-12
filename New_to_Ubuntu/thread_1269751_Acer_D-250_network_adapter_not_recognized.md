---
title: "Acer D-250 network adapter not recognized"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by deutschebag17 on 2009-09-18
Hi all:

I'm completely new to linux and have very, very limited experience with the OS.  I just bought an Acer Aspire One D-250 (the 1151 model) and installed the netbook remix version of ubuntu.  Everything on it works EXCEPT the ethernet and wifi.  I'm dual-booting, so I can confirm that the hardware functions properly (I'm posting this with the netbook).  I don't really know how to go about troubleshooting it, so if anybody can start pointing me in the right direction to get it working, that would be great.  I don't know what kinds of things I should be posting here to give more information about what's going on in linux, so directions would be great.

Thanks in advance, everybody.

---

### Post by vantsochev on 2009-09-18
Hi, and welcome to the forum. Please give output of the following command:

```
lspci
```


Thanks

---

### Post by deutschebag17 on 2009-09-18
Here it is:

	 	 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)  
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)  
 00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)  
 00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)  
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)  
 00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)  
 01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)  
 03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

---

### Post by vantsochev on 2009-09-18
Forgot to ask... Can you please give output of:

```
iwconfig
```

And also please mentioned which version are you using :)

---

### Post by deutschebag17 on 2009-09-18
Output was:

" 	 	 lo        no wireless extensions.  
 

 pan0      no wireless extensions. 



 "

 
And I installed version 9.04 netbook remix, the one that's currently available for download on the ubuntu website.

---

### Post by vantsochev on 2009-09-18
Okay then... Try the following:

```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by deutschebag17 on 2009-09-18
Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 E: Couldn't find package linux-backports-modules-jaunty

---

### Post by vantsochev on 2009-09-18
Open System>Administration>Software Sources and then check off all the boxes. Close and open terminal and type:

```
sudo apt-get update
sudo apt-get install linux-backports-modules-jaunty
```

If that doesn't work try searching for it in Synaptic.

---

### Post by deutschebag17 on 2009-09-18
Maybe I wasn't clear enough.  The ethernet and wifi are not functioning on my netbook, so the script failed to download anything because there is no network connection.  That's the problem I'm trying to solve.

---

### Post by vantsochev on 2009-09-18
Damn... Forgot about that, sorry. Then download the backports deb to some other PC and transfer them:

[ 32 bit](https://launchpad.net/ubuntu/jaunty/i386/linux-backports-modules-jaunty-generic/2.6.28.13.17)
[64 bit](https://launchpad.net/ubuntu/jaunty/amd64/linux-backports-modules-jaunty-generic/2.6.28.11.15)

Make sure you download the dependency and install that first.

---

### Post by deutschebag17 on 2009-09-18
Both links are dead.

"
There’s no page with this address in Launchpad.
                           If you got here from a link elsewhere on Launchpad,           sorry about that.           We’ve recorded the problem,           and we’ll fix it as soon as we can.         
                    Otherwise, complain to the maintainers of the page that linked here. 

"

---

### Post by vantsochev on 2009-09-18
Fixed.

---

### Post by deutschebag17 on 2009-09-18
Ok, so I have the file from that page saved to a thumb drive.  Where do I save it on my netbook?  And then what do I do with it?

---

### Post by vantsochev on 2009-09-18
Doesn't matter where you save it... just double click on it...

---

### Post by deutschebag17 on 2009-09-18
Double-clicked, and was presented with this error message:

"Error: Dependency is not satisfiable: linux-backports-modules-2.6.28-13-generic"

---

### Post by vantsochev on 2009-09-18
If you go back to the Launchpad you will find the binary packages.

---

### Post by deutschebag17 on 2009-09-18
Okay, so I"m looking at the launchpad page, and there's a couple of options here.  I downloaded the [linux-backports-modules-jaunty-generic_2.6.28.13.17_i386.deb]("http://launchpadlibrarian.net/27518524/linux-backports-modules-jaunty-generic_2.6.28.13.17_i386.deb") file.  What else on the page do I need to download and run to make it work?

---

### Post by deutschebag17 on 2009-09-18
Also, a little poking around revealed that I'm running 2.6.28-11-generic (at least that's what comes up in the terminal when I type "uname -a").  And I can't update because the network adapter on it isn't working, so there's no way to connect to the internet to update.

---

### Post by seshomaru samma on 2009-09-19
Hi

There might be a solution for you [here ]("http://ubuntuforums.org/showpost.php?p=7821376&postcount=6")

---

### Post by deutschebag17 on 2009-09-19
Thanks for the help.  I've been poking around and discovered that particular thread and couldn't follow it to save my soul.  Problem is, I still don't know any of the code stuff to be able to run any of what you've written below to do.  Can somebody walk me through that?

---

### Post by seshomaru samma on 2009-09-19
well you go to this site:
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
look for a driver called 
AR81Family-linux-v1.0.0.10.tar.gz
and download it
now put it in your home directory
next open your terminal
and input those commands one by one:
```
$ gunzip AR81Family-linux-v1.0.0.10.tar.gz
$ tar xvf AR81Family-linux-v1.0.0.10.tar
$ cd src
$ make
$ sudo make install
$ cd /lib/modules/2.6.28-11-generic/kernel/drivers/net/atl1e/
$ sudo insmod ./atl1e.ko
```
the only problem i can foresee is that ubuntu might complain that you don't have the right compiling tools to run the make install command. I don't know if the netbook remix contain such tools. If you encounter this problem, let me know, you will probably need to download the 'build essential' package from the ubuntu repositories (you need to know what version of ubuntu you are running)

---

### Post by deutschebag17 on 2009-09-20
Okay, that got it to work.  I can access the internet now.

That being said, I'm still running into problems when I try to download anything.  The updater application hangs at the same place each time, and whenever I try to download anything, it's like the adapter starts working.  I can confirm that it's NOT the network to which I'm connected, because under windows on the same machine and under leopard on a different machine, everything works just fine.  Is this fixable?

---

### Post by seshomaru samma on 2009-09-20
Not sure I understand 
Can you download stuff with firefox? or torrents ?
Are you referring to the software update application in Ubuntu?
Instead of using that, open the terminal and run these two commands:
```
sudo apt-get update
sudo apt-get upgrade
```
paste any errors

---

### Post by deutschebag17 on 2009-09-20
No errors come up, but it just hits a point halfway through and ceases to make any additional progress in one of the downloads.  And I know the network is fine because I'm posting this post on a different computer while I stare at the terminal.

---

### Post by deutschebag17 on 2009-09-20
error messages just started rolling in:

"err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
        Could not connect to us.archive.ubuntu.com:80 (91.189.88.140). - connect (113 No route to host)"

This has happened a couple of times with a bunch of different things, before the screen said that each individually couldn't be fetched.

---

### Post by deutschebag17 on 2009-09-20
And now to add to that: after things fail to download, I tried to use the internet again - no dice.  A message came up as I was waiting for Google to load that said that there was no ethernet connection, the same message that I was presented with BEFORE the new driver was installed.

---

### Post by seshomaru samma on 2009-09-21
Sorry ,all I can say is that the driver is probably not working properly and suggest a reinstall of the driver.

---

### Post by arasbm on 2009-10-07
Hi,
Have your problem been fixed? I just bought the same laptop (Aspire One D-250) and had the same problems as you so far. following the instruction above I installed the driver, and the wired network now comes up, but I still dont have wireless. Do you have wireless woking? 
I might return the laptop if this is not an easy fix.

---

