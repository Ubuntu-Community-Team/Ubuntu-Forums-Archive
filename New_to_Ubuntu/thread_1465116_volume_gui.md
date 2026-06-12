---
title: "volume gui"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-29
Is there really no simple gui for adjust volume in openbox other than alsamixergui or gamix?Don't need the whole mixer shown,only a simple volume regulator.

---

### Post by Paresh on 2010-04-29
I'm sure you can simply click the speaker icon in the top task bar and you get a simple slider to adjust the volume.

---

### Post by dzon65 on 2010-04-29
In openbox?

---

### Post by tarps87 on 2010-04-29
It depends, are you using a panel? If so there is probably a sound control module.  I am using lxpanel which has a simple master control built in.

---

### Post by kerry_s on 2010-04-29
> **dzon65 said:**
> Is there really no simple gui for adjust volume in openbox other than alsamixergui or gamix?Don't need the whole mixer shown,only a simple volume regulator.

i thought you was using gnome panel?

---

### Post by tarps87 on 2010-04-29
Just seen another of your posts, if you are using gnome-panel make sure you have the notification area on the panel, this should contain the volume control

---

### Post by dzon65 on 2010-04-29
No,it doesn't.

---

### Post by kerry_s on 2010-04-29
for now you can just stick 2 launchers to click on, 1 for up & 1 for down.

commands:

up-> amixer set Master 3+
down-> amixer set Master 3-
just in case, mute-> amixer set Master toggle

zenity?

#!/bin/bash

num=`zenity --scale --min-value=0 --max-value=100 `
amixer set Master $num

---

### Post by dzon65 on 2010-04-29
Well,I've got a gui to change the volume (gamix)but like alsamixer it opens up the whole mixer.

---

### Post by dzon65 on 2010-04-29
> **tarps87 said:**
> Just see another of your posts, if you are using gnome-panel make sure you have the notification area on the panel, this should contain the volume control

That's just the point.Even with a volume applet showing under gnome,it won't show in a OB session.

---

### Post by dzon65 on 2010-04-29
This is the simplest I can come up with.Guess I could edit the gamix script to make it smaller.

---

### Post by kerry_s on 2010-04-29
dang, your stuff is dark!

i got bad eyes, had to put my glasses on to see the pic. :lolflag:

---

### Post by dzon65 on 2010-04-29
Used dark star before.I'll keep it like this,it's the simplest I could find/make.

---

### Post by tarps87 on 2010-04-29
> **dzon65 said:**
> That's just the point.Even with a volume applet showing under gnome,it won't show in a OB session.

You say that you are using gnome-panel and the standard package for this includes the volume applet, this should work as I used gnome-panel under openbox for a while before switching to lxpanel, admittedly this is on an Arch system.  If I'm to assume that you have a gnome session and an openbox session on this machine and it works in the gnome session I would check how you are starting the gnome-panel

---

### Post by dzon65 on 2010-04-29
Found some threads by urukrama and indeed it will not show in openbox.Perhaps in arch but not on this setup.(minimal/openbox)

---

### Post by kerry_s on 2010-04-29
try running "gnome-volume-control-applet" in your terminal & see if the volume icon appears. if it works add to your startup.

thats the old gnome-panel mixer, suppose to still be there just not used.

---

### Post by dzon65 on 2010-04-30
Well,I did add it,doesn't show but messed something up.All sounds gone.Have to do a reinstall anyway so gonna avoid as much gnome as I can.Should've stayed with gamix but what can you do.:lolflag:

---

### Post by dzon65 on 2010-04-30
The sounds back.Was due to gnome-media.I had gamix installed and when you install gnome-media,this, or overrules or kills gamix.Aaand,gamix and rhytmbox live stream audio won't work or partially when alsamixergui isn't installed.

---

### Post by Zill on 2010-05-02
> **dzon65 said:**
> ...Have to do a reinstall anyway so gonna avoid as much gnome as I can...
You could try [CrunchBang]("http://crunchbanglinux.org/")...OpenBox WM with a simple volume control (volwheel) as standard. :-)

---

### Post by dzon65 on 2010-05-03
I installed the alsamixergui.It's lighter and stabler than volwheel.As for crunchbang,well I like my setup,it's fully packed,quite fast (next to openbox and thunar it's loaded with leightweight progs and comes at 2.3 Gb,that's included gimp and some openoffice stuff)
Kind regards,J.

---

