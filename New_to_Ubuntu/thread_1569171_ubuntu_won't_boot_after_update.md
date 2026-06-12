---
title: "ubuntu won't boot after update"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by holyskeleton on 2010-09-06
so one day i installed some update in the update manager, then next time i restart ubuntu it stops at the loading screen with the dots all orange so it's finished but it won't go to the desktop so it just stucks at the loading screen. ctrl+alt+del still works...

---

### Post by yeats on 2010-09-06
This sounds like a problem with your X server.  What kind of graphics card to you have?

---

### Post by holyskeleton on 2010-09-06
Ya I suspected that too except I have no idea on how to fix it. I have nvidia geforce m8600GS. How do I reset the x server, if that'll fix it?

---

### Post by sandyd on 2010-09-06
> **holyskeleton said:**
> Ya I suspected that too except I have no idea on how to fix it. I have nvidia geforce m8600GS. How do I reset the x server, if that'll fix it?
press ESC while booting.
select recovery mode.

---

### Post by theophiles on 2010-09-06
I've got the same thing going on with the same card. Booting to the old kernel works. Here is the conversation I've been having:
[http://ubuntuforums.org/showthread.php?t=1567193]("http://ubuntuforums.org/showthread.php?t=1567193")

We haven't figured it out so it might not be particularly helpful, but the more minds the better (which is one of the major reasons I like Ubuntu).

---

### Post by sandyd on 2010-09-06
propper bug report link comming up in next few minutes.
Need to sort through dupes.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/572279)

don't think its this one... (mentions busybox, which you don't have...)
[https://bugs.launchpad.net/ubuntu/+bug/590999](https://bugs.launchpad.net/ubuntu/+bug/590999)

Explanation for why your seeing the message...
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984/comments/27](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/532984/comments/27)

If you have more than one screen:
[https://bugs.launchpad.net/bugs/533135](https://bugs.launchpad.net/bugs/533135)

Try doing this.
at the grub screen
press esc to show the menu...

press e at the linux entry.

at the kernel line, remove the words "quiet" and "splash" from the end of the line

press control X to boot.
If the above solution works, see -> [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/620606/comments/3](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/620606/comments/3)

---

### Post by utnubuuser on 2010-09-06
I got around this problem by booting an older kernel, enabling "pre-released/proposed updates" in synaptic,updating, then switching off "pre-release/proposed updates" again.

---

### Post by holyskeleton on 2010-09-06
> **carlee said:**
> press ESC while booting.
select recovery mode.

nothing happens when i press esc at the splash screen. some times it'll check system files but nothing besides that. if the dots turns orange then it gets stuck for good. i've been trying to constantly press esc but it doesn't help either.

---

### Post by MooPi on 2010-09-06
Use the shift key instead and see if that helps. Esc was used on previous versions of Ubuntu and it has switched to the shift key on the latest

---

### Post by holyskeleton on 2010-09-06
nope. nothing happens...

---

### Post by holyskeleton on 2010-09-08
so... does anyone know how i can reset the x server settings if i load into live USB image? or i can uninstall the restricted driver altogether while in live mode?

---

### Post by sandyd on 2010-09-09
> **holyskeleton said:**
> nope. nothing happens...

press shift and keep on pressing it (dont hold it! ) as soon as you push the power button.

---

### Post by holyskeleton on 2010-09-09
Same thing...

---

