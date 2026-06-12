---
title: "Cisco aironet 350 WPA"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by bucky0 on 2008-08-19
Hey all, I've searched all around and havn't found a solution. I have a cisco aironet 350 pcmcia card in my laptop, which works great with the airo kernel driver. Unfortunately, WPA doesn't work. This card has an updated firmware which supposedly supports WPA (dmesg says so when plugging it in), but when I try to connect to a WPA-based network with network-manager, it only gives the option for wep and LEAP.

Any suggestions? I'd file a bug report, but I don't know where to stick it.

---

### Post by central_beerangi on 2008-08-19
I want to echo this call for help. My security is WPA as well. I also do not have the updated firmware or know how to get it. my stuff is perhaps dated. IBM t30 from 2003. Thnx in advance.

---

### Post by NadmanET on 2008-09-04
What cipher are you using?  The Aironet 350 card does support WPA but not with AES encryption; you will have to use TKIP.  LEAP is an authentication protocol that can be used with WEP or WPA security.

I wish I could give you more on setting this up but I have never set up a 350 (or any wireless) on Ubuntu.  I just wanted to tell you before you pull your hair out to make sure that you are not using AES because that won't work.

You can get a CB21AG on ebay pretty cheap these days.  That is a possible work around.  Sorry I can't give you more advice on configuration settings from within Ubuntu.

---

