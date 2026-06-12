---
title: "Samba Password? I never set one...why is it asking for one?"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by zachthejones on 2008-08-23
okay, this is my primary frustration with my home network (both wired and wireless computers involved). I use Samba to share my files on my linux Desktop and laptop. The Desktop (runny Gutsy) doesn't ask for a password when you try to access the shared folders on it from another computer (my laptop), yet when trying to access my laptop (which is running Hardy right now) from the desktop, I get prompted for a password and username - neither of which I have ever setup with Samba.

My username and password do not work - even the root password won't work.

Where can I set the password and username access? Or is my system just screwed up?

I also have a similar problem trying to access shared folders on either laptop or desktop from my wife's Vista machine - it prompts for a username/password and mine do not work. And the reverse is frustratingly true as well, when I try to access the shared folder on the Vista machine, it get a prompt for a username and password, and when I enter my wife's (which is the administrator one) or mine (for that computer), neither work.

Help please!!!

---

### Post by realfstkid on 2008-12-07
bump, I have the exact same problem. Could this be because I had to use the workaround to be able to "change permissions" in nautilus by using gksudo nautilus to right-click and share the media?

Please help, this is annoying. Neither root nor any other user accounts work for this as the OP said.

Thanks in advance

---

### Post by Iowan on 2008-12-08
There are two accounts required for Samba.  First is the Ubuntu user account, which is the user accounts I presume you've been trying.  Then, Samba has it's own list of users/passwords.  Have you set them up (via smbpasswd)?

> **superprash2003 said:**
> after creating the samba user mentioned above , you need to add it to the /etc/samba/smbusers file . For reference Step 5 [http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html)

---

