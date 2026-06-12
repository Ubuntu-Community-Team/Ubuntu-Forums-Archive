---
title: "Dual  Boot  problems"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Origen2 on 2010-12-12
I have been using Ubuntu for many months, when suddenly it will no longer boot. When the operating system selction is offered on start up, when I toogle to Ubuntu and press enter , the computer simply restarts the operating section page again. I can start Windows XP, but Ubuntu seems to have dissappeared> Does anyone know what the problem might be? I looked at the solutions to similar threads, but  don't understand how you  can fix this without wiping out the current intallation  and re-installing Ubuntu?  The instructions for the  fix seem to assume that the Ubuntu  terminal is available, which since Ubuntu  will not start  at all  seems like a non-solution??

---

### Post by amjjawad on 2010-12-12
> **Origen2 said:**
> I  ahve been  using Ubuntu  for  many months, when suddenly  it will no  longer boot.  When the  operating system  selction  is offered on  start up,  when I toogle to  Ubuntu and press enter ,  the computer simply  restarts the operating section  page again.   I can start  Windows XP,  but Ubuntu  seems to  have  dissappeared>  Does anyone know what the problem might be?

Hello and welcome :)

Most likely you have problem with your bootloader.
In order to be able to help you, please follow the instruction in this link and post back the result here but wrap up the text with "#" or "CODE" tags :)

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Also, please list your machine specification :)

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

I hope it is a Wubi install i.e, Ubuntu installed inside Windows.

If yes, see problem # 2 here.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If you are not sure about your setup, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by drs305 on 2010-12-12
Most likely Problem 2 from here:
[Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

Ahhhh, what *sikander3786* said ... ;-)

---

### Post by Origen2 on 2010-12-12
So I  will  need to  creat an  Ubuntu disk?

---

### Post by sikander3786 on 2010-12-12
Definitely. Or a Live USB. You'll need the Ubuntu image for that and can be done from Windows as well. Use unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by Origen2 on 2010-12-23
I  have  been totally  defeated by this problem,  repairing the Grub upgrade and despite spending  hours trying to fix this  I  cannot  get Ubuntu to  boot.. and I  guess my  stuff  has  been lost.  I  guess that Ubuntu  is not for me.. I  used it for over a year,  but apparently  defective upgrades are worse than  viruses. Is there a forum where one  can  check for problems  before installing upgrades, if I decide to go back  to using it?

---

### Post by sikander3786 on 2010-12-23
If you want a stable Ubuntu setup for production purposes, install it properly on its own separate partition not via Wubi. Wubi was intended for testing Linux, just for giving you a basic idea of how Linux looks like, how it works and once tested, you need to install it properly ;-)

Many people have adopted Wubi permanently and then they keep on complaining at Ubuntu and Updates. Wubi is just a virtual folder on your Windows partition so how can you expect an OS to be stable while running virtually.

If you really want to try Ubuntu with its full capabilities, do a proper install. If you need any help regarding that, we'll happily try to help you. You can definitely dual boot Windows and Ubuntu that way also.

Good Luck!

---

### Post by Origen2 on 2010-12-23
I don't think that I installed Wubi?? I  downloaded and installed Ubuntu  from the website. I  guess it does not matter at this point.. I  just have to  figure out how to get my  data off of Ubuntu...

---

### Post by sikander3786 on 2010-12-23
Did you take a look at the thread we linked to in post # 3 and 4 above?

Anyhow, boot an Ubuntu Live CD/USB and locate your Windows partition. From Applications > Accessories > Terminal,

```
sudo fdisk -l
```

Assuming sda1 is your Windows partition (it might be different, find it from the output of above command).

```
sudo mkdir /media/win 
sudo mount /dev/sda[COLOR="Red"]1[/COLOR] /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

It should appear under /mnt folder and you should be able to copy/paste any data to a safe location.

If you don't have a Live CD/USB at the moment, download and follow the instructions here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Feel free to post back if you need further help :-)

---

### Post by Origen2 on 2010-12-23
Thanks for the suggestions..let me try this again. Have  been  such  big  booster of Linux/Ubuntu to my  colleagues and students, I  should not give up  so easily, I  guess...but it has  been so time  consuming right at the end of the semester...

---

### Post by amjjawad on 2010-12-23
> **Origen2 said:**
> Thanks for the suggestions..let me try this again. Have  been  such  big  booster of Linux/Ubuntu to my  colleagues and students, I  should not give up  so easily, I  guess...but it has  been so time  consuming right at the end of the semester...

"Never give up nor surrender" << that's my motto.

Do that when you have time. You'll find all the support you need in this forum. You don't need another forum, trust me.

---

