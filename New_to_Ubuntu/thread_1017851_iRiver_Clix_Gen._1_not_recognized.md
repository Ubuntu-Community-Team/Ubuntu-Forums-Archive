---
title: "iRiver Clix Gen. 1 not recognized"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by jewblahsky on 2008-12-21
Noob here, just switched from Winders to Ubuntu.

I'm in the process of attempting to transfer files to/from my iRiver Clix 4gb player. It's a Gen. 1, so it only supports MTP. Ideally I'd like to be able to access the player like I could in Winders ie like a flash drive.

However, when I plug the player into Ubuntu, it isn't recognized. I can access it through Rhythmbox, but I really prefer drag-and-drop because it's much quicker and easier for me. Also, I couldn't figure how to edit the track titles, artists' names, etc. through Rhythmbox, and browsing the device like a jumpdrive will fix that, too.

Any suggestions on how to tell Ubuntu to see my player?

---

### Post by jewblahsky on 2008-12-21
forgot to mention:
ubuntu ibex 8.10

---

### Post by jewblahsky on 2008-12-22
help.
i need somebody.
help.
not just anybody.

---

### Post by jewblahsky on 2008-12-22
Well, does anyone have any ideas why Ubuntu fails to recognize the device, while Rhythmbox does?

---

### Post by atngplusultra on 2008-12-22
how again does Ubuntu not see it if Rhythmbox does?

---

### Post by jewblahsky on 2008-12-22
I suppose I should say the device doesn't appear in Places like a jump drive.

I recently ran into the command "mtp-detect," and found that Ubuntu does recognize the player as being connected, but does not display it anywhere.

Although Rhytmbox allows me to manage my audio, I have recordings, video, and pictures on the player that Rhythmbox can't access.

---

### Post by atngplusultra on 2008-12-22
interesting.
maybe, try editing fstab? go to a Terminal and type:
```
sudo gedit /etc/fstab
```
and changing settings in there. 
look around at the lines in that, and by that, you should be able to tell which is your device and which are your harddrives.
adding a # at the beginning of the line for a specific device will make it "ignore" something, or automatically boot (I'm a bit of a noob when it comes to that kind of thing, so I am REALLY not clear on the exact term.)

so, yeah, it's a shot in the dark, but it's totally worth a try if you ask me.

---

### Post by jewblahsky on 2008-12-23
The device doesn't show up in the fstab file, so I can't edit anything there. Maybe I could add a line? Is it dangerous to edit this file without really knowing what you're doing?

The device is only recognized through either the mtp-detect command or Rhythmbox.

---

### Post by jewblahsky on 2008-12-23
Following these instructions I'm able to browse the device like a jump drive:
[http://www.anythingbutipod.com/forum/showthread.php?t=32817](http://www.anythingbutipod.com/forum/showthread.php?t=32817)

Seems to work great.

---

### Post by atngplusultra on 2008-12-23
Good to hear you got it working.
ought to mark this as solved

---

### Post by jewblahsky on 2009-01-01
I would mark it solved, but now I'm having different issues with Ubuntu's interactions with the Clix, so instead of toying around with it, I decided to use Winders to manage the Clix.

---

