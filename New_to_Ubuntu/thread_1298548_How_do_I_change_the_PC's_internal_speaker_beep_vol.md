---
title: "How do I change the PC's internal speaker beep volume or pitch?"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by OrangeVixen on 2009-10-22
Hi, I'm trying to change the volume and pitch of the PC's internal speaker when it beeps.

I have already tried using xset in the .xinitrc script but gnome overrides it.

I have already tried System->Preferences->Sound and turning off the Alert Sound, it works but it turns it off completely, what I wanted to do was make it softer and not so loud. I don't know where to set this.

I have already searched through the archives but I couldn't find any solutions that worked.

---

### Post by SirSlipALot on 2009-10-22
I have the same problem.

all I could do was:

Turning Off The System (hardware) Beep : System --> Preferences --> Sound --> Sounds tab --> Visual Alert ---> right click and choose "Flash screen"
                     System --> Preferences --> Sound --> Sounds tab --> disable "Play alert sound"

---

### Post by OrangeVixen on 2009-10-22
Yeah the flashing of the screen or window is even more annoying than the beep. :/

I noticed that running xset to set the beep in the gnome terminal does affect only that terminal. So I think that the only way to set the internal speaker beep volume is to set it in gnome somewhere... but where?!

---

### Post by undecim on 2009-10-23
The internal speaker is managed by the pcspkr module. Perhaps there is an option that could be passed to that module when it's loaded that will change the volume/pitch? I could be wrong, but I can't find a way to get a list of module options to verify this idea.

EDIT: found out about modinfo -p. pcsplk doesn't have any options, so scrap my idea

---

### Post by OrangeVixen on 2009-10-23
Bump, thanks any ways :)  If anyone else has suggestions... (?)

---

### Post by coolbrook on 2009-10-23
If you're comfortable with it, then you can open your case and muffle the speaker or get someone to do it for you.

---

