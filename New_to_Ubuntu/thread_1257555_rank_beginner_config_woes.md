---
title: "rank beginner config woes"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Keith A on 2009-09-03
I have just installed ubuntu 9.04 and as a rank beginner, am having a number of problems.  As a long time Windows user, I don't understand any of the jargon associated with ubuntu. I have downloaded the pocket guide but it doesn't help me solve these problems:-
 
1)Cannott get any change to my monitor resolution, or aspect ratio. It looks like the system is just putting up a default format and not recognising my ACER X223 screen.
 
2)Cannot get online with my mobile wireless network (it works fine with XP)
 
3)Cannot get my printer to be recognised. It is a canon ip3000. 
(My HP flatbed scanner does work OK with ubuntu.)
 
4)Will not recognisie my Hercules sound card
 
I'm sure there will be more things to confront but if I can get these important bits going, I'll be a happy chappie for a while.
Any help appreciated, Thanks.
Keith.

---

### Post by benj1 on 2009-09-03
> 1)Cannott get any change to my monitor resolution, or aspect ratio. It looks like the system is just putting up a default format and not recognising my ACER X223 screen.
have you looked in system-->administration--> display ? that should let you change settings

 
> 2)Cannot get online with my mobile wireless network (it works fine with XP)
what kind of modem is it
 > 
3)Cannot get my printer to be recognised. It is a canon ip3000. 
(My HP flatbed scanner does work OK with ubuntu.)
 
4)Will not recognisie my Hercules sound card

cant help with those sorry

---

### Post by Keith A on 2009-09-04
> **benj1 said:**
> have you looked in system-->administration--> display ? that should let you change settings
 Thank you for your reply.
Yes I have tried the above but there is no monitor recognised in the window. It is a blank window?
 
 
what kind of modem is it
It is a HAUWEI Mobile Connect 3G modem  (USB)
 
 
cant help with those sorry
 OK, Thanks. Perhaps someone else will know.
 
I am tempted to reinstall Ubuntu but I can't find out how to uninstall the present one. Any clues?
 
Thks, Keith

---

### Post by Paqman on 2009-09-04
> **Keith A said:**
>  
I am tempted to reinstall Ubuntu but I can't find out how to uninstall the present one. Any clues?


You don't need to uninstall, just pick the "use entire disk" option during installation and it'll install the new one right over the top of the old.

Do you actually need to reinstall though?

Re your wifi: check in System > Admin > Hardware drivers for a driver that might be available. Otherwise let us know what type of card it is. There should be a sticker underneath the laptop saying what model of wifi card you've got.

Your printer doesn't seem to be officially supported by Canon on Linux. Getting it to work could be tricky, although you should definitely get it to work if you [throw some money at the problem]("http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_iP3000").

No idea about your sound card sorry. There's a [guide]("http://ubuntuforums.org/showthread.php?t=205449") in the multimedia forum of this site that might be a good place to start.

---

### Post by Sealbhach on 2009-09-04
Most of these Huawei 3G modems should work automatically in Ubuntu 9.04.

Try booting up with the modem attached (normally you wouldn't need to).

Also, check if your modem model is included in this list here:

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards](https://wiki.ubuntu.com/NetworkManager/Hardware/3G#Mobile%20Broadband%20cards)

.

---

### Post by benj1 on 2009-09-05
re your monitor problems you will probably have to add an xorg.conf file

theres a bit of a tutorial [here]("http://hardc0l2e.wordpress.com/2009/07/08/modifying-display-resplution-in-ubuntu-9-04/")

---

### Post by Keith A on 2009-09-05
> **benj1 said:**
> re your monitor problems you will probably have to add an xorg.conf file
 
theres a bit of a tutorial [here]("http://hardc0l2e.wordpress.com/2009/07/08/modifying-display-resplution-in-ubuntu-9-04/")
 Thanks for that info, I will try it next.
What does your little routine do? How can I use it to help me. Sorry, I am not very bright:(
 
Out of the blue and with nothing that I did, I suddenly found that I have an internet connection now. However, I cannot browse the www with it. It just says that it can't find the server, whether that be Google, Yahoo, or whatever. Any suggestions please?
Thanks,
Keith

---

### Post by Keith A on 2009-09-05
[quote=Keith A;7903882]Thanks for that info, I will try it next.
What does your little app do? How can I use it to help me. Sorry, I am not very bright:(
 
Oh, dear! Well, I was able to do the command line thing in your instructions but when I got to 3), I am in the dark. How do I do 3),  4) and 5) please?
Thanks.
 
Still no luck with getting on line with ubuntu.:(

---

### Post by benj1 on 2009-09-06
> **Keith A said:**
> [quote=Keith A;7903882]Thanks for that info, I will try it next.
What does your little app do? How can I use it to help me. Sorry, I am not very bright:(
 
Oh, dear! Well, I was able to do the command line thing in your instructions but when I got to 3), I am in the dark. How do I do 3),  4) and 5) please?
Thanks.
 
Still no luck with getting on line with ubuntu.:(

xorg.conf is used by ubuntu to configure certain devices on startup.
first to see if you have an xorg.conf file
```
ls /etc/X11/xorg.conf
```
it will print it if its there if not will bring up an error about there being no such file or directory.
if it is 
```
sudo nano /etc/X11/xorg.conf
```
will allow you to edit it (basically youre on to step 3 of the linked walk through), if not you need to create an xorg.conf.

if you dont have one you can just create the blank txt file and add what you need.
you can also get you current settings and copy them in from /var/log/Xorg.0.log to xorg.conf and get rid of everything _not_ inbetween
'(==) --- Start of built-in configuration ---'
and
'(==) --- End of built-in configuration ---'

so
```
sudo cp /var/log/Xorg.0.log /etc/X11/xorg.conf
```
will copy Xorg.0.log to xorg.conf
then
```
sudo nano /etc/X11/xorg.conf
```
to get rid of the stuff you dont need and add the bits that you do (step 3 of that link).

ps if youre unsure about any commands 
```
man command
```
will tell you about it 'man nano' will tell you its a text editor
'sudo' basically gives you root permission to do things such as modifying system files etc which as a normal user you arent allowed to do, (im sure google or a forum search will provide a better explanation if you need)

re your internet how do you know its working? are you successfully pinging ?
second thoughts its a dongle isn't it, i had a different dongle that i had to install a separate driver for but when launched firefox would default to browsing offline, if i changed it to browsing online it worked(file --> work offline (checkbox)), if thats the problem there is a fix on google.

---

### Post by Keith A on 2009-09-06
> **benj1 said:**
> [quote=Keith A;7904117]
 
xorg.conf is used by ubuntu to configure certain devices on startup.
first to see if you have an xorg.conf file
```
ls /etc/X11/xorg.conf
```
it will print it if its there if not will bring up an error about there being no such file or directory.
if it is 
```
sudo nano /etc/X11/xorg.conf
```
will allow you to edit it (basically youre on to step 3 of the linked walk through), if not you need to create an xorg.conf.
 
if you dont have one you can just create the blank txt file and add what you need.
you can also get you current settings and copy them in from /var/log/Xorg.0.log to xorg.conf and get rid of everything _not_ inbetween
'(==) --- Start of built-in configuration ---'
and
'(==) --- End of built-in configuration ---'
 
so
```
sudo cp /var/log/Xorg.0.log /etc/X11/xorg.conf
```
will copy Xorg.0.log to xorg.conf
then
```
sudo nano /etc/X11/xorg.conf
```
to get rid of the stuff you dont need and add the bits that you do (step 3 of that link).
 
ps if youre unsure about any commands 
```
man command
```
will tell you about it 'man nano' will tell you its a text editor
'sudo' basically gives you root permission to do things such as modifying system files etc which as a normal user you arent allowed to do, (im sure google or a forum search will provide a better explanation if you need)
 
re your internet how do you know its working? are you successfully pinging ?
second thoughts its a dongle isn't it, i had a different dongle that i had to install a separate driver for but when launched firefox would default to browsing offline, if i changed it to browsing online it worked(file --> work offline (checkbox)), if thats the problem there is a fix on google.
 
Thank you. I really appreciate your kind attention to my problems. :D
Re my internet problems:  I am connected but cannot find any servers. I cannot ping. I do not get any of the browsing details that you mention on screen.
I will now go back to ubuntu and try your suggestions above, re my display problem.
Isn't it a nuisance to have to keep switching between Windows and ubuntu? :(

---

### Post by halitech on 2009-09-06
lets get a little more info so we can work on the problems specifically instead of blindly.

can you post the output of
```
lspci
```
```
lsusb
```
```
 lshw -C network
```
```
lshw -C video
```
```
sudo ifconfig
```

---

