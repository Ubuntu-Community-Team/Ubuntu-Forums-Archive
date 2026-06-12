---
title: "using dongle to connect to internet"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by recumbentpete on 2010-06-11
I am a new user.  I would like to connect to the internet using a dongle.  I have been told by my local 3g shop that I will need a patch to get it working.

any advice or assistance would be appreciated.

---

### Post by Peter09 on 2010-06-11
Some dongles work, some don't. What type of dongle is it?

---

### Post by Pushpalanka on 2010-06-11
I too have the same problem. I tried to fill the Mobile Broad Band settings and to connect. I got my service provider in the list, but the default APN given was not what the company said:confused:. Anyway I tried both, but no good reaction.

Im using a HUAWEI E1550 dongle. Hope for a help.

---

### Post by Peter09 on 2010-06-11
well here is a guide for that one
 
[http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu](http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu)

---

### Post by mbuotidem on 2010-06-11
You may or may not need a patch for your dongle to work. It depends on a lot. Your version of Ubuntu as well as, as Peter09 said, your dongle. 

I use Ubuntu 10.0 Lucid Lynx, and a Huawei E160g. It was detected automatically and I used the default settings for my country and provider and everything worked great except for 1 glitch. my connection kept disconnecting on its own.

recumbentpete, try it out first and if it doesn't work, tell us what happened, the steps you took and the outcomes and the community will surely help. I'm new too and everytime i have a problem, i ask and its answered. 

Pushplanka, since your dongle is already detected by Ubuntu, and you are only having problems connecting, you might try what i tried when i had the problem of constant disconnection. I inserted my dongle into a windows company, (this is assuming your dongle comes with a software like Mobile partner, that auto installs itself on windows and creates a connection!) Install the software and try connecting so that you are sure of two things. The type of connection you have in your area, whether wcdma or edge, etc, that is the one that the mobile partner software easily connects on. and 2, browse to network connections on your windows pc, and look at the properties of the connection automatically created by the mobile partner software. In my case, my provider is called Glo. the mobile partner  software is called, GLO 3G PLUS, and the connections created are GLO 3G PLUS, and GLO 3G PLUS PREPAID. I use GLO 3G PLUS PREPAID. So look at the properties and note every detail. Then try to replicate those setting in your Ubuntu, using the network connection applet, Edit connections option. I discovered that my problem was one of the authentication method. On default, all authentication methods are selected. Simply deselecting all the irrelevant methods and ticking only the relevant method, which i got from looking at the connections properties in windows, solved my problem. 

Now, going back to the first thing i said, when you determine what type of connection exists in your area, that is Wcdma or edge, you can download a software, its called mobile data monitoring application, its free, but windows based. Just google it and you'll find it. run it, but you must close your mobile partner software, before running it. Here is a screenshot of the program:
[IMG]http://www.nerve.org.za/mdma/mdma.png[/IMG]

Where it shows 3G connection. click on the dropdown arrow, and select either 3g or edge only, depending on which standard the mobile partner application successfully connected with. if it connected using wcdma, then select 3g only, if it connected using edge, then select edge only. Then click apply. What this does is that it forces your modem to always try to connect using that standard. It may or may not help you, but it helps me.

whew. that was a lot of typing. i hope its understandable though.

---

### Post by recumbentpete on 2010-06-11
Gosh that's a lot of information.  Thanks for that.  Currently I do not have a dongle.   I borrowed my son's 3G when I had windows on my netbook.  Could anyone suggest which provider might be best.

---

### Post by Pushpalanka on 2010-06-13
Thnx mbuotidem. My dongle is using 3Connect software.It already have the facility of forcing connection to 3G or EDGE. I have already checked both of what you suggeted  except for the all combinations of authentication methods.I have tried some and was fed up with trying it. Is there a method to find them?

---

### Post by spiky001 on 2010-06-13
hi have a look here
[http://ubuntuforums.org/showpost.php?p=7622263&postcount=3](http://ubuntuforums.org/showpost.php?p=7622263&postcount=3)

---

### Post by gandaran on 2010-06-13
> **Pushpalanka said:**
> I too have the same problem. I tried to fill the Mobile Broad Band settings and to connect. I got my service provider in the list, but the default APN given was not what the company said:confused:. Anyway I tried both, but no good reaction.

Im using a HUAWEI E1550 dongle. Hope for a help.
the APN settings you just leave it blank (remove whatever is there) if your ISP uses Dynamic APN, or if your IPS require a static APN then fill in the one provided by your ISP for your contract.

---

### Post by gandaran on 2010-06-13
> **Pushpalanka said:**
> Thnx mbuotidem. My dongle is using 3Connect software.It already have the facility of forcing connection to 3G or EDGE. I have already checked both of what you suggeted  except for the all combinations of authentication methods.I have tried some and was fed up with trying it. Is there a method to find them?
if you have a computer running windows and your mobile internet connection go to the mobile 3g dongle properties, there you will find out what type of authentication method plus the APN it uses.
that's how I found out everything I needed to get my e1550 working.

edit,
you have to reboot the computer after filling in the setup details in network manager, you dont need to install any other 3g sofware to make it work except maybe usb-modeswitch if the dongle is not detected.
it wont work without the reboot.

---

### Post by RJB10 on 2010-06-21
I also have a 3g dongle and in help under advanced tools is where to find the APN which is 3internet and should be for anyone on three.My dongle worked perfect on ubuntu 9.10 but i have been unable to get it working on ubuntu 10.04 using the same methods.Ill try the advice from gandaran.Cheers!

---

### Post by sabbir.id on 2010-07-19
I need this help too. can you tell me step by step? i'm a new user

---

