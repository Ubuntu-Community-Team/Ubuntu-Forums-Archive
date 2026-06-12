---
title: "Help with Syching iPod Touch Wirelessly"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by UnknownFear on 2009-03-19
I am following a tutorial on how to synch the iPod Touch in Ubuntu [here]("http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux"), but I ran into some problems. I am at the part where I install "ipod-convenience" and I put in my iPod's IP address. When I type "ipod-touch-mount" into the terminal, this is what I get:

```
daniel@daniel-desktop:~$ ipod-touch-mount
touch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.

```

Can anyone help me out? I'm so close to be able to synch my iPod with Linux, yet I have one little problem. Thanks for any help :)

---

### Post by UnknownFear on 2009-03-20
Does anyone have any suggestions?

---

### Post by hostilejosh on 2009-03-20
did you see this:

"UPDATE: Since the release of the 2.0 firmware for iPhones and iPod touch, the exact method detailed below will not work. Ubuntu's wiki-style community documentation, however, has posted work-arounds, including a method that's similar to this feature's system, and another that uses a third-party music player for fewer data mishaps. Refer to that link before attempting any of the below with an iPhone or touch model sporting 2.0 firmware or later&#8212;and always back up your phone before jumping into murky, jailbroken waters"

it also seems that you need to type 
```
sudo ipod-touch-mount
```

to get root permissions


edit: or maybe not, just read it more thoroughly.

---

### Post by UnknownFear on 2009-03-20
> **hostilejosh said:**
> did you see this:

Ah, my mistake. This works perfectly! I am now copying over all the songs from my iPod to my Music folder via iTunes_Control. Thanks and sorry for not reading more thoroughly :P

---

