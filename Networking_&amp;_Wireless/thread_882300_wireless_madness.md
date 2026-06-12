---
title: "wireless madness"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by stringy07 on 2008-08-06
Hi all

This is my first post after deciding to create a dual boot ubuntu/vista environment on my Sony VAIO laptop.

I have already installed the latest ubuntu release alongside windows and dual boot works fine, however!

My wireless card point blank refuses to work, it is reported in vista device manager as a LAN Express card, which after a search apparently uses an atheros chip.

Now i have read over the past few days alot about the Madwifi drivers and tried on more than 10 occasions different ways of installing them, but still no joy.

Has anyone got any idea how to get my wifi working????

(other than installing ubuntu, i am a complete noob)

---

### Post by Lori700698 on 2008-08-06
Yea I had a hard time too!  This worked the best
[http://ubuntuforums.org/showthread.php?t=718244&highlight=madwifi+driver](http://ubuntuforums.org/showthread.php?t=718244&highlight=madwifi+driver)
and I skipped the 
gksudo gedit /etc/network/interfaces
I don't like messing with these unless absolutly necessary.
No last thing I did different was use the new ath5k and you can use this link  
[http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6](http://svn.madwifi.org/madwifi/branc...i-hal-0.10.5.6) 
in place of the ones in the first set of directions.  And if you do you won't be going into trunk it will be 
cd madwifi, then cd madwifi.0.10.5.6
sudo make
sudo make install
sudo modprobe ath_pci
I'm loving this driver so far, it just dont want to play nice with my security.  Still need to work that out!

---

