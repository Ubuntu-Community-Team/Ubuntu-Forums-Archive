---
title: "sound indicator applet gone"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by libihero on 2010-08-18
when trying to fix my skype audio, i came across a thread that suggested removing "pulseaudio" and adding alsamixer, and that fixed my skype.  however, what this ended up doing was completely removing the sound indicator applet.  sound still works fine, but i have to adjust it with alsa mixer.  when i go to system>prefrences>sound, a box comes up that says "waiting for sound system to respond"

anyway i can get the sound indicator applet back without reinstalling pulseaudio?

---

### Post by jmfal on 2010-08-18
To restore sound applet: system>preferences>sound right click, select add to panel

Or you can install Gnome alsa mixer in synaptics in one of the Gnome sections
  
I have both with no problema

---

### Post by libihero on 2010-08-18
i already have gnome alsa mixer downloaded, and the indicator isnt there
when i right click on add it to panel, it just makes a launcher. and even that it just goes "waiting for sound system to respond".
i want the indicator applet for easily changing the sound volume, not just opening a window that can change it

---

### Post by kernlbob on 2010-10-03
I had the same problem.

I got the sound indicator back by instantiating a new indicator applet.

1) Right-click in blank area of panel.  "Add to Panel...".  Indicator Applet.

2) Watch all indicators jump from old indicator applet to new one.

3) Right-click old indicator applet.  "Remove from Panel".

4) Slide the new indicator applet to the position where it belongs.

Hope this helps.

---

### Post by zenthor on 2010-11-10
> **kernlbob said:**
> I had the same problem.

I got the sound indicator back by instantiating a new indicator applet.

1) Right-click in blank area of panel.  "Add to Panel...".  Indicator Applet.

2) Watch all indicators jump from old indicator applet to new one.

3) Right-click old indicator applet.  "Remove from Panel".

4) Slide the new indicator applet to the position where it belongs.

Hope this helps.

it helped me, i deleated the one where it shows which keyboard config you have (cause i have my keyboard on english but configured as spanish), and i wanted to take it out, but only the keyboard part, so when i clicked remove from panel, the whole thing went off, the batery indicator, the sound, and the icon that integrates the empathy chat+evolution mail++ so, I went nuts, even tyied to reinstall the indicator applet, and nothing, to the point i decided to reinstall the whole ubuntu ;S and happend me again, so this 4 steps solutions you posted helped me TONS mate, thanks a lot :)

---

