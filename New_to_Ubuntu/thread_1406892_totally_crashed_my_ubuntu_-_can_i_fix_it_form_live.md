---
title: "totally crashed my ubuntu - can i fix it form live cd?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by Caramin on 2010-02-14
Hello!

I made a mistake trying to change ubuntu (karmic koala) to studio - the system isn't bootable anymore. I am currently running from CD. I used some thread with an explanation how to install without iso. - but I don't find it anymore. While doing the first changes (in terminal) I decided to download the ubuntu  studio iso and ended the terminal, because it seemed to complicated....it surely was... ( I think some kernel or something was erased from harddisc to be replaced).

Can I repair it from here (live -CD?)

THX!!!

---

### Post by niffcreature on 2010-02-14
that was a bad guide. if it was telling you to the kernel with a realtime one instead of just add one, thats ridiculous. there is an ubuntu wiki page for upgrading to studio from normal ubuntu.
most people never get rid of their normal kernel, and if they install ubuntu studio from scratch they have another installation too.
if you were halfway through actually replacing a kernel then there probably isnt any hope.
but it sounds really unlikely that is really the case. try installing ubuntu studio on a new partition, it may very well have been something simple such as the bootloader

---

### Post by phillw on 2010-02-14
Hi,

When your computer starts, does grub give you any option of a kernel to boot into ?

Regards,

Phill.

---

### Post by Caramin on 2010-02-14
would that make the ubuntu on the first partition work again? btw - I am not sure it was the kernel. it just doesn't boot.

---

### Post by Caramin on 2010-02-14
@[phillw]("http://ubuntuforums.org/member.php?u=824544") unfortunaltely just nothung happens - when I try to boot.

---

### Post by niffcreature on 2010-02-14
well, then you should check your power button, jack and battery lol

what do you mean by that? it stays at the bios screen?

if grub doesnt exist anymore then you can reinstall it easily with any ubuntu cd

---

### Post by Caramin on 2010-02-14
:) 
no no id needs a while and then I get the message that there is no bootable system. powerbutton works fine, the notebook is just one week old (as my experience with ubuntu :) )  - just had to read what grub means..

how could I repair grub - or is there some way checking the system through live-cd terminal?

---

### Post by phillw on 2010-02-14
If you can boot with LiveCD, then you *can* put a kernel on - We've just had a similar issue, so the instructions are pretty freshly written :D

The thread in its entirety is here --> [http://ubuntuforums.org/showthread.php?t=1406761](http://ubuntuforums.org/showthread.php?t=1406761)

The instructions from that thread are that new, they're only on my test area, but you can get them here --> [http://forum.phillw.net/viewtopic.php?f=4&t=35&p=50#p50](http://forum.phillw.net/viewtopic.php?f=4&t=35&p=50#p50)

Regards,

Phill.

---

### Post by Caramin on 2010-02-14
thx a lot befor i start trying this have some more infos

i was searching parallely and i found what i've done - i just did the fist step here - than i was asked something in the  terminal and i quit! i ran a while, but then i tried to restart and it didn't work..

[https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

---

### Post by phillw on 2010-02-14
Hi, well, not knowing how far you got, does make it difficult !!

> sudo aptitude .....  linux-rt

Had put on a new kernel, if you haven't finished the installation, your system is quite probably **very** confused, hence not being able to find an OS to boot.

I'd suggest putting on the kernel as per the instructions in the link I posted. That should take you back to Ubuntu.

From there, you can go get Ubuntu-Studio again - Only this time, let it complete ;)

Regards,

Phill.

---

### Post by Caramin on 2010-02-14
It worked! Shalalalalala! Thank you! Thank you! Without your help i'd really be lost. I wish you the best!!!

---

### Post by phillw on 2010-02-14
> **Caramin said:**
> It worked! Shalalalalala! Thank you! Thank you! Without your help i'd really be lost. I wish you the best!!!


Now I can tell you that you're the first person to use those instructions, we were still actually editing them as you were doing them !!! (nothin major, just issued a sudo -i at the start instead of multiple sudos') - although you may have caught the final version ;)

I'm real glad it helped :p

Regards,

Phill.

---

