---
title: "How do I install client managaer 3? and use AOSS?"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by godfromdfo on 2007-11-07
my router is on a windows xp pc and it is a AOSS one and it works on windows xp upstairs (which has windows xp) but im making the upstairs pc have ubuntu and don't know what to do =[[ I tried installing client manager 3 but a pop up come up.... I'm very new to ubuntu. so any help aprecciated =[

---

### Post by spd106 on 2007-11-07
I don't know of any AOSS client for Linux at this time, so you will have to set it up manually. The settings should be accessible through your router's web interface.

I remember reading that there was work being done on WPS for Linux, but I haven't heard of any recent progress or that it's being integrated into any of the utilities we currently have. Driver support is a much bigger issue.

---

### Post by godfromdfo on 2007-11-07
> **spd106 said:**
> I don't know of any AOSS client for Linux at this time, so you will have to set it up manually. The settings should be accessible through your router's web interface.

I remember reading that there was work being done on WPS for Linux, but I haven't heard of any recent progress or that it's being integrated into any of the utilities we currently have. Driver support is a much bigger issue.

Would you be able to tell me how to set it up manualy then please? I havant manuay done wireless before

---

### Post by spd106 on 2007-11-07
Ok, you only need three pieces of information.

1) The SSID or name of your network - This is usually named after your device manufacturer i.e. Netgear or Belkin.

2) The wireless encryption type - This could be WPA or WPA2 and should be detected automatically by Ubuntu, but it's nice to know for the next part. You can also use WEP, but I wouldn't recommend it.

3) The encryption key - This is the most important part and should probably be written down temporarily. It can either be a automatically generated long string of random ASCII digits or a passphrase that you can set yourself.

You will find all three of these somewhere on the router's web management interface. To access this interface you will need a PC that's already connected to it and web browser. It's usually a good idea to access this using a wired connection. Then just enter the IP address of the router into your web browser, as it says in the router's manual.

Once you have the three pieces of information you need to enter them into the nm-applet up in the top right corner of the screen. Click on the network name and you will be prompted to enter the key. After a brief pause you should be connected.

Incidentally, I had a look around and it appears that Wifi Protected Setup (WPS) is currently being integrated into wpa_supplicant (the backend for wifi security in Ubuntu). I suspect this won't be ready for the next release of Ubuntu in March, but it shouldn't be too far off.

---

