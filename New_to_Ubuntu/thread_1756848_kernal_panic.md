---
title: "kernal panic"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-05-12
My sister was using my laptop with 11.04 and I'm not quite sure what happened but she had a kernal panic. She called me over and I was stumped...

What do I do once we have a kernal panic?

---

### Post by TeoBigusGeekus on 2011-05-12
Select a previous kernel from grub and wait until an update fixes the problem or a new kernel is installed.

---

### Post by skyzthelimit230 on 2011-05-12
As this is a new install, I have no previous kernals atm. Is a kernal panic indicative of a major problem?

---

### Post by TeoBigusGeekus on 2011-05-12
In rare cases kernel panics can occur because of a hardware failure.
Boot with a live cd/usb to see if everything works ok.
If it does, the only thing I can suggest is Lucid or Maverick.

---

### Post by drs305 on 2011-05-12
Boot from the LiveCD, download, run the Boot Info Script (BIS) from the link in my signature line, and post the contents of RESULTS.txt. It will show us the status of the boot files.

Even if it looks ok, we can give you the commands to try a manual boot from the Grub command prompt. (There can be lots of reasons for a kernel panic, but this worked for another user a couple of hours ago.)

---

### Post by TeoBigusGeekus on 2011-05-12
> **drs305 said:**
> Boot from the LiveCD, download, run the Boot Info Script (BIS) from the link in my signature line, and post the contents of RESULTS.txt. It will show us the status of the boot files.

Even if it looks ok, we can give you the commands to try a manual boot from the Grub command prompt. (There can be lots of reasons for a kernel panic, but this worked for another user a couple of hours ago.)

Yes, quite a few kernel panics today; it must be a bad update...

---

### Post by Gr72 on 2011-05-12
Please Help, I'll try your above suggestion but I don't know if it will work
[http://ubuntuforums.org/showthread.php?p=10807713#post10807713](http://ubuntuforums.org/showthread.php?p=10807713#post10807713)

---

### Post by skyzthelimit230 on 2011-05-12
See attached. I just ran the script and there are the results.

---

### Post by jerrrys on 2011-05-12
hay guys:

he hasn't updated.  could he not go to recovery mode and apt-get update himself a new kernel?

---

### Post by drs305 on 2011-05-12
> **TeoBigusGeekus said:**
> Yes, quite a few kernel panics today; it must be a bad update...

I agree. I was surprised that the 'grub boot' fix worked since I suspected it was something else. We'll see if it was unrelated to these newly reported panics.

---

### Post by skyzthelimit230 on 2011-05-12
> **drs305 said:**
> I agree. I was surprised that the 'grub boot' fix worked since I suspected it was something else. We'll see if it was unrelated to these newly reported panics.

So, do I have to update Grub? :|

---

### Post by Gr72 on 2011-05-12
Isn't BIS just showing you what's in your grub.cfg???

---

### Post by drs305 on 2011-05-12
skyzthelimit230,

Things look normal, although we rarely see Ubuntu installed on sda4. I'm assuming you manually set this as your partition.

You can try the following from the Grub 2 menu just to see if it boots. From the menu, press 'c' to get to the grub prompt. Then:
Note you can use TAB completion to help - as you type the vmlinuz and initrd filenames you can press TAB to partially complete the name.
```
set prefix=(hd0,4)/boot/grub
set root=(hd0,4)
insmod (hd0,4)/boot/grub/linux.mod # May report already loaded
linux (hd0,4)/boot/vmlinuz-2.6.38-8-generic root=/dev/sda**4** ro nomodeset
initrd (hd0,4)/boot/initrd.img-2.6.38-8-generic
boot
```

If you get any errors note what they are. If you successfully boot we will have to make some permanent changes, so stay booted and report back to us.

---

### Post by drs305 on 2011-05-12
gr72,

I've moved your post back into your own thread. I know the situation appears the same but it's better to work on each problem individually, at least until the OPs is solved.

I'll post in your thread in a bit if I find anything.

---

### Post by Gr72 on 2011-05-12
Ok, thank you, and sorry if it was a little long, or annoying, or time consuming.

---

### Post by skyzthelimit230 on 2011-05-12
booted successfully. Remained booted.

errors I noted:

test wp failed: assume write enabled

asking for cache data failed

---

### Post by drs305 on 2011-05-12
> **skyzthelimit230 said:**
> booted successfully. Remained booted.

errors I noted:

test wp failed: assume write enabled

asking for cache data failed

:-)

I'm not sure about the error messages. In any case, run these two commands to ensure we preserve the current boot setup:
```
sudo grub-install /dev/sda # Do not include the partition number.
sudo update-grub
```

This should be all that is necessary. The 'nomodeset' option will not be used during the next boot, which may fix the errors above. If the boot fails, you can use the previous grub prompt instructions (including nomodeset) and we may have to work on the 'nomodeset' issue.

If it boots normally the next time and you don't have any other issues, please mark the thread solved via the 'Thread Tools' link at the top right of the first post.

---

### Post by skyzthelimit230 on 2011-05-12
hey, thanks for all your help. One last question: i noticed Grub2 has Windows 7 listed twice. Why is that? 

I've noticed this long before the kernal panic though :)

---

