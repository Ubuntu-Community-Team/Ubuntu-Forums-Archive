---
title: "Unetbootin install lock me from using it again! Help"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by nooby on 2010-01-17
Edit after waiting and no feedback 
[B]
It is not solved but none seems to care about so what to do?[/B]

I used Unetbootin to install Ubuntu 9.10 and to have dualboot with win Vista but it is a frugal install which is what I want so that is as it should be 
[B]
but my problem is that that installation does lock me from using Unetbootin again to create USB for other linux distros![/B]

By lock I mean that the program only allow me to uninstall it instead of using it. 

But if I let it uninstall itself then it also uninstall the Grub it created that allowed the dual booting of ubuntu and vista. 

Sure I could another computer to make usb but that is not practical. 

this the second time this happen. Last time I accepted it to find out what would happen. It did not tell me that it would restore the mbr or maybe it was windows that restored it. Don't remember. Anyway I started all over letting it install ubuntu 9.10 instead of puppy this time and then changed the menu.lst so it also had puppy going. so now it has both Ubuntu and Puppy and Vista as a choice in the grub. 

This time I test to delete instead of uninstall the UNetbootin that lock the use of it and see if that take away the grub. 

[B]
Does any of you know what is going on? Is this a "bug" in UNetbootin? [/B]

I searched to see if I habe written about this before but could not find it. I have a poor memory.

No it did not help to delete/eraze every UNetbootin. 
Vista seems to have some kind of "note" that it once "installed" using Unetbootin 
so even if I delete all of them and download a new one and try to use it then it ask me 
Unetbootin is already installed do you want to uninstall it? 

which I don't because that would destroy the Grup once more. 

so what is the option? Next I will try to download the UNetbootin for Linux and do USB 
creating from there instead. 
[B]
but would be great if somebody help me take away the thing that makes it fail to work in Vista. [/B]

---

### Post by nooby on 2010-01-17
No it did not work from Ubuntu. One needed to know what name the USB had in Linux language and there was no way to find out for me as a newbie. 

I tested also to rename it or to change to Admin in Vista but it still says that the program is already installed and do you want me to uninstall it for you. 

I need to know why it behave that way. Is that a UNetbootin bug or a Vista bug? 

I see no reason for it to say that and to denie me to access it. 

what is causing this very odd behavior? 

**Edit one week later. **

I started all over. Installed Ubuntu9.10 with wubi. 
then installed NeoGrub with EasyBCD and there I added in frugal install some 5 different Puppy versions. Pup431JP, Macpup, Dpup, Stardust puppy, Lighthouse puppy. 

I also tested to do frugal install of a remastered Linux Mint and that actually worked well except due to being a "live user" CD version it can not save changes. But it can save documents like html and pictures and such. and bookmarks can be written manually into a html file that I have on hotmail and gmail open in the browser. 

Encouraged by that "success" I tried to do same with Super OS Ubuntu but that failed due to me not knowing how to set it up.Booting didn't find the files they expected. 

I write from SuperOS now but booted from a 2GB USB mem stick. I have tried to do it persistent by having a casper-rw file on it but don't know where to place it or how to make use of it.

---

### Post by nooby on 2010-02-16
I wrote to tuxcantfly and asked him as developer but got no answer as I know of. 

So I take that as either something my Vista machine did and none else has ever told him about this error. Or it is set up this way by him and there is no way to get around it and that is why neither him nor anybody else comment on it. It is an un-welcome feature of the way it is set up. Nothing to do about so I deleted all of it and made a manual frugal install instead. 

It is not solved but none seems to care about so what to do?

---

