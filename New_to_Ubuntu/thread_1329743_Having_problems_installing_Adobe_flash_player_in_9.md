---
title: "Having problems installing Adobe flash player in 9.10"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Scrambles on 2009-11-17
Everytime I try to install the plugin I get this error message and I'm not sure what to do. I'm pretty new to Ubuntu so I still haven't figured everything out. Thanks for any help.

[ATTACH]136647[/ATTACH]

---

### Post by Sealbhach on 2009-11-17
Hi, go into Synaptic Package Manager and install

flashplugin-nonfree

Make sure you have ticked the Multiverse box in your Software Sources too.

.

---

### Post by Scrambles on 2009-11-17
> **Sealbhach said:**
> Hi, go into Synaptic Package Manager and install

flashplugin-nonfree

Make sure you have ticked the Multiverse box in your Software Sources too.

.
I just tried that, there was nothing for flashplugin-nonfree.

---

### Post by bkratz on 2009-11-17
You could  go here

[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

download the .deb file for linux

---

### Post by Scrambles on 2009-11-17
> **bkratz said:**
> You could  go here

[http://get.adobe.com/flashplayer/?promoid=DXLUJ](http://get.adobe.com/flashplayer/?promoid=DXLUJ)

download the .deb file for linux
That didn't work, just got this error messsage.

[ATTACH]136671[/ATTACH]

---

### Post by RandomP on 2009-11-17
That's not an error, that tells you what it will do... (Unless you mean the red text which is blurry and unreadable)
I am guessing you can't click install then?

---

### Post by Scrambles on 2009-11-17
> **RandomP said:**
> That's not an error, that tells you what it will do... (Unless you mean the red text which is blurry and unreadable)
I am guessing you can't click install then?
Under Status it gives me an error message saying "Error: Wrong Build"

---

### Post by Sealbhach on 2009-11-17
> **Scrambles said:**
> I just tried that, there was nothing for flashplugin-nonfree.

That must be because you haven't added Multiverse to your software sources.

.

---

### Post by garvinrick4 on 2009-11-17
run in Terminal.

sudo gedit /etc/apt/sources.list 


Look in list that opens and make sure you have this.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

If not you have to copy and paste the line starting with deb
to Software Sources to other software tab to ADD and paste it
in APT line click add source and close.

While in Other Software tab make sure disbled on upgrade to karmic
and disabled on upgrade to karmic non-free   are checked.

close and will be added to repositories.

Go to Terminal Code:   sudo apt-get upgrade

Now add your software.

---

### Post by lidex on 2009-11-18
It's here:
[http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=karmic&section=all]("http://packages.ubuntu.com/search?keywords=flashplugin&searchon=names&suite=karmic&section=all") so apparently, as stated, you don't have that repository enabled.

---

### Post by garvinrick4 on 2009-11-18
To No one in particular:

They are disabled on upgrade to karmic and sometimes users forget to enable
and reload repositories and there is flash found when trying to re-install. Happens
a lot.  Seems that karmic partners is never in their sources list either. 

Software Sources in Administration:  Check the disabled on upgrade to karmic boxes 2 of
them.  And click add then add  the  karmic partner.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

close and reloads.

 Open Terminal Code:      sudo apt-get update

Install your software of choice.

ubuntu-restricted-extras or flashplugin-nonfree


Always seems to solve the issue.

---

