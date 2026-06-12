---
title: "'Will remove  desktop' as well"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by MG&amp;TL on 2011-07-14
Currently I'm using lubuntu, but I've had this problem on xubuntu and ubuntu too.

When I use the software centre, (this is happening less often now, but I still use it.) and I remove what I consider to be an unnecessary package that came pre-installed, like language support-it's not just language support that does this, though. It pops up with a window that says it needs to 'remove the l/x/ubuntu desktop environments' in order to remove the package.

this does not sound good. 

a) what happens if I do remove the desktop environment?

b) what can I do to get around this?

thanks everyone. :D

---

### Post by Quackers on 2011-07-14
I would leave the package as it was. It probably doesn't use much space anyway.

---

### Post by DannyDroid on 2011-07-14
lubuntu-desktop for example is just a collection of applications and when removing a application is it no longer a complete package. 

It should have no ill effect what-so-ever.

lubuntu-desktop is manily used as a way to install lubuntu from another "version" of ubuntu such as ubuntu itself or kubuntu.

Someone, please correct me if I am wrong.

---

### Post by MG&amp;TL on 2011-07-14
I would, too, I was partly annoyed and partly interested as to why deleting a language pack or game kills the whole desktop system? Ubuntu is a considerable improvement on MS, but it isn't half fragile at times-which I guess is half the appeal, if there wasn't bugs, we would be bored. :D

---

### Post by Quackers on 2011-07-14
Well there is that, I suppose :-)

---

### Post by DannyDroid on 2011-07-14
I've removed the games packages as well as some other things from Lubuntu and I can update everything fine (I did so this morning).

It's just no longer a complete package.

---

### Post by MG&amp;TL on 2011-07-14
Okay, will try that. Carefully. I don't suppose anyone knows how to restore the desktop if it goes bad? No disrespect, DannyDroid, but you don't sound too sure...:p great to have help though.

EDIT: right, here we go then!

---

### Post by Quackers on 2011-07-14
From a cli login sudo apt-get install (l)ubuntu-desktop might do it.

---

### Post by DannyDroid on 2011-07-14
I'm not, I'm still quite young in the Linux world, well, more like I don't feel as home as I do on a Windows machine, I know my way around them like the back of my hand.

To restore:
sudo apt-get lubuntu-desktop

Change lubuntu to your version (such as ubuntu, kubuntu, etc)

I did this all (removing and playing with packages) last night after installing Lubuntu. I promise you it wont break if you are just remove unused applications.

---

### Post by MG&amp;TL on 2011-07-14
One load of **** removed. thanks guys :D

---

### Post by bodhi.zazen on 2011-07-14
> **DannyDroid said:**
> lubuntu-desktop for example is just a collection of applications and when removing a application is it no longer a complete package. 

*-desktop is a so called meta package

```
This package depends on all of the packages in the Ubuntu desktop system  It is also used to help ensure proper upgrades, so it is recommended that it not be removed.
```

[http://packages.ubuntu.com/natty/ubuntu-desktop](http://packages.ubuntu.com/natty/ubuntu-desktop)

> It should have no ill effect what-so-ever.

Despite what the package page says, it can be removed, but you should not do so unless you know what you are doing or wanting to learn. It can always be re-installed.

> lubuntu-desktop is manily used as a way to install lubuntu from another "version" of ubuntu such as ubuntu itself or kubuntu.

Someone, please correct me if I am wrong.

In general, it is easier to either:

1. Accept the cruft and stay with a default install.

2. Perform a minimal install and add only the applications you need.

then to perform a standard *-desktop install and then start to remove things ;)

---

### Post by MG&amp;TL on 2011-07-15
Thanks for the clarification bodhi. Does that mean I can't upgrade if I've removed these packages or is it just easier for the system?

---

### Post by bodhi.zazen on 2011-07-15
> **MG&TL said:**
> Thanks for the clarification bodhi. Does that mean I can't upgrade if I've removed these packages or is it just easier for the system?

Removing the -desktop package(s) is unlikely to cause a problem. On one or two  occasions I have seen minor problems (basically the person who removed it removed more then they bargained for and decided they did not want such a minimal system). In the event you have a problem you would simply re-install it.

My general advice is to start with a minimal system and build up, generally easier.

My second piece of advice is that it is sometimes easier to get a minimal installation with alternate distros, such as Arch or Debian or Fedora, as package per package Ubuntu tends to list more dependencies. The advantage of Ubuntu is that it will be easier to build such a system as you will more likely pull in all the dependencies you need, the disadvantage is an Ubuntu system will often be sightly larger.

If you start with a default -desktop installation, and want to start removing things, you really need to understand what you are removing and review the package list. You need to make sure that that "cool" list of 100 packages to be removed does not include some critical package (usually apt-get will warn you if this is the case). You will run into problems if you just start removing packages you do not understand.

---

### Post by MG&amp;TL on 2011-07-15
I'm not looking to cut THAT much space...nope, ubuntu is fine for me currently, I'm just removing things that irritate me. I like having a clean system.

---

### Post by bodhi.zazen on 2011-07-15
> **MG&TL said:**
> I'm just removing things that irritate me. I like having a clean system.

Sounds reasonable to me. When you are ready, try a minimal install + lightweight gnome or other window manager. Sort of depends on how many irritations you have with the default desktop.

---

### Post by MG&amp;TL on 2011-07-15
Sounds good to me...is there instructions somewhere for a minimal install? 

Secondly, does it have a partitioning tool that's not a command-line? Because I have  a Windows partition that :
a) complains very loudly if there's a partitioning error somewhere.
b)checks the disk every time I install a new OS
c) refuses to boot if I remove the ubuntu partition

Therefore I don't want to muck it up...

Thanks for help, bodhi. :D

---

### Post by bodhi.zazen on 2011-07-15
> **MG&TL said:**
> Sounds good to me...is there instructions somewhere for a minimal install? 

Secondly, does it have a partitioning tool that's not a command-line? Because I have  a Windows partition that :
a) complains very loudly if there's a partitioning error somewhere.
b)checks the disk every time I install a new OS
c) refuses to boot if I remove the ubuntu partition

Therefore I don't want to muck it up...

Thanks for help, bodhi. :D

Personally when I install Ubuntu I user the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Post install you will have a command line only system, you then add yoru graphical interface , gnome rather then ubuntu-desktop, xfce rather then xubuntu-desktop, fluxbox, openbox, etc.

Then add only the apps you use.

See: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall)

There is a bit of a learning curve, and everyone has their favorite applications.

My application list generally includes vim, cream, gedit, firefox, xchat, audacious, and nitrogen. Your application list will obviously vary.

In terms of window managers I tend to use Fluxbox, openbox + tint2, and xfce.

If you want to take such a system for a test drive, I built Zenix (it is debian squeeze rather then Ubuntu, but you can take it for a spin).

[http://zenix-os.net/screenshots.html](http://zenix-os.net/screenshots.html)

After you learn to build such a system, it is fairly easy to do with most any distro.

---

### Post by MG&amp;TL on 2011-07-15
"I built Zenix"

You made...an OS? =D>[-o<

Anyways... yep, that sounds fine...I'm busy for a few days, but as soon as I get back I shall burn the cd. How do you configure the internet required to 'sudo apt-get install' things ? I've always done that graphically.

---

### Post by MG&amp;TL on 2011-07-15
Sorry, I'm pestering, but would a usb wireless converter or in-built wireless LAN do, rather than ethernet?

It's just that my home uses a HomeHub sytem with a central transmitter, and I'm not even sure if my laptop supports ethernet...

The support has been fantastic, bodhi. Will definitely have a look at your OS after ubuntu minimal, (it's just that I've 'grown up' with ubuntu)

---

### Post by DannyDroid on 2011-07-15
I learnt a lot, thank you bodhi :D .

---

### Post by bodhi.zazen on 2011-07-15
> **MG&TL said:**
> Sorry, I'm pestering, but would a usb wireless converter or in-built wireless LAN do, rather than ethernet?

It's just that my home uses a HomeHub sytem with a central transmitter, and I'm not even sure if my laptop supports ethernet...

The support has been fantastic, bodhi. Will definitely have a look at your OS after ubuntu minimal, (it's just that I've 'grown up' with ubuntu)

Should work, did you need to do anything to get your wireless working in the first place ?

> **DannyDroid said:**
> I learnt a lot, thank you bodhi :D .

You are most welcome.

---

### Post by MG&amp;TL on 2011-07-15
On ubuntu 10.04, it was dodgy and sometimes dropped out, but on any previous releases I've tried, it's been fine. The good people at canonical have obviously been fiddling with their wireless drivers. :)

---

