---
title: "please help, Rt2500 device with WPA2 on Dapper 6.06"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by alanmzifa on 2007-11-03
**Hi, I need some help to get a rt2500 chipped PCCard working on a laptop using WPA2 security.**

I've read many threads here including the sticky but they've only helped confuse me. It seems there's a multitude of ways you can set this device up, ndiswrapper or not, different drivers. 
I'm not clear whether I should be using WPA supplicant, if I need another driver when using WPA, whether I use Network Manager or not.

My Laptop is old so the install is Dapper 6.06. I previously had this device working in the machine but with WEP. My home network is now set up to use **WPA2 AES although I'd settle for WPA TKIP** if I had to.

As well as many hours reading threads here and elsewhere I've spent a few hours tinkering myself. The card and rt2500 driver seems to be being recognised, it seems to pick up nearby networks and signal strength, looks like it's sending data packets  but not receiving any.
[B]
I need someone to go back to the beginning and show me what utilities and drivers I should be starting off with for WPA2 on a rt2500 PCCard on Dapper 6.06.[/B]

 Can anyone help me please?

---

### Post by Lambert on 2007-11-03
Did you read through this?

[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29#head-af86b211b480d43b791cd9b4e698f96638d6d25f](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29#head-af86b211b480d43b791cd9b4e698f96638d6d25f)

not sure if it offers anything or if you have read it but there is some decent info on the page for this chipset.

---

### Post by alanmzifa on 2007-11-04
I hadn't read that Lambert. I'll print it off and give it a good chew over before I do anything as it seems it's really been written with  Gutsy 7.10 in mind not Dapper 6.06. I'm still not clear whether I should have wpa supplicant downloaded or network manager, both or neither.


**If  anyone thinks they know a more straightforward or more certain way to make a Ralink 2500 device work on Dapper 6.06 with WPA2 or WPA please add your thoughts to the thread.**

---

### Post by wieman01 on 2007-11-04
Yes, there is a way to do it, however, a bit of manual work is required. Have you seen the Ralink HOWTO in my signature? Please give it a whirl and post there if you have issues. 

First thing we need to do is to set up your card and get an unencrypted connection working. Then we move on to WPA which is not a big deal if the Windows driver supports it.

---

### Post by alanmzifa on 2007-11-04
wieman01, thanks for replying. I've been downstairs trying to configure the wireless, changing this and that  using the guide the previous poster had linked to. Card seemed to be seeing other networks, broadcasting but not receiving, using the driver that comes built into Ubuntu 6.06.

Just came upstairs to got to bed (1.45am here) and noticed your reply. Will take a look at that and start working on it tomorrow night. Had it previously working with WEP last time I had 6.06 installed on that laptop (forget how) but now want to use WPA2, perhaps WPA if necessary.

---

### Post by wieman01 on 2007-11-04
> **alanmzifa said:**
> wieman01, thanks for replying. I've been downstairs trying to configure the wireless, changing this and that  using the guide the previous poster had linked to. Card seemed to be seeing other networks, broadcasting but not receiving, using the driver that comes built into Ubuntu 6.06.

Just came upstairs to got to bed (1.45am here) and noticed your reply. Will take a look at that and start working on it tomorrow night. Had it previously working with WEP last time I had 6.06 installed on that laptop (forget how) but now want to use WPA2, perhaps WPA if necessary.
Alright then. But do yourself a favor and try to get it working on open wireless networks first, then embark on WPA. I'll see you through the guides, no worries.

---

