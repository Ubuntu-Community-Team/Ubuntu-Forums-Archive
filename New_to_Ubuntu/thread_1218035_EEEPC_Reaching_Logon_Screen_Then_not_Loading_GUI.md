---
title: "EEEPC Reaching Logon Screen Then not Loading GUI"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by /usr/sbin on 2009-07-20
I have recently installed UNR onto my Asus EEEPC 901, the first two times that i used UNR it worked perfectly booting up quickly and working correctly, now it reaches the Logon screen and i input my username and password but the it does not load the gui and i cannot access anything.

Thanks Adam

---

### Post by yeats on 2009-07-20
Sounds like an x-server problem...  Have you changed anything about your xorg.conf file lately?

You can boot into "recovery mode" (forget if that's the exact wording) from the GRUB menu and reconfigure your x-server...

---

### Post by /usr/sbin on 2009-07-20
I havent touched a sngle config file, all i have used the netbook for is to check that it worked. I have got to the recovery mode but now it has given me a list of options:

resume normal boot
try to make free space
repair broken packages
file system check
update grub bootloader
drop to root shell prompt with networking
drop to root shell prompt
try to auto repair graphic problems

which do i choose?

---

### Post by nothingspecial on 2009-07-20
try to auto repair graphic problems

---

### Post by /usr/sbin on 2009-07-20
I have selected that option and a black screen with some writing pooped up. Now i am back at that menu now. Should I continue with normal boot now?

---

### Post by nothingspecial on 2009-07-20
Yup

---

### Post by /usr/sbin on 2009-07-20
I have just done that and it has still come up with the same problem. Should i try to boot into the terminal? Adam

---

### Post by /usr/sbin on 2009-07-20
What command do i need to run firefox and to activate the internet?

---

### Post by /usr/sbin on 2009-07-20
Is there any other way of getting the gui back or do i need to reinstall it again? Thanks Adam

---

### Post by nothingspecial on 2009-07-20
Boot into text mode and try

```
sudo /etc/init.d/gdm start
```

If that doesn`t work try

```
startx
```

---

### Post by /usr/sbin on 2009-07-20
OK, thankyou. i have tried the first method and it took me to the logon screen, but the it froze and i had to restart it.

---

### Post by /usr/sbin on 2009-07-20
I tried startx and now the gui has started again. Thanks Adam

---

### Post by /usr/sbin on 2009-07-20
Now the netbook froze and i had to restart it again. When it restarted i chose to boot from the latest kernel and the same thing has happened again. I am at a loss for what to do. I think that the best idea is to reinstall UNR

---

### Post by nothingspecial on 2009-07-20
> **/usr/sbin said:**
>  I think that the best idea is to reinstall UNR

Sometimes that`s the quickest and easiest method.

We can look further into it from the recovery mode if you like but if you just want a working netbook as soon as possible then go ahead.

---

### Post by /usr/sbin on 2009-07-20
Well i have another latop with windows on and a desktop so im not too desperate for it. But I'm not sure how else to solve it.

---

### Post by nothingspecial on 2009-07-20
Well the first thing to look at would be dmesg

Boot into recovery mode or failsafe terminal and type ```
dmesg | less
```

Does anything suspicious and nasty? It`s a very long file unfortunately.

---

### Post by /usr/sbin on 2009-07-20
When i typed it in, there was a lot of text which appeared on screen. What do you want me to do with the file? It is possible to save it to show?

Adam

---

### Post by nothingspecial on 2009-07-20
I want you to look for errors in it. It is messages from the kernel (sort of).

If you want to save it the command would be ```
dmesg > dmesg.txt
```

Which would create a file in your current directory which you could then move to a usb stick. I`m not sure if usb storage devices automount in recovery mode.

To check (after you`ve inserted the stick) type ```
mount
``` and there should be a entry such as ```
/dev/sdb1 on /media/disk
```

If that is the only usb stick you have plugged in then you should type ```
cp dmesg.txt /media/disk/
```
cp is the copy command.

Then ```
sudo umount /media/disk
```

Then the stick is safe to remove and you can plug it into your other box.

I`d rather not have to read the whole file, it`s errors we`re interested in.

Also bear in mind that I`m making the kids tea right now then it`ll be bath, stories etc.

And that I have no idea what`s up with your netbook I`m just trying to help you diagnose it.

Another useful place to look is in /var/log. This is where all your logs are stored. There will be a boot log and other files it might be worth looking at.

To get there type ```
cd /var/log
```

To see which logs are in there type ```
ls
```

To view a particular one use the cat command eg

```
cat boot
```

To be honest though, unless you`re interested in this sort of thing (which I am sometimes), you might be better reinstalling or waiting until a guru who knows exactly where to look and what might be wrong sees this. I`m far from an expert at this sort of thing.

(I know I have a lot of posts but that`s just coz I like helping and have needed a lot of help)

---

### Post by /usr/sbin on 2009-07-20
Thank you for your help so far. I hate to disturb you so i will try to figure this one out on my own then post what i have found out later/tomorrow.

---

### Post by /usr/sbin on 2009-07-20
Thanks, i have decided to just do a reinstall because it is simpler and requires a lot less hassle. Thank you

---

### Post by nothingspecial on 2009-07-20
> **/usr/sbin said:**
> Thank you for your help so far. I hate to disturb you so i will try to figure this one out on my own then post what i have found out later/tomorrow.

You weren`t disturbing me. Like I said I like to help, it`s just I`ve greater responsibilities than UF (jeeze they can be hard work, but I love `em to bits - I mean the kids not Ubuntu Forums). 

It`s not the done thing here to recommend a fresh install. Most problems, even yours will have a simple solution. The hard part is usually finding the solution. However, if you have a relatively new install that is completely borked, as yours seems to be (and you have no important data or config that would be difficult to replicate), then it can be the better option. Hopefully though, you`ve learned a little bit in the process.

I have a broken acer aspire one that I picked up for free that I use for two purposes. Watching tv/movies in bed, but more than that, breaking it so that I can try to fix it. I only mention this because you seem to have an interest in diagnosing and fixing a problem. It`s the best way to learn linux in my opinion.

You can see it [[COLOR="Magenta"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1210182&page=2") in all it`s glory.

Happy `buntuing :D

---

