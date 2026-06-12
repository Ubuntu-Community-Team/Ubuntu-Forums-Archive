---
title: "[SOLVED] Unable to aquire an IP address--Wired network"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by Dark Hornet on 2007-12-20
OK..heres the deal.  I have one machine set up with Ubuntu 7.10, working great.  I decided that I wanted to go 100% Ubuntu, so I popped in the live CD on my other box, and everything worked fine INCLUDING the internet and networking.  I thought great...so I installed it.  Now after reboot, I am unable to connect to anything.  My computer is unable to get an IP address from my router (even though my router seems to have assigned one).

I have tried many different things from the different posts on the forums, all with no luck--please help.

---

### Post by LennyO on 2007-12-21
I have had the same problem in Feisty and now Gutsy.  What I notice when I display the connection information in Network Manager is that all the information is zero (IP Address, DNS addresses, etc.).  I then disable the connection in Network Manager, wait about 15 seconds, and then enable the connection.  Now all the information is filled in correctly.  This has always worked for me.  I don't know why it doesn't connect at boot up even though it says that it is connected.  After disabling the connection I wait about 15 seconds before re-enabling it because I found that if you enable it too soon the system locks up.

---

### Post by ubutufan on 2007-12-21
First make a back-up of the file  /etc/network/interfaces. For example rename it interfaces.bak
Then edit the file and make sure that the only entries are
--------------------------------
auto lo
iface lo inet loopback
--------------------------------
Nothing else!!!!!!!!!!!!!!!!!!!!!!!!!

save this file as /etc/network/interfaces     Be careful not to confuse yourself with the .bak file

Reboot ubuntu
Let us know the outcome

---

### Post by fb314 on 2007-12-21
wired, or wireless ?

On my notebook (toshiba P200, quite new), I from times to times also loose my wifi connexion with gutsy. I have to unload then reload the network module to re-enable it.

And I just installed gusty on a brand new PC: the wired ethernet is ok until install. But as soon as I load the last available updates, the ethernet goes down. I'm still looking for why ...

---

### Post by darkrider2k6 on 2007-12-21
> **Dark Hornet said:**
> OK..heres the deal.  I have one machine set up with Ubuntu 7.10, working great.  I decided that I wanted to go 100% Ubuntu, so I popped in the live CD on my other box, and everything worked fine INCLUDING the internet and networking.  I thought great...so I installed it.  Now after reboot, I am unable to connect to anything.  My computer is unable to get an IP address from my router (even though my router seems to have assigned one).

I have tried many different things from the different posts on the forums, all with no luck--please help.

I'm having the exact same problem, and I haven't come across a solution yet. Have you tried booting from the LiveCD again? If you're able to get an IP address when booting from the CD, then take a look at your /etc/network/interfaces file and post it here.

Also, do you run into the same problem if you try a wireless connection? If your wireless connections work and your wired ones don't, then you might be having a driver issue.

---

### Post by gigaferz on 2007-12-21
have you tried using the terminal to find out whats going on?

type 
ifconfig
ifdown -a                                                 brings down all devices
ifup -a                                                     activates devices
sudo /etc/init.d/networking restart               well the name says it all
sudo dhclient eth0                                   this one will request an Ip address

your device can be eth0,eth1,ath0,wlan0,ra0 etc
if you are not sure type sudo lshw and check the network section 

this will help only if your ethernet card has been  detected by gutsy

---

### Post by darkrider2k6 on 2007-12-21
I tried reactivating and restarting everything as you suggest, but no luck: "No DHCPOFFERS received." 

Any other ideas?

---

### Post by Dark Hornet on 2007-12-21
Update--I tried everything I could think of/get off of the forums and web.  Nothing worked.  I did read in a few places that people where having issues with nVidia "forcedeth" modules loading, etc.  At any rate, I just went to the store and bought a D-LINK wired NIC.  (and I even verified that it is compatible with Linux)  no luck...I am getting the same issue. (No working leases in persistent database -sleeping).   

I put the live CD back in and took a look at things...my ./etc/network/interface file only shows two lines:

auto lo
iface lo inet loopback

EVERYTHING works great with the live CD--I even did an "lsmod" to check to see what modules the kernel was loading--I saved it to a flash drive to compare with the installed version.

So--I take the Live CD out, and boot normally--no internet.  I check my /etc/network/interface file, and it is identical to the one used by the live CD.  I did a "diff" on the lsmod from the live cd and the installation, and they are also exactly the same.

I am at a real loss here....the computer that I am using right now to type all of this is on the same network, and has the same release of Ubuntu...infact, the /etc/network/interfaces file is the same.

PLEASE HELP!

--one last thing...in looking at my router, it has located my NIC, and has even assigned an IP address through DHCP.  My router sees the MAC address of my NIC as well.

---

### Post by trobbins on 2007-12-21
I had a similar problem involving wired NICS failing to obtain leases from DHCP.  Do this: System > Administration > Tools > Network > Properties , uncheck "enable roaming mode" and set the interface to static or DHCP.

---

### Post by ubutufan on 2007-12-21
What wireless card are you using?

---

### Post by ubutufan on 2007-12-21
I am almost sure that "No DHCP offers" is a signal instigated by the router. I have seen that one before. is your router configured for DHCP or static?

---

### Post by Dark Hornet on 2007-12-21
My router is set up for DHCP.  I have tried rebooting the router as well....no luck.

---

### Post by gigaferz on 2007-12-21
hey try  like connecting the modem to the computer do not use the router, It happeend to me a while ago, that was the only way to get internet.
Then I turned off everything :computer modem router 
 I also pressed "reset" on the router.

 then turn on everyhting on again

---

### Post by Dark Hornet on 2007-12-21
I will try that out when I get home from work...the thing that is bothering me is everything works great on my other ubuntu box...why not this one?

---

### Post by Dark Hornet on 2007-12-22
--Well...it turns out the issue is not Ubuntu, not my NIC---it was my...wait for it...wait for it....Microsoft Router MN-700.  (i don't even remember where I got it...lol).   At any rate, I replaced it with a Linksys router I had laying around, and the problem is solved.

I did some research on the MN-700, and it turns out it does have some issues with DHCP from time to time....so thanks to everyone who has suggested different solutions.

---

