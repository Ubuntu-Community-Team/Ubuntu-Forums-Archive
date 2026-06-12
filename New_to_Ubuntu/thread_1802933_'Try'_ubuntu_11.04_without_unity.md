---
title: "'Try' ubuntu 11.04 without unity"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by e_james on 2011-07-12
Is it possible to try ubuntu 11.04 without unity before installation?

---

### Post by BrandonC19 on 2011-07-12
> **e_james said:**
> Is it possible to try ubuntu 11.04 without unity before installation?
Boot the live CD.
Select "Try Ubuntu"
After the Unity Desktop loads, log out.
Select the Classic Gnome option in the "Sessions" menu and Log In as user: "Ubuntu" and no password.
Hope this helps you :)

---

### Post by MG&amp;TL on 2011-07-12
Should be, by default unity probably won't work as you won't have got any graphics drivers.
 If that is not the case, I don't know, Normally I would say to change the option at the login screen, but if you haven't made an account, that won't be an option.
 Try it, it will probably, but not definitely, pop up with 'you do not have the hardware to run unity' when you 'try' the cd.

EDIT: Beat me to it! Yep, didn't realise logging out was  an option on the cd. Thanks Brandon, I've learned something too!

---

### Post by Swagman on 2011-07-12
I've never had Unity load on a Live CD. It needs correct graphics drivers to be installed but if you do that you have to reboot to activate and that loses the Live environment because a cd can't be written to.

Unless my sytem is a slouch but I don't think so

Asus EVO Mobo
Phenom IIx4 965 Black edition
nVidia GT8800 (512mb)
4gb RAM
Xonar Dx2
800 watt Corsair Psu
26" LCD monitor
1Tb HD

and a partridge in a pear tree

---

### Post by e_james on 2011-07-12
BrandonC19

I did think of the logout option and I have used it on older distros, but it doesn't seem to be available on this pc (eeepc 901). Sometimes I miss the blindingly obvious. I'm not actually using a live cd but a usb stick made from the desktop iso. Where I would expect to find a logout option I can only see Suspend, Restart, Shut down and System settings.

---

### Post by bodhi.zazen on 2011-07-12
Depends on what you mean by "without unity"

xubuntu, kubuntu, and lubuntu all come without unity ;)

---

### Post by coffeecat on 2011-07-12
> **MG&TL said:**
> Should be, by default unity probably won't work as you won't have got any graphics drivers.

If you didn't have graphics drivers, you'd have a blank screen! :wink: I think you mean 3d capable drivers. In fact the situation you describe affects mostly nvidia cards which need the proprietary driver for Unity. Many ATI cards and Intel graphics chipsets work just fine in the live session with their default open source drivers to give you Unity.  

> **e_james said:**
> Where I would expect to find a logout option I can only see Suspend, Restart, Shut down and System settings.

Even though the logout option is missing in the live session, there is a workaround. Press Alt+PrtScr+k to kill the xserver. With some systems you have to use the AltGr key instead, and the PrtScr key is sometimes labelled SysReq. You will be taken to the login screen where you can choose the classic desktop, using "ubuntu" for username and a blank for the password.

---

### Post by e_james on 2011-07-12
bodhi.zazen

Perhaps your comment is the essence of my problem. In the past I had a look at xubuntu and kubuntu (not lubuntu) and the one that most appealed to me was ubuntu (classic).

It may be helpful to add that I'm 63 and my favourite version of Windows is XP Pro because Vista and 7 are designed to do the things that Microsoft thinks are most important to the iPhone, YouTube, Twitter generation. Unfortunately Unity seems to be following the same path. So far, Linux Mint is not (I think). I'm hoping that I will not soon be forced into building my own distro because all the others have jumped on the same bandwagon. I would happily stick with ubuntu 9.10 but I find that I need the updates for new hardware etc.

---

### Post by bodhi.zazen on 2011-07-12
> **e_james said:**
> bodhi.zazen

Perhaps your comment is the essence of my problem. In the past I had a look at xubuntu and kubuntu (not lubuntu) and the one that most appealed to me was ubuntu (classic).

It may be helpful to add that I'm 63 and my favourite version of Windows is XP Pro because Vista and 7 are designed to do the things that Microsoft thinks are most important to the iPhone, YouTube, Twitter generation. Unfortunately Unity seems to be following the same path. So far, Linux Mint is not (I think). I'm hoping that I will not soon be forced into building my own distro because all the others have jumped on the same bandwagon. I would happily stick with ubuntu 9.10 but I find that I need the updates for new hardware etc.

Your problem moving forward will be that gnome 2 is no longer maintained by the gnome developers, they have moved on to gnome 3 (while Ubuntu has been working on Unity).

While some distros will be striving to maintain gnome 2, if the gnome developers could not maintain gnome 2, I doubt any fork of gnome 2 will last too long.

I would suggest you try Unity for a week, you might like it (yes I know change is hard).

If you still want gnome, try gnome 3 / gnome shell for a week.

If that does not work for you, then you are looking at a change, KDE, XFCE, LXDE, Fluxbox ...

[http://gnome3.org/faq.html](http://gnome3.org/faq.html)

> GNOME 2 had a long life, and parts of it became difficult to maintain  over that period. As a result, continued releases of the entire GNOME 2  desktop was never a practical option for the GNOME Project, and several  parts of the old GNOME 2 desktop will not receive new releases after  GNOME 3 is released. The traditional GNOME 2 desktop will not disappear  overnight, however: releases of GNOME 2 will continue to be supported by  distributions for years to come.

---

### Post by e_james on 2011-07-13
bodhi.zazen

Thanks for the comments.

My big mistake - maybe. I should have looked at lubuntu sooner. It appears that the designers of lubuntu think rather like me. I have now made a usb stick with kubuntu, xubuntu and lubuntu. Kubuntu doesn't look like ubuntu with unity; it looks a bit like the original Xandros installation on my eeepc 901 and I didn't like that, which is why I installed ubuntu. I could probably get on well enough with xubuntu but, on first impressions lubuntu looks right. The first problem is that I can't see the procedure to set up the wireless networking. I have posted a separate thread for help but no reply so far.

---

### Post by Swagman on 2011-07-13
You could also try Peppermint.. which is a slimmed down version of mint. It looks similar to Lubuntu.

[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by e_james on 2011-07-13
Swagman

Definitely worth a look, although I have no big issues with Mint itself - yet.

In addition - lubuntu network problem resolved. It has done everything I have asked it to do so far (except start Firefox). It takes a little more work to install video and audio codecs but then I get to choose only the ones I need.

---

