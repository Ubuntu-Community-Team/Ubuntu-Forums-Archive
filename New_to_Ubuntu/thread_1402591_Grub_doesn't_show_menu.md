---
title: "Grub doesn't show menu"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Vohr on 2010-02-09
How can I configure Grub to make it show a menu when I boot?
I changed my /boot/grub/menu.lst file, commented the hiddenmenu option, and added a timeout of 20 seconds. But when i turn on my computer, it goes straight to Ubuntu (it doesn't show a menu or wait 20 seconds).
I'm using Ubuntu 9.10 and GNU GRUB 0.97 (according to grub-install -v)

---

### Post by tom.swartz07 on 2010-02-09
> **Vohr said:**
> How can I configure Grub to make it show a menu when I boot?
I changed my /boot/grub/menu.lst file, commented the hiddenmenu option, and added a timeout of 20 seconds. But when i turn on my computer, it goes straight to Ubuntu (it doesn't show a menu or wait 20 seconds).
I'm using Ubuntu 9.10 and GNU GRUB 0.97 (according to grub-install -v)

Id be willing to bet you forgot to run

```
sudo update-grub
```
after you did your changes.

Does that fix it?

---

### Post by Vohr on 2010-02-09
You would win the bet :P
But anyway, I tried running that, restarting my computer, and nothing changed.

---

### Post by tom.swartz07 on 2010-02-09
> **Vohr said:**
> You would win the bet :P
But anyway, I tried running that, restarting my computer, and nothing changed.

What was the output of update-grub? You could also try update-grub2

Make sure you saved the changes- they might have reverted since you restarted, then run the command again and post the output here.

---

### Post by zeroseven0183 on 2010-02-09
Try holding the SHIFT key when booting. And I believe you're already using GRUB2 that's why it's not /boot/grub/menu.lst rather /boot/grub/grub.cfg and is not recommended to be edited.

---

### Post by Vohr on 2010-02-09
This is the output:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

After running this command, I checked /boot/grub/menu.lst and my changes are still there:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

update-grub2 doesn't work, it says "command not found".

---

### Post by tom.swartz07 on 2010-02-09
> **Vohr said:**
> This is the output:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Looks all good from here. Since it says update-grub2 isnt found, youre probs running grub legacy.


> 
After running this command, I checked /boot/grub/menu.lst and my changes are still there:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

update-grub2 doesn't work, it says "command not found".

Theres your problem- you didnt uncomment the hidden menu entry

change it so it says 

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

---

### Post by Vohr on 2010-02-09
> **zeroseven0183 said:**
> Try holding the SHIFT key when booting. And I believe you're already using GRUB2 that's why it's not /boot/grub/menu.lst rather /boot/grub/grub.cfg and is not recommended to be edited.
This worked, holding shift made the menu visible, but now i'm more confused than before!
If this worked, it means I have GRUB2, right?
But still, when I run grub-install -v it says my version is 0.97, isn't that GRUB 1?
Also, when I tried running update-grub2 (which I assume, is for GRUB2) it didn't worked.

---

### Post by tom.swartz07 on 2010-02-09
> **Vohr said:**
> This worked, holding shift made the menu visible, but now i'm more confused than before!
If this worked, it means I have GRUB2, right?
But still, when I run grub-install -v it says my version is 0.97, isn't that GRUB 1?
Also, when I tried running update-grub2 (which I assume, is for GRUB2) it didn't worked.

Youre right- you have the old version of grub.

See my last post- it seems you simply forgot to uncomment the hidden menu entry

---

### Post by zeroseven0183 on 2010-02-09
Did you upgrade from 9.04 (or earlier)? It seems that you're still using the Legacy boot loader (that is, Grub 0.97). Anyway, here's how you can upgrade your Grub: open a Terminal and type

```
sudo apt-get install grub-pc
```

then follow the instructions in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Vohr on 2010-02-09
> **tom.swartz07 said:**
> Youre right- you have the old version of grub.
 
 See my last post- it seems you simply forgot to uncomment the hidden menu entry
I changed it to:
 ## hiddenmenu
 # Hides the menu by default (press ESC to see the menu)
 hiddenmenu
 
 After that, I ran sudo grub-update, restarted, and it didn't show the menu.
 By the way, how does the "hiddenmenu" option work? I assumed it would hide the menu if I left it uncommented, not the other way around.

> **zeroseven0183 said:**
> Did you upgrade from 9.04 (or earlier)? It seems that you're still using the Legacy boot loader (that is, Grub 0.97). Anyway, here's how you can upgrade your Grub: open a Terminal and type

```
sudo apt-get install grub-pc
```then follow the instructions in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

This is a clean 9.10 install.
I'm still confused anyway, because when I held shift while booting, the menu appeared and it said GRUB 1.97 beta 4 (which means GRUB2 afaik). And I think holding shift only works with GRUB2, GRUB1 required to hold ESC.
This, and the fact that GRUB seems to be ignoring the menu.lst file, leads me to think Ubuntu is booting with GRUB2. But for some reason, when I'm already on Ubuntu, every command seems to indicate I have GRUB1...

---

### Post by tom.swartz07 on 2010-02-09
> **Vohr said:**
> I changed it to:
 ## hiddenmenu
 # Hides the menu by default (press ESC to see the menu)
 hiddenmenu
 
 After that, I ran sudo grub-update, restarted, and it didn't show the menu.
 By the way, how does the "hiddenmenu" option work? I assumed it would hide the menu if I left it uncommented, not the other way around.



This is a clean 9.10 install.
I'm still confused anyway, because when I held shift while booting, the menu appeared and it said GRUB 1.97 beta 4 (which means GRUB2 afaik). And I think holding shift only works with GRUB2, GRUB1 required to hold ESC.
This, and the fact that GRUB seems to be ignoring the menu.lst file, leads me to think Ubuntu is booting with GRUB2. But for some reason, when I'm already on Ubuntu, every command seems to indicate I have GRUB1...

[IMG]http://www.fallen-legion.eu/news/data/upimages/DoubleFacePalm.jpg[/IMG]

Youre right. I dont know what I was thinking.



Try editing the files in /etc/default/grub rather than /boot/grub/menu.lst

Dont forget to update-grub!

---

### Post by Vohr on 2010-02-09
I edited /etc/default/grub, but update-grub doesn't even check this file (and it updates menu.lst, not grub.cfg) >.<

I think I'll just reinstall GRUB :P

---

### Post by lidex on 2010-02-09
Interesting. Legacy grub is simply called "grub" and grub2 package is "grub-pc". Scroll down to "Installation" section on this page:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Do you have both installed?

---

### Post by zeroseven0183 on 2010-02-09
I hope Mr. Vohr was able to sort this out yesterday. I fell asleep waiting for the reply. Sorry.... :oops:

---

### Post by Vohr on 2010-02-10
Sorry I wasn't able to post earlier, I had high fever yesterday :(
I upgraded from GRUB to GRUB2 and now everything works as expected.

Thank you!! :)

---

### Post by zeroseven0183 on 2010-02-11
> **Vohr said:**
> Sorry I wasn't able to post earlier, I had high fever yesterday :(
I upgraded from GRUB to GRUB2 and now everything works as expected.

Thank you!! :)

That's good to know. Anyway, can you do us a favor? Please mark this thread as SOLVED and don't mind the fever (it'll leave) ;) Keep yourself healthy.

Have fun with Ubuntu!

---

