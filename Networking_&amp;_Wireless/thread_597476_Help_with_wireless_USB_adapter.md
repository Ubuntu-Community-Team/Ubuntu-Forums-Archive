---
title: "Help with wireless USB adapter"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Teronap on 2007-10-30
Hi,
just installed Gutsy, but my wireless network does not work.  my wireless USB adapter is detedted, and when i go applications-> system -> network, i can view it and change the settings, and it finds the network, however in the network applet in the top bar, when i right click, it does not say anything about wireless networking, the model I have is Linksys WUSB11 ver 2.6.  When I boot to winbdows, tthe network is fine.  Any ideas?

---

### Post by era_new on 2007-11-10
I just found two of my old wireless USB adapters and decided to get them working in two old computers. I have WUSB11 versions 2.5 and 2.8, but I'm guessing 2.6 would work similarly. One computer is Ubuntu and one is Xubuntu and I installed both the same way.

I think the problem is that Gusty only has an older version of the drivers. This is what I did to get them working:

Using synaptic, i installed the following packages:
[LIST]
[*]linux-source
[*]linux-headers
[*]build-essential
[/LIST]

Then I downloaded the latest at76_usb drivers from [http://developer.berlios.de/projects/at76c503a/]("http://developer.berlios.de/projects/at76c503a/").
[LIST]
[*]tar -zxvf the file
[*]cd into the new directory
[*]make
[*]sudo make install
[/LIST]

Then I downloaded the latest at76_usb-firmware from the same website.
[LIST]
[*]tar -zxvf the file
[*]cd into the new directory
[*]sudo cp *.bin /lib/firmware/
[/LIST]

After that I rebooted, and after I was back into my desktop plugged the adapters in and the worked like a charm. Hopefully this will work for you and anyone else wanting to use these wireless adapters.

---

### Post by Teronap on 2007-11-10
thanks, will try it tonight

---

### Post by bnex10 on 2007-11-10
Do you think that will work on Version 3.0?
I have that.

---

### Post by Teronap on 2007-11-11
I tried it last night, and now my network has a decent signal strength, but wont connect.

---

### Post by MariusSilverwolf on 2007-11-11
Teronap,

Although you're using a slightly different version, try following the How-To here: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045)

You'll need to change the drivers from the rt2570 to the appropriate version listed in the Hardware Guide at rt2x00.serialmonkey.com, but that should be the only difference.  Everything else is applicable.

G'luck!

---

