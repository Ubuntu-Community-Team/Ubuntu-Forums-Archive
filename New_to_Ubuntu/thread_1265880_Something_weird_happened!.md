---
title: "Something weird happened!"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by mesmith on 2009-09-14
I installed a second file manager (pcmanfm) to complement Thunar.  Played with it for a bit, liked it, then played with Thunar a bit, adding a couple of extras such as directory search from right click.  Signed off.  Came back a few hours later and did a cold start.  No /Home on my desktop, and no application menu.  I do have launch icons in a panel so that is how I'm communicating with this forum.  Any way to get my /Home and menu structure to return?

Help appreciated.

---

### Post by ankspo71 on 2009-09-14
Hi,
I'm not an xubuntu user, but I am guessing that thunar got replaced with pcmanfm when you rebooted (which probably couldn't be done while thunar was still in use, and that's probably why you were still able to use it). 

Was there any conflicting dependencies listed in Synaptic Package Manager? It might still show that info too.

What happens when you type pcmanfm or thunar in the terminal?

I'm sure there are some techies here that can be of more help, such as showing you how to get your preferred file browser to run automatically. Unfortunately, I don't know how to help in that department.

If you think you need to reinstall thunar you can do that via synaptic package manager. If for some reason that doesn't work, you could try installing "xfce" or "xubuntu-desktop" through synaptic too.

_Be sure to back up anything important before doing that._

Hope I was of some help.
James.

---

### Post by Mrandersonjr on 2009-09-14
Try opening a terminal and typing:

sudo thundar and then see if that brings it back,if not then try sudo nautilus and then see if that brings it back.:popcorn:

---

### Post by egalvan on 2009-09-14
> **mesmith said:**
>  **No /Home on my desktop**, and no application menu.  Any way to get my /Home and menu structure to return?

Help appreciated.

I have a "desktop" in my /home,
but no /home on my desktop.

so I'm confused. :confused:

---

### Post by mesmith on 2009-09-14
Thanks for the advice.  In the end I restored my linux partition using partimage and a recent backup.  Didn't lose anything but a few emails.  I do appreciate the help, but don't have much patience when it comes to fixing my distro.  Partimage and my System Rescue disc have saved my *** half a dozen times over the last year.

Thank you again.

---

### Post by kerry_s on 2009-09-14
did you check "manage desktop" in the pcmanfm settings?

---

