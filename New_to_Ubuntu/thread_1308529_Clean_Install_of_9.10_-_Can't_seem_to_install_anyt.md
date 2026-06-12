---
title: "Clean Install of 9.10 - Can't seem to install anything"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by MuWarriors on 2009-10-31
Hello All.  

I just recently did a clean install of 9.1.  I have 8.04 and 9.04 before, so I was trying to install some of the apps I used to have.

So I try to install Pidgin:

sudo apt-get install pidgin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpurple-bin libpurple0
E: Package pidgin has no installation candidate

If I try to use the Ubuntu Software Center, I am not able to download anything either.  It seems that there is never an "install" button as the help references too.  If I click on an app, and then I with the screen shot, the help states there should be an install button.  I do not see one.  Also, the Install option from the menu is disabled.  

Is there something I am missing?  I really like the way 9.10 looks so far, so I am excited to get my applications back.

Thanks

---

### Post by diesch on 2009-10-31
pidgin is in 9.10, see [http://packages.ubuntu.com/karmic/pidgin](http://packages.ubuntu.com/karmic/pidgin) Maybe the repository mirror you are using isn't complete.

---

### Post by mvdoso on 2009-10-31
I had the same problem last time (9.04) when I put it on my other laptop.  What fixed it for me was re downloading it from a different download source (I did University of Oregon, which didn't work so I tried University of Utah) and I used a USB drive instead of a CD.  I don't know if it was one of those things that fixed it, or just the fact that I re installed.  But it worked for me.  (And now I always download from University of Utah and use a USB drive)

---

### Post by MuWarriors on 2009-10-31
So I should do a new install of the OS?  Is there any other things I can try?

---

### Post by sdpiowa on 2009-10-31
My install button disappeared when 9.10 couldn't connect to the internet effectively.  I added OpenDNS to Ubuntu's DNS servers, and it fixed the problem.

---

### Post by Gene_J on 2009-10-31
I am running into this same problem. Nothing "sudo" seems to be working. I cannot "apt-get install" any programs.

---

### Post by Gene_J on 2009-11-01
I reinstalled from the same CD I used the first time. Still no joy. I shall download and burn again to see if that solves the problem.

---

### Post by samrat1985 on 2009-11-01
hey guys,

I had the same problem! I did 

[FONT="Courier New"]sudo visudo[/FONT] 

& added my user name to use sudo without password

[FONT="Courier New"]sam ALL=NOPASSWD: ALL[/FONT]

then I did

[FONT="Courier New"]sudo apt-get update [/FONT]

from the terminal. Now it is working. I was trying
to install "console-tools" Hope this helps:)

I am having problems with gnome-panel

* I can't change time || deleted the panel & readded clock, now it shows "change time & date"
* cannot remove all icons from gnome-menu "Menus have icons" doesn't remove icons from "Application" & "places"

---

### Post by diesch on 2009-11-01
> **MuWarriors said:**
> So I should do a new install of the OS?  Is there any other things I can try?

No. most likely it's enough to go to "Software Sources" and choose another server.

---

### Post by j1nn on 2009-11-08
what helped to me was switching to root user [with su] and updating apt db from it. then an update from a user worked fine, and I can install packages.

hth

---

