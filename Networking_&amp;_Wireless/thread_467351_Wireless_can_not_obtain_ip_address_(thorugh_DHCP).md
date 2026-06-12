---
title: "Wireless can not obtain ip address (thorugh DHCP)"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by clegg13 on 2007-06-07
i have been trying for 2 days now =)

tried all sort of HOW TO's and guides/tips/tidbits, even the one which involved reinstalling ubuntu, i get stuck at one place, my wifi scan (both in network manager and wifi radar) can see my AP (SSID Clegg Home) it is secured .... but whatever i might do, none of those managers are able to obtain an IP, tried manually and still no show, tried without any security on my wifi , still nothing. iwconfig and iwlist scan both show the AP with complete detail. 

kindly let me know what info i should provide besides the above so that you may be able to help me =)

---

### Post by stinkypudding on 2007-06-07
Have you tried sudo dhclient?

---

### Post by clegg13 on 2007-06-08
yes, i have. infact, the dhcp service itself is working fine, my wired network connects and obtains ip from DHCP without any trouble at all. its just the wireless. and its painful to be able to see my AP , its signal strength and everything , and not being able to connect to it =)

i am using latest versions of ndiswrapper and 151517 drivers by the way, running on 7.04

---

### Post by Mr. C. on 2007-06-08
Have you verified that your system is associated with the AP ?

You won't be able to get an IP address or communicate with the AP until then.

Verify that first.

MrC

---

### Post by clegg13 on 2007-06-08
what exactly do you mean by 'associated' ? its a standard wifi setup at home, you see the network, you try to connect, it asks for passkey you put that in and thats it. i dont know what you mean further than that ? thats how i connect when im in windows, or anyone else who comes over to my place.

---

### Post by Mr. C. on 2007-06-08
A Wireless card "assosciates" with an AP.  This means, the've negotiated the proper protocols, authenticated, etc.  Only after this is done will the AP allow networking.

What looks to you like your system not getting an IP address via DHCP is often a problem with not being able to associate with the AP.  Being able to associate in Windows but not a Linux system is common.  Windows drivers are typically highest priority to most vendors; *nix systems are lower.

Review the info here, and perform the basics to see if your wireless card is configured correctly, and is associated:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

MrC

---

### Post by clegg13 on 2007-06-08
oh i have already used that guide, thats whee i intially started from, but nothing doing. as i said, i even tried remove all security from my wifi router (making it public) it still did not connect.

---

### Post by clegg13 on 2007-06-08
i have no tried both the ndiswrapper HOWTO and the alternate one (that uses firmware) both with fresh clean installs and i get stuck at the same point in both cases: my system does not obtain IP from the router. SO, as suggested earlier it seemed like a problem of authentication with the secured connection, i tried both methods manually and guess what, the ndiswrapper method worked IF i put in manual IP setting and i dont setup any security in the wireless router. 

knowing this i went and tried in detail all the suggestions/hints/tips in the wifi security HOWTO. but to no avail. the only thing that seems to work is an an unsecured network with manual settings.

i am using a DELL 1500 a/b/g/n mini card, i would appreciate if anyone can let me know if they have successfully logged into a secured network with that yet.

any information that an expert might require to help me further, please ask, i really want to completely switch over to ubuntu and free up the space windows takes up on my laptop =)

cheers

---

### Post by novembercamel on 2007-07-30
*sigh* So I finally got mine working.  Same exact symptoms.  Here are the steps I took (ended up being ridiculously easy).

**Disable IPv6:**
Open up _/etc/modporbe.d/aliases_

**Search for "ipv6" and make the entries look like this:**
```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

```

Restart...
Make a sandwhich...
Consume sandwhich...
Continue.

Type in these commands:
```
$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r prism2_pci
$ sudo modprobe orinoco_pci
```

Enable wireless by right clicking on the NetworkManager Applet, etc, etc.

Thanks to:
[http://ubuntuforums.org/archive/index.php/t-87798.html]("http://ubuntuforums.org/archive/index.php/t-87798.html")
[http://ubuntuforums.org/showthread.php?t=505920]("http://ubuntuforums.org/showthread.php?t=505920")

---

### Post by jonp5769 on 2008-07-15
I am having the same problem, have tried above tips but still no joy. It detects the wireless card. Will "connecct" to a network but will not assign an IP address. 
Thanks 
Jon 
Newbie

---

