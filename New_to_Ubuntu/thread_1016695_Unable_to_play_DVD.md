---
title: "Unable to play DVD"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by mclaughlin97 on 2008-12-20
Hi Guys

Have got ubuntu going on my laptop and loving it so far. However am unable to play normal DVD movies. I have Totem movie player installed. When I try to play a DVD i recieve the following error message.

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Any help please

Regards

David

---

### Post by taurus on 2008-12-20
Looks like you need to install libdvdcss2 first.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jonobe on 2008-12-20
i think you need the codecs for the player.  I ahd similar problem.

You can get these by going to Sytem>Administration>Synaptic Package Manager

you will be asked for your password.

Search for 'gstreamer', or scroll down until you find the gstreamer packages - there are quite a few.

The one you most likely need to add on is the gstreamer0.10-plugins-ugly.

Mark it for installation by clicking on the square next to it.  Then Apply, which is a button near the top.

All should run fine.

You might also find gxine is better than totem player.  You can download it easily through Applications>Add/Remove dialogue, or again through synaptic manager



this will give all the licenses/codes you should need.

if still a problem, install the multiverse variant of gstreamer.

good luck

---

### Post by mclaughlin97 on 2008-12-20
Thankyou everyone for very quick replies. Have installed libdvdread3 and now can play

---

### Post by KEE on 2008-12-23
> **jonobe said:**
> i think you need the codecs for the player.  I ahd similar problem.

You can get these by going to Sytem>Administration>Synaptic Package Manager

you will be asked for your password.

Search for 'gstreamer', or scroll down until you find the gstreamer packages - there are quite a few.

The one you most likely need to add on is the gstreamer0.10-plugins-ugly.

Mark it for installation by clicking on the square next to it.  Then Apply, which is a button near the top.

All should run fine.

You might also find gxine is better than totem player.  You can download it easily through Applications>Add/Remove dialogue, or again through synaptic manager



this will give all the licenses/codes you should need.

if still a problem, install the multiverse variant of gstreamer.

good luck

hmm im going to try what you first mention.. i get gxine going any more =(

---

### Post by mapes12 on 2008-12-23
> **mclaughlin97 said:**
> Hi Guys

Have got ubuntu going on my laptop and loving it so far. However am unable to play normal DVD movies. I have Totem movie player installed. When I try to play a DVD i recieve the following error message.

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

Any help please

Regards

David
The ultimate multimedia guide is here: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

