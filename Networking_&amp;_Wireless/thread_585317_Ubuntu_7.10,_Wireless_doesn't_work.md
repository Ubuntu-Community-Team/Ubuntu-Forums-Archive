---
title: "Ubuntu 7.10, Wireless doesn't work"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by ericderace on 2007-10-21
Hi,

I'm using Ubuntu 7.10 on a Thinkpad T60 with Intel 3945 wireless.
I'm trying to connect to a wireless AP with is WPA, PEAP, TKIP with MSCHAPv2 authentication.

I've been trying for days to get this working and I can't get it to work with NetworkManager.
I've been sucessful connecting to other networks, but not this particular one.

Can anyone help?

Thanks,

---

### Post by jasonswedlow on 2007-10-21
Sadly, I've had the same problem.  A working feisty fawn install (it was so easy!!!!) with a rt2500 chipset was upgraded to gutsy, and now I can't get the the card to recognize the network.  lspci shows the card, and wlan0 has a 169.... address.  Yes, the network is up (that is how I am writing this).

Feisty worked so well, without having to do the whole ndiswrapper dance !  Any suggestions would be appreciated.

Thanks!

---

### Post by cgreydak on 2007-10-22
I have T60p and have problem as well.  Did you try 

[http://ubuntuforums.org/showthread.php?t=202834&highlight=7.10+wpa+peap](http://ubuntuforums.org/showthread.php?t=202834&highlight=7.10+wpa+peap)

---

### Post by jamyskis on 2007-10-22
I have the Intel PRO 3945 wireless chipset in mine and I have the same problem...it appears to connect and find the networks, but won't log in and connect to the internet, despite the wireless key being correct. I even tried switching off the encryption, which makes no difference. My PSP connects fine to the network.

I've noticed that typing ifconfig in the terminal doesn't bring up eth1, which should be the wireless chipset, but iwconfig does. Also, going into Network Tools only shows the loopback device and eth0 (the LAN interface)

I heard about using wicd, but I actually need to get onto the net in the first place to download it onto the laptop.

Any suggestions?

---

### Post by rdtrain on 2007-10-22
I use a desktop with a Netgear WG311V3 pci wireless card. It worked in feisty but had trouble in gutsy.. I have it with ndiswrapper. I found something that worked for me and that is a wireless networking manager called WICD. If you go to their web site it tells you how to put it in the repository. I don't know if this will work for you but it might be worth a try.. 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Kiyo86 on 2007-10-22
I was having the same problem with my HP dv1000 with the Intel ProWireless 2200BG. What I found was that the network manager is, in fact, connecting to the server, but it is being denied. The server at my College was reporting that it was denying my computer because it was attempting to authenticate with an "unknown username and password". Basically, in Windows, for networks like these, there is an option with the MSCHAPv2 to prevent the computer from attempting to authenticate with the computer's login and password. Usually, this box needs to be unchecked. In networkmanager, (and Knetworkmanager), there is no box for this. The solution that we are using now is to input the username and password, leave the "Phase Two" option set to "NONE" and leave the certificate field blank. In windows, you need to have the certificate, but in Macs, the certificate is downloaded and auto installed by the computer. In Fiesty, it could work either way, but it worked much better if you had the certificate. It seems that in Gutsy, it works better if you let it download the cert on its own. This worked in Kubuntu Gutsy with the standard Knetworkmanager. I'm sure that there are other programs that also work, but I have tried Wicd, and It didn't work for me. If you want to use the networkmanager, (or Knetworkmanager), this might be one way for it to happen. I hope this works for you.

---

### Post by caricc on 2007-10-23
I have just loaded 7.10 on my compaq v2000. I did have wicd installed in 7.04. What I did, this is so easy, I went into my package manager. Marked my network-manager for removal.
applied. rebooted. Now it's working just fine. :lolflag::guitar:

---

### Post by bigboy_pdb on 2007-10-23
For those of you who don't want to use ndiswrapper (and you'd prefer to use the modules that came with Gutsy) you might want to try the solution that worked for me. It can be found here:
[http://ubuntuforums.org/showthread.php?t=587727](http://ubuntuforums.org/showthread.php?t=587727)

---

### Post by ericderace on 2007-10-23
My problem doesn't look like a driver problem (I believe..) since I can connect to my home network which is WPA-PSK, and a secondary uncrypted wireless network at the University.

Is there a way to debug the authentication ?

I would need networkmanager or some sort of network profile manager since I use my laptop on different networks.

I've tried pretty much everything which I was able to find in the treads.(Exept Wicd)

---

### Post by wieman01 on 2007-10-23
> **jasonswedlow said:**
> Sadly, I've had the same problem.  A working feisty fawn install (it was so easy!!!!) with a rt2500 chipset was upgraded to gutsy, and now I can't get the the card to recognize the network.  lspci shows the card, and wlan0 has a 169.... address.  Yes, the network is up (that is how I am writing this).

Feisty worked so well, without having to do the whole ndiswrapper dance !  Any suggestions would be appreciated.

Thanks!
"ndiswrapper" is one solution you could try. See my signature.

---

### Post by thebrade on 2007-10-23
I can confirm that WICD works great with intel wireless. It replaces the standard network-manager and gets rid of any problems I was having. Just follow the download link on this site: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by ericderace on 2007-10-23
Unfortunately, Wicd does not support WPA-PEAP with TKIP and MSCHAPv2....

---

### Post by Kiyo86 on 2007-10-23
> **ericderace said:**
> Unfortunately, Wicd does not support WPA-PEAP with TKIP and MSCHAPv2....

I posted on this a little farther up, but since the post was a little dense, it might have been passed up, but the solution that I found was to leave the "Phase Two" a.k.a. (MSCHAPv2 option) set to "NONE", enter your authentication materials, and don't attach the certificate. Linux will pull down the certificate on it's own. I hope this works for you. Good Luck.

---

### Post by ericderace on 2007-10-23
> I posted on this a little farther up, but since the post was a little dense, it might have been passed up, but the solution that I found was to leave the "Phase Two" a.k.a. (MSCHAPv2 option) set to "NONE", enter your authentication materials, and don't attach the certificate. Linux will pull down the certificate on it's own. I hope this works for you. Good Luck.

I did try that, and it didn't work.  Thanks anyway.

I wish there was a way to debug this authentication thing..

---

### Post by pizpot on 2008-03-23
---

---

### Post by Rascal79 on 2008-04-27
Guys, I tell you what, I have tried with many ways, no luck. But when I tried with that new comer Hardy Heron, it works out of the box without any effort. So think about it.

---

