---
title: "After upgrading to kernel 2.6.27-13 it won't boot"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by lobo-tuerto on 2009-03-04
Hi guys,


A couple of days ago the 2.6.27-13 kernel update was released. After I upgraded my Ubuntu installation to it, I haven't been able to boot. The screen goes black and no Ctrl+Alt+F1 (or any other) will work.
If I use the last one (2.6.27-12) it works just fine (although my sound is muted now...)

The only way for it to react seems to press the "power button", then it will rollback something and poweroff. The lines I have seen where it stops seems to have to do with checking something about my battery or some power management feature, dunno really (but I will be glad to assist if you tell me how).

Any ideas?

Ubuntu 8.10
HP Pavillion dv9000 (laptop)

---

### Post by civillian on 2009-03-04
there have been a number of threads with issues similar to this, a few of them are 

[http://ubuntuforums.org/showthread.php?t=1084783](http://ubuntuforums.org/showthread.php?t=1084783)
[http://ubuntuforums.org/showthread.php?t=948584&highlight=kernel+update+broke](http://ubuntuforums.org/showthread.php?t=948584&highlight=kernel+update+broke)

it seems that the new kernel release has broken a number of systems (including my own) so if you can select the older one(s) from grub, then choose the most recent working kernel version for you and select that at boot. 

You can automate this by commenting out the newest (broken/buggy) kernel in your grub.lst

---

### Post by Eisenwinter on 2009-03-04
I just want to say, that this is an excellent example of why you should not immediately dump your older kernel after updating to a newer version.

---

### Post by civillian on 2009-03-04
I totally agree (although I'm not sure how constructive your comment is :P) this whole kernel issue has flagged up some useablility issues which distros like linux mint address:ie flagging new kernel updates as a dangerous update for your pc. The whole issue made me long for a nice install of debian testing :P although the more i think about it the more a clean install every 6 months is the way forwards :D

---

### Post by lobo-tuerto on 2009-03-04
Thank you guys, seems like a fairly common problem. Guess I will just wait for the next kernel version then... even booting in recovery mode yields a black screen.

---

### Post by civillian on 2009-03-04
Afraid so :( 
I get error messages, and it seems to have broken something in graphics drivers etc (on my machine at least), I'm just waiting for jaunty to be released now :)

---

### Post by linuxisevolution on 2009-03-04
I believe your problem is that you've installed kernel-specific graphics drivers and then changed your kernel without changing your graphics drivers. This will cause no video :P

---

### Post by civillian on 2009-03-04
probably, just a reinstall of drivers, or update would fix it, but I'm on a restrictive connection (university) so its a bit difficult, however, the version I have works fine for now :D

---

### Post by lobo-tuerto on 2009-03-04
Well, you were right, it has to do with graphic drivers. I did uninstall them, then rebooted and I could boot with the new kernel version.

Then I reinstalled the newest graphic drivers. Rebooted and same problem.

Seems like it's either wait for new kernel, or new graphic drivers.

Still no sound. In whichever kernel version.

---

### Post by Hentai_Jeff on 2009-03-04
Or you could do what I do and compile the latest kernel.

---

