---
title: "Extra long boot up time? What's going on?"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2011-03-03
I am running Ubuntu 10.10.  After my laptop starts and Ubuntu starts to boot, I just have a black screen with a blinking icon in the top left (I think it's a "_" but it might be a "/"), and this stays like this for about 1 or 2 minutes, and then Ubuntu loads normally.  There is nothing else displayed during this time.  It has been doing this for a few days consistently now, and I am not sure what is causing it or how it started.  

Any ideas on what is going on or how to further diagnose this issue?

Thank you.

---

### Post by maqtanim on 2011-03-03
How much is your memory/RAM? Did you use wubi to install Ubuntu? Sometimes wubi setup has some issues like that.

---

### Post by x C0MMAND0 x on 2011-03-03
4gb; I'm running 64bit OS.  Ubuntu is installed on it's own partition and I use Grub; no Wubi for me.

---

### Post by oldos2er on 2011-03-03
Try booting into text mode, perhaps you'll see something that points to the problem. Run ```
gksu gedit /etc/default/grub
``` and change the line 

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"

to 

GRUB_CMDLINE_LINUX_DEFAULT="text"

Then run **sudo update-grub**. Reboot. When you see login:, login with your username and password as usual. Type **startx** to start your GUI. To change back to a graphical login, reverse the changes to /etc/default/grub and rerun **sudo update-grub**.

---

### Post by PunkLV on 2011-03-03
Would it not be easier to edit the boot string directrly in grub in OS select menu? Editing it will not change the grub.cfg

Press E in grub menu on boot
Replace 
linux=/path uuid=00000 slash ro quiet
with
linux=/path uuid=00000 **no**splash ro quiet
Press F10 to boot this. One-time override of grub.cfg.

---

### Post by x C0MMAND0 x on 2011-04-07
When booting into text mode, I am getting 2 errors so far.

The first is as follows:

```
chown: invalid user: 'dnsmasq:nogroup'      [fail]
```

The second is I had Crashplan installed, and I used the uninstaller, but I don't think it uninstalled completely and the boot seems to be hanging at 

```
/etc/rc2.d/S99crashplan CrashplanEngine not found
```

and it doesn't go any further.  I tried booting into recovery console but that didn't seem to want to boot either. I found a [link to completely remove]("http://mikebeach.org/2010/07/how-to-uninstall-crashplan/") all of the Crashplan crap, but I have to be able to actually boot into my system first.

I am thinking of just doing a backup and complete new install.

---

### Post by x C0MMAND0 x on 2011-04-07
*Update*

I was able to get into recovery and remove all of the Crashplan stuff.

Now, I have the following 2 errors and I know where it is freezing on boot.

Error 1: ```
chown: invalid user: 'dnsmasq:nogroup'   [fail]
```

Error 2: ```
* Starting VirtualBox kernel module...  [fail]
```

Here is where it is freezing.  I currently see this:
```

* Checking battery state...   [OK]

_

```

And the underscore is just blinking....

---

### Post by x C0MMAND0 x on 2011-04-10
bump

---

### Post by Grendel336 on 2011-04-11
> **x C0MMAND0 x said:**
> I am running Ubuntu 10.10.  After my laptop starts and Ubuntu starts to boot, I just have a black screen with a blinking icon in the top left (I think it's a "_" but it might be a "/"), and this stays like this for about 1 or 2 minutes, and then Ubuntu loads normally.  There is nothing else displayed during this time.  It has been doing this for a few days consistently now, and I am not sure what is causing it or how it started.  

Any ideas on what is going on or how to further diagnose this issue?

Thank you.

I am getting this "_" on boot up as well. 

I just installed the beta 11.04 as a dual boot to Mint 9 and when I boot to Natty I get that black screen with a "_" in top left corner of screen for what seems like a very long time.

---

### Post by x C0MMAND0 x on 2011-04-11
Here are some bootup issues from the last time (see pictures).  I am booting into text mode, then logging in, then typing "startx".  Sometimes it boots quickly, sometimes it takes minutes.  I can't seem to find a pattern.

Do these images tell anything?

---

### Post by oldos2er on 2011-04-11
Check this thread for the DRDY error: [http://ubuntuforums.org/showthread.php?t=1034762](http://ubuntuforums.org/showthread.php?t=1034762)

---

