---
title: "Evolution is asking me for a keyring password?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-15
I'm trying to use evolution and it's asking for a keyring password.  I've tried to enter no password at all and it won't accept it.  This isn't actually on my computer it's on someone else.  Come to think of it I know of one other password to try.

But on my own computer I have never once had to enter a keyring password for evolution.  How the heck do I remove this prompt so they're not asked to type anything in?

---

### Post by baruch60610 on 2009-01-16
I don't know whether it's possible to make it stop doing that.  What I think is happening is that Evolution will grab the password for the mail server from the keyring, but protects that password by requiring you to enter a password.  The reason for this has so far eluded my feeble grasp.

You might try setting Evolution up so that it doesn't "remember" the e-mail password.  In this case the user will have to enter this password every time they want to get their mail.  Just like if they had the password protected by the keyring.

---

### Post by diablo75 on 2009-01-16
I figured out how to fix this.

I opened my home folder, revealed hidden files/folders with CTRL-H, and then opened the /.gnome2/keyrings folder and deleted the login.keyring file (really any file that might have been sitting in this folder could be deleted).  I did this on my own PC to try this out and managed to find a fix for something else that's driven me crazy:  Having to type in a keyring password after auto-login to establish a wireless connection.

After deleting the file, I was asked to re-enter my WPA password and my email account password in evolution.  When prompted to create a keyring password to put a lock overtop these two passwords, I left it blank instead.  It then asks if I want to use "unsafe storage" of my passwords, to which I said yes.

Now my PC automatically logs into my account and connects to my wireless network without having to enter a keyring password!  Deleting the keyring file on the other persons computer and re-entering their email account password, then a blank key ring password, solved their problem as well.  I understand the point of the keyring, but it's an inconvenience to me.  To others it's probably a great idea.  To each their own!  Glad I got this figured out.

---

### Post by Stephen Shellard on 2009-01-17
This worked for me.  I would just point out that I don't have a password on my wifi network(I live at the end of a country road and don't see the need for it) and for this reason the WPA  was confusing to me. Anyway, once I'd consulted Wikipedia on the meaning of WPA((Wifi protected access) all became clear.

---

