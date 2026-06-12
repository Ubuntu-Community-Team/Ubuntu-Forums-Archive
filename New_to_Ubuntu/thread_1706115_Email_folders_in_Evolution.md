---
title: "Email folders in Evolution"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by guru_r236 on 2011-03-13
Hello There,

I am new user of Linux.

I had installed ubuntu 10.10 and wanted to setup the email in evolution. I was successful to an extent. But I see all my messages from hotmail and dumped into the Inbox in evolution and there are no subfolders.
Also all the emails are with status not read. I also had tried with Thunderbird. There too I have the same issue.
I had also installed Windows live mail (on Vista) and there the folders from the server are replicated to client and also the status of the mails is up-todate. 
I need the folder structure in my client too.

Please advice.

Best regards,
Guru

---

### Post by cap10Ibraim on 2011-03-13
switch to gmail !

---

### Post by vanadium on 2011-03-13
As far as I know, Windows Hotmail provides POP access, except if you use their proprietary software as an email client. POP mail is the old protocol and involves that you download messages from the server to your own computer.

In order to actually work on the server with your email client, your email server must support IMAP. Thus, if you insist on using an email account through a local client, your only option is to switch to a provider that support IMAP access. This is the case for gmail and yahoo mail, and probably (by now) several others.

---

### Post by Old_Man_Unix on 2011-03-13
Hotmail  - officially "*Windows Live Hotmail*" - is owned by Microsoft so it should not be surprising that it is integrated with other MS applications such as their mail applications. When called by those applications, it uses protocols  other than the POP and the SMTP.

Evolution - or any other FOSS clients - aren't so well integrated with Hotmail.  What that means for one thing  is that  while you can receive and transmit through Hotmail, there is no way to "sync" your email as would be the case with an IMAP server. Or as MS clients do with Hotmail.

If you need to sync your email, please heed the preceding advice about using an IMAP server.

---

