---
title: "Locked out of 10.10 - GRUB confusion"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by brasini on 2011-05-20
I posted about this earlier but I think I was on the wrong forum and the wrong thread with it:

I'm dual booting (windows/Ubuntu 10.10) but have locked myself out of Ubuntu. The laptop battery died and the machine switched off whilst a liveCD of the ubuntu 10.10 Netbook was still on the desktop (was going to use on another machine). I think that caused a boot problem. Since then every time I choose ubuntu from the GRUB menu it takes me to BusyBox. I followed the advice of no. 5 on thread [http://ubuntuforums.org/showthread.php?t=681130](http://ubuntuforums.org/showthread.php?t=681130) and can get a list of 'possible files' (via c [enter], root hd0, 2 [enter], kernel / [tab]). That gives a list of possible files including: initrd.img vmlinuz cdrom / .local/initrd.img.old and vmlinuz.old. I'm guessing that the first two are what I left on the desktop when the laptop shut down and that the last two are what I need to get back into the main ubuntu OS on the partition. 

Is there a way to delete the liveCD from the ubuntu desktop? Or any other way to get back into the installed Ubuntu OS?

---

### Post by dniMretsaM on 2011-05-20
You could try booting the Live CD again and reinstalling GRUB.

---

### Post by brasini on 2011-05-20
Great. Please could you say a bit about how to reinstall grub? Thanks

---

### Post by _0R10N on 2011-05-20
You can take a look a this page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 
Don't worry about it being a guide for repairing grub after installing windows, it should do the trick for you as well.

Kind regards!

---

### Post by dniMretsaM on 2011-05-20
Try the instructions here [here]("http://www.rocko.me/?p=141"). You will probably need to remove your current GRUB2 installation first, so run ```
sudo apt-get purge grub grub-pc grub-common
```I believe that should do it. Good luck. Be sure the CD that you use is the same version as the installed OS.

You could also read this, but it's fairly complicated as it contains a lot of information.

---

### Post by brasini on 2011-05-20
Thanks people

---

### Post by dniMretsaM on 2011-05-20
Did it work? If so, mark as solved!

---

### Post by brasini on 2011-05-20
I'm still on the making a live cd of the desktop version bit. :( These things take a bit of a while for me. I'll definitely post back results.




I have to wait it out on this one. Have not been able to make a live CD as I can't verify the integrity of the couple of CDs I've tried to make - there's a spot-on guide on how to prepare them here [http://members.iinet.net.au/~herman546/p17.html#Checking_the_.iso](http://members.iinet.net.au/~herman546/p17.html#Checking_the_.iso) as recommended in another thread. It says that a file that somehow got corrupted during download can cause problems later. So I've ordered a bunch instead. Which means my friends will get some too.

---

