---
title: "Just Won't Connect!! HELP!"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by mastermarcus355 on 2008-09-07
I am a newbie and I honestly spend all of my free time, when not working or in class, on this site. I have successfully solved all of my problems by reading through threads on this site. Now I seemed to be stumped and others do as well because I havn't found an answer to this problem yet. I have a Broadcom 4306 and with ndiswrapper installed. Now I've gone through most everything and have it now set up so it uses bcmwl5.inf and blacklisted others. I've got to the point where it finds my network, I enter in my passphrase, then it attempts to connect. After a little while it will again ask me for my passphrase and it does this over and over again. Now when I log into windows I connect to the same network using the same passphrase!! I even tried to connect to an "open" network and got nothing! I'm so confused now :confused: Any help is greatly appreciated! Thanks

---

### Post by jimv on 2008-09-08
Does the network have a password on it?  Is it WEP or WPA?

---

### Post by rlzyoner on 2008-09-08
Have you tried connecting manually.
Check out the sticky

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by mike310z on 2008-09-08
I have been trying to find a solution to this for a few days. 
Its frustrating as the logs iwlist etc all show the router being seen correctly, shows the essid, power level, encryption state but it never actually completely connects and gives you an IP address.
I tried no encryption, WEP, WPA all rational combinations before I tired multiple recipes or manual configuration from these forums without any luck so far.
Works perfectly when booted to windows XP.

---

### Post by mastermarcus355 on 2008-09-08
Yes, The network is encrypted and it's WEP 128. I hadn't seen the "manual network configuration how to" before so I'm going to give that a try tonight. Thanks again

---

### Post by mastermarcus355 on 2008-09-08
So I manualy confiured the network and it said it was connect. I tried using firefox and that was a no go. Then I check the network settings and it showed that I had 3 DNS Servers and 1 Search Domain, something comcast.net. So it appears that I'm connected but I can't get a ping or use the internet! I'm so confused on what to do now!

---

### Post by knix on 2008-09-08
If you use the terminal to associate, you need to run dhclient afterward. I've heard rumors that ndiswrapper doesn't always work with 128 bit encryption. I have had some problems with the network applet, and disabled it.

---

### Post by mastermarcus355 on 2008-09-08
OK..so I tried running it through the terminal and I didn't get anything but I didn't have the network applet dissabled. Does that make a difference? Also I tried connecting to an unencrypted network and didn't have any luck there either. hmmm...well how do I go about dissableing the network applet so I can try establishing a connection through the terminal again? thanks

---

### Post by knix on 2008-09-08
I had to disable the applet (killall nm-applet), then sudo iwconfig <iface> essid <network name> key <key>. then iwconfig to check forassociation. If you're no associated then the next step is pointless. then sudo dhclient.

---

