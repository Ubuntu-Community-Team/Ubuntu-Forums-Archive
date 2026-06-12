---
title: "video program install issues"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Hugsifer on 2009-01-05
I attempted to download a linux version of realplayer and I couldn't figure out how to open it to install it. 

Also for future reference is this something I'll be comming across with all of the linux based programs or have I just missed some critically important intalls/programs?

---

### Post by jimmy the saint on 2009-01-05
If you are on Intrepid (8.10) Just open synaptic (system>administration>Synaptic package manager) and search for real player.  Install it.  It will be under sound&video in your applications menu.

---

### Post by Tim Sharitt on 2009-01-05
Most applications for ubuntu can be installed via Synaptic or Add/Remove. Realplayer is availible in a .deb file, There is a link for it under the main download link on the realplayer site. If your new to linux, that is probably your best bet. Once the file is downloaded, you should be able to double click it and bring up Gdebi. Just click Install in the top right corner of the window.

---

### Post by Sef on 2009-01-05
> If you are on Intrepid (8.10) Just open synaptic (system>administration>Synaptic package manager) and search for real player. Install it. It will be under sound&video in your applications menu.Real Player is not in Add/Remove.  However, an open source player, Helix, is in the repositories.  At Show: set it to 'All Open Source Applications' .

> Also for future reference is this something I'll be comming across with all of the linux based programs or have I just missed some critically important intalls/programs?It depends on whether the software manufacturer has decided to support GNU/Linux or not.

---

### Post by jimmy the saint on 2009-01-05
Realplayer has been added to the repositories.  It is ill advised, especially for someone new to Linux, to install a program from a website when it is already available in the repositories.  It is better to get in the habit of installing via the repositories rather than hunting down applications at websites and then wondering how your machine has so many issues.  

Just use the version in the repositories and you will be fine.

*Edit* I apologize.  I forgot that realplayer was added to the Medibuntu repositories rather than the main repos.  I say add the medibuntu repos (guide below) because it makes a lot of useful apps like picasa, google earth, better media codecs etc. available as well as reaplayer.  In addition, If an updated gets added to the repos, you will automatically receive that update rather than having to do it yourself.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by RomeReactor on 2009-01-05
Hi. You don't need Real Player; you can use VLC, Mplayer, or Smplayer to play RM, RAM or RMVB files. You'll probably need more codecs, so install **ubuntu-restricted-extras**. Look for them in Synaptic (System->Administration->Synaptic), or:

* [click here]("apt:vlc") to install VLC

* [click here]("apt:mplayer") to install Mplayer

* [click here]("apt:smplayer") to install Smplayer

* [click here]("apt:ubuntu-restricted-extras") to install ubuntu-restricted-extras

To install codecs for wmv and asf files you can get [w32codecs]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu3_i386.deb") (for Ubuntu 32-bit) or [w64codecs]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu2_amd64.deb") (for Ubuntu 64 bit); just download and double click to install. However, read the [disclaimer here]("https://help.ubuntu.com/community/Medibuntu#Disclaimer") first.

In any case, if you really want Real Player you can follow Jimmy's instructions. And it would be best if you [added the Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories") so you can keep the w32codecs (or w64codecs) up to date.

@ Jimmy: The realplayer .deb package is actually in the Medibuntu repository.

---

