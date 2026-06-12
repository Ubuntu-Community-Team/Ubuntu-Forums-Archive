---
title: "Evolution- setting up personal domain gmail"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by completeidiot on 2010-06-02
I'm trying to set up email in Evolution for a gmail account that uses my domain. it's not an @gmail.com address. I've done it before, but I can't remember how I did it for the life of me. My @gmail.com address is set up perfectly. Please point me in the right direction. I just upgraded to 10.04 and forgot to back this up.

thanks

---

### Post by zkriesse on 2010-06-02
Take a look at these two links...might help ya out.

[https://help.ubuntu.com/community/Evolution](https://help.ubuntu.com/community/Evolution)

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

---

### Post by sites on 2010-06-02
INCOMING:
imap.gmail.com
[email]youremail@yourdomain.com[/email]
SSL encryption
password authentication

OUTGOING:
smtp.gmail.com
server requires authentication
TLS encryption
login authentication
[email]youremail@yourdomain.com[/email]

That "just works" for me.

---

### Post by completeidiot on 2010-06-02
still not working....can't figure out what it could possibly be. has been working fine for ages and then i did a fresh install after using 9.10 flawlessly and now i can't get it back to work. my standard gmail account is working but i can't get it to work with the @mydomain.com email

---

### Post by sites on 2010-06-02
That's odd.  These settings have worked for me in every version since Hardy.  I've found it helpful to backup my settings from the "File" menu.  This creates a evolution-backup.tar.gz file and saves me a lot of trouble when i re-install.  Just for the record, i never do upgrades.  Clean installs only.

---

### Post by completeidiot on 2010-06-02
I did do a clean install.
I forgot all about creating the backup file.

Either way, i'm stumped.

---

### Post by sites on 2010-06-04
Here's an idea.  Try a Karmic LiveCD.  Set up your account in evolution while in a Live environment, create a backup, then import the backup file on your Lucid installation.  Or, create a usb startup drive using a Karmic disc, boot it and follow the same steps.

---

### Post by completeidiot on 2010-06-04
changed it to pop and it works.
swear i tried that first and it didn't work.

---

### Post by sites on 2010-06-05
I know this has been "solved", but i just wanted to ask.  Did you have IMAP enabled in your Gmail settings before you tried the POP option?

---

