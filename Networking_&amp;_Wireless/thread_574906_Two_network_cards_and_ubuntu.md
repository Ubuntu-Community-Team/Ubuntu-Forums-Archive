---
title: "Two network cards and ubuntu?"
date: 2007-10-13
forum: Networking &amp; Wireless
---

### Post by xadloki on 2007-10-13
Hi,
At the moment I have a dual boot setup with windows XP and ubuntu, I've used Ubuntu for about a year. 
I've had to reinstall XP since I wanted to play some games, for me XP works but I need Ubuntu for some things that I don't feel comfortable in windows.

I have 2 network cards, a router and a Mac PC. Network card 1 connects to the router, and network card 2 connects directly to the Macs ethernet port.
Filesharing works well between XP and Mac, they both see eachother in the network. 
I wan't to do the same with Ubuntu. But first I can't even get web pages to load. 
I installed Ubuntu 7.10 yesterday, and tried it a bit and I could load web pages and the usual. 
Today I tried to change the Network settings to Static IP and the "Network settings" just froze for 3-4 minutes and then it changed the setting. 
After this point I could not connect to the internet so I switched it back to roaming mode, again it took several minutes for the change to happen.
I then tried to see if I could connect and google.com loaded, did some searches and it worked, however no other site loads, i tried yahoo, slashdot, 
ubuntuforums... nothing loads except google, although pidgin connects well.
I tried this before with 7.04 and had the exact same problem. 
After that I just gave up trying and did only minor things in Ubuntu since it was too much of a hassle to reboot each time. 
It was either that or removing the second network card which I tried and it was sort of working again... but I need to have this connection to the Mac and removing the card is not an option.

So I can't figure out what is going wrong here, some help would be appreciated.

---

### Post by jamieno10 on 2007-10-13
Similar problem for me.

I just received an 8 core mac pro and it has 2 ethernet cards. Exactly the same problem. I can connect to the web in OS X, but in Ubuntu 7.04 or 7.10, I can't. 

for me, Web access in the office is only via static IP settings and no I can't comment on DCHP.

I tried various things like using ifdown and ifup to set up the ethernet cards, looked at /etc/network/interface to see if everything is set up and still doesn't work.

As I have not been able to install/boot up ubuntu, these problems were encountered using the LiveCD.

This is currently hindering my attempts to install Ubuntu.

---

### Post by xadloki on 2007-10-14
bump..

---

### Post by xadloki on 2007-10-15
No-one has ANY suggestions to what the problem is? How complicated can it be to have 2 network cards ?

---

### Post by xadloki on 2007-10-16
I was able to solve part of my problem, which was that I could load a few pages (google, ibm.com) but most pages would not load, some pages I could ping that would respond like ubuntuforums.org but would not load in firefox, when I tried to ping ibm.com it would not respond but in firefox it would load...
Seems that this is a common problem since there are many posts about this... I found that instructed to type this into the command line
sudo ifconfig eth0 mtu 1400
that solved it right away... in my case it was eth1 instead of eth0 since I have 2 cards... and I'm not sure this has anything to do with the router but there is a mtu setting in my router that is set to 1400, your's might be different ? 
anyway the post I found this solution is this one [http://ubuntuforums.org/showthread.php?t=424394](http://ubuntuforums.org/showthread.php?t=424394)
hope this helps...

---

### Post by davit on 2007-10-16
Just did a Ubuntu Destop 7.10 install on a 2 net card pc. 
eth0 = (realtek) static ->internal,  and the (Davicom) eth1 = Dynamic -> internet

Cant seem to get the static to work, even after many changes manual and or via 
System-->Administration-->network.

[ I have a dual boot (ugh!) WinNT4 for a gateway/proxy which works, so I want to do the same for Ubuntu setup. First tried Ubuntu Server 7.10 yesterday but could not get both cards working either on that system so I reinstalled (clean) to a desktop 7.10, however, I was able to see the internet on the Server OK too. My Desktop configs see the Realtek Card OK, so I assume drivers are loaded. ]

---

### Post by davit on 2007-10-17
Well, after a night sleep, I tried again.

cp -i /etc/network/interfaces  /etc/network/interfaces_bk
sudo gedit /etc/network/interfaces

Modified with the following (assuming 192.168.0.1 is your internal network and DHCP is your internet link)


""""
   auto lo
   iface lo inet loopback

   iface eth1 inet dhcp
   auto eth1

   iface eth0 inet static
   address 192.168.0.1   
   netmask 255.255.255.0
   auto eth0

""""
and now all seems to work. However, there is the necessity to refresh the DNS, by unpluggin the wire for at least 10 seconds, so that a new Dynamic address is cleared, allocated and DNS is found.

Also, changes via user do not appear to save correctly, I believe it must be root or sudo. When changes are made then perform a complete network interface cycle. 

sudo ifdown -a
sudo ifup -a

IMPORTANT
I do not know why LOCATION name is not saved and where it is saved.

---

