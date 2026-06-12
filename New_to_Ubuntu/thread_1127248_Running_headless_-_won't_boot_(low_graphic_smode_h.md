---
title: "Running headless - won't boot (low graphic smode hangs)"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by doogs on 2009-04-16
Hi,
Ok here's the problem and it's been driving me nuts for about 4 hours last night. I've searched google and these forums but can't seem to find a solution as yet. Hope someone can help!

I have Ubuntu 8.10 desktop installed, I've set up a static ip and can connect to the machine from another machine on my lan via ssh or vnc. This works fine when a screen is attached to the Ubuntu machine.

The problem is that if I shutdown the ubuntu machine, disconnect and reboot - the machine stops at "ubuntu is running in low graphics mode" (I found this out by reconnecting a monitor). The boot process won't proceed until I click "ok".

The question - how do I get Ubuntu to boot with no monitor connected?

Any help would be greatly appreciated.

Cheers,
Doogs.

---

### Post by lloyd_b on 2009-04-16
It sounds like your video card is trying to probe the monitor, and since it can't find it, it's assuming the lowest possible video capability.

You can try attaching a "VGA Terminator" to the VGA output and see if it helps - you can find one by Googling the term.

Lloyd B.

P.S. If you intend to run the machine headless, you can also try uninstalling Xorg, but then you won't be able to connect a monitor in the future and have a GUI...

---

### Post by doogs on 2009-04-16
Cheers.
Is there any way to stop Ubuntu from looking for a monitor and just boot anyway?

---

### Post by lloyd_b on 2009-04-16
> **doogs said:**
> Cheers.
Is there any way to stop Ubuntu from looking for a monitor and just boot anyway?

I believe that's part of the GUI subsystem. 

If you plan on running the machine always headless, then I'd recommend the server install (which doesn't install any GUI by default).

Lloyd B.

---

### Post by doogs on 2009-04-16
I started of with a server install but, installed the ubuntu desktop on top to help me get the hang of working with linux.

---

### Post by jaygo on 2009-04-17
once you've installed ubuntu desktop, it's going to automatically boot into gnome until you tell it not to. Maybe look into changing the default session from gnome to headless or whatever it may be called.

---

### Post by speaktek on 2009-04-23
Try this:

[http://ubuntuforums.org/showthread.php?p=7126984#post7126984](http://ubuntuforums.org/showthread.php?p=7126984#post7126984)

---

### Post by doogs on 2009-04-24
> **speaktek said:**
> Try this:

[http://ubuntuforums.org/showthread.php?p=7126984#post7126984](http://ubuntuforums.org/showthread.php?p=7126984#post7126984)

Cheers,
I had heard about a vga terminator elsewhere. I've got the bits from maplin and will construct one at the weekend.

Thanks,
Doogs.

---

