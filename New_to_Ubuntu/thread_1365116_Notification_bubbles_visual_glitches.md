---
title: "Notification bubbles visual glitches"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by Pas_sa on 2009-12-26
Hi guys. On both Ubuntu and Xubuntu, on my laptop, the notification bubbles appear as such:

[[IMG]http://img706.imageshack.us/img706/2764/screenshotso.th.png[/IMG]](http://img706.imageshack.us/i/screenshotso.png/)

They render correctly if compiz is enabled. This also happens when I open the system monitor:

[[IMG]http://img690.imageshack.us/img690/6098/screenshot2yj.th.png[/IMG]](http://img690.imageshack.us/i/screenshot2yj.png/)

The laptop is an IBM Thinkpad R50. Pentium M 1.4GHz, 1.5GB RAM, 32MB Radeon 7500. Any ideas? Thanks.

---

### Post by tom.swartz07 on 2009-12-26
> **Pas_sa said:**
> Hi guys. On both Ubuntu and Xubuntu, on my laptop, the notification bubbles appear as such:

[[IMG]http://img706.imageshack.us/img706/2764/screenshotso.th.png[/IMG]](http://img706.imageshack.us/i/screenshotso.png/)

They render correctly if compiz is enabled. This also happens when I open the system monitor:

[[IMG]http://img690.imageshack.us/img690/6098/screenshot2yj.th.png[/IMG]](http://img690.imageshack.us/i/screenshot2yj.png/)

The laptop is an IBM Thinkpad R50. Pentium M 1.4GHz, 1.5GB RAM, 32MB Radeon 7500. Any ideas? Thanks.

Seems like a compositing problem. Is it imperative that you leave compiz off? 
I know for a fact that the Notification popups use compositing to draw correctly so thats why those wont work, but as far as the system monitor, Im without a clue.

Maybe you could just run it so that you have compositing and no other features (wobbly windows, transparency, etc) so that the windows will draw correctly.

Hope this helps!

---

### Post by Palanthas on 2009-12-26
I had the same issue. Here is what I found to fix it.

Add the *Option "AccelMethod" "EXA"* (either EXA or OFF) to /etc/X11/xorg.conf
> 
Section "Device"
	Identifier	"Configured Video Device"
	Option "AccelMethod" "EXA"

To edit xorg.conf open terminal. (applications/accessories) "cd" to etc/X11/:

> sudo gedit xorg.conf

The only problem I have at the moment is that some of the games I run on linux seems to lock the computer up after making this change. Still looking into that...

---

### Post by Palanthas on 2009-12-26
I need to change one of those commands...

Instead of sudo gedit use gksu gedit.

> gksu gedit xorg.conf

---

### Post by Pas_sa on 2009-12-27
> **Palanthas said:**
> I had the same issue. Here is what I found to fix it.

Add the *Option "AccelMethod" "EXA"* (either EXA or OFF) to /etc/X11/xorg.conf


To edit xorg.conf open terminal. (applications/accessories) "cd" to etc/X11/:



The only problem I have at the moment is that some of the games I run on linux seems to lock the computer up after making this change. Still looking into that...
I tried that but my xorg server failed to boot at startup. So I had to use nano to remove the AccelMethod lines.
> **tom.swartz07 said:**
> Seems like a compositing problem. Is it imperative that you leave compiz off? 
I know for a fact that the Notification popups use compositing to draw correctly so thats why those wont work, but as far as the system monitor, Im without a clue.

Maybe you could just run it so that you have compositing and no other features (wobbly windows, transparency, etc) so that the windows will draw correctly.

Hope this helps!
Enabling compiz makes Xubuntu lag to an unusable state. Ubuntu is fine with compiz enabled.

Thanks for the help so far. Any other ideas?

---

### Post by spiderbatdad on 2009-12-27
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

---

### Post by Pas_sa on 2009-12-27
Thanks for the reply. Though I'm not sure what information you wanted me to glean from that page. The sample xorg.conf there again lands me at a text login screen at boot.

Any other ideas or suggestions? :)

---

### Post by stuart.reinke on 2009-12-27
> **Pas_sa said:**
> Thanks for the reply. Though I'm not sure what information you wanted me to glean from that page. The sample xorg.conf there again lands me at a text login screen at boot.

Any other ideas or suggestions? :)

I had the same problem with my ThinkPad R40e.

I solved it by using synaptic to remove all the Ati video drivers, leaving only the Vesa generic driver. 

I don't use any desktop effects, so I don't know how those are affected by the change, but everything I use the computer for works flawlessly now.

hope this helps.

Stu

---

