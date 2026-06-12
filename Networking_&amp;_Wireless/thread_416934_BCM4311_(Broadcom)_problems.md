---
title: "BCM4311 (Broadcom) problems"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by andrewfrueh on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am still having problems with my Broadcom wireless. I have an HP nx6125 laptop with a Broadcom BCM4311. I am running Feisty (7.04). I have tried ndiswrapper (with several different Windows drivers) -- without success (it even made the hardware "disappear").  Eventually I learned about fwcutter from[ this guide]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom"). 

Here is my account:

After completing a fresh reformat and OS install, the wireless did not work at all. Then I used synoptics package manager to install "bmc43xx-fwcutter". That went great (very easy). It "fetched" the firmware and did its thing. After the install, the hardware is at least recognizing the networks within range (in "roam" mode) -- so it did help a bit. 

But, I still cannot connect to any of the networks (WEP protected or not). Any help on how to proceed would be appreciated.

p.s. I filed a [bug report here]("https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579")

---

### Post by ziadoz on 2007-04-21
I have the same problem on my Broadcom using ndiswrapper.

---

### Post by alesdoc on 2007-04-23
I use my laptop (nx6125 - py461et) at work so i wait always for the Stable Release to install it.

Yesterday i installed Feisty (32-bit) and used bmmxx-fwcutter to get my wireless card working (i didn't use te driver  fetched by bcm. I use my driver). It works. I can connect my laptop to my home-wifi-connection (mac filtered).

It has some problem with network-manager. No way to connect my pc if nm-applet is running.

---

### Post by beta.tester on 2007-04-23
> **andrewfrueh said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I am still having problems with my Broadcom wireless. I have an HP nx6125 laptop with a Broadcom BCM4311. I am running Feisty (7.04). I have tried ndiswrapper (with several different Windows drivers) -- without success (it even made the hardware "disappear").  Eventually I learned about fwcutter from[ this guide]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom"). 

Here is my account:

After completing a fresh reformat and OS install, the wireless did not work at all. Then I used synoptics package manager to install "bmc43xx-fwcutter". That went great (very easy). It "fetched" the firmware and did its thing. After the install, the hardware is at least recognizing the networks within range (in "roam" mode) -- so it did help a bit. 

But, I still cannot connect to any of the networks (WEP protected or not). Any help on how to proceed would be appreciated.

p.s. I filed a [bug report here]("https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/108579")


Hi

I amusing my nx6125 now :) however I have the broadcom 4318 - I found this thread in forums:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

My wireless has been working ever since.

However it has a slight flaw I can live with :) I use WPA-TKIP and have to manually enter my key on reboot. May be worth a look. It basically is a debian script a guy has written and is proving a big success.

kind regards

john

ps have attached the .deb script he kindly wrote:

---

### Post by bdogg64 on 2007-04-25
Here is a great guide that I used for my bcm4311 with ndiswrapper

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

