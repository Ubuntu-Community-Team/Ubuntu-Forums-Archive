---
title: "Ubuntu hibernate - not working"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by drusmanbashir on 2010-11-07
Hello everyone, 

I use a intel corei5 with ATI HD5770 (if that info helps)
i just installed ubuntu 10.04,

when i use 'hibernate'
it says some sort of freeze error and the screen comes back on
i will be happy to convey any more required info

---

### Post by tajiknomi on 2010-11-07
[SIZE=2]i think u r using **Wubi**...isn't?

Wubi doesn't allow Os for the Hibernation...

moreover,follow the same thread [/SIZE][http://art.ubuntuforums.org/showthread.php?t=1107025](http://art.ubuntuforums.org/showthread.php?t=1107025)

Consider it as a** bug** in Wubi

---

### Post by marl30 on 2010-11-07
I have the same problem in 10.10. Been looking for a solution for a while now too.

---

### Post by vallvi on 2010-11-07
Same problem here. Since many years, and on different machines. This one: Acer, AX8310, plenty 6GB memory... (no wubi - real Ubuntu partition) No hibernate, no suspense.

Is this a bug?

---

### Post by bcbc on 2010-11-07
To hibernate you need a swap partition that is larger than the size of your ram. How much larger depends on the 'overflow' and is not well defined. e.g. on karmic my 1GB ram hibernated with a 1GB swap partition. On Maverick I need 1.5GB and I've had issues even with that.

When you change the swap partition, you need to update the uuid in the /etc/initramfs-tools/conf.d/resume file and run 'update-initramfs -u' afterwards in addition to the /etc/fstab changes.

If you still have problems, check the syslog (search for PM: )

PS wubi installs can also hibernate as long as there is a swap partition (but not used much since the point of wubi is not having to partition).

See this for more info [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Verbeck on 2010-11-07
dont know if this is related. worth a try though
[http://ubuntuforums.org/showpost.php?p=10051992&postcount=19](http://ubuntuforums.org/showpost.php?p=10051992&postcount=19)

---

### Post by drusmanbashir on 2010-11-07
well my swap partition is 8G and my RAM is 4G so that cannot be the reason

---

### Post by AngusH on 2010-11-07
Hey, from my understanding some hardware setups will simply not be able to hibernate with ubuntu/linux.
Hibernating makes a lot of use of the hardware, so if there drivers aren't almost perfect you're going to encounter problems. Unfortunately linux is far from perfect in the driver department because it's a minority os. It may be something you just have to live with.
Alternatively, why do you need hibernate? I've never had much use for it. I find in most cases either suspension or turning the computer off are the best options.
Regards
Angus

---

### Post by SaintDanBert on 2010-11-07
LOTS OF FOLKS HAVE VARIOUS TROUBLES WITH "HIBERNATE" and "SUSPEND."

You [highlight]must must must[/highlight] have a swap partition.
The partition must be (a) at least as large as physical ram, and (b) have a little extra space.

There are known troubles if you have mounted external USB, flash, media (SD, CF, etc) cards and devices (web cam, etc).  You can add a script into /etc/pm/sleep.d/* that will unmount everything if this is your gremlin.

Some video cards and network cards cause trouble either going down or waking up.

Bonne chance,
~~~ 0;-Dan

---

### Post by tajiknomi on 2010-11-09
[SIZE=2]Hay ...Follow the **link **and see the Post of **John dias**[/SIZE], 

[SIZE=2]It Work's..!![/SIZE][http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

---

### Post by tajiknomi on 2010-11-09
link is here [http://ubuntuforums.org/showthread.php?t=1444822](http://ubuntuforums.org/showthread.php?t=1444822)

---

