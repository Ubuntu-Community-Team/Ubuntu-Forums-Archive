---
title: "Printer authenication"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by billtown77 on 2011-05-23
Sent a test page to print to my network printer. A small menu pops up asking for authenication, a password to be entered under my logon name. I enter my logon password, but it comes back asking for a password. again. Where do I go from here.:confused:

---

### Post by fritz269 on 2011-05-23
I had the same problem with my Lexmark x6650. I solved the problem by running the install using root terminal. It should not prompt you for the password after that.

---

### Post by garvinrick4 on 2011-05-23
> **billtown77 said:**
> Sent a test page to print to my network printer. A small menu pops up asking for authenication, a password to be entered under my logon name. I enter my logon password, but it comes back asking for a password. again. Where do I go from here.:confused: Tell users Name of Printer and is it connected to a Windows computer and using
Windows Workgroup using Samba? Need more info for folks to give you a hand.

---

### Post by billtown77 on 2011-05-24
Printer is an HP 3210, connected via my network to a Windows XP desktop. I had no problem installing using ubuntu.

---

### Post by garvinrick4 on 2011-05-24
You did use Windows printer via samba hit browse and select Windows machine and then
your printer, then authenticate and hit forward to select driver and done.

Put this in URL line and you can see your printer:
[http://localhost:361/](http://localhost:361/)

---

### Post by billtown77 on 2011-05-24
You are helping a real newbie and to tell me to start/use Samba means nothing. How do I start Samba??:confused:

---

### Post by garvinrick4 on 2011-05-25
If you have the printer shared in Windows, then on install of Ubuntu it will be part of
Windows Workgroup and it just say Workgroup and samba when you go to choose a 
network printer while installing printer in Ubuntu. Just make sure you Windows machine has
printer shared, right click and share. Ubuntu works out of box.
Check out your network and sharing in Windows!! Only time you need to install any samba items in Ubuntu
is if you want to makes shares in your Ubuntu box. (Have other computers mount directorys (folders) from your Linux box like say /home for instance)

---

### Post by billtown77 on 2011-05-26
I have the printer, which is attached to a windows xp desktop as Shared. Ubuntu knows this printer is installed, as when I click on printers, there it is listed. Whne I try ro print , it just gets into a loop, asking over and over for authentication. I enter my ubuntu it just comes back asking for it again.
Unubtu is installed on my windows 7 laptop and I can print from it, in Windows mode.:(

---

### Post by garvinrick4 on 2011-05-27
> . Whne I try ro print , it just gets into a loop, asking over and over  for authentication. I enter my ubuntu it just comes back asking for it  again.
When you install on machine that is not attached to printer using Workgroup & Samba it asks you
to authenticate right before you go to get your driver. Is that working to authenticate then.
If not you have the wrong smb://WORKGROUP/xxxxxx look at your ubuntu machine that is
working and get that and write it down. Then on machine that isnt working type this in URL
localhost:631 and press enter will go to a Cups page: Hit add a printer and type that smb://
in there. Will add a printer from there no problem. You most likely are getting the wrong location or that smb:// xxxxx.

---

