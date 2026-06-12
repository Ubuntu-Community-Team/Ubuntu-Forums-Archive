---
title: "No Wireless Status Indicator?"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by mrbucket on 2007-05-28
I just installed Feisty Fawn. Love it! Probably the least frustrating linux distro i've worked with in my past.

However, I cant seem to get my wireless working. There's no status indicator in the panel, and in the network configure applet there are settings to configure my wireless card, but no option for WPA. I can do the command line configuration, but shouldnt the graphical applet handle this all for me?

I have a Dell Precision M90 with an Intel PRO/Wireless 3945. The driver does show up in the restricted driver manager.

---

### Post by ugm6hr on 2007-05-28
> **mrbucket said:**
> I just installed Feisty Fawn. Love it! Probably the least frustrating linux distro i've worked with in my past.

However, I cant seem to get my wireless working. There's no status indicator in the panel, and in the network configure applet there are settings to configure my wireless card, but no option for WPA. I can do the command line configuration, but shouldnt the graphical applet handle this all for me?

I have a Dell Precision M90 with an Intel PRO/Wireless 3945. The driver does show up in the restricted driver manager.

Assuming you have Ubuntu7.04:
I believe that the Intel3945 is supported in Linux, so it should be easy.
In the "network configure applet" - try ticking "enable roaming mode"
In Terminal: type *nm-applet*
There should now be an icon in the taskbar top right that looks like 4 vertical grey bars: right-click on it and enable networking and wireless, then left click and it should bring up a list of access points.

---

### Post by uamuzeme on 2007-05-28
I'm having the same problem with a status icon too. What I have looks like two computers, one behind the other and when I hover over it it says "Manual network configuration". I'd like some bar thingy and there doesn't seem to be much of a way to find other networks. Windows finds 5 others in my area, even though they are locked but ubuntu only seems to find mine. Roaming does nothing but give me no connection at all.

---

### Post by ugm6hr on 2007-05-28
What happens with typing
nm-applet
in Terminal?

---

### Post by uamuzeme on 2007-05-28
I don't know about Mr Bucket, but when I type nm-applet I just get another one of those computer behind computer icons. When I right click the icon on about, it says "NetworkManager Applet 0.6.4. Notification area for managing your network devices and connections".

---

### Post by mrbucket on 2007-05-28
Well, I feel like an idiot!

I didnt recognize the applet with no connection enabled. When I typed nm-applet i looked up and saw two identical icons. Thanks for the help!

---

### Post by ugm6hr on 2007-05-28
> **uamuzeme said:**
> I don't know about Mr Bucket, but when I type nm-applet I just get another one of those computer behind computer icons. When I right click the icon on about, it says "NetworkManager Applet 0.6.4. Notification area for managing your network devices and connections".

It's the right icon.
As stated:
right-click on it and enable networking and wireless, then left click and it should bring up a list of access points.

---

