---
title: "Got rid of Windows."
date: 2010-03-01
forum: New to Ubuntu
---

### Post by peace.gangsta on 2010-03-01
After spending some time on Windows/Ubuntu dual boot,I removed windows permanently.
Initially there were two partitions C(50Gigs) where my windows and Program Files were present and D(250 Gigs)which was a secondary partition.
Now while installation I formatted C drive and installed Ubuntu on this drive.But this has lead me into a problem. All my songs and other media files are on partition D ,which has to be mounted every time I log in.
I use file sharing softwares like DC++ which now requires re-sharing every time I restart my computer. This is very frustrating. Is there any solution?
Also there is something wrong with my Amarok, it just doesn't play songs.I have already added media present on an ntfs partition 'D'.Whenever I click on the play button it goes through a couple of songs rapidly without playing them and eventually crashes.
I am attaching a crash report.

---

### Post by beany1 on 2010-03-01
install ntfs-config for easy config of drives inc making them mount at boot, as for amarok, did you install the medibunti/restricted extras?

---

### Post by alexandari on 2010-03-01
Try setting amarok to alsa. It's in it's settings. Happens to me when I'm using oss with some app. Skipping songs and then crashing.

---

### Post by peace.gangsta on 2010-03-01
I am using Songbird presently, but nothing can possibly beat A\m/arok :P

---

### Post by davec64 on 2010-03-01
If you want to use a graphical tool try Mount Manager. It will write the required code to fstab for you. :)

Then again if you want you can edit fstab yourself using a text editor like Gedit.

:)

This way your data partition will be mounted at boot and therefore you'll be able to access the shares.

---

### Post by peace.gangsta on 2010-03-01
> **beany1 said:**
> install ntfs-config for easy config of drives inc making them mount at boot, as for amarok, did you install the medibunti/restricted extras?
I have Gstreamer plugins for mp3 installed. And if the other players can play mp3 files properly,then what is the problem with Amarok ?

---

### Post by peace.gangsta on 2010-03-01
> **alexandari said:**
> Try setting amarok to alsa. It's in it's settings. Happens to me when I'm using oss with some app. Skipping songs and then crashing.
How do I set Amarok to alsa ?
I however set my audio device to HDA Intel (Alsa Mixer).
Also something happens whenever I launch amarok.I get this pop on my top right at the volume control applet:
> Phonon:KDE's Multimedia Library
The audio playback device HDA Intel(STAC92XX Analog) does not work.Falling back to HDA INTEL HDMI (HDMI Audio Output).
The device which I have selected in Volume control is HDA Intel(Alsa mixer).

---

### Post by peace.gangsta on 2010-03-01
> **davec64 said:**
> If you want to use a graphical tool try Mount Manager. It will write the required code to fstab for you. :)

Then again if you want you can edit fstab yourself using a text editor like Gedit.

:)

This way your data partition will be mounted at boot and therefore you'll be able to access the shares.
What does Mount Manager does at root level.
I keep an extra partition just cause it saves me the trouble to back-up files even when I am formatting or even changing my Operating System, as I usually do.
After doing what you suggest will it destroy the partition and append the partition to the main/Primary partition?

---

