---
title: "Backing up cloud email to a local IMAP server"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by fhsm on 2008-09-27
I’ve got a bunch of webmail (gmail, ymail, live mail, etc) accounts over which I’ve got no real control.  I’d like to maintain an automatic backup of this mail ‘just in case.’

I don’t need this repository to be web accessible.  I’d like to have an ubuntu server on my LAN sync with the cloud and store the messages as IMAP mailboxs locally.  If/when I want to get at the backup I can use a mail client to hit the local server from my laptop on the local network.

I’ve got the local server configuration nailed down using Devecot running on 8.04.  Obviously I know how to get at each of my cloud accounts via a mail protocol (pop/imap).  The question is how to connect the two?  

In effect I want to make one IMAP server a client for the other IMAP server.  I don’t want to push changes from local to cloud I just want local to keep up with cloud (ie when I delete a message from gmail I don’t want a copy living on my local server forever).

Anyone have any good ideas about how this could best be done?  I thought about fetchmail but that looks like it’s one way.  The perl script imapsync looks promising but I’ve read mixed results.

---

