---
title: "I've been having problems with Shutting Down and Restarting..."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by brucewagner on 2008-12-30
I've been having problems with Shutting Down and Restarting...

When I shut down, or restart, the computer (an HP tower dual core AMD64 running Ibex 32bit) does not completely power off.  Then, it won't start up again.  I've had to pull the AC power cord completely from the back of it... several times... before I could get it to boot again.

Today, it did that same thing...  But now I can't get it to boot no matter what I do.

It powers on.  The fan is on high,  The CD rom accesses.  But there's no video signal, and the fan stays on high.  Doesn't boot.

Could this be hardware?   Or a shut-down software issue?

How can I fix it?

---

### Post by pdtpatrick on 2008-12-30
when you turn it on .. do you see the initial splash screen? or can you get to bios? where does it stop loading .. also you mentioned CD. Is it booting off a CD or does it just try to see if a CD rom is in the drive (this happens sometimes when u have it the CD as your first boot device).

---

### Post by gjoellee on 2008-12-30
This CAN be your hardware. IT seams like you have a not to old computer... Now if you buy a computer with the newest hardware, it might take up to 9 months before support for the hardware gets into the kernel. And without a working kernel, you got no working Linux.

However does shutting down with this command work?
```
sudo shutdown -h now
```

I guess we would need some more information:
-Your hardware

-You current kernel, use the command ```
uname -r
``` and give the output

-Have your tried Ubuntu 64-bit? That might solve your problem

-Do you get any errors? (and I mean...ANY error)

---

### Post by pdtpatrick on 2008-12-30
gjoelle -- i dont think running all those commands would work considering he said the computer no longer boots :)

---

### Post by brucewagner on 2008-12-30
I will try those commands if/when I am able to get it to boot.

In the meantime...

To answer the other questions:

No.  I don't get any splash screen.  Not even the blue HP screen (no access to the BIOS).  No video signal at all.

It accesses the CD ROM drive.... checking for a disk.  But the drive is empty.

I even tried inserting an Ubuntu Live CD once... to see if it would boot from the CD.   Nope.  Still won't boot.

Because it does not even display the HP blue (BIOS-access) screen...  it makes me think it's hardware.   Or maybe the video card....?

Called Micro Center. They want $70 to diagnose the problem.  Plus parts & labor on top of that.

---

### Post by albinootje on 2008-12-30
> **brucewagner said:**
>  It powers on.  The fan is on high,  The CD rom accesses.  But there's no video signal, and the fan stays on high.  Doesn't boot.


Did you check whether your monitor still works with another machine ?
Does the motherboard have those nice leds inside which can show what the problem is ?
Is there any beep codes or not at all ?
Do you have another videocard lying around which you can try ?
Is the cable of the hard disk attached properly ?
What about the RAM modules ? are they attached properly ?
(Be careful, RAM modules are very sensitive about "static electricity"!)

You can also take out the CMOS battery for a few minutes and then put it back, and/or look up in the manual of your motherboard how to reset the CMOS. See what that does.

---

