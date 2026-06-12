---
title: "How Do You Get The Mobile Broadband Software To Work In Ubuntu?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by londonlad on 2010-10-13
Hi all,

My 3 mobile broadband software runs in Windows, but how can you get it to run in Ubuntu? I assume you use Wine, but I am not sure how! :(


[IMG]http://i56.tinypic.com/2by0br.png[/IMG]

---

### Post by AndyM3 on 2010-10-13
There is a possibility that you can just plug the modem in, wait a minute for NM to detect it, select "New Mobile Broadband Connection" from the NetworkManager menu, pick your country and network and it'll just work. Did you try that?

---

### Post by londonlad on 2010-10-13
Yes the modem works & I can get online, but I am wanting to know how to get the S/W working so I can send/receive text messages!

Thanks.

---

### Post by corcomp84 on 2010-10-13
what is the device spec's,, I was thinking about doing the same thing..

---

### Post by londonlad on 2010-10-13
> **corcomp84 said:**
> what is the device spec's,, I was thinking about doing the same thing..

Device specs? What dya mean, I am a noob! :confused:

---

### Post by AndyM3 on 2010-10-13
Looks like you can't send/receive SMSes ([look here]("http://www.eigenmagic.com/2009/02/02/3-australia-prepaid-mobile-broadband-with-ubuntu/")). And I don't think Wine is able to run something like their app. Sorry. :(

---

### Post by bennachie on 2010-10-13
I'm not sure about the current UK situation, but here in Australia, using 10.04 or 10.10, the method suggested by AndyM3 works just fine with the 3G modems provided by Telstra and Optus, and with most of those provided by Vodafone. 

If you have one of the exceptions, or absolutely must have access to SMS messages, Vodafone Mobile Connect for Linux will do the trick, and can be freely downloaded from [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12). You want the latest deb versions of ozerocdoff (0.4-2) and vodafone-mobile-connect (2.25.01-1). Don't worry about downloading usb-modeswitch, you've got a later version already installed.

I understand that, with a little manual intervention, VMC will also handle some of the recalcitrant modems distributed by other telcos in the UK, but haven't tried that. 

In any case, Network Manager has always worked for me on UK-based prepaid modems while travelling there in the past. I haven't tried Three (now merging with Vodafone over here, as it happens) but T-Mobile, O2 and Vodafone units work just fine.

---

### Post by yunone on 2010-10-13
i just use google voice now when i connected with my USB modem. its free and works great!

---

### Post by alexfish on 2010-10-13
> **londonlad said:**
> Yes the modem works & I can get online, but I am wanting to know how to get the S/W working so I can send/receive text messages!

Thanks.

Hi

have you tried WAMMU

alexfish

---

### Post by apmcd47 on 2010-10-13
If you have 10.04/Lucid, try [this page]("http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc").

Basically run this:```
sh -c 'wget http://www.betavine.net/repository/bcm_lucid_install.sh -O /tmp/bcm.sh && /usr/bin/xterm -e sudo sh /tmp/bcm.sh'

```It will give you something you can text with. I was using vodafone, I don't know if it will work with other networks.

Andrew

---

### Post by alexfish on 2010-10-13
> **apmcd47 said:**
> If you have 10.04/Lucid, try [this page]("http://www.betavine.net/bvportal/blog/view.html?blogId=133&postId=ff8080812942915f01294cd0e6e322bc").

Basically run this:```
sh -c 'wget http://www.betavine.net/repository/bcm_lucid_install.sh -O /tmp/bcm.sh && /usr/bin/xterm -e sudo sh /tmp/bcm.sh'

```It will give you something you can text with. I was using vodafone, I don't know if it will work with other networks.

Andrew

According to the site these are Beta Versions :

If you have problems with the software , Betavine would welcome user input
Hopefully Advancing the Final Release:

If you are a Novice at installing and un-installing this type of software "Think twice and request help from Betavine".

Andrew Bird seem's to have an understanding of how things work


Remember This Section is **Absolute Beginners Talk**
alexfish

---

