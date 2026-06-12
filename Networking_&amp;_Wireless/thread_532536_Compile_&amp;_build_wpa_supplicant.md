---
title: "Compile &amp; build wpa_supplicant"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Skrypt on 2007-08-22
Let me begin with two things: I am stupid and I am frustrated beyond belief. 

I've spent the past week endlessly trying to figure out how to get the internet here at the University of Florida to work and someone kindly pointed me toward this wiki [http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=Linux_802.1x](http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=Linux_802.1x)

However, the instructions for installing the wpa_supplicant are very vague to say the least. Also, I have no internet on the target computer and thusly, I'm unaware of how to obtain the required compiling scripts from the feisty repo's, etc.

If someone could help me... i'd be greatly obliged.

---

### Post by Jamie Jackson on 2007-08-22
I have Feisty and can automatically connect to unsecure, WEP, and WPA networks (haven't tried WPA2), without having had to manually install wpa_supplicant.

I think a lot of new Ubuntu users think they need to jump through hoops to connect to WPA APs.

What does "lshw -C network" output, by the way?

Edit: Oh, and AFAIK wpa_supplicant comes in Feisty by default, or is that not adequate for some reason? To check whether it's installed, try "wpa_supplicant -v"

---

### Post by Skrypt on 2007-08-22
lshw -C network returned no output.

wpa_supplicant -v returned "wpa_supplicant v0.5.5"

I connected it to the internet when I arrived and only received the DHNet homepage saying I was connecting from an outside source and there was no way to authenticate myself and get access to the internet.

---

### Post by Jamie Jackson on 2007-08-22
Are you trying to connect via wireless or ethernet?

For ethernet, I'm looking at the [Mac instructions]("http://www.circa.ufl.edu/cd-rom/version6f/mac/connect/dhnet.htm"), and while I don't suggest necessarily trying to translate them for your setup, they do seem pretty darn generic.

If wireless, did you read through [this]("http://net-services.ufl.edu/provided_services/wireless/user.html") yet?

---

### Post by Skrypt on 2007-08-22
Ethernet.

also, those instructions are out dated as of this year. they've gone stupid with security.

---

### Post by kevdog on 2007-08-23
Can you tell me what you have tried at this point.  I mean specifically as far as configuring a wpa_supplicant.conf file??  You could also consult the Sticky at the top of the networking forums written by Weiman about wpa.  Thats a good place to start.  If you have wpa_supplicant installed already, then no need to compile from scratch.

---

