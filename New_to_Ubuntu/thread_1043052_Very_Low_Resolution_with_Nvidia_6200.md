---
title: "Very Low Resolution with Nvidia 6200"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by a.v.l on 2009-01-18
On rebooting my PC the resolution has dropped down to 640x480 with a refresh rate of 73 Hz. There are no other options available to change this setting. My graphics card is a Nvidia GeForce 6200 and has been working well until this. Can someone help please

---

### Post by HavocXphere on 2009-01-18
Probably a driver issue. Check whether the gfx drivers is still activated.

If you're really fed up with it you can go for a band-aid fix: [http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401](http://kubuntuforums.net/forums/index.php?topic=3100136.msg161401#msg161401)
Worked for me (60hz hurts teh eyes:() but Strictly @ own risk of course since it can cause physical damage to screens.;)

---

### Post by alienexplorers on 2009-01-18
Did you try uninstalling and the reinstalling your video driver.  Have you done any recent kernel updates, sice that may have busted things.

---

### Post by sadaruwan12 on 2009-01-18
> **a.v.l said:**
> On rebooting my PC the resolution has dropped down to 640x480 with a refresh rate of 73 Hz. There are no other options available to change this setting. My graphics card is a Nvidia GeForce 6200 and has been working well until this. Can someone help please

I think it's your drivers some thing have corrupted your drivers it's better to reinstall your drivers.

---

### Post by a.v.l on 2009-01-18
> **sadaruwan12 said:**
> I think it's your drivers some thing have corrupted your drivers it's better to reinstall your drivers.

I've had problems with desktop effects so disabled them and since rebooting, I have experienced this problem. How do I reinstall the Nvidia drivers and which ones?

---

### Post by RomeReactor on 2009-01-18
Hi. Before you try reinstalling the drivers, you might want to reboot, go into grub and enter recovery mode; there, select **xfix** and see if you get your resolution back.

If the desktop effects problem you mention is the one where the [title bars glitch]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508"), you can solve it by installing the **nvidia-glx-180** driver. Look for it in Synaptic (if you want the driver to appear in 'System->Administration->Hardware Drivers' so you can manage it there, install **nvidia-180-modaliases**).

---

### Post by a.v.l on 2009-01-18
> **RomeReactor said:**
> Hi. Before you try reinstalling the drivers, you might want to reboot, go into grub and enter recovery mode; there, select **xfix** and see if you get your resolution back.

If the desktop effects problem you mention is the one where the [title bars glitch]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508"), you can solve it by installing the **nvidia-glx-180** driver. Look for it in Synaptic (if you want the driver to appear in 'System->Administration->Hardware Drivers' so you can manage it there, install **nvidia-180-modaliases**).

You will not believe this but this is precisely what I did fifteen  minutes ago and to my relief it fixed the problem. I was just going to let everyone know when I saw your post. Thanks very much had I not already tried this, your post would definately have been the fix I needed.

---

### Post by RomeReactor on 2009-01-18
Glad you got it working! :popcorn:

By the way, if you want to mark the thread as "Solved", go to **Thread Tools**  near the top of the page.

---

### Post by a.v.l on 2009-01-18
> **RomeReactor said:**
> Glad you got it working! :popcorn:

By the way, if you want to mark the thread as "Solved", go to **Thread Tools**  near the top of the page.

I was unable to find solved under @Thread Tools@ I'm afraid. The only options which appear there were.

Show printable version
Email this page
Subscribe to the thread
Add a poll to the thread

Have I been looking in the wrong place perhaps?

---

### Post by RomeReactor on 2009-01-18
> **a.v.l said:**
> I was unable to find solved under @Thread Tools@ I'm afraid. The only options which appear there were.

Show printable version
Email this page
Subscribe to the thread
Add a poll to the thread

Have I been looking in the wrong place perhaps?

I think [UbuntuGeek]("http://ubuntuforums.org/member.php?u=1") disabled some forum features after the servers were hammered a few days ago.

---

### Post by a.v.l on 2009-01-18
> **RomeReactor said:**
> I think [UbuntuGeek]("http://ubuntuforums.org/member.php?u=1") disabled some forum features after the servers were hammered a few days ago.

Thanks for that. Now I only have to work out why I'm unable to play or mount any CD or DVD but that may need to go in another thread I suspect.

---

