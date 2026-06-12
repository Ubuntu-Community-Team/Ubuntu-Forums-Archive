---
title: "WPA in Network applet"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by tlg on 2007-06-11
I have Ubuntu 7.04 installed on a Dell 630M laptop which has an Intel 2915ABG wireless chipset.

When I run the network admin tool from System/Administration/Network it shows 
Wireless connection
Wired Connection
Modem Connection.

The Network Tools Devices tab shows the Wired port on eth0 and the Wireless port on eth1.

In the network admin tool, choosing Wireless connection and clicking on Properties brings up the Settings dialog. 
The drop down list for Network name shows several nearby networks.
The drop down list for Password type shows WEP (ascii) and WEP (hex)

There is no sign of anything to do with WPA.

If I set up my network or WEP I can connect OK, however I want to use WPA-PSK on my network.

I have checked in Synaptic Package Manager that wpasupplicant and wireless-tools are installed.  xsupplicant is also installed.

I followed the HowTo in Wiemans sticky post in this forum to edit the /etc/network/interfaces file to set up the WPA on my network and it all works.

My question is whether I should be able to set up WPA from the GUI interface instead of having to edit the interfaces file.

Is there something else I need to do to make the WPA options show up in the Network tool, or is there some other admin application that I should be using.

While I am OK with editing the inerfaces file, I am trying to set up Ubuntu for family and colleagues who want to move on from Windows, and editing config files isn't going to cut it.

Thanks in advance for any help.

---

### Post by jwm0z on 2007-06-11
I think if click manually connect or something like that, you can specify wpa in a drop down box.

---

### Post by tlg on 2007-06-11
Thanks. Can't find anything like manual connect. Any hints as to where it might be?

---

### Post by jwm0z on 2007-06-11
It's on the network manager icon at the top right, it might be create network or something, it's def on there just try right or left clicking.  You specify the network name then select WPA and enter the key.

---

### Post by jingba on 2007-06-18
I am having the same problem with my wireless.  I have a D-Link DWL-G122 B2 and I just got it to pull up on the system.  I can't enable it on my WPA system.  There are no options to do this in the network tab.  

I followed the directions on the following link [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html"), but it did not work.

Maybe you'll have better luck with it.  Let me know...

---

### Post by Sailorcancer on 2007-06-18
Yeah same problem as well.  Hopefully you can find out how to work it :D

I think whatever you find out should be helpful to me as well.  Even though I'm running on Xubuntu.

---

### Post by tlg on 2007-11-26
Apologies for the delay in replying.

I have switched to using WICD instead of Network Manager and it handles WPA PSK and AES just fine and is a lot more configurable that NM.

Just Google WICD Home and follow the instructions on the Download tab page.

---

