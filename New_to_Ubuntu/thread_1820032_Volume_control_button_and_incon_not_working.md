---
title: "Volume control button and incon not working"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by chitragurung on 2011-08-07
I have been using UBUNTU 10.04 with my Dell Inspiron min 10. Now I got problem with volume control. I have volume control button in my keyboard. when i push it no response. Sound is working fine but I can not up and down volume. I have volume control button at panel and it also does not work when I click it it has two option like mute all and sound preference. Mute all is light but when i click on sound preference it gives error message

'waiting for sound system to response"

But nothing happened.

How to fix ? I try to find in forum and tried some solutions but could not fixed yet. Anybody have solution for it ?

---

### Post by Frogs Hair on 2011-08-07
I had a multifunction keyboard that no longer worked because Windows or Linux could not supply a driver. Though , none of multifunction keys worked the screen functions worked fine. I have to ask if this is a new problem or has it been this way since installation .

---

### Post by chitragurung on 2011-08-09
It was not in the beginning. I have been using this note book since last three years and it is noticed after couple of weeks before.

Thanks

---

### Post by _shake on 2011-08-10
I'm also having this problem, running 11.04 on a laptop. This has just started to be a problem in the last few days, the volume is 100%, but the volume control looks like this:

[[IMG]http://img855.imageshack.us/img855/584/screenshot1ol.png[/IMG]](http://imageshack.us/photo/my-images/855/screenshot1ol.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

The keyboard shortcuts have stopped working as well...

---

### Post by damianb on 2011-08-11
Today, my volume controls (via sound indicator menu and function keys) stopped having any effect.  Sound seems to be at 100% and I cannot change volume or mute.

I also noticed that my brightness controls (functions) do not have any effect.

Has something changed in the latest updates to 11.04?

Thanks,
Damian.

---

### Post by Frogs Hair on 2011-08-11
I'm not sure what's happening , but open the software center and look at history and that will display the most recent updates .

---

### Post by _shake on 2011-08-11
TBH i've just moved to ubuntu about 6 weeks ago, so i've been installing and uninstalling software every other day, trying to get a feel for it, i'm not sure what i should be looking for...

---

### Post by damianb on 2011-08-11
Weird.

I just checked my sound preferences and output was set to HDMI, rather than internal analog sound card.

After setting it back, sound controls work.

Not sure what is going on.

No change to brightness controls however...

---

### Post by damianb on 2011-08-11
Double weird.
Just added brightness control option to the Device section in my xorg.conf file and all is well.

Something bizarre happened in the past week and mucked up my configuration.  Anyway all is good now.

---

### Post by Szellszi on 2011-08-12
Hey guys!

Had the same problem. It was because pulseaudio could not start. When I tried to run it, by hand (terminal: start-pulseaudio-x11), it said: "Home directory is not ours.". So i checked the permissions, and it seemed something screwed it up, all things owned by user 4294967294.
So I googled it and found a solution here:
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

In short:
set in /etc/default/nfs-common: 
NEED_IDMAPD=yes

(I also set NEED_STATD=yes)

Hope this helps.

---

### Post by aia832003 on 2011-08-23
I am having the same problem and cannot launch sound preferences either. Please help.

---

