---
title: "can't connect to WPA2 wireless network"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by epgui on 2008-01-07
Hi there!

I have access to the wireless network at school from windows XP/Vista and from MacOS X. However, i cannot connect from my ubuntu installation. The network uses WPA2 enterprise with TKIP, PEAP and MSCHAPV2. The network does not broadcast it's BSSID, but i know it is named either 1355-G or 1355-G (2).

When I put these settings in the windows XP wireless manager, what happens is the network asks for credentials (user name, password and server). I connect using username someusername, password blahblah and server NBSS. Then it asks me if i want to accept a certificate, which i do, and then windows connects to the network.

I would very much like to be able to connect to my school's network, but if i put that information into the Ubuntu network manager, it tries to connect, detects the network with above-mentionned name, then asks for all the settings again, again and again.

Anyone?

---

### Post by dannyboy79 on 2008-01-07
network manager I don't think works with WPA2. check this out

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy)

---

### Post by PriceChild on 2008-01-07
> **dannyboy79 said:**
> network manager I don't think works with WPA2. check this out

[http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+gutsy)No, certain drivers don't support it, such as ralink or madwifi supposedly.

---

### Post by dannyboy79 on 2008-01-07
> **PriceChild said:**
> No, certain drivers don't support it, such as ralink or madwifi supposedly.

correct, that's what the WPA guide states. Also, another user here states that Network manager doesn't even have a drop down for WPA which is why I said what I did. Can you confirm that Network manager allows for WPA authentification? Here's the other thread: [http://ubuntuforums.org/showthread.php?t=660959](http://ubuntuforums.org/showthread.php?t=660959)

---

### Post by PriceChild on 2008-01-07
Yes I am currently using it for a router with WPA-PSK using an atheros card and nm-applet.

---

### Post by lift28 on 2008-01-07
i had a bitch connecting my daughters lappy to OSU wireless- but it turn out to be simple-- right mouse click the netwok manager and choose connect to other network- then add user and password.
if you are finding that you do not see any wireless networks in the network manager -- edit your /etc/network/interfaces
jay@jay-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


 #iface eth1 inet dhcp <<<<my wireless card


hope this helps

---

### Post by kevdog on 2008-01-07
Hold on --- Im using wpa2 with madwifi with nm.

---

### Post by epgui on 2008-01-07
i'm using the driver package featured here -> [http://joshuadavis.wordpress.com/2007/04/12/fully-working-ubuntu-with-a-compaq-presario-v2000/](http://joshuadavis.wordpress.com/2007/04/12/fully-working-ubuntu-with-a-compaq-presario-v2000/)

As i say, i can connect (same card) with windows. =(

However i have to say i'va switched to ubuntu it's been a while now and i love the experience (cheers to compiz fusion, among other things! =D )

Connecting to this network is primordial to me as i spend about six hours a day at school, and they don't have very long Cat-5 cables... =P

---

### Post by kevdog on 2008-01-07
Ok I skimmed the post you referenced, but all I learned is that you are trying ndiswrapper.  You need to start posting some output so we can figure out what is wrong.

---

### Post by epgui on 2008-01-08
administrator@WATSON-linux:~$ ndiswrapper -h
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

---

### Post by jhallward on 2008-04-18
Ya, something tells me that's not the output kevdog wanted.  It's been a while since you last posted though, so if you ended up finding a solution, post it here, since I'm having a similar problem, and it looks like lots of people are having wpa2 enterprise (your schools system I'm guessing) related problems.  Too bad nobody is posting useful output and so none of us have any idea if we're all dealing with the same bug or a bunch of separate bugs.

Here's a list of useful sources of output, since some of you seem to have no idea where to go:
dmesg
tcpdump/wireshark (wireshark can save the packets in a .cap file you can then upload here, be aware that you're uploading your encryption keys too if you do this)
/var/log/messages or whereever your syslog output is stored.

For the record, my problem is not networkmanager related.  It happens with wpa_supplicant too.  My card (a broadcom 4311v1) supports wpa2, but I can't tell if my drivers are the issue or not.  I haven't gotten ndiswrapper working (so I can't test the windows drivers).  Something makes me thing it's a configuration issue and not a driver issue, since I had the same problem with the bcm43xx drivers as I do now with the new b43 drivers.  I'd managed to fix it on the bcm43xx drivers, so it is possible to make this work with my setup, though I'm not sure how (I had to restore my partition to an image of an earlier date, and can't figure out how to fix the wpa2 again).

---

### Post by epgui on 2008-04-29
It's been a long time since I posted this, but I just happened to fix the problem today on my new Ubuntu Studio 8.04 installation. :)

What I did was to install the Joshua Davis drivers (see link on page one), enable the restricted drivers, install network-manager.

Switched from WPA2 Enterprise to WPA Enterprise (haha weird, it worked with WPA2 on Windows :confused:), TKIP + MSCHAPv2 + PEAP.

Where network-manager asks for an identity, i put NBSS\guillaume.pelletier (where NBSS is the logon domain, a backslash, and username). input password.

Apparently there was no need to accept a CA certificate (which it does in windows) and thereafter I had a fully functional wifi connection.

However, I experience frequent intermittence (no big deal on most internet apps, but kind of annoying on Pidgin and apt-get...) and my range is far shorter than with windows. :(

I have never successfully used ndiswrapper (but i wouldn't mind trying it out if it might somehow fix the minor issues described above).

---

