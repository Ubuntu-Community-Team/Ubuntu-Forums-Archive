---
title: "ndiswrapper claims its working zv5000"
date: 2005-09-08
forum: Networking &amp; Wireless
---

### Post by asimon623 on 2005-09-08
my latest problem is the latest post

0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

bcm43xx.cat     invalid driver!
bcmwl5  driver present, hardware present
bcmwl5a.ini     driver present, hardware present
bcmwl5.sys      invalid driver!
bcmwld2k.exe    invalid driver!
bcmwlhoa.ini    invalid driver!
bcmwlhom.ini    invalid driver!

I tried ndiswrapping some other files to see if that would help...which it didn't. 

This is for a hp zv5240us laptop internal card. The internal wifi light is not on. 

the command modprobe ndiswrapper gives a FATAL error message


any ideas?

---

### Post by Steve1961 on 2005-09-09
Are you using the ndiswrapper version from synaptic or have you compiled version 1.2?  The newer version works much better with the driver that seems to be the correct one for your card - bcmwl5a.inf. I've used this with a broadcom card using the same driver and it works fine.  Also, have you made sure that the .sys file is in the same directory as the .inf file.

---

### Post by asimon623 on 2005-09-09
I dont know what i have any more in terms of ndiswrappers...ive used the deb package and ive also used synaptic and alo apt-get install 

my problem seems to come when i type modprobe ndiswrapper

i get a fatal error saying Module ndiswrapper not found

I dont know if I need to be in a certain directory when typing that or what, but it doesn't work. I've read something about headers and kernel being wrong but I dont know what that means

---

### Post by Steve1961 on 2005-09-09
Right, it's time to do a cleanup and start again.

Go into the terminal and type:

sudo ndiswrapper -e bcmwl5a  - *and repeat for each of the drivers you have loaded*
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Then start again, but download version 1.2 of ndiswrapper.  This is how I installed it:


[http://ubuntuforums.org/showthread.php?p=334239#post334239](http://ubuntuforums.org/showthread.php?p=334239#post334239)

Make sure you have the right drivers.  You can extract them from your CD of from a windows installation that they're installed on.  Alternatively, download the latest driver package and get them from there.

---

### Post by asimon623 on 2005-09-09
sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules

---

### Post by Steve1961 on 2005-09-09
My mistake, if you haven't been able to modprobe ndiswrapper you just need to uninstall the drivers from ndiswrapper and then remove ndiswrapper ultils.

---

### Post by asimon623 on 2005-09-09
ok and 1.2 isn't available anymore...is 1.3 ok to install?

---

### Post by asimon623 on 2005-09-09
installing 1.3


root@alexlaptop:/home/alex/Desktop/ndiswrapper-1.3rc1 # make
make -C driver
make[1]: Entering directory `/home/alex/Desktop/ndiswrapper-1.3rc1/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/alex/Desktop/ndiswrapper-1.3rc1/driver'
make: *** [all] Error 2

---

### Post by asimon623 on 2005-09-09
up

thanks for the help so far, it seems like Im so close

---

### Post by Steve1961 on 2005-09-10
Did you start by installing these packages:

sudo apt-get install debhelper build-essential fakeroot linux-headers-$(uname -r)

Also, go into synaptic and see if there's an ndiswrapper-modules package you can install - first make sure you have universe, multiverse and backports enables.  I thought this was installed by default but if not just install it and try again.  You're nearly there.

Looks like they've just removed 1.2 - it was there a fortnight ago - but 1.3 should be fine.

---

### Post by asimon623 on 2005-09-10
delete post

---

### Post by asimon623 on 2005-09-10
got it to work using instructions from another site...i had to make deb from the ndiswrapper thing i downloaded and then install the utils and modules produced by that

now ive got a new problem...when I restart, i get an error on the networking thing in the upper right corner that stflag something something device not found...I run modprobe ndiswrapper...this goes away

then i do dhclient wlan0  and it tries to obtain an address from 255.255.255.255 which I dont understand

If I just enter
192.168.2.9
255.255.255.0
192.168.2.1

as static....I can access the internet without wires

---

### Post by asimon623 on 2005-09-10
[QUOTE=asimon623]got it to work using instructions from another site...i had to make deb from the ndiswrapper thing i downloaded and then install the utils and modules produced by that

now ive got a new problem...when I restart, i get an error on the networking thing in the upper right corner that stflag something something device not found...I run modprobe ndiswrapper...this goes away

then i do dhclient wlan0  and it tries to obtain an address from 255.255.255.255 which I dont understand

If I just enter
192.168.2.9
255.255.255.0
192.168.2.1

as static....I can access the internet without wires[/QUOTE]
 i went to restart again and I saw "save setup" so I checked it and that made my card work on boot

but I'd still like to figure out dhcp

thanks

---

### Post by stimms on 2005-09-10
I have a similar problem with a zv5000 (5210ca to be exact).  I was wondering if you had the website where you found the instructions on making a .deb.

---

### Post by asimon623 on 2005-09-10
[QUOTE=stimms]I have a similar problem with a zv5000 (5210ca to be exact).  I was wondering if you had the website where you found the instructions on making a .deb.[/QUOTE]
 [http://wiki.vislab.usyd.edu.au/moinwiki/Installing_Debian](http://wiki.vislab.usyd.edu.au/moinwiki/Installing_Debian)

go down to wireless network

where it says ndiswrapper-1.1 replace it with the 1.3rc or whatever the proper name of the one you downloaded is.

(my problem was with modprobe ndiswrapper command)

---

