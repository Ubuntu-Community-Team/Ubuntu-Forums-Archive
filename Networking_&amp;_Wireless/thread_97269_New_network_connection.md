---
title: "New network connection"
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by okfalls on 2005-11-30
Hi all. When I initiailly installed Ubuntu my ethernet card was not setup. How does one now setup a new network connection without reinstalling the OS? Am I going to have to do some command line work to do this? I am new to Linux/Ubuntu and not familiar with the OS that well. I know my network card works because I access now using my mac(dual boot with XP)

I realize that this might already have been covered, but I can't seem to find any messages related to this concern. I appreciate any help I get with this matter.

Rod :smile:

---

### Post by mfreeze on 2005-11-30
Is the card already in your machine?  Is it working?  You can check from the command line by typing 'ifconfig'. If you see something that looks like 'eth0' then that is your network card.  If you are connecting to a router and using dhcp to get an addresss, you should be able to see that address also. Your card really should install and configure itself.

---

### Post by darth_vector on 2005-11-30
you can set up your ethernet card in two ways (or at least 2) - the first is by editing the file /etc/network/interfaces. the second is by going through the ubuntu menus to menu -> system -> administration -> networking.

to set up the file /etc/network/interfaces you must be root. so you would open the text editor with sudo, as in:

sudo vim /etc/network/interfaces

hope that helps :)

---

