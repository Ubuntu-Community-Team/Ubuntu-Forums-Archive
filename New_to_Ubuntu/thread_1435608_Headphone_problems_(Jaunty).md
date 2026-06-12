---
title: "Headphone problems (Jaunty)"
date: 2010-03-21
forum: New to Ubuntu
---

### Post by RBTR on 2010-03-21
Alright. My internal speakers on my laptop works just fine, but when I plug my headphones in, the headphones do not work. The good news is that the speakers turn off when it is plugged in.
[B]
A few notes:[/B]

I have no Headphone options in any of my sound menus.

I also am not the one who originally installed Ubuntu onto my laptop. It was someone who "thinks" he knows what he's doing when it comes to this stuff. *sweatdrop*

-------------------------------------------------------------------------------

**What info I do have:**

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/card0/codec#* | grep Codec
Codec: VIA VIA VT1708

```



If you need information to help me, please tell me what commands to run. Thanks.

---

### Post by lidex on 2010-03-21
Do this for me please. Run the alsa-info script so we can get the full picture. Right-click the link in my sig and "save as" to your user folder. then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```

Post a link to the script output in your next post.

---

### Post by RBTR on 2010-03-22
Here you go:

[http://www.alsa-project.org/db/?f=875596d463be9d3695765bc0f2b875e5f80f0502](http://www.alsa-project.org/db/?f=875596d463be9d3695765bc0f2b875e5f80f0502)

---

### Post by lidex on 2010-03-22
Your best bet is to upgrade alsa. Click the alsa-upgrade script link in my sig. Instructions are there.

---

### Post by RBTR on 2010-03-23
....thats did it....thanks a lot.....

*extends hand for a handshake*

---

### Post by lidex on 2010-03-23
You're welcome. Enjoy.

---

