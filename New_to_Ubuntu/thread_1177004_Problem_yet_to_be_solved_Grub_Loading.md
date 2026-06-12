---
title: "Problem yet to be solved: Grub Loading"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Reckers on 2009-06-02
No one has yet to solve this problem, and after attempting myself, I'm stumped.

Whenever I shut down my computer cold, it takes three tries to get past "Grub Loading Stage 1.5."  What I mean by that is I shut it down, then later restart it, get to that point, and freeze.  Shut down, restart, freeze.  Shut down, restart, works.

This is beyond annoying.

I just put in a new hard drive, so I know it isn't that because I had this problem before.  I also just created a new Live CD, and reinstalled Ubuntu through that, still no luck.

I skimmed through that new Ubuntu Pocket Guide, which looks great, and on page 17, page 35 on the PDF, it says:

"When installation has finished, you’ll be prompted to install the GRUB boot loader. Select YES and hit Enter. Once this is done, reboot the computer when prompted."

I never receive that prompting.  Could that be the problem?

Thanks to anyone's help.  This could be a challenge for ya.

---

### Post by Nixie Pixel on 2009-06-02
From what you are saying I suggest looking at and testing your hardware first. What kind of hard drive did you install?

---

### Post by lavinog on 2009-06-02
It seems odd that grub would freeze, unless there is a hardware fault.
Since you had this problem before with a different drive, could your cpu be overheating?
Can you give us some specifics about your setup? (cpu, motherboard, harddrive)

The fact that it works after a couple of tries is odd too.

---

### Post by Reckers on 2009-06-02
I installed a Western Digital Scorpio Blue 500 GB Hard Drive, and I would agree right now it seems to be running hot, but this three times is the charm starting pattern occurs when my computer has been turned for for hours as well.

I'm not sure what you want to know about my setup. I can tell you I have a Toshiba Satellite M200, and according to System Properties, I have a Intel Core 2 Duo CPU Processor, 2 GB of RAM, and a 32-bit OS.  Tell me where else to look for any other necessary information and I will do so quickly.

Thanks again.

---

### Post by lavinog on 2009-06-03
When grub hangs, can you do a ctrl-alt-del to reboot?

Also you may want to try and reinstall grub, in case there was an issue with the installation: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Are you dual booting into windows at all?

---

### Post by Reckers on 2009-06-03
ctrl-atl-del to reboot huh?

i'll look into reinstalling grub tomorrow afternoon.

i dual boot into windows about 50% of the time yes.

---

### Post by Reckers on 2009-06-03
I tried to reinstall grub as that link suggested.  Seemed to work successfully, but the problem still persists as before.

---

### Post by LewRockwell on 2009-06-03
is booting and running from the Ubuntu 9.04 live-run CD working properly?

---

### Post by Reckers on 2009-06-03
I think I'm running off of an 8.04 Live CD. I know its Hardy Heron, that is 8.04, right?

And yeah, it starts up just fine whenever I boot from the cd.  And then I run off of the Live CD "without making changes to my computer", and it works fine.  I used that to try reinstalling grub as previously mentioned, to no avial.

---

### Post by lavinog on 2009-06-04
What version of ubuntu did you first install grub with?
also pressing ctrl-alt-delete should reboot your computer when grub is loading. After ubuntu is loaded, its behavior is modified.
Being able to reboot this way should give some more insight to if grub is hanging or if the whole system crashed.

---

