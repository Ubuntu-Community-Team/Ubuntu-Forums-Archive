---
title: "Urgent: Computer freezes off"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by oaridus on 2011-08-10
Hi all, I have Thinkpad T61 and Ubuntu 10.04 installed and fully updated. Nowadays my computer freezes off randomly especially if I put some USB adapter like device. This happens like 6/10 times. In general, if the computer stops responding and no keyboard works, what is the best way to come out of this.. Right now I force reboot with the power button on the keyboard.. Any help will be greatly appreciated..

---

### Post by Arijit_Kundu on 2011-08-10
as far as i know, it may be caused by several reasons. one reason can be the problem is with bios, then you need to update the bios. Another reason can be with the power manager. try ths:

sudo nano /etc/laptop-mode/conf.d/usb-autosuspend.conf

and then change from BATT_SUSPEND_USB=1 to BATT_SUSPEND_USB=0.

from [here]("http://ubuntuforums.org/showthread.php?t=1692753")

---

### Post by MyR on 2011-08-10
You can also try these steps next time:
[Recover from system freeze]("http://linuxdeal.com/how-to-kill-processes-and-recover-from-system-freeze")

They work for me sometimes even if the keyboard seems like it's not responding.

---

### Post by zealibib slaughter on 2011-08-10
If you have to force shutdown the system then the proper way is with a key combination called the magic system keys.  Hold down <alt> <SysRq/print scrn> and press each one of these keys allowing a few seconds break between each.
<r> places keyboard in raw mode
<s> syncs the filesystem
<e> terminates all processes
<i> kills all processes
<u> remounts filesystem read only
<b> reboots the system
 
Here is a cheet sheet to all the magic keys: [http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf](http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf)

---

### Post by oaridus on 2011-08-11
Thanks guys, I will check it out and get back to you all

---

### Post by amjjawad on 2011-08-11
> **Arijit_Kundu said:**
> as far as i know, it may be caused by several reasons. one reason can be the problem is with bios, then you need to update the bios.

What [BIOS ]("http://en.wikipedia.org/wiki/BIOS")has to do with this?

---

### Post by amjjawad on 2011-08-11
> **oaridus said:**
> Hi all, I have Thinkpad T61 and Ubuntu 10.04 installed and fully updated. Nowadays my computer freezes off randomly especially if I put some USB adapter like device. This happens like 6/10 times. In general, if the computer stops responding and no keyboard works, what is the best way to come out of this.. Right now I force reboot with the power button on the keyboard.. Any help will be greatly appreciated..

[http://ubuntuforums.org/showthread.php?t=1820915](http://ubuntuforums.org/showthread.php?t=1820915)

See if your scenario match the above one.

For Ubuntu Search: [www.googlubuntu.com](www.googlubuntu.com)

---

### Post by mikewhatever on 2011-08-11
There is a bug report with similar symptoms.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

It's supposed to be fixed in the recent kernel update.

As for the suggestions above, the keyboard doesn't work when it freezes, and the only thing to do is press and hold the power button.

---

### Post by oaridus on 2011-08-11
> **amjjawad said:**
> [http://ubuntuforums.org/showthread.php?t=1820915](http://ubuntuforums.org/showthread.php?t=1820915)

See if your scenario match the above one.

For Ubuntu Search: [www.googlubuntu.com](www.googlubuntu.com)

I have just updated my OS, but not upgraded or downgraded it.. So I think this is not the case. Thanks anyway for pointing this important thread out...

---

### Post by oaridus on 2011-08-11
> **Arijit_Kundu said:**
> as far as i know, it may be caused by several reasons. one reason can be the problem is with bios, then you need to update the bios. Another reason can be with the power manager. try ths:

sudo nano /etc/laptop-mode/conf.d/usb-autosuspend.conf

and then change from BATT_SUSPEND_USB=1 to BATT_SUSPEND_USB=0.

from [here]("http://ubuntuforums.org/showthread.php?t=1692753")

This conf file does not seem to exist in Ubuntu 10.04.. I also searched in /etc folder but can't find it.. Is it only with the higher version of Ubuntu or do I have to create this file and type the next line with =0

---

### Post by oaridus on 2011-08-11
> **MyR said:**
> You can also try these steps next time:
[Recover from system freeze]("http://linuxdeal.com/how-to-kill-processes-and-recover-from-system-freeze")

They work for me sometimes even if the keyboard seems like it's not responding.

This seems to be very nice method.. I will try it and see.. Thanks a lot...

---

### Post by oaridus on 2011-08-11
> **zealibib slaughter said:**
> If you have to force shutdown the system then the proper way is with a key combination called the magic system keys.  Hold down <alt> <SysRq/print scrn> and press each one of these keys allowing a few seconds break between each.
<r> places keyboard in raw mode
<s> syncs the filesystem
<e> terminates all processes
<i> kills all processes
<u> remounts filesystem read only
<b> reboots the system
 
Here is a cheet sheet to all the magic keys: [http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf](http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf)

The cheatsheet is wonderful... I have two questions.. First, <b> needs to have file system unmounted. Then why should be press <u> before that. Is there a command for unmounting file system..Second, what does the <c> option do.. Does it reboot the system? It looks like it brings out the system if it is hung? The last question.. do I have to set up this facility. What are the first 4 lines..

---

### Post by amjjawad on 2011-08-11
> **mikewhatever said:**
> There is a bug report with similar symptoms.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/811745)

It's supposed to be fixed in the recent kernel update.


In that bug report, problem occur when a user "safely remove" his/her USB. The problem with the OP starts when he/she plugs an USB Drive to his/her machine.
Not sure how similar these two cases are but it's good idea to go for that option and see if it does fix the problem or not.

---

### Post by oaridus on 2011-08-12
> **amjjawad said:**
> In that bug report, problem occur when a user "safely remove" his/her USB. The problem with the OP starts when he/she plugs an USB Drive to his/her machine.
Not sure how similar these two cases are but it's good idea to go for that option and see if it does fix the problem or not.

It seems this bug is the main problem. I have updated my kernel to 33.72 version.. Lets see if it fixes everything. thanks a lot..

---

### Post by amjjawad on 2011-08-12
> **oaridus said:**
> It seems this bug is the main problem. I have updated my kernel to 33.72 version.. Lets see if it fixes everything. thanks a lot..

Ok, please keep us updated :)

Good luck!

---

### Post by zealibib slaughter on 2011-08-13
> **oaridus said:**
> The cheatsheet is wonderful... I have two questions.. First, <b> needs to have file system unmounted. Then why should be press <u> before that. Is there a command for unmounting file system..Second, what does the <c> option do.. Does it reboot the system? It looks like it brings out the system if it is hung? The last question.. do I have to set up this facility. What are the first 4 lines..
 
<u> actually unmounts the file system then attempts to remount it as a read only partition.  This is done so that you can examine logs if you need to, but it needs to be done since it unmounts the FS as a readable/writable state.  The <c> option basically makes a crash dump for debugging.  It can be useful but I've never actually used it.  To activate the magic sysrq keys just login and open a terminal then code:```
[FONT=BitstreamVeraSansMono-Roman][SIZE=3][FONT=BitstreamVeraSansMono-Roman][SIZE=3]
echo 1 > /proc/sys/kernel/sysrq
[/SIZE][/FONT][/SIZE][/FONT]
```

---

### Post by oaridus on 2011-08-14
> **zealibib slaughter said:**
> <u> actually unmounts the file system then attempts to remount it as a read only partition.  This is done so that you can examine logs if you need to, but it needs to be done since it unmounts the FS as a readable/writable state.  The <c> option basically makes a crash dump for debugging.  It can be useful but I've never actually used it.  To activate the magic sysrq keys just login and open a terminal then code:```
[FONT=BitstreamVeraSansMono-Roman][SIZE=3][FONT=BitstreamVeraSansMono-Roman][SIZE=3]
echo 1 > /proc/sys/kernel/sysrq
[/SIZE][/FONT][/SIZE][/FONT]
```

Thanks for clarifying.. Before I saw your reply, in the comments to bug reply, I saw that you have to press the ctrl key too. So it is CTRL + ALT + SYNRQ/PRTSC and then those keys you mention.. I tested it out and it works great.. I will try enabling the magic keys and see also.. Thanks a lot..

---

### Post by Hakunka-Matata on 2011-08-14
> **zealibib slaughter said:**
> If you have to force shutdown the system then the proper way is with a key combination called the magic system keys.  Hold down <alt> <SysRq/print scrn> and press each one of these keys allowing a few seconds break between each.
<r> places keyboard in raw mode
<s> syncs the filesystem
<e> terminates all processes
<i> kills all processes
<u> remounts filesystem read only
<b> reboots the system
 
Here is a cheet sheet to all the magic keys: [http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf](http://www.isotton.com/devel/docs/sysrq-cheatsheet/sysrq-cheatsheet.pdf)

I've always seen the magic key combination given as ALT + Sys Rq <R> <E> <I> <S> <U> <B>
to memorise **BUSIER **
Mind you, I'm not arguing, just that I've not seen it presented your way before.

---

### Post by oaridus on 2011-08-15
> **Hakunka-Matata said:**
> I've always seen the magic key combination given as ALT + Sys Rq <R> <E> <I> <S> <U> <B>
to memorise **BUSIER **
Mind you, I'm not arguing, just that I've not seen it presented your way before.

I guess this seems logical.. You first terminate the processes and then sync and remount the file system in read only mode before reboot.. Since I am a novice, I would like to get some expert's opinion..Anyonee...:confused:

---

### Post by oaridus on 2011-08-15
> **oaridus said:**
> Thanks for clarifying.. Before I saw your reply, in the comments to bug reply, I saw that you have to press the ctrl key too. So it is CTRL + ALT + SYNRQ/PRTSC and then those keys you mention.. I tested it out and it works great.. I will try enabling the magic keys and see also.. Thanks a lot..

I enabled the magic keys, but only the ALT key does not work.. I get a printscreen and save option.. I have to use CTRL + ALT +  PRTSC with the following subkeys to get things done..

---

### Post by oaridus on 2011-08-15
> **amjjawad said:**
> Ok, please keep us updated :)

Good luck!

Guys, after 4 days of trial, I have had NO problems.. The main solution.. fix of the kernel to 3.72 version.. Things are smooth now. Thanks a lot guys.. Learnt a lot from you all..:popcorn:

---

### Post by zealibib slaughter on 2011-08-17
> **Hakunka-Matata said:**
> I've always seen the magic key combination given as ALT + Sys Rq <R> <E> <I> <S> <U> <B>
to memorise **BUSIER **
Mind you, I'm not arguing, just that I've not seen it presented your way before.
 
 
The order which I use comes from the mnemonic "Raising Skinny Elephants Is Utterly Boring".  Its debated which way is better, to sync the file system first or to kill and terminate processes.  Either way as long as you are not force rebooting a filesystem thats mounted with write permissions then you should not have any major problems.

---

