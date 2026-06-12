---
title: "iPod not recognized. HELP."
date: 2011-08-16
forum: New to Ubuntu
---

### Post by jimkenstein on 2011-08-16
i plug, unplug, and plug in back my iPod touch but an error message prompts:

"[B]Unable to mount iPot
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)[/B]"

help. i wanna sync my mp3s but i cant. even gtkpod iPod Manager cant read my iPod.

---

### Post by dniMretsaM on 2011-08-16
Try this:
```
sudo add-apt-repositoryppa:pmcenery/ppa
sudo apt-get update
sudo apt-get remove libimobiledevice1
sudo apt-get install libimobiledevice0
```

---

### Post by jimkenstein on 2011-08-17
> **dniMretsaM said:**
> Try this:
```
sudo add-apt-repositoryppa:pmcenery/ppa
```

that first command cant be initiated. it responses "command not found". is the repository spelled correctly?

---

### Post by Paddy Landau on 2011-08-17
> **jimkenstein said:**
> that first command cant be initiated. it responses "command not found". is the repository spelled correctly?
There is a space missing. Try this:
```
sudo add-apt-repository ppa:pmcenery/ppa
```

---

### Post by jimkenstein on 2011-08-17
> **Paddy Landau said:**
> There is a space missing. Try this:
```
sudo add-apt-repository ppa:pmcenery/ppa
```

still cant mount my ipod.

---

### Post by pi.boy.travis on 2011-08-17
Do you have the brand-new iPod touch firmware? I can't get mine to work in Ubuntu 11.04 with the new firmware either. Apple invents new ways of keeping Linux from working with iPods, but usually a new kernel release fixes things up. If all else fails, try a newer kernel version, or just wait for Ubuntu 11.10 to be released.

---

### Post by dniMretsaM on 2011-08-17
Ok, what device model and what firmware are you on. And what version of Ubuntu?

---

### Post by jimkenstein on 2011-08-17
any other ubuntu experts could help here? (:

---

### Post by dniMretsaM on 2011-08-17
If you answer the questions in my previous post, I might be able to help. Also, go into Synaptic and search for libimobiledevice and tell me what you see (a screenshot would work).

---

### Post by Paddy Landau on 2011-08-18
> **pi.boy.travis said:**
> Apple invents new ways of keeping Linux from working with iPods...
Apple's support for Linux is disgraceful; indeed, puzzling when you remember that the Mac operating system is much closer to Linux than to Windows.

I avoid Apple products, not because they're bad (they're actually usually excellent), but because of the lock-in.

---

### Post by dniMretsaM on 2011-08-18
Yeah, Apple's restrictions disgust me. Sadly, I have an iPod Touch (which I currently can't get to work with Linux, but that's another story). When I decide it's time to upgrade, I'm getting an old Android phone instead.

---

### Post by pi.boy.travis on 2011-08-18
> **Paddy Landau said:**
> Apple's support for Linux is disgraceful; indeed, puzzling when you remember that the Mac operating system is much closer to Linux than to Windows.

I avoid Apple products, not because they're bad (they're actually usually excellent), but because of the lock-in.

It's always puzzled me. Since Mac OS X is POSIX compliant, it seems to me that porting iTunes to Linux would be a breeze compared to porting it to Windows. Apple has made some good contributions to Open Source however, remember that Apple developed CUPS, along with the (generally) excellent printer support we brag about.

---

### Post by pierreyy on 2011-08-18
Is your ipod touch software version the newest one out?... that maybe the problem... ive connected several ipods and ipod touches to my computer and ive never had a problem... if your efforts fail then....wait until an update comes out

---

### Post by pi.boy.travis on 2011-08-18
Just out of curiosity tried with vanilla kernel 3.1-rc2 and my iPod touch is working with the latest firmware.

---

### Post by dniMretsaM on 2011-08-18
> **pi.boy.travis said:**
> It's always puzzled me. Since Mac OS X is POSIX compliant, it seems to me that porting iTunes to Linux would be a breeze compared to porting it to Windows. Apple has made some good contributions to Open Source however, remember that Apple developed CUPS, along with the (generally) excellent printer support we brag about.

Apple did not develop CUPS. They bought it from Michael Sweet in 2002. It was already GPL'd when they bought it, so it still is. I can guarantee it would have been proprietary if Apple had actually started it. The only reason they bought it was so they could develop proprietary extensions.

---

### Post by trozamon on 2011-08-18
I've had my iPod for a while, and the only way it works with Ubuntu for me is when it's jailbroken.

---

### Post by dniMretsaM on 2011-08-18
> **trozamon said:**
> I've had my iPod for a while, and the only way it works with Ubuntu for me is when it's jailbroken.

That shouldn't have anything to do with it I don't think.

---

### Post by pi.boy.travis on 2011-08-19
> **dniMretsaM said:**
> Apple did not develop CUPS. They bought it from Michael Sweet in 2002. It was already GPL'd when they bought it, so it still is. I can guarantee it would have been proprietary if Apple had actually started it. The only reason they bought it was so they could develop proprietary extensions.

Wow, I didn't know that! Thanks!

---

