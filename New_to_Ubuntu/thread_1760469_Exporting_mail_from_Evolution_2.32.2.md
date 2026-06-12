---
title: "Exporting mail from Evolution 2.32.2"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by walt11 on 2011-05-17
[SIZE=2]Is there a way to export mail from Evolution in a form which can be imported into Thunderbird?  --Thanks[/SIZE]

---

### Post by bennachie on 2011-05-17
There are several ways of doing this, but I prefer to stick with a plain vanilla approach where you can see exactly what is going on at each stage.

The first step is to install Thunderbird, and set up your mailboxes (yes, this is a bit of a pain, but Thunderbird does its best to keep the pain to a manageable level). Then export your existing mailboxes from Evolution, saving them in "mbox" format. Download and install the "ImportExportTools" add-on to Thunderbird. 

Right click on the mailbox that you want to populate with imported messages, and select the "import/export" option. The resultant dialogue will guide you through a straightforward process of importing the messages from your saved mailboxes.

You can transfer Evolution contacts in a similar manner, saving the relevant address books in "csv" format. Download and install the "MoreFunctionsforAB" add-on to Thunderbird. You will then be able to import the contacts from your saved address books (use the normal "import" option in the "tools" menu). Do be careful to ensure that the heading equivalences presented for your approval in the subsequent dialogue are correct - they may need some minor adjustment. 

You'll find both add-ons at:

[http://nic-nac-project.org/~kaosmos/index-en.html](http://nic-nac-project.org/~kaosmos/index-en.html)

---

### Post by HermanAB on 2011-05-17
Howdy,

The generic way to transfer mail from one system to another (possibly incompatible) system is to bounce the mail through an IMAP mail account.  Google Mail uses IMAP.  So the trick is to configure the old and new mail clients with a temporary Google mail account, then click-drag-drop the mail from the old client to Google, then click-drag-drop the mail from Google using the new client.  

Important: Do not 'forward' the mail - that is the wrong way to do it, since it will change the mail headers. 

You can also use your own (temporary) email server to do that.  Citadel can be set up in about 20 minutes, using the Easy Install script and then you can do the same as above much faster, since it is on your LAN, which is much faster than the internet WAN.

The long term solution is to run your own mail server, then you never have to transfer mail again - just leave it on the server.  Citadel is of course a good choice, since it uses a database back-end for everything.

---

### Post by walt11 on 2011-05-17
[SIZE=2]Thanks to both of you for your very helpful responses - and for responding so quickly. I'm now well on the way to getting everything transferred over.

I transferred my contact lists (thanks for the link to those extensions) but I couldn't find a way to export more than one email folder at a time from Evolution (and I have quite a few) so elected to use the Gmail IMAP method. Haven't used an IMAP account before, and it was instructive, and so far all appears to be working.

I was apprehensive about trying Citadel. I'm going from one computer to another, and while they're both on the same LAN, I can't seem to get them to see each other. In any case, thought I might get into more problems than I wanted right now, but perhaps will try it later.

Thanks again.
[/SIZE]

---

