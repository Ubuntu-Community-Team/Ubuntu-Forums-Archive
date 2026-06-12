---
title: "Hibernate never &quot;wakes up&quot;"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Kjasontu on 2009-11-11
I am not sure which one I need to be using.  I love 'Sleep' in windows.  I am trying to use Hibernate (I think that is the equivalent), but I can never get it to become active again.  Is there a special set of keyboard commands that wakes it up?

---

### Post by Paqman on 2009-11-11
The equivalent to sleep is suspend.

Sleep/suspend = suspend to RAM
Hibernate = suspend to disk

Hibernate is pretty slow, but it may also be that it just doesn't work on your hardware. What type of PC are you using?

---

### Post by Kjasontu on 2009-11-11
> **Paqman said:**
> The equivalent to sleep is suspend.

Sleep/suspend = suspend to RAM
Hibernate = suspend to disk

Hibernate is pretty slow, but it may also be that it just doesn't work on your hardware. What type of PC are you using?

Hibernate will not wake up at all.  Suspend will wake up if you hit the Reset button once, but the keyboard will not work.  Once you Suspend the computer, you can never use the keyboard again and have to Restart anyway.  Very strange.

Dell computer
AMD 64 X2 duel-core
2G RAM

---

### Post by emeraldgirl08 on 2009-11-11
suspend doesn't work on my laptop either. I had to remove the battery and push the power button a couple of times then it finally restarted. Trying to restart by power button alone would not do anything. The lights on my panel would flash as if it were starting up and then nothing.

Very strange indeed.

---

### Post by Kjasontu on 2009-11-12
This is kind of a show stopper for me.  I can't use an OS if I can't step away from the computer without shutting down. :(

Anyone have any other ideas before I reinstall windows?

---

### Post by jflinux on 2009-11-12
Run synaptic 
and add package
uswsusp

vim  /etc/pm/config.d/00sleep_module
# SLEEP_MODULE="kernel"
Change the line to:
SLEEP_MODULE="uswsusp"

---

### Post by synicalx on 2009-11-13
> **Kjasontu said:**
> This is kind of a show stopper for me.  I can't use an OS if I can't step away from the computer without shutting down. :(

Anyone have any other ideas before I reinstall windows?

Before reinstalling windows, which version of Ubuntu do you have?

9.10 refused to sleep/hibernate on my desktop so I went back to 9.04, whereas 9.10 refused to work full stop on my netbook so I -had- to go back to 9.04:D

Regardless of which version your using though, try installing a newer/older one and tell us how that goes.

EDIT: Wow that was odd, my post didn't come through until just now, jflinux beat me to a solution!

---

### Post by coldReactive on 2009-11-13
Are you also by any chance trying to hit a key to wake it up?

that won't work with linux, linux requires you to press the power button to wake up.

---

### Post by djurny on 2009-11-13
> **coldReactive said:**
> Are you also by any chance trying to hit a key to wake it up?

that won't work with linux, linux requires you to press the power button to wake up.

that is not true.. there is (was) /proc/acpi/wakeup where you can see and set devices that can cause wakeup-from-sleep (s3/s5) events.. configuring is not that straightforward but possible!

---

### Post by Anarci on 2009-11-13
This may be unrelated to your problem but suspend will not work unless you have more swap space than ram as the entire ram contents get copied to swap.

---

### Post by coldReactive on 2009-11-13
> **djurny said:**
> that is not true.. there is (was) /proc/acpi/wakeup where you can see and set devices that can cause wakeup-from-sleep (s3/s5) events.. configuring is not that straightforward but possible!

But default is the power button, it's what I always had to do, so I expect it to be the same now.

---

### Post by djurny on 2009-11-14
> **Anarci said:**
> This may be unrelated to your problem but suspend will not work unless you have more swap space than ram as the entire ram contents get copied to swap.
please do not confuse hibernate with suspend,
hibernate: copy all needed ram content to disk and power down
suspend: keep ram powered, but turn off all (or most) surrounding devices

---

### Post by pensioner77 on 2009-11-14
I have seen this and another post about problems with hibernate & suspend in 9.10. I have the exact opposite,I could not get them to work with Jaunty,like another reply I had to completely shut down,disconnect the battery to get a restart, but with9.10 both work quite well,as has been mentioned in another answer it took me a time to realise that it needs the power button to pressed to "wake" it up. I have an E-System laptop.
Hope these comments are of some help.

---

