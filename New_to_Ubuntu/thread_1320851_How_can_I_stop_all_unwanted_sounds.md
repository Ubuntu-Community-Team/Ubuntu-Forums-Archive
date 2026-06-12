---
title: "How can I stop all unwanted sounds?"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Mariane on 2009-11-09
How can I stop all unwanted sounds, please? By unwanted I mean all sounds which are not the result of my telling the computer to play music or a video. 

I would need a keyboard command because I do not have the graphical user interface yet, following the upgrade to 9.10. But the first thing is to make this machine keep quiet, it is stressful enough to see the upgrade messed it up badly without it screaming at me. 

Example: when I type "sudo reboot now" it beeps very very LOUDLY. 

Please help. 

Mariane

---

### Post by ALMeehan on 2009-11-09
The beep you hear on reboot is the built-in PC speaker, I'm thinking.
Try modprobe -r pcspkr to get rid of that, and maybe add it to the modprobe blacklist if you never want to hear it again :)

/etc/modprobe.d/blacklist

Aaron

---

### Post by Mariane on 2009-11-09
Thank you ALMeehan, but wouldn't that ban all sound from the pc speaker? 

Mariane

---

### Post by lallalla on 2009-11-09
I have the same problem and 'solved' it by muting the whole system: pulse audio volum control - internal audio analog stereo - mute

but I am obviously not happy with this solution and hope someone will come up with a better idea....

---

### Post by lallalla on 2009-11-09
I tried the 
/etc/modprobe.d/blacklist
and it did not work for some reason...

---

### Post by ALMeehan on 2009-11-09
It most certainly will cause the PC speaker to be silent, but not the speakers connected to your sound card.  I think "set bell-style none" from your bash prompt may also accomplish the same thing without removing the module from the kernel.

Aaron

---

### Post by sandyd on 2009-11-09
> **lallalla said:**
> I tried the 
/etc/modprobe.d/blacklist
and it did not work for some reason...
try using alsamixer to set the PC beep down.

---

### Post by Mariane on 2009-11-09
"set bell-style none" worked ):P 

That's one of these commands I'll write down on the laptop until I memorise it, like "synclient TouchpadOff=1". (WARNING: This one is when you use a mouse with a laptop and the touchpad keeps sending the cursor away from where you are trying to type, if you use it with no mouse plugged in you'll get stuck until you reboot). 

Thank you

Mariane

---

