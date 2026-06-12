---
title: "Can WINE offer a route to install EXE hardware drivers on a Ubuntu alone Ubuntu ?"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by openick on 2011-02-24
Hello

I have driver files that are files with file extensions exe cat inf sys ini   

If [COLOR="RoyalBlue"]**WINE **[/COLOR]can read these files, can the exe files be run to install these WIMAX, MODEM and scn ( screen ? ) driver files on a **[COLOR="RoyalBlue"]Ubuntu only Ubuntu table[/COLOR]t** ?[-o<

---

### Post by cariboo on 2011-02-24
The simple answer is no, wine doesn't have access to the hardware layer. What driver are you having a problem with?

---

### Post by openick on 2011-02-24
> **cariboo907 said:**
> The simple answer is no, wine doesn't have access to the hardware layer. What driver are you having a problem with?

Hello Cariboo907,


Thank you for your reply.

These are apparently windows drivers for [SIZE="3"]modem / wifi and possibly touch[/SIZE], for a touch tablet. The manufacturer sent me the windows drivers, wondering if there is a way to install the drivers, [COLOR="Navy"]if I have to.[/COLOR]

Thank you for the response. The files list is at page [http://paste.ubuntu.com/571929/](http://paste.ubuntu.com/571929/)

---

### Post by wishyjr on 2011-02-25
this might be a little too heavy a solution but have you considered creating a windows virtual machine, then use the drivers on that?

---

### Post by openick on 2011-02-26
> **wishyjr said:**
> this might be a little too heavy a solution but have you considered creating a windows virtual machine, then use the drivers on that?


Hellow WishyJr

Thank you.

If that could be one of the solutions, I would very much like to go ahead and try.  Should I try Virtual Box OSE ? Or is there any other solution that you would recommend?

The page [http://downloadsquad.switched.com/2008/02/10/run-windows-in-a-virtual-machine-using-ubuntu-and-virtualbox/talks](http://downloadsquad.switched.com/2008/02/10/run-windows-in-a-virtual-machine-using-ubuntu-and-virtualbox/talks) about some problems, particularly about USB not working, and cites and cites thread [http://ubuntuforums.org/showthread.php?t=341740](http://ubuntuforums.org/showthread.php?t=341740) which leaves the problem unresolved.

What I have is a tablet PC without a keyboard and mouse, so I will need USB ports to connect the keyboard and mouse to work within virtual box

Q2:  What commands do I type to enumerate hardware components without drivers ?   At the moment sound does not work ( or not turned on ),  wifi does not work, touch does not work, I am merely assuming that the drivers do not exist within Ubuntu. It is possible that some of these components could already work with the drivers already developed ( some with generic ??? drivers, such as the keyboard drivers that make any keyboard work )

Thank you.

---

### Post by openick on 2012-01-10
I am revisiting this thread after 6 months, to post some interesting information on my experiments on which I have not exactly kept a chronological log.


--- Tried either 11.04 or 11.10 and found the touch screen working, but no wifi
---  Used ndiswrapper to load wifi drivers - but wifi did not work
---  Deleted everthing and installed android 4, Touch was working 
---  Installed 12.04 touch was not working, wifi was not working
---  Installed Windows 8 Developer Preview, loaded all windows drivers (windows 8 as dual boot)

( Had an issue with grub after that, boot repair resolved it )

Booted 12.04,  WiFi and audio are WORKING, only problem left now is touch, about which I have created a post in installation & upgrades, with some attachments as the output of lsusb and lspci

( Posting this wondering why wifi is working now:

--- Is it because the hardware became active on the tablet after a one time installation of drivers in windows environment, irrrespective of whether windows is booted or not ?

--- Or a complex process of available drivers and windows drivers with ndiswrapper in a previous ubuntu installation (11.04 or 11.10) is retained by the new installation even after the ubuntu partition has been replaced with a new 12.04 installation? )

If this is interesting, I am open to posting the output of any command in this thread.

Thank you

---

