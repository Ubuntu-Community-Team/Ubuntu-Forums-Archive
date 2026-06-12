---
title: "Ubuntu vs. UNR ?"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by kevindubrow on 2009-04-22
I am thoroughly confused. What is the difference between Regular Ubuntu and Ubuntu Netbook Remix?

I ordered an HP Mini 1000Mie edition (its a netbook), but I want to get rid of HP's Ubuntu because it seems very limited. I'm trying to figure out what I should use to replace MIE though. Any suggestions? Thanks!

---

### Post by snowpine on 2009-04-22
Ubuntu NBR = Ubuntu with the "netbook interface" designed for 7-10" screens
Ubuntu MID = Designed for small touchscreen devices like pda's and cell phones

(edit) To answer your question, I would probably put regular or NBR on the HP, depending on whether or not I liked the netbook interface (I personally prefer the regular desktop).

---

### Post by kevindubrow on 2009-04-22
Ok, so is the Ubuntu Netbook Remix just regular Ubuntu with a different user interface?

I guess what I want to know is if I lose any functionality with UNR and what UNR does to improve Ubuntu for netbooks.

(to your edit, haha) Yeah, I'll probably end up just using the regular version of Ubuntu unless the UNR does something to improve performance or battery life...or something similar.

---

### Post by snowpine on 2009-04-22
Yes, in fact if you wanted to, you can fully convert regular Ubuntu to NBR, and vice versa, by adding/removing packages. They are completely interchangeable. The key is the netbook-launcher package.

Here is a full list of the packages in each so you can compare:
[http://packages.ubuntu.com/jaunty/ubuntu-desktop](http://packages.ubuntu.com/jaunty/ubuntu-desktop)
[http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix](http://packages.ubuntu.com/jaunty/ubuntu-netbook-remix)

Ubuntu MID is not interchangeable with the other two because it uses a different kernel. I tried it on my Dell Mini 9 for about 3 minutes; it really is designed for a different type of device.

---

### Post by mlentink on 2009-04-22
Please be also aware that the HP MIE version was compiled specifically for the ATOM processor in your HP mini. 
AFAIK, UNR is not.

---

### Post by kevindubrow on 2009-04-22
Thanks for the info and links!

Do you know what problems I'll run into because Ubuntu isn't compiled for my processor exactly?

---

### Post by nwadams on 2009-04-22
no problems, infact better software support. However you may lose a small amount of battery life due to a less efficient kernel.

---

### Post by kevindubrow on 2009-04-22
Awesome! And I can deal with the lower battery life...I upgraded to the 6 cell battery.

I'm just kinda worried now... I have been noticing a lot of threads about how 8.10 isn't working too well on the Mini 1000. Hah, hopefully 9.04 works better.

---

### Post by nwadams on 2009-04-22
you can always get the battery life back with some tweaking of things. 
I haven't noticed much about the HP mini 1000 but post your problems on the forums and ask questions. I'm sure we can solve most if not all of the problems with it.

---

### Post by kevindubrow on 2009-04-22
Yeah, I'm sure. The forums have never failed me yet! Thanks again!

---

### Post by gigoguy on 2009-04-22
Slightly off topic, but does anyone know where to find the compatibility list for UNR?  The press release mentioned that UNR had been fully tested for several popular netbooks, but I haven't been able to find a full list.

---

### Post by bluester on 2009-04-23
> **gigoguy said:**
> Slightly off topic, but does anyone know where to find the compatibility list for UNR?  The press release mentioned that UNR had been fully tested for several popular netbooks, but I haven't been able to find a full list.

You can find information here:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

The jaunty-netbook-remix images can be found here:
[http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-netbook-remix/daily-live/current/)

Based on the information I read - there is a desktop switcher applet which allows users to switch desktop modes (ubuntu-netbook-remix or classic ubuntu)

Additionally I read somewhere, the latest version (dated April 20, 2009) has support for the Atom processor. The April 20, 2009 build is based on Jaunty (9.04).

Let us know how it works for you. :popcorn:

---

### Post by kevindubrow on 2009-04-23
Ok, I'm going to try out UNR. I was reading about it though and it says somewhere that it works for up to 10 inch screens...mine is a 10.1. Will I have any trouble?

Also, I want all of the Ubuntu Packages also...should I install Ubuntu first and then put UNR on top of it or the other way around?

And one last one, am I able to turn off the UNR desktop at will or do I have to unistall it if I don't want it on temporarily?

Thanks so much! My netbook is in the mail!

---

### Post by snowpine on 2009-04-23
> **kevindubrow said:**
> Ok, I'm going to try out UNR. I was reading about it though and it says somewhere that it works for up to 10 inch screens...mine is a 10.1. Will I have any trouble?

Also, I want all of the Ubuntu Packages also...should I install Ubuntu first and then put UNR on top of it or the other way around?

And one last one, am I able to turn off the UNR desktop at will or do I have to unistall it if I don't want it on temporarily?

Thanks so much! My netbook is in the mail!

1) 10.1" will be perfect... I tried NBR once (by accident) on a 20" monitor. It works fine on larger monitors, it's just that the icons are cartoonishly huge. :)

2) I recommend installing NBR (rather than regular, then putting NBR on top). It is a fully functional OS with most of the applications you'd want. Whatever is missing, you can easily install through the usual methods.

3) Yes, if you go into System->Preferences, there's something like User Interface Switcher (I forget the exact name) that switches between NBR and a "classic" Gnome desktop. You could even have NBR for one user and classic Gnome for another if you wanted.

Like I said before, there is no limitation on an Ubuntu NBR install. You can install anything you can install on a regular Ubuntu install. (The only exception I am aware of is that you can't use Compiz and the NBR launcher at the same time.)

---

### Post by ddrichardson on 2009-04-23
> **gigoguy said:**
> Slightly off topic, but does anyone know where to find the compatibility list for UNR?  The press release mentioned that UNR had been fully tested for several popular netbooks, but I haven't been able to find a full list.
The [release announcement]("http://www.ubuntu.com/news/ubuntu-9.04-unr") for 9.04 says:

> Ubuntu 9.04 Netbook Remix has been fully tested for use on a range of netbook models including:  
 
[LIST]
[*] Acer Aspire     One
[*] Asus eee PC     1000
[*] Dell Mini 9
[/LIST]


---

### Post by kevindubrow on 2009-04-23
Thanks so much for the help! I'm going to just install UNR for the time being and see how it works for me. 

Again, thanks a lot! The people on this site are always so helpful.

---

