---
title: "unable to play my video files"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by koyakishore on 2009-06-25
hi mates..

i'm unable to play my video files in any of my players..

i use vlc n tottem movie player..

the player getting terminated as soon as i open a video file..

no prob with audio files..
wat may be the reason..??

plz help me out..

---

### Post by Divider on 2009-06-25
Video drivers most likely.

Repost output for:
```
lspci
```

If you know your video drivers are config'd correctly, then heres the rundown:

If your using "desktop effects" (compiz) try disabling them, make sure that vlc is set to play with X11 as the playback output.

if all else fails, try installing the GStreamer codecs.

Lastly, it could be your file type, .rmvb is not supported in vlc or totem, only mplayer can do that.


```
sudo apt-get install mplayer
```

try that and get back to me.

---

### Post by masux594 on 2009-06-25
maybe you don't have the right codecs? What kind of video do you want to play?

Sysc, A

---

### Post by Divider on 2009-06-25
> **masux594 said:**
> maybe you don't have the right codecs? What kind of video do you want to play?

Sysc, A

Well VLC comes stock with almost EVERY codec imaginable. Out of the box it's played everything ive thrown at it execpt realmedia.

---

### Post by koyakishore on 2009-06-25
my video format is avi... so that is not the prob..

by the way...i'm very new to ubuntu..
i dint get ur point "Repost lspci"

plzz...clear it..

and one more thing is..
I reinstalled vlc.. then it got opened but no display.. i cud just hear audio..but no video..
then i tried to change the settings i.e. X11..
as soon as i changed.. the initial prob is back again..
vlc player gettin terminated..

---

### Post by koyakishore on 2009-06-25
out for "lspci"

root@Home:~# lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Modem: ALi Corporation SmartLink SmartPCI563 56K Modem

---

### Post by Divider on 2009-06-25
Tinker with the output options, and hope for a bit of luck.

I cant remeber how to open a media file from terminal thru vlc, that would give you the full error.


By the way, did you disable compiz?

system>pref>appearance

goto desktop effects

select none and then close

---

### Post by koyakishore on 2009-06-25
yaa... i disabled compiz..

---

### Post by koyakishore on 2009-06-25
shall i try installing Gstreaming codecs..??

if yes..
give me the command for that..:)

---

### Post by Divider on 2009-06-25
go into your synaptic package manager. type in GStream

---

### Post by koyakishore on 2009-06-25
system-admin-synaptic package manager..

is this right..??

then..where to type GStream..???

as i already said..i'm very new to ubuntu..

so..plz dont mind.. and reply me..

thanks in advance..:)

---

### Post by Sef on 2009-06-25
Applications > Add/Remove > Show: All Available Applications > Search: Restricted > Click on the box next to Ubuntu Restricted Extras > Apply Changes > Apply > Close.

---

### Post by koyakishore on 2009-06-25
reply to above post..

when i chose ubuntu restricted extras..

i got the below msg displayed..

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

how will i know that software..??

---

### Post by koyakishore on 2009-06-25
i dint solve my problem yet..:confused:

i'm still unable to play my video files..

i did the following steps..

1.disabled compiz..
2.reinstalled my vlc..
3.installed GStreamer codec..


but still...d same prob..

plz some1 help me out...

video files playing well in windows..but not in ubuntu..

i'm struggling since yesterday...:confused:

---

### Post by pablolie on 2009-06-25
the restricted extras install does conflicts if you have already been installing bits and pieces while cruising the net with Firefox. 

i think ubuntu should just install the resrticed extras as a standard part of the installation, or at least have a question during install saying something like "for maximum out of the box usability with rich internet content, we recommend to install restricted extras bla bla" - most people would do it and it would reduce the number of issues in these forums by at least 50%.

i recommend everybody install the restricted extras *right* after the Ubuntu clean install.

---

### Post by koyakishore on 2009-06-25
yaa...i installed that too...

restricted extras are also installed... but.:(

---

### Post by koyakishore on 2009-06-25
how will i know if it is a video drivers prob..??

---

