---
title: "Problems after system update"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by jhar64 on 2010-12-05
Just installed ubuntu 10.10 and after the install the system prompted for me to do system updates so i did and then prompted for a restart. Upon rebooting instead of taking me to the regular graphical ubuntu login it takes me to a command line type screen asking for username and password. I put in the credentials and then just sits there and waits for commands. I dont really even know what that screen is and dont know how to get out of it and back to the regular ubuntu desktop. Please help.

---

### Post by wilee-nilee on 2010-12-05
After logging in try startx, otherwise do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

I would rather see the bootscript first though.

---

### Post by jhar64 on 2010-12-05
So in the command only type 'startx' ??  is anything else required before or after?  So this is probably a stupid question.

---

### Post by wilee-nilee on 2010-12-05
> **jhar64 said:**
> So in the command only type 'startx' ??  is anything else required before or after?  So this is probably a stupid question.

So in a perfect world as you describe getting to a command line login after logging in starx should start the desktop up.

Did you perchance install startup manager at some point?

Really the script will save us from this questions stuff and get to the heart of the matter most likely.

---

### Post by sikander3786 on 2010-12-05
And it would also be handy to know about your graphics card in addition to boot script output. Which graphics card is there and did you install any proprietary drivers?

```
lspci | grep VGA
```

---

### Post by Messyhair42 on 2010-12-05
I am adding that I have had a similar problem with login after an update. I'm using Lucid.
after the update i get a Gnome screen, with the default background and a login prompt (I use neither for normal operation) and the prompt does not accept my password. I tried running dpkg from recovery mode. and netroot doesn't help me.
my next course of action would be to setup a hardwire network connection and try netroot and ```
sudo apt-get install gnome-panel
``` because i believe it's a problem with Gnome itself and not the kernel or other OS functions

---

