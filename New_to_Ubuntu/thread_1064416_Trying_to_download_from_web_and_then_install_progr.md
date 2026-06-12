---
title: "Trying to download from web and then install program"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Coinneach on 2009-02-08
First off, I am new to Linux which makes me new to Ubuntu 8.10; I need the bash command to install a lightscribe program called LaCie LightScribe Labeler. 

the link is: [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm)

I think it goes something like:
sudo wget [http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm](http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm) install

but that is all I know and would appreciate any help in installing program so I can use the darn thing

Thanks

Coinneach

---

### Post by MarblePanther on 2009-02-08
Ubuntu (unlike Redhat, Mandriva, etc...) does not use .rpm package format.  Ubuntu uses the .deb format.

You could use a program called alien to convert .rpm to .deb if you wish to use it--but they have a .deb package for Ubuntu on their site, so use that:

simply go here and download the .deb to your desktop.  then click on it and install.

[http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372](http://www.lightscribe.com/downloadsection/linux/index.aspx?id=1372)

---

### Post by Dougie187 on 2009-02-08
Also, since you are new, any commands that you are using you can type into man to get more information about them
```
man wget
```

That will help you know what you are doing.

---

### Post by Coinneach on 2009-02-08
Thanks MarblePanther and Dougie187

checking out the link .. thanks alot

man wget is good to know, it helps alot. thanks

much appreciated

Coinneach

---

### Post by Coinneach on 2009-02-08
ok it is installed but how do you start the program lol :)

am I supposed to use this program in terminal?

---

### Post by XanderCrews on 2009-02-08
It's not necessarily a command line interface program, if that's what you mean by using it in the terminal.

The most likely locations are /usr/bin or /usr/local/bin.

You can also look it up in Synaptic, by searching for "lightscribe"
and then select properties > installed files.  Though there may be quite a few entries, confusing things a bit.

---

### Post by MarblePanther on 2009-02-08
[http://www.lacie.com/support/support_manifest.htm?id=10204](http://www.lacie.com/support/support_manifest.htm?id=10204)

[http://www.linux.com/feature/118705](http://www.linux.com/feature/118705)

[http://www.hackitlinux.com/50226711/how_to_use_your_lightscribe_cddvd_writer_on_linux.php](http://www.hackitlinux.com/50226711/how_to_use_your_lightscribe_cddvd_writer_on_linux.php)

---

### Post by Coinneach on 2009-02-08
Thanks for the support .. I have a fair bit of reading to do

Thanks again, much appreciated

Coinneach

---

### Post by MarblePanther on 2009-02-08
Hope you figure it out.

-Happy Ubuntu-ing!

---

### Post by ramjet_1953 on 2009-02-09
Hi, there!

I'm afraid you have fallen into the trap that many new players experience.

You have run off looking for an application from the Internet, and then run into problems with package conversion and getting it running, when all you needed to do was to check the Synaptic Package Manager for a package that is ready to go.

If you enable all of the repositories in Synaptic there is a huge selection.
Follow these steps:

> Navigate to SYSTEM>Administration>Synaptic Package Manager
When the window opens, click on Settings>Repositories
When the window opens, put a tick in all the boxes, except Source Code.
Close the window.
Now, click on the Search button and type in 4l
You will now be able to install a LightScribe labeler for Linux


Regards,
Roger :D

---

### Post by Coinneach on 2009-02-09
Roger

I did look at the repositories in Synaptic, there was no lightscribe, well there may of been but when I searched the word lightscribe there was nothing. 4l did not show up either after I did what you said to do. That was one of the first things I learned actually, Synaptic and add/remove. 

appreciate the feedback Roger, much appreciated ;)

Coinneach

---

### Post by Coinneach on 2009-02-09
After installing, here are the included files:

./
etc/
etc/lightscribe.rc
usr/
usr/lib/
usr/lib/liblightscribe.so.1
usr/lib/lightscribe/
usr/lib/lightscribe/elcu.sh
usr/lib/lightscribe/updates/
usr/lib/lightscribe/updates/fallback.sh
usr/share/
usr/share/doc/
usr/share/doc/lightscribeLicense.rtf
usr/lib/liblightscribe.so


Now that it is installed, can someone tell me how to start the lightscribe program, pleaseeeeeee

Thanks
Coinneach

---

### Post by XanderCrews on 2009-02-09
Looks like you have only two choices, elcu.sh and fallback.sh. My guess would be to try elcu.sh and see what happens.

XC

BTW did you download both packages?

Looks like you need both the Lightscribe System Software (LSS) and application software that uses the LSS.

---

### Post by Coinneach on 2009-02-09
Ok I got it download and burn but it is a LightScribe Simple Labeler, I want to do photos on discs and this one only does text, anyone know where to find the program that does photos?

---

### Post by XanderCrews on 2009-02-09
Find out what files the second package installed.  Odds are it installed something into /usr/bin or /usr/local/bin, and will be fairly obvious.

XC

---

### Post by unplugged23 on 2009-02-09
> **Coinneach said:**
> Thanks MarblePanther and Dougie187

checking out the link .. thanks alot

man wget is good to know, it helps alot. thanks

much appreciated

Coinneach

You can type "man" any thing to get a detailed help section for the command.

---

### Post by Coinneach on 2009-02-09
Thanks unplugged23

Good to know, now I just need to learn all the commands :lolflag:

---

### Post by baracuda68 on 2009-02-10
> **Coinneach said:**
> After installing, here are the included files:

./
etc/
etc/lightscribe.rc
usr/
usr/lib/
usr/lib/liblightscribe.so.1
usr/lib/lightscribe/
usr/lib/lightscribe/elcu.sh
usr/lib/lightscribe/updates/
usr/lib/lightscribe/updates/fallback.sh
usr/share/
usr/share/doc/
usr/share/doc/lightscribeLicense.rtf
usr/lib/liblightscribe.so


Now that it is installed, can someone tell me how to start the lightscribe program, pleaseeeeeee

Thanks
Coinneach
try 
gksudo 4L-gui     in terminal.

Then you can make a menu item for it using that command .
I did...works great!:)

---

### Post by baracuda68 on 2009-02-10
But also remember that you have to have the lightscribe system software installed FIRST in order to have it work...
[http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814](http://www.lightscribe.com/downloadSection/linux/index.aspx?id=814)  ;)

---

### Post by Coinneach on 2009-02-10
Thanks baracuda68 and yes I have the lightscribe system software installed
 >   try
gksudo 4L-gui in terminal.

Then you can make a menu item for it using that command . 

tried that and got: 

kol@kol-desktop:~$ gksudo 4L-gui
kol@kol-desktop:~$ 

so now how do I go about making a menu item?  Seems a bit advanced for me but I'll write this down. 

Thanks
Coinneach

---

### Post by 3rdalbum on 2009-02-10
So you got the GUI appear when you used that command?

It's easy to create a menu item. Right-click the menu and click Edit Menus. Click in the category that you want the menu item in, and click New Item. Type a name ("Lightscriber" or something) and then put the commad in the "command" box. Close all the windows and you're done.

---

### Post by Coinneach on 2009-02-10
> **3rdalbum said:**
> So you got the GUI appear when you used that command? 

No, but I was able to create a new item under applications and found the path to LightScribe Simple Labeler.

What I want is a LightScribe program that allows pictures to be scribed into the disc.

Thanks 3rdalbum, I finally know what baracuda68 was talking about

Cheers
Coinneach

---

