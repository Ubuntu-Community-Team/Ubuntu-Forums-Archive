---
title: "Hi, I've got a problem..."
date: 2009-03-25
forum: New to Ubuntu
---

### Post by osuplayer on 2009-03-25
... with my laptop.

Anyway, I'm new around here, I should Introduce myself

My name is Tom, I'm a student in a school called Shatin College in HK. I'm currently a member of the SC (school abbreviation) Linux Development team. We are using 8.04 Hardy Heron and everything is going well (Except the Networking). Hopefully, I'll post some questions and you guys answer it.

Back to topic, here is what I posted in another Tech forum

> I have a problem with the Ubuntu (Version 8.10). Ubuntu doesn't like my Integrated Sound Card.

When I plug my headphones in, Realtek Sound Manager disables the integrated Speakers, but that doesn't happen in Ubuntu (no, Realtek doesn't make software for Linux), can anyone help me? I've tried alot of things in the Ubuntu community and it didn't help.

About Laptop Config:

Fujitsu A6210

Intel Core 2 Duo P8400
Intel Mobile Chipset PM 45
RealTek ALC269 HD
ATI Radeon HD 3470 with HDMI output

Also as a added bonus- If you can get my Authentec AES2500 (Fingerprint reader) working, I'll give them a cookie :)

If anyone can help, I'll be grateful. If you need more info, don't hesitate and e-mail me.

---

### Post by llamabr on 2009-03-25
Hi.  I'm not sure, but I believe that if you give your question a more descriptive subject line, you'll get better replies.

also, since this is a sound issue, you might take it to the appropriate forum, where experts in this thing hang out.

good luck.

---

### Post by LowSky on 2009-03-25
Could you please give us more information on the  network issue.

As for Sound (again more info on your issue will help us) have you looked into the Volume manager top right on the panel, sometimes you need to enable certain ports for it to work correctly (I had to do this to get my mic working)

the fingerprint reader might be a tough one, but check out this link
[http://ubuntuforums.org/showthread.php?t=503928](http://ubuntuforums.org/showthread.php?t=503928)

---

### Post by taavikko on 2009-03-25
Hello, I'll give you a hint for the sound problem.

Some audiochips aren't properly regognized and you need to add extra options for it to properly function.

You can test them by removing sound module
```
sudo rmmod snd_hda_intel
```

and testing the right combination
```
sudo modprobe snd-hda-intel model=acer
```

The option "model=X" X is what your after.

There's multiple model's to choose from, and I just can't remember them all :(

When you find the working one, just add correspondent line to 
/etc/modprobe.d/alsa.conf file

---

