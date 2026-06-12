---
title: "Ubuntu 10.04 not booting after upgrade"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by pradeepbp on 2010-04-25
I was having Ubuntu Karmic installed on my laptop with Vista as the alternate boot. Yesterday, I downloaded the alternate CD for Version 10.04 for performing an upgrade. I mounted the iso image, which was in my home folder, to /media/cdrom0 and ran the upgrade command from console. The upgrade went fine till the computer was restarted. After restart, when I chose the newly installed Ubuntu from grub menu, blank screen with blinking cursor was displayed and it refused to boot. After a few unsuccessful attempts, I decided to  reinstall Karmic again. So, when I pop in the live CD and boot the computer I get a I/O error message.
I am sure that there is no problem with either the live CD or the CD drive as the live CD works fine with other computers and the CD drive works fine in Vista.

Now, are both problems interrelated ?
What is the way forward?

---

### Post by garyedwardjohnston on 2010-04-25
not an expert on this but...

i would use the live cd to diagnose the problem and try reformatting the ubuntu partition then try installing again

---

### Post by pradeepbp on 2010-04-25
> **garyedwardjohnston said:**
> not an expert on this but...

i would use the live cd to diagnose the problem and try reformatting the ubuntu partition then try installing again

That's right, but as I mentioned in the post I am unable to boot from the live CD also.

---

### Post by bville09 on 2010-04-26
What do you mean it refused to boot? I had a similar problem with upgrading from Karmic to Beta 1, where I had a blank screen with the blinking cursor, before the screen went completely black. Ubuntu was boot up fine, but the problem was that it didn't detect my monitor. This was fixed with the release candidate though (which was a bit buggy, but installing nvidia drivers fixed this).

If you downloaded it yesterday, then it should be the RC, but I'm guessing you have a different kind of problem.

What is the I/O message from the Karmic CD?

---

### Post by pradeepbp on 2010-04-26
> **bville09 said:**
> What do you mean it refused to boot? I had a similar problem with upgrading from Karmic to Beta 1, where I had a blank screen with the blinking cursor, before the screen went completely black. Ubuntu was boot up fine, but the problem was that it didn't detect my monitor. This was fixed with the release candidate though (which was a bit buggy, but installing nvidia drivers fixed this).

If you downloaded it yesterday, then it should be the RC, but I'm guessing you have a different kind of problem.

What is the I/O message from the Karmic CD?


I get a message "Error Reading Boot CD" and there is a button for Reboot

---

### Post by klemes on 2010-04-26
I would definately try to remaster the ISO-image burning it at a lower speed in a CD (or DVD - for some reason I get better results if I burn an CD-ISO into a blank DVD)and using md5sum after downloading it.I don't think there are too many other options for this I am afraid.

---

### Post by cuberts on 2010-04-26
> **pradeepbp said:**
> I was having Ubuntu Karmic installed on my laptop with Vista as the alternate boot. Yesterday, I downloaded the alternate CD for Version 10.04 for performing an upgrade. I mounted the iso image, which was in my home folder, to /media/cdrom0 and ran the upgrade command from console. The upgrade went fine till the computer was restarted. After restart, when I chose the newly installed Ubuntu from grub menu, blank screen with blinking cursor was displayed and it refused to boot. After a few unsuccessful attempts, I decided to  reinstall Karmic again. So, when I pop in the live CD and boot the computer I get a I/O error message.
I am sure that there is no problem with either the live CD or the CD drive as the live CD works fine with other computers and the CD drive works fine in Vista.

Now, are both problems interrelated ?
What is the way forward?I am not an expert at the newest version, but I think that it is still the beta version, it may be having more issues. I suggest that you wait until the launch of 10.04

---

