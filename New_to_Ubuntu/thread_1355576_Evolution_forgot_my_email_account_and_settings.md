---
title: "Evolution forgot my email account and settings"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by diablo75 on 2009-12-15
I've been using Evolution for years on multiple computers.  I have never had a problem like this.  Just a moment ago, I fired it up and it logged into my account and downloaded the latest emails.  I've been having a problem with spam lately and the inbox said there was something like 200+ messages unread... but the inbox list (where you actually see the emails listed with the subject line and date and all that) only showed about 35 of the unread emails.  I deleted them, attempted to refresh the mailbox with the send/receive button but it said there was an error.  I didn't bother checking to read the error for more details.

I just did a complete restart of the system, and when I went to start Evolution up, the first thing I see is the Evolution Setup Assistant, which is what you see if you've never set an email account up in the past.

The next thought that came to mind is hard drive space.  I just checked to see what I have available and it said there was 4.2 GB left (and I just created a large ISO file for a DVD that I don't really need so I deleted it, give me about 8 or 9 GB).  Then I restarted again.  That didn't help.

I checked the hidden folders in my home folder and there is an .evolution folder still there that's taking up 1.1GB of space so it would seem like everything for my email account should still be in place but I have no idea why it's not loading properly.  I haven't applied any updates today so I don't know what's going on.

Any ideas?

By the way I'm running Ubuntu 9.04.

---

### Post by diablo75 on 2009-12-15
I went ahead and just reconfigured evolution and deleted the old .evolution folder to start from scratch.  One odd thing that I found was that when I tried to open my .gnome2/keyrings/keyring.login (I think that was the name of the file) that it wouldn't open in gedit.  It said it was in some kind of non-standard format and couldn't display it as text.  So I deleted that file as well.

Hopefully I'm not looking at a problem with hard drive corruption because the volume is encrypted... I don't know how encrypted volumes handle things like data corruption...

---

