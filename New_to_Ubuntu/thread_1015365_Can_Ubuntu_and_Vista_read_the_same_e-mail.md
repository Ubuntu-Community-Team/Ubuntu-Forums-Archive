---
title: "Can Ubuntu and Vista read the same e-mail?"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-18
Hello,

Is it possible to access the same e-mail from Vista and Ubuntu? Like, if my wife checks e-mail in Vista and it all gets downloaded to windows, is there a way to set it up so I can also access it from Ubuntu?

---

### Post by iaculallad on 2008-12-18
> **Chris Hansen said:**
> Hello,

Is it possible to access the same e-mail from Vista and Ubuntu? Like, if my wife checks e-mail in Vista and it all gets downloaded to windows, is there a way to set it up so I can also access it from Ubuntu?

Yes, it will be possible for you to access your email from both Ubuntu and vista, provided that you're current email setting saves it's mail from the server when downloaded on mail applications such as Evolution, Eudora, Thunderbird, or Outlook in that matter.

---

### Post by Mykle87 on 2008-12-18
If you receive your current email through POP3, the messages are taken off of the server and placed on your computer so you would not be able to read the same emails on multiple computers. Check if you ISP allows IMAP. The IMAP protocol allows you to interact with the email server so messages stay on the server allowing you to read the same emails on multiple computers.

---

### Post by donkyhotay on 2008-12-18
Email is Email regardless of the computer, your OS will not make any difference. It would be the same as if you both had ubuntu (or both had vista) and tried accessing the same Email. Most pop3 Email servers by default delete Email on their system once it's downloaded but you can often change this to keep the Email on the server at which point it can be accessed by multiple computers.

---

### Post by Myglaren on 2008-12-18
Yep, I check and send email from five accounts on Vista, XP and Ubuntu computers, also from my mobile (Windows Mobile).
I only use webmail, don't download anything.
Works just the same on all of them.

---

### Post by bob-linux-user on 2008-12-18
I don't know if you can on Vista but you certainly can on XP and Ubuntu. I dual boot a PC with the following setup:-

1st partition of HD:Windows

2nd partition of HD All my documents+thunderbird profile+firefox profile

3rd partition Ubuntu

That way all my emails (including old ones) are readable whether I am running in XP or Ubuntu. Also my Firefox bookmarks are always the same and up to date.

---

### Post by the.phantom on 2008-12-18
in thunderbird 
edit
account settings
server settings

you can have it download from server or stay there, or have it delete from server in XX days 

i have 4 different computers and my main is set to delete from server
the other 3 have it to keep on server for 2 days
works for me

---

### Post by Kellemora on 2008-12-18
Hi Chris

As other's have said, you CAN flip a switch that tells your ISP to LEAVE the mail on the Server!

OR, you can store your e-mails in a common ntfs partition, if you are both using the same e-mail program.

I use Eudora and have everything download into a folder named Eudora Data on an ntfs partition, so it doesn't matter which computer I sit down to, the e-mails are saved into the same folder.  Those I've already read still show read, because the conf file is in the Data Folder.

If an e-mail for the Frau is in the main inbox and not filtered to her box, I just highlight it and hit transfer to her mailbox.

The only thing is, it's a single user program, so we both can't be reading the mail at the same time.  I don't think! I'm afraid to try it, might mess up the pointer files somehow, hi hi.....  

I'm using Eudora in WINE, since it's a Doze program.
The Eudora add-on to Thunderbird is still Thunderbird that only looks like Eudora, don't work like Eudora though!

TTUL
Gary

---

