---
title: "Madwifi - Ubuntu - DWL-G520 - Headache"
date: 2005-11-02
forum: Networking &amp; Wireless
---

### Post by Peleus on 2005-11-02
Hi guys, how are you today?

I've just installed ubuntu straight from the downloaded CD version 1.10. 

The first thing I'm trying to do now is get my DWL-G520 wireless network card working because as we all know as soon as you get on the net you can fix anything and get anything. 

From my understanding I need to get the madwifi-cvs-current.tar.gz onto the computer (done) then install that program, to get the drivers working, to get the card working, to get the net. 

At the moment I have three problems. 

1) I'm a complete linux and ubuntu newb, so I don't even know how to install it. 

2) after following some guides, it seems a lot use apt-get from online sources which obviously i can't do because I don't have the net on that computer. 

3) It seems I need some tools like sharutils which my comptuer is saying I don't have (true or not I'm not sure). 

If anyone could take the time to post a step by step guide of how to do it, or at least a link to one, that deals with ubuntu programs straight off the set up CD, without the internet, it would be greatly appreciated. 

Apart from that any tips or comments are only going to get me further. 

Thanks guys - appreciate your help.

---

### Post by spd106 on 2005-11-02
If you've installed Breezy 5.10 then it should just work. The [MADWIFI]("http://madwifi.org/wiki/UserDocs/Distro/Ubunt") drivers are included.
All I can say is [check]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards") which version of the card you have. ie make sure it has an atheros chip.
To do this try **lspci** and **dmesg** at the terminal.

---

### Post by Lambert on 2005-11-02
Madwifi is included on breezy and it should work. Are the lights lit up on your card?

Have you gone into networking to try and configure.

Click on system>admin>networking

You should see under connections wireless connection The interface ath0 is inactive. Highlight this and click on properties. Enter your access information and click ok. Then click on activate.

If you're using wpa encryption you have have to do a little more work to get it working as I've read many posts with others having problems with wpa.

---

### Post by PsTJsT on 2006-02-06
As noted above, one shouldn't need to use ndiswrapper/Windows drivers for an adapter with an Atheros chipset under Breezy (most D-Link DWL-G520 adapters have Atheros chipsets). The madwifi drivers included in Breezy work great once the device is activated.  If you want to use WPA or WPA2, install/configure wpasupplicant per the excellent How-To/thread at [http://www.ubuntuforums.org/showthread.php?t=90450](http://www.ubuntuforums.org/showthread.php?t=90450).

---

