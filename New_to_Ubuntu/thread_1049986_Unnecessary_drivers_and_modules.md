---
title: "Unnecessary drivers and modules"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by davbren on 2009-01-25
Hey, I know nothing on this subject so pardon my ignorance. For Linux to be used on any machine, it requires a whole load of drivers loaded on to it. Now...I have a Samsung Q310. It's a great lil machine. It, like most machines, only has one hardrive, one webcam, one sound card and so forth. Would it improve the performance of the laptop if I got rid ofthe drivers I didn't need?

Also, how would I got about this?

---

### Post by overdrank on 2009-01-25
Moved to Absolute Beginner Talk and bumped to the top :)

---

### Post by txcrackers on 2009-01-25
Linux drivers, except for the most commonly used (like USB), are loaded dynamically. Example: if you have an Intel networking chip, the RealTek driver is **not** loaded. So, no, there's no need to "get rid of drivers" unless you feel compelled to build custom kernels...

---

### Post by pi.boy.travis on 2009-01-25
You would likely not see a performance improvement by removing drivers.  However, you would likely see a large performance boost by compiling your own kernel.  But be warned. . .  it can be tricky. . .

---

### Post by oldos2er on 2009-01-25
Uninstalling unnecessary drivers (or modules) will save you some hard disk space, and not much more, as was mentioned. I think it would be more beneficial, if you're looking to speed up your boot process, to turn off services you don't need. There's a great tool for this: sysv-rc-conf. Read [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) for more info.

---

### Post by davbren on 2009-01-26
Ok cool. Cheers for the tips. How would compiling a kernel imprve performance?

---

### Post by sdennie on 2009-01-26
> **davbren said:**
> Ok cool. Cheers for the tips. How would compiling a kernel imprve performance?

It may or may not depending on how you use the machine.  If you are just doing web/chat/office/programming type things you probably won't see a difference.  For gaming or a server, you might see a difference depending on the options you use to compile the kernel.  There are also some options that can save power on laptops that are not enabled by default in the Ubuntu kernel (ASPM specifically).

---

### Post by davbren on 2009-01-26
There are three reasons I ask about this really. Firstly I don't feel like I'm getting the performance I should be getting from the OS. Secondly, my battery life is terrible in comparison to MS. Lastly, programs in windows seem to load, tons faster than in Linux. I can understand that the wine programs I have installed will take a bit longer, but gnome programs are loading slowly. What can I do to resolve this?

---

### Post by sdennie on 2009-01-26
To help with battery life try: [www.lesswatts.org](www.lesswatts.org) or [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773") (maybe not specific to your laptop but, it's the general idea).  As for speed, try preload:

```

sudo apt-get install preload

```

After a while that will make your applications start faster because it preloads the cache with information that you often use.  Other than that, linux machines generally get faster the longer they run (and preload just helps them get faster quicker).

---

### Post by stchman on 2009-01-26
> **davbren said:**
> There are three reasons I ask about this really. Firstly I don't feel like I'm getting the performance I should be getting from the OS. Secondly, my battery life is terrible in comparison to MS. Lastly, programs in windows seem to load, tons faster than in Linux. I can understand that the wine programs I have installed will take a bit longer, but gnome programs are loading slowly. What can I do to resolve this?

Remember Ubuntu Hardy, Intrepid is a much newer OS that XP or 2000.  The minimum system requirements are far less for XP or 2000.  It makes sense that for the equivalent hardware Ubuntu would be slower.

The one thing about Ubuntu is that it's speed does not decrease significantly with age.  Windows installs slow to a crawl after time.

---

### Post by davbren on 2009-01-28
Yh I agree with that, the only worry is that Vista is running better. I won't convert back coz it frustrates me. I am however concerned that I've done something wrong.

---

