---
title: "No sound! Fresh install of 8.10, Won't play any sound."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by d0cta ew on 2009-01-12
Hello All,

I'm a newbie to linux, and just wiped my laptop and installed Ubuntu 8.10.  I cannot get any sound to play on my laptop, and have been attempting to use this thread-I havent found anything on my current problem.

[http://ubuntuforums.org/showthread.php?t=205449&highlight=how+to+setup+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=how+to+setup+sound)

Unfortunately, i get lost when i am directed into the sudo nano /etc/modules part, i know my driver but I don't know where to go from there. Any advice?

Thanks in advance, and if i just missed a good thread on this in search feel free to direct me.

-d0cta ew

---

### Post by kansasnoob on 2009-01-12
Go to Applications > Terminal and enter:

```
aplay -l
```

Copy-n-paste that output here.

BTW, that's a lower case L.

---

### Post by d0cta ew on 2009-01-12
Will do, I just had to come back to work from lunch, I'll post it in about an hour and a half when I get home.  Thanks!

---

### Post by kansasnoob on 2009-01-12
> **d0cta ew said:**
> Will do, I just had to come back to work from lunch, I'll post it in about an hour and a half when I get home.  Thanks!

That will tell us whether your sound card is recognized or not.

---

### Post by d0cta ew on 2009-01-12
here we go!
when i type aplay -l in the terminal i get

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by d0cta ew on 2009-01-14
/bump :D

---

### Post by Lod on 2009-01-14
You might take a look at this topic: [http://ubuntuforums.org/showthread.php?t=921556](http://ubuntuforums.org/showthread.php?t=921556) in [post #18](http://ubuntuforums.org/showpost.php?p=6218963&postcount=18).
I believe you have a similar soundcard?

It worked for me anyway.

---

### Post by linux_tech on 2009-01-14
what is output of:



```

cat /proc/asound/card0/codec#* | grep Codec



```
Also what make and model of pc is this?

---

### Post by usererror on 2009-01-14
I had the same problem on my laptop.

It installed the sound card driver, and I had the volume mixer on the gnome bar, but no sound.  I found that I had to unmute and "turn up" one of the additional volume bars in the advanced mixer.  It was called something weird.

If you want a screenshot of mine I can do that when I get home.

---

### Post by d0cta ew on 2009-01-14
ok i'm going to be able to take a look at this in about 20 mins, i'll post a big reply to all of these. Much appreciated. :D

---

### Post by d0cta ew on 2009-01-14
@usererror 

which was it that you had to unmute? all of mine are unmuted when i open volume control.

thanks.

@linux_tech
my laptop is a gateway, model 3040GZ.  (Little old, I know i know.)

output of ```
cat /proc/asound/card0/codec#* | grep Codec
```

is
```
cat: /proc/asound/card0/codec#*: No such file or directory
```

---

### Post by usererror on 2009-01-23
I will have to check it tonight.  I don't have it with me...unless you've already figured it out. :)

---

