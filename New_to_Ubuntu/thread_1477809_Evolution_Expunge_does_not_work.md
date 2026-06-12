---
title: "Evolution Expunge does not work"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by bwallum on 2010-05-09
Hi

I have been trying to Empty Deleted Items and Evolution gives me the following error message:-

> Error storing '~/.evolution/mail/local/Inbox/EOW (mbox)': Error storing '~/.evolution/mail/local/Inbox/Launchpad (mbox)': Error storing '~/.evolution/mail/local/Inbox/UbuntuForums (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Summary and folder mismatch, even after a sync

The error message is never quite the same and refers to different email folders each time. E.g.

> Error storing '~/.evolution/mail/local/Inbox/Clients/Janet (mbox)': Error storing '~/.evolution/mail/local/Inbox/Clients/James (mbox)': Error storing '~/.evolution/mail/local/Inbox/Clients/Erica (mbox)': Error storing '~/.evolution/mail/local/Inbox/Clients/David (mbox)': Error storing '~/.evolution/mail/local/Inbox/Clients/Catherine (mbox)': Error storing '~/.evolution/mail/local/Inbox/Clients/Amanda (mbox)': Error storing '~/.evolution/mail/local/Inbox/EOW (mbox)': Error storing '~/.evolution/mail/local/Inbox/ECS Support (mbox)': Error storing '~/.evolution/mail/local/Inbox/Denise (mbox)': Error storing '~/.evolution/mail/local/Inbox/TW (mbox)': Error storing '~/.evolution/mail/local/Inbox/TWdev (mbox)': Error storing '~/.evolution/mail/local/Inbox/Launchpad (mbox)': Error storing '~/.evolution/mail/local/Sent (mbox)': Summary and folder mismatch, even after a sync

It appears to be a mismatch between index and folders actually found.

How do I correct this please?

---

### Post by bwallum on 2010-05-11
Fixed by deleting folders.db in home/user/.evolution/mail/local. Evolution resolves itself by regenerating it's index.

EDIT
For 11.04 folders.db can be found in:-
home/user/.local/share/evolution/mail/local/

'dot' files are hidden files; to view toggle with <Ctrl> h

---

### Post by clevertomato on 2010-08-18
This helped me. Thanks.

---

### Post by Psychobudgie on 2010-09-24
Switched my servers over to IMAP and encountered this issue. Your solution worked a treat. Many thanks.:KS

---

### Post by m0dcm on 2010-10-29
> **bwallum said:**
> Fixed by deleting folders.db in home/user/.evolution/mail/local. Evolution resolves itself by regenerating it's index.

This worked a treat for me, thanks for the info....

---

### Post by lorelami on 2010-12-29
This solution worked for me too!

---

### Post by David Oxland on 2011-01-03
folders.db in home/user/.evolution/mail/local

I've been plagued with this problem and can't find these folders anywhere.

---

### Post by bwallum on 2011-02-02
It's a hidden folder. Use 'ctrl h' to toggle hidden files when in nautilus (Places). Navigate to Places>Home Folder. Hold down the control key and then press the h key. You will see the 'dot' folders appear.

---

### Post by David Oxland on 2011-02-24
Thanks very much 
I'll give it a go

---

### Post by Maxthrust on 2011-03-18
[FONT=Comic Sans MS][COLOR=Navy]I just had this issue myself...thanks for the clear write-up.[/COLOR][/FONT]

---

### Post by Manjuvajra on 2011-08-12
Thanks again - I had the same problem and this solution fixed it.:D

---

