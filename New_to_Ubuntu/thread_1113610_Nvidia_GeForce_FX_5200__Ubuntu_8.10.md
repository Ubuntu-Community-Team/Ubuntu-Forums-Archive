---
title: "Nvidia GeForce FX 5200 / Ubuntu 8.10"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by Shibblet on 2009-04-01
I installed this card in a old Dell Dimension 2400, and I can finally get better resolution than 640x480.  The problem now is that I can't enable the desktop effects.  I am using the new 173.14.18 drivers also.

Everytime I try to switch over, it tells me that Desktop Effects cannot be enabled, and goes back to standard mode.

Any help would be greatly appreciated.

---

### Post by abyssius on 2009-04-01
> **Shibblet said:**
> I installed this card in a old Dell Dimension 2400, and I can finally get better resolution than 640x480.  The problem now is that I can't enable the desktop effects.  I am using the new 173.14.18 drivers also.

Everytime I try to switch over, it tells me that Desktop Effects cannot be enabled, and goes back to standard mode.

Any help would be greatly appreciated.

How do you know you're actually using the 173.14.18 driver? It sounds like you have the standard nv driver enabled. If you had a low resolution problem and fixed it by using the Recovery mode's [Try to fix X-Server], this would disable the NVIDIA driver and re-assert the std. nv driver. You need to check this first.

---

### Post by Shibblet on 2009-04-02
I went through removing whatever driver was in there by default, and the loaded the Nvidia 173.14.18 manually from the .run file.

Now I can get the 1280x1024 res, but can't enable Desktop effects.

---

### Post by marceld7 on 2009-04-07
Hi,

I've had the same problem with the desktop effects...but somehow I fixed it. I'm relatively new to Ubunt(linux period for that matter) so i dont know why this worked.

I went and got the compiz fusion icon from the add\remove. make sure you set it to show all available applications in case it doesnt show up.. after thats installed go ahead and run it in the system tools menu. right click the icon in the top panel or where ever your notifications are, and click the reload window button. that should enable desktop effects for you..as long as you have the compiz settings you should be able to fine tune your effects.

hope this helps!! it some how worked for me.;)

marcel

---

### Post by Shibblet on 2009-04-10
I don't know.  Maybe I am asking for more than what this computer is capable of.  1280x1024 (Got that, but only with the GeForece Card), and then Desktop Effects to be enabled.

I think it has more to do with xorg.conf but I don't know the first thing about editing it for this card.  I've been fighting this computer for a week now, to no avail.

I'd love to get this fixed, any more ideas?

---

### Post by marceld7 on 2009-04-15
Thats weird because i have a Geforce FX 5200 as well. When i first encountered the problem i looked around and just about every one with this card couldnt enable desktop effects or had resolution problems. i really cant even begin to know why mine is working. everytime i restart the computer i have to re enable compiz but it still works none the less.

i would try re installation, just to start from a clean slate, and try again from there. somethings bound to give...but if that doesnt work then downgrade to Ubuntu 8.04. im pretty sure it works relatively well in hardy. dont know what hardy has that intrepid doesnt. i hope jaunty fixes this bug though...:lolflag:

Marcel

---

### Post by mick316 on 2009-04-16
I believe it is something to do with the xorg.conf settings. 

You have to make sure that your monitor refresh rates (Horizontal and Vertical)are correct.

I got mine to work by running the Gutsy Live Cd, then opening a terminal and typing command "sudo dpkg-reconfigure xserever.xorg" (without the commas) and manually entering the Monitor Settings and the resolutions that the monitor was capable of. 
Once done, Launch gksu nautilus from terminal and copy the Xorg file that you have just edited (from the /etc/x11 folder over to the one on your system. Reboot, remove live cd and you should be working.

I did this with my FX5200 Card and can get 1400 x 900 Resolution on Intrepid along with the visual effects as well.

I am sure there is an easier way, but this is what worked for me.

---

### Post by divague on 2009-04-16
Open a terminal and run:

```
$compiz
```

If it doesn't enable compiz it will show you the reason why it's not being enabled

---

### Post by Shibblet on 2009-05-02
Thanks!  Here is the problem...

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity
```

---

### Post by Shibblet on 2009-05-07
Bump!  Anyone know how to fix this?

---

### Post by Shibblet on 2009-05-10
Figured it out on my own.  Ran Compiz-check and found out the issue.  Pressed yes for ignore and off it went.

---

