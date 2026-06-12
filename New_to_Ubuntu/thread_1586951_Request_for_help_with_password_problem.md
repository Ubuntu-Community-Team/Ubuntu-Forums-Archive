---
title: "Request for help with password problem"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by Old Jimma on 2010-10-02
Hi Community:

I really screwed up changing my password using System > Preferences > About Me and now Ubuntu and I don't agree what my password is...

In fact, I don't know what Ubuntu thinks my password is anymore.

How to I recover my password?

Thanks,
Phil Smith
DUluth, GA

ps. I really screwed up my right index finger in a table saw a few years ago and it makes typing a little more difficult.

---

### Post by sisco311 on 2010-10-02
Boot into recovery mode and reset your password:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by Hippytaff on 2010-10-02
have you tried resetting it - [http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by Old Jimma on 2010-10-02
Thanks for your reply, Hippytaff:

I was running lucid lynx. It doesn't show that grub page on boot-up.

Phil

---

### Post by sisco311 on 2010-10-02
> **Phil Smith said:**
> Thanks for your reply, Hippytaff:

I was running lucid lynx. It doesn't show that grub page on boot-up.

Phil

Hold down SHIFT during the bootup.

---

### Post by Old Jimma on 2010-10-02
Also, holding the shift key during boot-up did not work.

Thanks,
Phil

---

### Post by sisco311 on 2010-10-02
Boot a Live CD, chroot into Ubutnu and change your password:
```
sudo mount **/dev/sdXY** /mnt
sudo chroot /mnt
passwd **username**
exit
sudo reboot
```
Where **/dev/sdXY** is the device name of the root partition (you can check it in System -> Administration -> GParted, i.e. /dev/sda1) and **username** is your login name.

---

### Post by nlsthzn on 2010-10-02
Please forgive my off-topic but I find it scary that it seems so easy to get into an Ubuntu system that you don't know the password too...

---

### Post by sisco311 on 2010-10-02
> **nlsthzn said:**
> Please forgive my off-topic but I find it scary that it seems so easy to get into an Ubuntu system that you don't know the password too...

Physical access is root access, take a look at:

[thread=1463735]Root access granted in recovery mode[/thread]
[thread=989517]Physical access is root access[/thread]
and
[thread=510812]Ubuntu Security[/thread]

---

### Post by Old Jimma on 2010-10-02
Thanks, sisco311:

I'll give it a try. It will take 20 minutes or so to download and burn a live CD.

Phil

---

### Post by nlsthzn on 2010-10-02
> **sisco311 said:**
> Physical access is root access, take a look at:

[thread=1463735]Root access granted in recovery mode[/thread]
[thread=989517]Physical access is root access[/thread]
and
[thread=510812]Ubuntu Security[/thread]

I had never thought about that, thank you for the links...

---

### Post by Old Jimma on 2010-10-02
Hi Sisco:

Got the ISO burned... I'm working on it now.

Thanks,
Phil

---

### Post by Old Jimma on 2010-10-02
Dear Sisco:

Many, many thanks for your help. I am very grateful for it. If you send me a private message w/ contact info, I'll send a gift of appreciation.

It worked! :)

YOU DA MAN, SISCO!!!

Very sincerely,
Phil Smith
Duluth, GA

---

### Post by nlsthzn on 2010-10-02
> **Phil Smith said:**
> Dear Sisco:

Many, many thanks for your help. I am very grateful for it. [B]If you send me a private message w/ contact info, I'll send a gift of appreciation.
[/B] 
It worked! :)

YOU DA MAN, SISCO!!!

Very sincerely,
Phil Smith
Duluth, GA

It's a trap! j/k ;)

---

### Post by sisco311 on 2010-10-02
> **Phil Smith said:**
> Dear Sisco:

Many, many thanks for your help. I am very grateful for it. If you send me a private message w/ contact info, I'll send a gift of appreciation.

It worked! :)

YOU DA MAN, SISCO!!!

Very sincerely,
Phil Smith
Duluth, GA

My pleasure!

Please mark this thread as [SOLVED] and we'll cry quits. =)

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu then "Mark this thread as Solved".



> **nlsthzn said:**
> It's a trap! j/k ;)

[noparse]:)[/noparse]

---

### Post by Old Jimma on 2010-10-02
Done, Sisco. You da man!
:)
Phil Smith, Duluth, GA USA

---

