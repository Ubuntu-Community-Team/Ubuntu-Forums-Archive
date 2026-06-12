---
title: "Suddenly booting into Grub, how do I return to direct boot?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by watchpocket on 2010-02-01
I'm booting into the Grub menu suddenly.  

(I did have some problems earilier that caused this, but I don't think I need to be doing it now.)

I don't dual boot or anything, and would prefer to go back to booting directly into Ubuntu.  How do I do that?

---

### Post by Sealbhach on 2010-02-01
Hi, if you're using Ubuntu 9.10 then you can edit the Grub config file to change the Grub Timeout to zero, which means the grub menu will not be displayed. To do this the command is:

```
gksudo gedit /etc/default/grub
```

Change this line so it looks like:

```
GRUB_TIMEOUT=0
```

Then to update the Grub config file run:

```
sudo update-grub
```

.

---

### Post by watchpocket on 2010-02-01
Thanks a lot for your response -- I'd never have known to look in /etc/default/grub.

GRUB_TIMEOUT  was set to ="10", so   I changed it to "0" and ran the update command as per your post.

However, when I re-started, I still got the grub menu, strangely enough. Here's my grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by psavva on 2010-02-01
> **watchpocket said:**
> Thanks a lot for your response -- I'd never have known to look in /etc/default/grub.

GRUB_TIMEOUT  was set to ="10", so   I changed it to "0" and ran the update command as per your post.

However, when I re-started, I still got the grub menu, strangely enough. Here's my grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

I think the problem is the QUOTES ""

Try remove them.
From
```
GRUB_TIMEOUT=**"**0**"**
```

To

```
GRUB_TIMEOUT=0
```

Remember to run
```
sudo update-grub
``` 
after you have made the change

---

### Post by watchpocket on 2010-02-01
> **psavva said:**
> I think the problem is the QUOTES 

Quotes removed, same problem.  I get the grub menu.  Very strange.

And I did run update-grub.

I'd've thought that would fix it.

---

### Post by watchpocket on 2010-02-01
Any ideas out there?

---

### Post by drs305 on 2010-02-01
> **watchpocket said:**
> Any ideas out there?

If Grub 2 detects a problem it will display the menu. 

Before editing the file, you might want to try to create a new "grubenv" file to clear any indicators and reboot to see if this corrects things:
```
sudo grub-editenv /boot/grub/editenv create
```

You can disable this feature by editing and disabling the "recordfail" actions in  */etc/grub.d/00_header*
```
gksudo gedit +138 /etc/grub.d/00_header
```

Find the section around line 138 and comment out the recordfail section.

From:
> if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi

To:
> [COLOR="DarkRed"]**#**[/COLOR]if [ \${recordfail} = 1 ]; then
[COLOR="DarkRed"]**#**[/COLOR]  set timeout=-1
[COLOR="DarkRed"]**#**[/COLOR]else
  set timeout=${GRUB_TIMEOUT}
[COLOR="DarkRed"]**#**[/COLOR]fi


Run "sudo update-grub" after making any changes.

---

### Post by watchpocket on 2010-02-01
...

---

### Post by watchpocket on 2010-02-01
> **drs305 said:**
> Before editing the file, you might want to try to create a new "grubenv" file to clear any indicators and reboot to see if this corrects things

I'll do that when I get home & thanks loads for the advice!

---

### Post by watchpocket on 2010-02-03
> **drs305 said:**
>  . . . Before editing the file, you might want to try to create a new "grubenv" file to clear any indicators and reboot to see if this corrects things:
```
sudo grub-editenv /boot/grub/editenv create
```

Just to confirm: Do you mean: ```
sudo grub-editenv /boot/grub/grubenv create
```And **not** /boot/grub/**editenv**  as in your code example?

---

### Post by drs305 on 2010-02-03
```
sudo grub-editenv /boot/grub/grubenv create
```
Yes, that is what I meant.

---

### Post by watchpocket on 2010-02-03
Wow, created the new grubenv file and that appears to have fixed the problem (or at least* this* problem). 

 I'm booting directly into karmic now instead of into the Grub menu.  I also no longer get a long nasty beep at logoff.

 Thanks a whole lot for the tip.  I still need to read the dox on grub, which I'll do today.

---

### Post by watchpocket on 2010-02-05
> **watchpocket said:**
> I'm booting directly into karmic now instead of into the Grub menu.

Actually, that only happens once after making a new /boot/grub/grubenv file.  Then I go back to booting into the grub menu, until I make a new grubenv file again.  Still looking for a way to regularly boot without first getting landed in the grub menu and having to hit enter.

---

### Post by watchpocket on 2010-02-05
I no sooner wrote that than I've now booted 4 times directly into karmic.  Weird, but good.

---

