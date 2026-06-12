---
title: "Newbie Trying to Configure Display with Xorg"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by bluetortilla on 2011-06-13
Hi. I'm sprout Newbie. I'm having display problems with an Intel graphics chip and was told in a previous thread that I'd need to configure it manually with xorg. That thread died out though (nothing for 5 days) and I'm stuck with the following commands that do nothing:

I've tried to start at Xorg Wiki, but I'm stuck at the commands. What  does the # sign mean? I can't get any response in Terminal:

planet@Planet2:~$ # pacman -Syu xorg-server 
planet@Planet2:~$ # pacman -Ss xf86-video
planet@Planet2:~$ 

If I could get the video command to work I could go on to the next step in the xorg wiki.

Thanks!

---

### Post by nothingspecial on 2011-06-13
I suspect the # from the instructions you are using is the root prompt.

As you are doing this as a user (signified by your $ prompt) your shell is interpreting the # as a comment which tells it to ignore everything following it on the line.

Remove the # from the beginning of each command and try again.

Btw, pacman will not do anything if you are using ubuntu. Which instructions are you following?

---

### Post by DirtyPC on 2011-06-13
[http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

---

### Post by bluetortilla on 2011-06-13
> **nothingspecial said:**
> I suspect the # from the instructions you are using is the root prompt.

As you are doing this as a user (signified by your $ prompt) your shell is interpreting the # as a comment which tells it to ignore everything following it on the line.

Remove the # from the beginning of each command and try again.

I figured it was something like that but I really know nothing!

Btw, pacman will not do anything if you are using ubuntu. Which instructions are you following?

But I did get Pacman- really, the game, in my terminal.

I'm getting these conf instructions from

[https://wiki.archlinux.org/index.php/Intel](https://wiki.archlinux.org/index.php/Intel)

---

### Post by nothingspecial on 2011-06-13
> **bluetortilla said:**
> But I did get Pacman- really, the game, in my terminal.


:lolflag:

I'm guessing that didn't help with your display.

You are following instructions for arch linux, which is fine if you are using arch.

If you are using ubuntu, have a look at the link that harrylucas1 posted.

---

### Post by TeoBigusGeekus on 2011-06-13
pacman == PACkage MANager for Arch Linux - nothing to do with the game.

PS: Posting in an epic thread...

---

### Post by bluetortilla on 2011-06-13
> **harrylucas1 said:**
> [http://www.grenage.com/xorg.html](http://www.grenage.com/xorg.html)

I have a broken laptop monitor and an external. The external looks fine, the resolution is good, I just want to turn the laptop monitor off as it's eating RAM. The hotkeys don't work for that.

But Display Settings in Ubuntu doesn't recognize any monitor at all.

---

### Post by nothingspecial on 2011-06-13
Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1243541](http://ubuntuforums.org/showthread.php?t=1243541)

---

### Post by bluetortilla on 2011-06-13
> **nothingspecial said:**
> Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1243541](http://ubuntuforums.org/showthread.php?t=1243541)

Thanks. I'll try this and report back.

Linux assumes you know what you're doing. Hah! I wish...

Still, with the help of the good folk on this board, my display is actually working now and Ubuntu is booting.

---

### Post by nothingspecial on 2011-06-13
You may be able to disable your monitor in the bios, but I wouldn't go messing about with that unless, you were sure you could switch it back, just in case.

This is the funniest thread ever btw, I actually spat my coffee out laughing, when you said the game pacman started. (I didn't know it was installed by default). I bet you weren't expecting that from a xorg tutorial.

---

### Post by bluetortilla on 2011-06-13
> **nothingspecial said:**
> You may be able to disable your monitor in the bios, but I wouldn't go messing about with that unless, you were sure you could switch it back, just in case.

This is the funniest thread ever btw, I actually spat my coffee out laughing, when you said the game pacman started. (I didn't know it was installed by default). I bet you weren't expecting that from a xorg tutorial.

Hah! It's true, check it out! My first Terminal Easter egg, lol...

---

### Post by el_koraco on 2011-06-13
> **bluetortilla said:**
> But I did get Pacman- really, the game, in my terminal.


That's something to tell the grandkids about.

---

### Post by bluetortilla on 2011-06-13
> **nothingspecial said:**
> Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=1243541](http://ubuntuforums.org/showthread.php?t=1243541)

This was the result so I assume I still need a manual conf.:

planet@Planet2:~$ EXTERNAL_OUTPUT="VGA"
planet@Planet2:~$ INTERNAL_OUTPUT="LVDS"
planet@Planet2:~$ 
planet@Planet2:~$ xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
xrandr: Failed to get size of gamma for output default
planet@Planet2:~$ if [ $? -eq 0 ]; then
>     xrandr --output $INTERNAL_OUTPUT --off --output $EXTERNAL_OUTPUT --auto 
> else
>     xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
> fi
xrandr: Failed to get size of gamma for output default
warning: output LVDS not found; ignoring
warning: output VGA not found; ignoring
planet@Planet2:~$

---

### Post by nothingspecial on 2011-06-13
> **bluetortilla said:**
> This was the result so I assume I still need a manual conf.:

planet@Planet2:~$ EXTERNAL_OUTPUT="VGA"
planet@Planet2:~$ INTERNAL_OUTPUT="LVDS"
planet@Planet2:~$ 
planet@Planet2:~$ xrandr |grep $EXTERNAL_OUTPUT | grep " connected "
xrandr: Failed to get size of gamma for output default
planet@Planet2:~$ if [ $? -eq 0 ]; then
>     xrandr --output $INTERNAL_OUTPUT --off --output $EXTERNAL_OUTPUT --auto 
> else
>     xrandr --output $INTERNAL_OUTPUT --auto --output $EXTERNAL_OUTPUT --off
> fi
xrandr: Failed to get size of gamma for output default
warning: output LVDS not found; ignoring
warning: output VGA not found; ignoring
planet@Planet2:~$

You are supposed to put it in a text file, as the thread suggests.

If you've had no other help by late morning (uk time), I'll show you what to do, although to be honest....... I'm not really sure how to solve this.

I might suggest putting a new thread in the Hardware & Laptops section named something like "How to disable monitor when external monitor is plugged in" eg.


**** off topic, I am going to send you a private message, you can view it by clicking on "your notifications" which should appear just under "**Welcome, bluetortilla** at the top right of any page on ubuntu forums.

---

### Post by bluetortilla on 2011-06-14
> **nothingspecial said:**
> You are supposed to put it in a text file, as the thread suggests.

If you've had no other help by late morning (uk time), I'll show you what to do, although to be honest....... I'm not really sure how to solve this.

I might suggest putting a new thread in the Hardware & Laptops section named something like "How to disable monitor when external monitor is plugged in" eg.


Although not very aesthetic, would it do any harm to just leave the monitors as they are? There doesn't seem to be much support for the Intel graphics and the lappy is old and crusty anyway. Maybe I should try some other Ubuntu things....

At least it boots now.

Super Mario?

---

### Post by nothingspecial on 2011-06-14
> **bluetortilla said:**
> 

Super Mario?

Type 

```
sonic --the --hedgehog 
```

:lolflag:

If it works, and you don't mind it the way it is. I'd leave it. You can do more harm than good following tutorials you might not understand yet.

btw (and I've posted this before)

When I first started using Ubuntu, I did exactly the same as you.

My problem was that my sound didn't work.

I copied and pasted all sorts of stuff I didn't understand in to my terminal to no avail.

In the end, the problem was that you have to have the speakers plugged into the green hole, not the pink one. :oops:

We've all been there.

But if you do want to fix it, keep looking and try and find something relevantly recent, that applies to your hardware and Ubuntu rather than another linux.

Post back if you need any more help.

Cheers.

---

