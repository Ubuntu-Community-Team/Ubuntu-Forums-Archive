---
title: "todays update has broken my system"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Big Gaz on 2010-07-24
I powered up my desktop today 10.04 LTS 32bit and there was a series of updates the update manager said, so I updated.

This is the second time since 10.04 was installed that I have done an update....

After uploading it asked me to restart my machine and I did so.

And bang I was hit by two problems

One the main problem:-

Low Graphics mode
Nvidia kernal module failed to load

Two the secondly problem:-

I can't click the ok button as the box is no longer recognising my mouse or keyboard (through a KVM)....

So I'm now going to have to tare down my KVM to release the keyboard and mouse and connect them directly and then have a look at the problem.

To say I'm disappointed is an understatement.

Why doesn't Ubuntu 10.04 just work.... why does every other update break something...

I don' have the time to keep rebuilding my KVM or fixing update problems... life is too short

This is about the fourth time I have come to Linux from windows and always the same old problems. video card and other hardware incompatibility or similar issues.

I don't want to be negative, but I thought this time 10.04 was going to be a keeper and I have even bought a new laptop to carry Ubuntu around with me.

Should I not do any upgrades other than security ones?
Should I not be using a KVM switch on my home desktop?
Do I have a hardware compatibility problem?
Should I be putting my home directory on a separate disk or partition?

I will post back once I have the keyboard and mouse ported over and I have got into the system deeper.

What the hell an non technical user would do in this situation is beyond me. He has a system and it breaks within a couple of weeks!:(

---

### Post by howefield on 2010-07-24
Probably an updated kernel that has triggered the breakage. 2.6.32-24 has just been released to the repository.

Boot into the previous kernel.

---

### Post by Big Gaz on 2010-07-24
Thanks for that quick replay

Once I had the keyboard and mouse sorted I was able to click on a few options (restart X) and rebuild video configuration, and reboot my machine.

I did have to turn recompisting on as docky was complaining and the screen had a large black section 1/3 up, it also appears to have broken wine.

Question

So I not update my kernal everytime, what is the norm. Just security patches?

Also I don't see the menu tree of old showing all the kernel versions on boot up. All I get is Ubuntu splash screen.

Is there a way to get this working

---

### Post by howefield on 2010-07-24
> **Big Gaz said:**
> So I not update my kernal everytime, what is the norm. Just security patches?

Not sure what you mean here, I'd always take the updates.

> Also I don't see the menu tree of old showing all the kernel versions on boot up. All I get is Ubuntu splash screen.

Pressing the shift key quickly after the BIOS boots should bring up the grub menu, you have to be quick, there isn't a large window between the BIOS booting and the Ubuntu splash screen.

---

