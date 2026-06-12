---
title: "new 9.04 install, no sound"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by thegrilledcheese on 2009-04-26
I bought a new hd and put a fresh install of 9.04 64bit on it, loaded grub on new drive and everything is working perfectly...except for sound.  I have none.

I'm like most new users in that I don't know much about configuring & administrating the system through the command line.   So I have no idea on how to check and see what if any sound card the system lists as installed.  

Windows reports the sound card to be "creative sb X-fi".  

My questions are:

1.) How do I check to see which sound card/driver ubuntu has listed.
2.) How do I get and install the correct drivers?

I went to system > hardware drivers and all that came up was the nvidia graphics drivers, which I installed.  Nothing related to audio.


Any help is appreciated.  Please try to dummy down your responses.  I've searched extensively on the forums but have found nothing specifically related to 9.04 and creative sb x-fi cards.

Thanks,

the grilled cheese

---

### Post by Bodsda on 2009-04-26
You shouldnt need to install drivers.

To get a list of soundcards use this command from the terminal

```

asoundconf list

```

Also, try running the following command then restarting your musci player and trying to play something

```

killall pulseaudio

```

Hope this helps,

Bodsda

---

### Post by thegrilledcheese on 2009-04-26
asoundconf list gives this:
Names of available sound cards:
default

did the killall command and nothing happened.

Still no sound.

- the grilled cheese

---

### Post by Bodsda on 2009-04-26
Hmm, so you have one card and pulseaudio isnt screwing up,

try doing this

```
asoundconf set-default-card default
```

Then reboot,

Not sure what else to suggest,

Bodsda

---

### Post by Sealbhach on 2009-04-26
Hi, give us the output of

```
aplay -l
```

```
lshw -C sound

```
Those are L's, not I's.


.

---

### Post by Sealbhach on 2009-04-26
Just found this thread here too, which will be of interest:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)


.

---

### Post by thegrilledcheese on 2009-04-26
result of aplay -l

**** List of PLAYBACK Hardware Devices ***

----------------------------
result of 
lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: SB X-Fi
       vendor: Creative Labs
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=5 mingnt=4


I also did this and rebooted but still no sound
asoundconf set-default-card default


- the grilled cheese

---

### Post by Sealbhach on 2009-04-26
It looks like you need to download the Creative drivers, compile them and install them, using the guide here:

[http://ubuntuforums.org/showthread.php?t=870001](http://ubuntuforums.org/showthread.php?t=870001)

Not very user friendly, but have a go, and just copy and paste the commands into the terminal to avoid errors.

.

---

### Post by thegrilledcheese on 2009-04-26
I now have sound.  Thanks for the help.  I knew switching to ubuntu from windows made sense for a reason...community support!

- thegrilledcheese

---

### Post by Sealbhach on 2009-04-27
> **thegrilledcheese said:**
> I now have sound. Thanks for the help. I knew switching to ubuntu from windows made sense for a reason...community support!
 
- thegrilledcheese
 
Cool, that's great. Let us know what worked so others looking this up later know what to do.
 
Did you follow that guide and compile the Creative drivers? If so, please note the comment he made - if there's a kernel update you will need to do it all over again (unfortunately).
 
 
.

---

### Post by thegrilledcheese on 2009-04-27
Yes I followed the directions exactly as described on this post:
 
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=870001[/COLOR]]("http://ubuntuforums.org/showthread.php?t=870001")
 
Sound worked immediately after restart.
 
- thegrilledcheese

---

