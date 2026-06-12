---
title: "wicd cannot reconnect to wireless network without rebooting"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by beew on 2010-07-22
Hi,

I have installed Ubuntu 10.04 on my Dell D410 laptop. I have been able to get connected to wireless network using the default gnome network manager without problem.  For the purpose of experimenting I have removed nm and installed wicd version 1.7 (the newest version in the Ubuntu repo) to see how it performs as I have read many good things about it.  

Here is what happens. I configured wicd to connect to my WEP encrypted  wireless network and it connects automatically at start up. However, after a while it disconnects, this happens apparently when the signal is momentarily weak and then when it tries to reconnect again it almost always fails because it says it cannot obtain an IP address. At this point there seems to be no way to get it reconnect even manually, I have tried restarting wicd at the terminal without avail. But as soon as I restart the computer, it connects quickly and smoothly without problem.

It seems this is an old problem going back a few years, discussions about it are scattered all over the places on the internet, but there doesn't seem to be a definitive solution and these discussions seem to be rather old and most concern older versions of Ubuntu and wicd which may not apply to Lucid and the current version of wicd. 

Any help would be greatly appreciated. Thanks.


P.S. I am using a netcore usb wireless card because the internal card is apparently dead. nm can connect without problem.

---

### Post by bodhi.zazen on 2010-07-22
> **beew said:**
> Hi,

I have installed Ubuntu 10.04 on my Dell D410 laptop. I have been able to get connected to wireless network using the default gnome network manager without problem.  For the purpose of experimenting I have removed nm and installed wicd version 1.7 (the newest version in the Ubuntu repo) to see how it performs as I have read many good things about it.  

Here is what happens. I configured wicd to connect to my WEP encrypted  wireless network and it connects automatically at start up. However, after a while it disconnects, this happens apparently when the signal is momentarily weak and then when it tries to reconnect again it almost always fails because it says it cannot obtain an IP address. At this point there seems to be no way to get it reconnect even manually, I have tried restarting wicd at the terminal without avail. But as soon as I restart the computer, it connects quickly and smoothly without problem.

It seems this is an old problem going back a few years, discussions about it are scattered all over the places on the internet, but there doesn't seem to be a definitive solution and these discussions seem to be rather old and most concern older versions of Ubuntu and wicd which may not apply to Lucid and the current version of wicd. 

Any help would be greatly appreciated. Thanks.


P.S. I am using a netcore usb wireless card because the internal card is apparently dead. nm can connect without problem.

I have not had this problem with wicd, but I did have it with NM.

If NM works better, revert.

Otherwise I suggest you file a bug report, hard to know if it is a problem with wicd, your kernel, or your wireless card.

---

### Post by beew on 2010-07-22
Actually nm works perfectly on this machine so my problem is not that I cannot get wireless.  I am rather in the process of experimenting and trying to get wicd to work. :p

As for bug report, quite few have been filed on the same question for different versions of Ubuntu and wicd and it seems that they all kind of get buried in oblivion. I am hoping that I can get some help here because the Ubuntu forum is a very active place visited by many Linux pros.

---

### Post by bodhi.zazen on 2010-07-22
> **beew said:**
> Actually nm works perfectly on this machine so my problem is not that I cannot get wireless.  I am rather in the process of experimenting and trying to get wicd to work. :p

As for bug report, quite few have been filed on the same question for different versions of Ubuntu and wicd and it seems that they all kind of get buried in oblivion. I am hoping that I can get some help here because the Ubuntu forum is a very active place visited by many Linux pros.

Well, that is because as I indicated, although the problem manifests when you run wicd, it could be anything from a kernel problem to a problem with your network card to a problem with your router to wireless security.

Does wicd work when you turn off WEP/WPA ?

---

### Post by beew on 2010-07-22
> **bodhi.zazen said:**
> 
Does wicd work when you turn off WEP/WPA ?

That I wouldn't know because I am sharing the router with 9 people. I have to wait til no one is around to try that out.

I read on the internet that it may have something to do with the new Linux kernel but then again nothing seems definitive. But if that is the case many people using wicd with Ubuntu 10.04 should experience the same problem. 

I have a full installation of Ubuntu on an external hard drive (you can never do such a cool thing with Windows) I will try to plug it in a different computer to see if it is a problem with the wifi card. Unfortunately I have no wireless access on the other computers that are available to me at the moment.

---

### Post by phillw on 2010-07-22
Hi beew,

there are plenty of things you can do to ubuntu to try and break it, most people search for solutions for when they have.

If you really want to do non standard things to help chase a bug, I would recommend that you set up a small partition to hold your "My test area" along side your "I know it works" area.

Keeping your /home areas up to date can be done by either sharing them or rsyncing them. If you are testing things out, please do keep a backup of your /home area.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) has how to do that, as you are inquisitive, I'd recommend you do that. It has stood me in good stead when I've gone ahead and broken things :p

Regards,

Phill.

---

### Post by beew on 2010-07-22
> **phillw said:**
> Hi beew,

If you really want to do non standard things to help chase a bug, I would recommend that you set up a small partition to hold your "My test area" along side your "I know it works" area.

Keeping your /home areas up to date can be done by either sharing them or rsyncing them. If you are testing things out, please do keep a backup of your /home area.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) has how to do that, as you are inquisitive, I'd recommend you do that. It has stood me in good stead when I've gone ahead and broken things :p

Regards,

Phill.

Thanks Phil. I have actually made a full installation of Lucid on an external hard drive (no a live usb with persistence, but a full blown installation) which I use to test stuffs. Besides being safe, it also has the advantage that I can plug it in different computers with different hardware configurations (like I said you can only do such a cool thing with Linux)

 My "real" installation is in my internal hard drive and it is pretty safe. :P

---

### Post by bodhi.zazen on 2010-07-22
> **beew said:**
> That I wouldn't know because I am sharing the router with 9 people. I have to wait til no one is around to try that out.

I read on the internet that it may have something to do with the new Linux kernel but then again nothing seems definitive. But if that is the case many people using wicd with Ubuntu 10.04 should experience the same problem. 

I have a full installation of Ubuntu on an external hard drive (you can never do such a cool thing with Windows) I will try to plug it in a different computer to see if it is a problem with the wifi card. Unfortunately I have no wireless access on the other computers that are available to me at the moment.

My previous network manager problem was kernel related and specific to a single wireless card I have. With an upgraded kernel the wireless has worked flawlessly.

But when you see bug reports all over the map like that it is usually an indication of multiple potential problems contributing to the defunct behavior, and so each "solution" is unique and applies only to some.

If you are interested , keep testing in various environments and watch the logs.

---

### Post by beew on 2010-07-22
You are of course correct that it could be many things, including kernel problem or wifi card. But the symptom is very specific, it can connect flawlessly at start up, just cannot reconnect once it is disconnected. Moreover the reason is specifically that it can't get an IP address.

 I am a newbie and don't know much of the ins and outs, but naively I think the symptom suggests that things are foundamentally sound, it is just that wicd somehow "forgets" something when trying to reconnect. Someone may know of a way to work around it by editing some configuration files by setting some parameters to be "True", for example.

---

### Post by phillw on 2010-07-22
> **beew said:**
> Thanks Phil. I have actually made a full installation of Lucid on an external hard drive (no a live usb with persistence, but a full blown installation) which I use to test stuffs. Besides being safe, it also has the advantage that I can plug it in different computers with different hardware configurations (like I said you can only do such a cool thing with Linux)

 My "real" installation is in my internal hard drive and it is pretty safe. :P

He he, you never got to see my little 80Gb hard drive with 5 verions running on it. It's amazing what you can squeeze in when you just have /home, /home_backup and share the /swap ;)

9.10 (Supposed to be my production area, i.e. safe); 10.04 alpha3 (started as the RC for alpha1, but I couldn't break it, so it became "production" to test day to day reliabilty on), 10.04 testing (all the betas), lubuntu 10.04 alpha2 (which then became production) and lubuntu testing. 

I'm taking a Gap year this cycle, it was 'fun' I had three pages of GRUB boot options !!! But, I'd recommend it to anyone :D

I use persistent USB sticks, and keep my 9.10 one from the shop safe as I **know** it will boot my system and remember who I am :p
:popcorn:

Do enjoy your time; it's not all serious - we are allowed to have some fun along the way.

Regards,

Phill.

---

### Post by beew on 2010-07-22
Hi, Phil,

It is amazing that you can cramp so many OS's in 80G.

I set up dual booting windows xp and Ubuntu Lucid on a 80G internal hard disk and there is actually a lot of room left. I need windows only to run a software which wouldn't work with wine and I don't have enough ram to run it in virtual box. 

I have a 4 G live USB with persistence for installation purpose. It runs fast (as it uses ram) but I didn't find it that satisfactory in testing things because you can't do things like kernel updates with a live usb even with persistence. But with a full blown installation you can. I have also installed a full blown installation of Ubuntu 10.04 on a 8G pendrive to see if it works. It totally works even if it is a bit slow as you would expect!:p

I have got only the latest version because I am a complete newbie, just started messing with Linux a month or two ago. Now I am trying to get Ubuntu to dual boot with Fedora. Folks have been helpful on the other thread on how to do it.

---

### Post by phillw on 2010-07-22
Oooh, I *really* shoudn't say this, but try putting lubuntu on to a usb stick. You can do it as persistent  or even as a 'full' install onto anything larger than 1GB (You'd need to factor in your requirement for data).

It's a cheeky little Meerkat, but available tamed as a Lynx in the 10.04 beta3 stable version over at [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

So, if you like to have a 'play' and want something low resource but still 'Maverick', you've found it ;)

There are more details in my Signature about lubuntu.

Regards,

Phill.

---

