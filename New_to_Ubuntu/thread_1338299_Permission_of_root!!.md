---
title: "Permission of root?!!"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by Yanno on 2009-11-26
Hi!
I found my screen brightness is too low on AC mode,so I tried to change the value in /sys/class/backlight/acpi_video0/max_brightness.I login as root and run the command "echo 14> /sys/class/backlight/acpi_video0/max_brightness",but it showed "Permission denied"!Even the owner(root) have no permission to write it?
How can I change the value by some means?thx!

---

### Post by MelDJ on 2009-11-26
you could just do it by going to system-pref-power management and adjust the brightness or add the brightness applet to your panel

---

### Post by ukripper on 2009-11-26
> **Yanno said:**
> Hi!
I found my screen brightness is too low on AC mode,so I tried to change the value in /sys/class/backlight/acpi_video0/max_brightness.I login as root and run the command "echo 14> /sys/class/backlight/acpi_video0/max_brightness",but it showed "Permission denied"!Even the owner(root) have no permission to write it?
How can I change the value by some means?thx!

Where you got this how to from? Can you post the link, need to make sure what this howto tells you is correct

---

### Post by Iowan on 2009-11-26
Depending on how you "login as root"... did you try it via:```
echo 14> /sys/class/backlight/acpi_video0/max_brightness
```

---

### Post by Mr. Devil on 2009-11-26
And here we go again .. /sys isn't *human writable*.

---

### Post by Iowan on 2009-11-26
:oops: Oops - solving symptoms instead of problems. :oops:

Even messed that up - I intended to add **sudo** to the front...

---

### Post by lhb1142 on 2009-11-26
Have you tried < sudo nautilus > and then going on from there?

( Edit: Sorry for this - I re-read your original post and I realize that you had already logged in as root.)

---

### Post by louieb on 2009-11-26
:lolflag:> **Mr. Devil said:**
> And here we go again .. /sys isn't *human writable*.

some of us have to stick a fork in the electrical outlet - before we learn our lesson!

---

### Post by ukripper on 2009-11-26
> **louieb said:**
> :lolflag:

some of us have to stick a fork in the electrical outlet - before we learn our lesson!

Yeh just like /proc. It is fun to mess things up sometimes i guess lol

---

### Post by Don1500 on 2009-11-26
> **Mr. Devil said:**
> And here we go again .. /sys isn't *human writable*.

Hay! It's my system! I wanna write to whatever I wanna write to! How come I can't write there? I log in as root all the time!

Anyone know why my hard drive is all corrupted?


	:-\"

---

### Post by bodhi.zazen on 2009-11-26
See

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by MaxIBoy on 2009-11-26
Messing with a file called "max_brightness" seems a good way to overvolt your LCD and screw up your laptop. If you can't get your max brightness up in the graphical configuration, that's probably an intentional maximum. Have you ever gotten higher brightness in another OS or something?



That being said, if you do something like 
```
sudo echo "foo" > /bar
```You will get an error like
```
bash: /bar: Permission denied
``` because it still can't create a file in /.



One way I've found to work around this is to do it this way:
```
echo "foo" | sudo tee /bar
```which will also show what is being added to the file as output.

---

### Post by falconindy on 2009-11-26
> **Don1500 said:**
> Hay! It's my system! I wanna write to whatever I wanna write to! How come I can't write there? I log in as root all the time!

Anyone know why my hard drive is all corrupted?
The issue is that, like /proc and /dev, /sys is dynamically generated on bootup and those files are maintained by the kernel. They're essentially for reference and not to be tampered with. Changing values in there can be an **excellent** way to hose something in a hurry.

---

### Post by egalvan on 2009-11-26
> **louieb said:**
> :lolflag:

Some of us have to stick a fork in the electrical outlet - before we learn our lesson!


zaap!!

+1
+1
+1
+1

---

### Post by egalvan on 2009-11-26
To the Original Poster

Please be aware that we are NOT laughing AT YOU...

We are laughing at OURSELVES, and hoping that you will see in the humor some lesson to be learned. :)

There is a  VERY high percentage of us that have borked our systems by "messing" around with things that we should have left alone.
Such as /sys   :)

But it IS a learning experience.

So Laugh With Us.

And Learn a Little

---

### Post by Don1500 on 2009-11-26
[sarcasim] I NEVER messed up my system but futzing around.[/sarcasim]

But it is a training moment. 

I will tell you that eventually you will get the system you thought you would have, stable, sound, video, graphics, server, everything. And when you get it you will know why you got it, not just a box off the shelf.

---

### Post by Mr. Devil on 2009-11-26
> **Don1500 said:**
> [sarcasim] I NEVER messed up my system but futzing around.[/sarcasim]

But it is a training moment.

[COLOR=Gray][ not to you personally .. just a general view ][/COLOR]
That's one of the things I simply can't afford to believe. You can't use Linux and don't mess anything up at all :D

---

### Post by lhb1142 on 2009-11-26
> **Mr. Devil said:**
> [COLOR=Gray][ not to you personally .. just a general view ][/COLOR]
That's one of the things I simply can't afford to believe. You can't use Linux and don't mess anything up at all :D

You said it!! I have lost count as to how many times I have had to do a complete fresh re-installation of Ubuntu because of something I "tried." But it really is a learning experience and, so far at least, I have never made the same mistake TWICE!

At least effecting a fresh re-installation is easy especially if you have, as I do, a written "cheat sheet" you can follow (I learned that it would be good to have that after about the fifth or sixth time I had to re-install and each time I couldn't remember what I had installed previously).

Ain't computers FUN?!? ):P

---

### Post by bodhi.zazen on 2009-11-26
> **MaxIBoy said:**
> Messing with a file called "max_brightness" seems a good way to overvolt your LCD and screw up your laptop. If you can't get your max brightness up in the graphical configuration, that's probably an intentional maximum. Have you ever gotten higher brightness in another OS or something?



That being said, if you do something like 
```
sudo echo "foo" > /bar
```You will get an error like
```
bash: /bar: Permission denied
``` because it still can't create a file in /.



One way I've found to work around this is to do it this way:
```
echo "foo" | sudo tee /bar
```which will also show what is being added to the file as output.

with complex commands with pipes and redirects, use 

```
sudo bash -c "command1 | command2 | yet_annother_command > foo.txt"
```

---

### Post by Don1500 on 2009-11-26
> **lhb1142 said:**
> You said it!! I have lost count as to how many times I have had to do a complete fresh re-installation of Ubuntu because of something I "tried." But it really is a learning experience and, so far at least, I have never made the same mistake TWICE!

At least effecting a fresh re-installation is easy especially if you have, as I do, a written "cheat sheet" you can follow (I learned that it would be good to have that after about the fifth or sixth time I had to re-install and each time I couldn't remember what I had installed previously).

Ain't computers FUN?!? ):P

When I go sailing if I don't dump it once in a while I know I ain't pushing as hard as I can. You can't do your best if you don't know your limit!

---

### Post by Yanno on 2009-11-27
I've tried before.But it 's still too low after making it to the highest level.

---

### Post by Yanno on 2009-11-27
I got it from a link,but I'm afraid that you won't  understand that ,it isn't English!I just wanna have a try whether this howto will help.

---

### Post by Yanno on 2009-11-27
I've tried...
I login as root by running "sudo -s -H" then I typed the code you showed above.

---

### Post by Yanno on 2009-11-27
> **egalvan said:**
> To the Original Poster

Please be aware that we are NOT laughing AT YOU...

We are laughing at OURSELVES, and hoping that you will see in the humor some lesson to be learned. :)

There is a  VERY high percentage of us that have borked our systems by "messing" around with things that we should have left alone.
Such as /sys   :)

But it IS a learning experience.

So Laugh With Us.

And Learn a Little


Thx!I love this forum!!!!

---

### Post by Yanno on 2009-11-27
The brightness is much higher in 9.04,maybe Karmic is a bit buggy in this...

---

### Post by MaxIBoy on 2009-11-27
Try filing a bug report in ACPI (which is as closely-related a package as I can think of.) If your monitor isn't as bright as it used to be that's a bug.
[https://bugs.launchpad.net/ubuntu/+source/acpi-support](https://bugs.launchpad.net/ubuntu/+source/acpi-support)

---

