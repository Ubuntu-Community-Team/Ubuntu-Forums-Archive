---
title: "Problems with Shared Folders in Xubuntu 8.04"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by LANjackal on 2008-04-26
Hey, I've been trying to share a folder over my network using the Shared Folders GUI in Xubuntu 8.04, but every time I start the GUI, I get a dialog telling me that the necessary services for Windows and UNIX sharing haven't been installed and that I need to install them.

When I install them and then try to unlock the app, I get an authentication error (correct password, double and triple checked). Exiting the app and starting it again only brings me back to square one - the dialog saying that the necessary services aren't installed.

Rebooting doesn't fix anything.

Help? Thanks :)

---

### Post by tvphil on 2008-04-26
I know you said you triple checked the password, but did you check to see if your password is all small case or large case? The password is case sensitive. Also, is the "caps lock" on, either on purpose or by accident? Everyone has been tripped up by these mistakes, so please don't be insulted by this response. It's happened to me, I thought it might have happened to you too.If that's not the case, then make sure samba dependencies are installed in Synaptic. They aren't by default.They are Samba, Samba Common, smbclient and smbfs.

---

### Post by LANjackal on 2008-04-26
No offense taken, it's a valid question. However, an incorrect password for an Unlock command usually results in another prompt, not an error message.

Besides that, I've been authorizing other stuff that worked well in the same session, and I'd tried Shared Folder several times over.

Just tried yet again, typing the password in carefully.

The exact error is:

> Cannot authenticate

An unexpected error occurred

---

### Post by tormod on 2008-04-27
Sounds similar to [https://bugs.launchpad.net/bugs/222860](https://bugs.launchpad.net/bugs/222860)

---

### Post by LANjackal on 2008-04-27
> **tormod said:**
> Sounds similar to [https://bugs.launchpad.net/bugs/222860](https://bugs.launchpad.net/bugs/222860)Yep. Given the CPU he's on, it looks like he may also have used the alternate install CD as I did. Maybe the problem's occurring on alternate installs only, because I just booted into a conventional Xubuntu desktop install on a faster machine and the same problem didn't emerge ...

---

### Post by LANjackal on 2008-04-28
Bump ... so just to make absolutely sure it's not an authentication problem, I logged in as root, and tried again:

Applications -> System -> Shared Folders

Once again, I was told that the necessary SMB and NFS services weren't installed. So I fired up Synaptic, only to find that they were in fact installed.

Canceling the installation notification in Shared Folders and attempting to proceed anyway doesn't work as although you can select the folder to be shared, the button to add it is greyed out.

Any ideas? Is there a CLI method of setting up Samba shares? It's a last resort (I hate CLI), but it looks like I may have to attempt it ...

---

