---
title: "MORE issues with gfxboot on Intrepid"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by xreaper on 2009-02-08
Hey all, me here again. I have followed various tutorials on getting 'grub like suse' working on my computer (dual booted with windows xp and ubuntu 8.10 32 bit)

And now, I think I am close to finishing, because after SEVERAL attempts in reinstalling grub (using different versions of gfxboot) i  have finally managed to get it working, not fully, but to the extent that it can load everything except the actual message file. 

basically, the problem is that grub won't load the message file, instead, it comes up with 'error: invalid file format' and continues to load the dull, boring grub boot loader.

I have tried various themes to try and get it working but alas, no avail. can someone please help me, or even point me in the right direction to get this working properly.

---

### Post by xreaper on 2009-02-08
no one has any idea?

---

### Post by UbNewbie on 2009-02-18
Hi xreaper,

It's true that there is some changing in file format for grub-gfxboot version 0.97-40. I think yoou have install that version otherwise it won't work with Intrepid at all..

Any way. What you can do e.g. install gfxboot-theme-zen from repository and compile it for your self.
It is not quit fancy but it works...

Steps that you need to do:

install gfxboot-theme-zen
cd /usr/share/gfxboot-theme-zen/
sudo make
sudo make install
cd install
sudo su
ls . |cpio -o > /boot/grub/message.zen

If somebody have an advise and approriate pointer to the right direction.. please....

Hope this help.

H2T

---

### Post by xreaper on 2009-02-24
hey,thanks for the reply ^^ I'll just try that now...

---

### Post by xreaper on 2009-02-24
wow it worked!!! just another question.. is it possible to do that with any other themes? if so, how?

---

### Post by ItJoker on 2009-03-02
Hi there!
Thanks to UbNewbie's code I solved the same problem.
Great! [-o<

Now, I saw a lot of beautiful themes for the old version of gfxboot... Do you know where to find someone ready for Intrepid?

Thank you!! :)

---

### Post by aniruddha on 2009-03-10
Hi. I would also like to know if it is possible to use older themes with Ubuntu 8.10 and (the latest) gfxboot.

---

### Post by UbNewbie on 2009-03-24
Yeah I am still digging for the answer!
I can't imagine that nobody have the experience yet..;)

So please share your experience with us.

Thanks..

ubnewbie

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111183[/ATTACH]

Hope this helps

---

### Post by karllv on 2009-04-26
How to use other message on 9.04?

---

### Post by xurxoham on 2009-07-22
> **Malac said:**
> I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111183[/ATTACH]

Hope this helps
Thanks a lot to UbNewbie and Malac. 
I was upset after trying lots of message.XXX and seeing that all of them only made to appear the same error message -_-' 
At last I put into my boot screen a smart menu to choose which OS. i want to use.

Thanks again!! :D

---

