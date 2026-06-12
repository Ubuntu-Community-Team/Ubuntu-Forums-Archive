---
title: "Cannot connect to network"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Fernglougher on 2010-09-14
I am not able to connect to any networks.

I have an HP Pavillion dvr-1222nr notebook PC that is running Ubuntu 9.04 (AMD 64 bit Desktop OS).  The system uses an AMD CPU, ATI video chip and a Broadcom network chip for ethernet and WiFi.  I have this system set up with a dual boot with Windows Vista Ultimate.  

The history of this system is that I needed to do non-technical consulting work  Linux-based system on site with a client.   The client used a Windows-based proxy server and their support staff configured my system to work with it.   Aside from the fact that I was constantly nagged to log-in all the time whenever I browsed from Firefox, networking generally worked from a wired connection.  Prior making these modifications, both wired and wireless communications worked in Linux in locations other than on the client's network.

Now, that I am no longer on that project and I am trying to use my Linux partition  again for another project, I find that the wireless light on my system is perpetually off (red instead of blue) and I am not able to connect to a wired network either.  Access to the person who set-up my system to talk to the other party is no longer available to me.  

However, when I boot Windows, both the wired and wireless connections work perfectly (the wireless light is blue).  Therefore, this is a software issue, not a hardware issue.

I am looking for recommendations on software diagnostics to determine what is wrong with the system.

Thanks!

---

### Post by fly-by-night on 2010-09-14
Just a suggestion:

Search around for all the various files that can hold configurations (networking related).  They might have set the network to theirs exclusively.  Proxy settings, DNS etc.  Maybe also locked your device to the company network if that's even possible.

Or

Preferences/Network Connections/Wired

Choose the listed item and **Edit** it.  IPv4 Settings, set to Automatic, save.  Depending on your home setup you might have to specify DNS and IP details.

Repeat for Wireless.

Hope it helps.

---

### Post by coffeecat on 2010-09-14
Since the Wireless did work before, I assume that both the Broadcom driver and firmware are installed.

First thing. Try a cold boot into Ubuntu. Sometimes when you do a warm reboot from Windows to Ubuntu, the firmware for some devices fails to load. I don't know whether this is true for Broadcom NICs, but it's worth a try.

If not, this page may give you some clues:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

At the very least it might help you find out what exactly was installed in the driver line.

One other thing. You say you have both wireless and ethernet Broadcom NICs. I believe that if you are using the STA driver, it and the ethernet driver can conflict. A useful post here:

[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)

---

