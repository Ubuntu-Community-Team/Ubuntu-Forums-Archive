---
title: "Ubuntu Software Center freezes"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by jermza on 2011-01-12
I thought this was once-off, but it happens quite often.  There is no pattern, really, but when I click on the Info tab of a number of programs, it doesn't open the info box and, instead, the software center freezes and greys itself out.  I then have to force quit.

If I go back to the same program, it seems that it freezes again.

Is this my system (10.10) or is it those programs?

---

### Post by vedster on 2011-03-05
Probably those programs, If you did install any new programs that fall into that category go to the Synaptic Package Manager and try removing them.

System > Administration > Synaptic Package Manager

---

### Post by heyho on 2011-03-05
I try to avoid using the software centre for exactly this reason.  I find it quite unreliable, which is a shame, as it is most likely the first port of call for new users wanting to install new software.

I try to use the terminal whenever possible to install new software.

---

### Post by alexis44 on 2011-03-05
I've had similar problems with it.  Not a crash, but it will hang and use too much of my resources. :confused:

---

### Post by Andrew_P on 2012-02-16
> **heyho said:**
> I try to avoid using the software centre for exactly this reason.  I find it quite unreliable, which is a shame, as it is most likely the first port of call for new users wanting to install new software.

I try to use the terminal whenever possible to install new software.

I agree.  I've just wasted a week trying to get Ubuntu Software Center working again since I uninstalled OpenOffice.org and installed LibreOffice 3.4.  For no apparent reason Software Center stopped working after that; it just *sits* there with the spinner cursor going 'round and 'round, and the software titles never load in the right pane.

There's now an online version of the Ubuntu Software Center, called the [**Ubuntu Apps Directory**]("https://apps.ubuntu.com/cat/") ([apps.ubuntu.com/cat/]("https://apps.ubuntu.com/cat/")) that supports Lucid Lynx (10.04) and later versions.  As long as your Web browser and Internet connection are working, you can access it.  I haven't figured out how to make the apt:// protocol work yet in my browser when I click on one of the "Install" buttons.  They should have included alternate http:// protocol links so that one might download the .deb files to one's hard drive and be able to install them by simply double-clicking on them.

**UPDATE:**
There's a description of how to make the apt:// protocol work in Firefox 3.5 at [https://getsatisfaction.com/allmyapps/topics/protocol_apt_and_firefox_3_5]("https://getsatisfaction.com/allmyapps/topics/protocol_apt_and_firefox_3_5").  I just tried it in SeaMonkey 2.7.  The procedure is essentially the same.

---

