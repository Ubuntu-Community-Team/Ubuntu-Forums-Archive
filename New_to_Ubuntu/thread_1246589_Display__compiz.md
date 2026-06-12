---
title: "Display / compiz"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by atngplusultra on 2009-08-21
I feel stupid for having to write this. I'm close to finding my solution, but I just cannot figure it out.

I plugged in a monitor earlier, and eventually it cooperated, but as a result, it turned off my accelerated graphics (i.e., compiz is pretty much crippled)

so, the monitor is, of course, unplugged now, and my compiz is still not doing anything like it was before the whole thing started. (all alt-texts are slow, window-switching is slow, no desktop cube/cube rotation, etc. are gone)

in System->Preferences->Appearance->Visual Effects, the only option the computer decides on is None.

this is a Toshiba Satellite A135 laptop, running a completely up-to-date kernel of Jaunty.

---

### Post by atngplusultra on 2009-08-21
also, when i DO try to up the Visual Effects, it stalls for a second or two, then the entire screen goes white, except for the cursor, and it stays that way for about a minute, then everything becomes visible again.

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by atngplusultra on 2009-08-22
Good grief.

Fixed this.

deselected Indirect Rendering in fusion-icon.

---

### Post by atngplusultra on 2009-08-23
This problem re-appeared when i rebooted the computer, and it seems that just toggling the rendering sets it right. which is managable, but still somewhat weird.

---

### Post by suhanduman on 2009-08-25
Hi atngplusultra;

I have experienced the same problem when i connect a projector.
Then i realised it generates a second xorg.conf and save the last one with the date.
Then i switched back to my original xorg.conf before i connect the projector.
suhan@sdx:/etc/X11$ sudo mv xorg.conf xorg.conf2
suhan@sdx:/etc/X11$ sudo mv xorg.conf.20090820102331 xorg.conf

If you run ls -alrt /etc/X11/ you can find a saved xorg.conf with the date you plugged the second monitor.
I think that there is a problem with the generated xorg.conf, but i can not say what was the difference between those two, because i have deleted the generated one.

May be you can check the difference.
Regards
Suhan

---

