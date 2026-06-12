---
title: "Exchanging Hard Drives"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by daniell59 on 2011-08-25
Will this work?
Can I remove the HD from a laptop, put it in a desktop, install Ubuntu, then replace the HD in the laptop, and have it successfully run?

Thanks

---

### Post by VOT Productions on 2011-08-25
No. You get different drivers. How about a USB stick instead?

---

### Post by androssofer on 2011-08-25
> **daniell59 said:**
> Will this work?
Can I remove the HD from a laptop, put it in a desktop, install Ubuntu, then replace the HD in the laptop, and have it successfully run?

Thanks

do u mean move ur HD from your laptop, put it in ur desktop, install ubuntu on it, then move it back to the laptop?

or put it in ur desktop, then install ubuntu and run ubuntu on the desktop and get a whole new HD for ur laptop?

---

### Post by jerrrys on 2011-08-25
are the plugs the same?  i didn't think they were.

i have successful swap out hdd's between desktops.  ubuntu will recognize new  equipment.  if your lappy requires special drivers, you will need to install them.

---

### Post by daniell59 on 2011-08-25
[QUOTE=androssofer;11185713]do u mean move ur HD from your laptop, put it in ur desktop, install ubuntu on it, then move it back to the laptop?\

Exactly

My laptop USB for some reason no longer functions.

---

### Post by androssofer on 2011-08-25
> **daniell59 said:**
> [QUOTE=androssofer;11185713]do u mean move ur HD from your laptop, put it in ur desktop, install ubuntu on it, then move it back to the laptop?\

Exactly

My laptop USB for some reason no longer functions.

never done it myself, but i'm almost certain you can. just make sure grub etc is all installed on the hard drive when you installing ubuntu. (which if you only have 1 hd will happen anyway).

then u might need to make sure its a boot device in your laptop bios.. but i'd say as long as u dnt turn on the laptop during all tht it will b set that way anyway. then run the updates on it when the laptop boots it, tht shud make sure all ur drivers are fine...

---

### Post by seawolf167 on 2011-08-25
Sure - if you need "special" drivers you'll need to install those after you swap back (i.e. anything from "Additional Drivers), otherwise it should be pretty straight-forward and easy.

---

### Post by Paqman on 2011-08-25
> **daniell59 said:**
> Will this work?
Can I remove the HD from a laptop, put it in a desktop, install Ubuntu, then replace the HD in the laptop, and have it successfully run?


Yep, lots of people do this. Should be fine for any hardware that works ok with the standard drivers in the kernel. Obviously anything else that needs additional drivers (wifi, GPU, etc) then you'd need to install that on the laptop once you put the drive in.

---

### Post by Paqman on 2011-08-25
> **jerrrys said:**
> are the plugs the same?  i didn't think they were.


For SATA they are, for IDE they're not IIRC.

---

### Post by daniell59 on 2011-08-25
[QUOTE=jerrrys;11185722]are the plugs the same?  i didn't think they were.

That is a good question. They look the same to me.

---

### Post by seawolf167 on 2011-08-25
> **daniell59 said:**
> [QUOTE=jerrrys;11185722]are the plugs the same?  i didn't think they were.

That is a good question. They look the same to me.[/QUOTE]

If the drive/laptop was purchased in the last couple of years it will  almost certainty be SATA, in which case the connections will be  identical.

---

### Post by daniell59 on 2011-08-26
I removed the hard drives from my desktop. I installed the laptop HD. I then installed Ubuntu 11.04 from a flash drive. I then reinstalled the laptop HD. It seems to be working flawlessly.

---

### Post by androssofer on 2011-08-26
> **daniell59 said:**
> I removed the hard drives from my desktop. I installed the laptop HD. I then installed Ubuntu 11.04 from a flash drive. I then reinstalled the laptop HD. It seems to be working flawlessly.

sweet! scratch 1up for ubuntu! :-)

---

### Post by seawolf167 on 2011-08-26
> **daniell59 said:**
> I removed the hard drives from my desktop. I installed the laptop HD. I then installed Ubuntu 11.04 from a flash drive. I then reinstalled the laptop HD. It seems to be working flawlessly.

Now just install any machine-specific drivers from "Additional Drivers", make a backup image in case something really bad happens ([Clonezilla]("http://www.clonezilla.org")) and you are set! (Oh, and mark this thread as solved :P)

---

### Post by jerrrys on 2011-08-26
here in the forum its normally the broke lappies we hear about.  i was just wondering what brand of laptop this is, that ubuntu works out of the box.  im betting 2 beans its an HP product...

---

