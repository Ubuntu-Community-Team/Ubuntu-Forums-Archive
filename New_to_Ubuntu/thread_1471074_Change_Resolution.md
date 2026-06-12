---
title: "Change Resolution"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Qwerty_ on 2010-05-03
G'day I just need some help to set the correct resolution on the 10.04 UNR. It is default to 1024X768 however the Netbook I am running (Acer Aspire one AO751h) runs native at 1366X768.

Now I have tried to run the following code which I have used multiple times in the past to fix resolutions.

```
sudo dpkg-reconfigure xserver-xorg
```

Does this not longer work in 10.04? If so how else can I reconfigure the x server to fix my resolution, as I think I am having performance problems due to the LCD not running in it's native resolution.

Also how can I make the brightness function keys work, sound keys work fine.

Also I have installed the restricted drivers that are available to me, that got the wireless working perfectly.

---

### Post by cbecker78 on 2010-05-03
If 10.04 still has an xorg.conf file, you can add 

```
SubSection "Display"
 Depth        16
 Modes      "1366X768"
 EndSubSection
``` under the Screen devices section.

---

### Post by Qwerty_ on 2010-05-03
I just did a search and was not able to find the xorg.conf what his it been changed to?

---

### Post by 23dornot23d on 2010-05-03
It does not exist in Lucid .... you need to do this in a terminal

sudo nvidia-xconfig

---

### Post by Qwerty_ on 2010-05-03
Sudo nvidia-xfconfig does not work for me. Probably because I'm not using the restricted drivers, this netbook has the Intel GMA950 graphics processor.

---

### Post by 23dornot23d on 2010-05-04
Have looked for more info on xorg.conf Intel GMA950 - Aspire one AO751h
 ...... but only found bug reports closed though

With a lack of information .... given on the Bug report ,,,, it was closed ...
[Bug Report on similar issue]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/426791")


The command should have been this ...... 

X -configure
Check that the etc/X11/xorg.conf looks ok

Post it on here after creating it  ..... if you would please .....
( the xorg.conf can always be deleted if it does not help - which will return the computer back to its current state )

so once done .....
Then .. try a reboot ... after the reboot check this file for useful information.
 
gedit /var/log/Xorg.0.log

and post the results .....

After doing some more searching .... on .....

[URL="http://www.uluga.ubuntuforums.org/AO751h%20linux%20graphics%20drivers%20solved"]AO751h linux graphics drivers solved
[/URL]
 this may not be a machine that runs well on Lucid ,,, 
Previous [BUGS]("https://help.ubuntu.com/community/AspireOne/AO751h") there are some solutions here though .....

But also look here ... there are some other success stories using LINUX ..... 
They may also show something that might help .... 
if you cannot go any further, to solve this .....

[SUSE Article]("http://www.linux.com/distrocentral/distroblogs/210140-opensuse-112-video-on-acer-aspire-one-ao751h")

[CrunchBang Article]("http://thatlinuxbox.com/blog/article.php/20100214220940151")

---

### Post by Qwerty_ on 2010-05-05
Thanks for your help mate, I followed the guide on editing grub and that has fixed the resolution for now. I am going to further look into setting up the drivers properly later as im hoping that will give me better performance because dragging windows around is currently sluggish. As is scrolling up and down in chromium.

---

