---
title: "[SOLVED] Print Server Instructions - Kubuntu?"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by MSchenker on 2007-11-18
Hi Everyone,
I have an HP PhotoSmart 8250 printer, which works very well from my Kubuntu desktop.  I also have a laptop running Kubuntu, which gets Internet access through the wireless router.

But I can't figure out how to let the laptop share the HP printer.

Here are the important details:
[LIST]
[*]The desktop is connected to the router via a cable.
[*]The printer is connected to the desktop via USB port.
[*]The laptop gets Internet access via the router with a wireless connection.[/LIST]I understand that I need to set up a print server, and I found instructions for doing this.  The problem is, the instructions are for Ubuntu, and I'm running Kubuntu.

Here's the Ubuntu page with nice instructions for setting up a print server: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Can someone help me "translate" these instructions into Kubuntu?

Thanks,
Matt

---

### Post by Blutack on 2007-11-18
You need to use the printing settings thing in Kubuntu - from what I remember it is more powerful to use than the gnome one!
Open it up, then hit F1 and see if there is anything in the help manual.  Otherwise, just poke around and you could probably figure it out from ubuntu page you posted.  If you get really desperate you could install the gnome-print-client, set it all up, then remove the gnome-print-client again.  Trouble is, that would pull in a LOT of gnome dependancies too I suspect.

---

### Post by MSchenker on 2007-11-18
Blutack,
Thanks for helping.  I've been through all the system settings in Kubuntu and there is nothing that resembles the information for Ubuntu.

Most of the time, I have no problem accessing an equivalent operation in Kubuntu, but this time I just can't find it.

I've posted this same question in the Kubuntu forum, so I'm hoping to get an answer soon.  I can't possibly be the only person trying to share a printer using *buntu!

Thanks,
Matt

---

### Post by Blutack on 2007-11-18
Bingo!
[http://localhost:631/admin/](http://localhost:631/admin/)
and then choose the Share Published printers option.
I got it from here - it is for debian sarge and mostly covers samba so ignore most of it :-)
[http://www.debian-administration.org/articles/425](http://www.debian-administration.org/articles/425)

Edit - the CUPS configuration page has a great Documentation Tab.

---

### Post by MSchenker on 2007-11-18
Blutack,
Thanks for finding that!  Nice detective work!

I went in and changed the settings.

My only remaining question is, why is this not more easily accessible through the Kubuntu control panel or something?  Like I said, I'm sure I'm not the only one who needs to do this!

Seems Ubuntu makes this process much easier than Kubuntu.

Thanks again for your help!
Matt

---

### Post by Blutack on 2007-11-18
I used to use KDE, and vaguely remembered the CUPS local web server thing.  I had to use it once too.  I suspect it is there, one of the difficulties I found with KDE was the plethora of options - it is so hard to find what you are actually looking for!
Glad to have been of help anyway, the CUPs localhost is available on all other *buntu's too if anyone else has this issue.

---

### Post by MSchenker on 2007-11-18
Blutack,
I just tested the setup, and what do you know -- IT WORKS!  Now I can work on my laptop and access my printer wirelessly.  Actually, once you gave me the address for that CUPS page, it was very simple.

Still, this is such a common need for *buntu users, I wonder why this is not a simple menu item in Kubuntu.

Matthew

---

### Post by Blutack on 2007-11-18
No idea, I'm sure it's in there somewhere :-)
If you could mark this thread solved it might help other long-suffering kubuntu users.

---

### Post by MSchenker on 2007-11-18
Blutack,
>  		No idea, I'm sure it's in there somewhere 
Maybe it is, but it seems to be somewhat hidden!  I'm still checking in the Kubuntu forums about this.

>  If you could mark this thread solved it might help other long-suffering kubuntu users.
OK, I'll do that.

Thanks again for the great help!

Matt

---

### Post by Blutack on 2007-11-18
No worries, if you are feeling particularly nice you could even write a howto
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by MSchenker on 2007-11-19
Blutack,
I just put together a how-to on setting up a CUPS print server in Ubuntu or Kubuntu.

Actually, I decided to write it up as a set of instructions that allow you to access the print server right from the K Menu.

For those of you with experience, this will seem obvious, but it may be helpful to people, like me, who are still learning their way around.

Here are the steps:
1. Right click on the K Menu
2. Choose Panel Menu > Configure Panel
3. In the "Configure - KDE Panel" window, click "Menus"
4. Click the "Edit _K_ Menu" button
5. In the "KDE Menu Editor" window, click on the menu where you want to add the CUPS tool
6. Click "New Item" and enter a name (such as "Manage Printing), then click "OK"
7. In the "Co_m_mand:" field, enter the following line: konqueror [http://localhost:631/](http://localhost:631/)
8. Click "Save" then click "Quit"

You should now see the "Manage Printing" service open from the K menu.  It should take you directly to the CUPS management screen.

Matt

PS: I also posted this on the Kubuntu forum [(http://kubuntuforums.net/forums/index.php?topic=3088772.msg101056#msg101056)]("http://kubuntuforums.net/forums/index.php?topic=3088772.msg101056#msg101056")

---

