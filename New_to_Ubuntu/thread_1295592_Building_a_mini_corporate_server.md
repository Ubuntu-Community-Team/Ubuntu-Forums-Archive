---
title: "Building a mini corporate server"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-19
Hi Forum,

I've just finished a project for a company who uses Ubuntu for everything from CRM to ERP. Not a Windows machine in the building.

Now that I've seen it is possibe, I'd like to move my 3-man company to Ubuntu.

We'd like to start with a network server, which should replace MS Exchange and serve our rarely visited webpage.[URL="http://ubuntuforums.org/showthread.php?t=1231456"]

This Post[/URL] suggests that we use Zimbra for the mail and address book.

What about hardware? Does anyone have experience building a server with Intel Atom? Will I get away with using the Fritzbox as a hardware-firewall and DCHP or should I be configuring those things on the server?

I guess I can expand the server to include apache webserver and public ftp in the future. Also maybe vtiger?

Thanks in advane for any tips.


Rich

---

### Post by ZankerH on 2009-10-19
If you've got 3 clients and all you need is central file storage, mail, apache for intranet, an atom should more than suffice, just make sure it isn't bottlenecked by a lack of ram, which is often the case in commercial setups that use the Atom.

I use an atom-based server at home for file storage, torrents and LAMP, and it doesn't have any trouble serving an average of 5 clients at a time.

---

### Post by Hospadar on 2009-10-19
If it's serving such a small workgroup (3 people), I think just about any consumer hardware would be fine.  I'd just use a plain old router (maybe with dd-wrt if you really want) with port forwarding for the server.
Use apache for you web, you could use zimbra, or go LDAP and postfix.  I suspect ldap & postfix are going to be easier to set up since there are lots of tutorials and they are used by many non-enterprise types.

That said, any of these things are probably going to be something of a pain to set up, but not too bad if you are determined to do it.

---

### Post by k3lt01 on 2009-10-20
I have built a server at home which will in time, over the next 12 months or so, host a website I am building, keep all the information for my business and provide an email system.

I cannot comment on Zimbra as I haven't enough knowledge of it. I am currently setting up the default Ubuntu Mail Server programs but the system broke and will only do a partial upgrade. Now I am just going to wait for Karmic Koala and do it all with that.

Apart from that everything else has been relatively easy. These include setting up a network printer, setting up Samba so my sister can also use the server (I did need a little help with that).

It is basically an old amd 1800 (I think, can't remember exactly) with 3 hard drives, 2 20gb and 1 200gb. Over the next month, when finances allow, I am going to get 2 1tb or larger hard drives and make it a raid setup so the information can be kept on at least 2 hard drives in case of a hardware failure.

---

### Post by RichardCL on 2009-10-20
Thanks for the replies so far.

Can anyone tell me where to look for moving the Email server from a commercial provider. At present, I have 3 commercial solutions running.

 - My small company (currently held on a commercial provider server, allows fowarding, POP3 and IMAP)
 - An internal email at a client (supports only IMAP over SSL)
 - GMX Webmail (allows a POP3 download of mail content)

I'd like to have at least the corporate mail stored on the server since the size of the mailbox makes it costly. Ideally, I can view all the mailboxes in one hit.

I've got a dyndns account already to ensure the server can be seen from the internet. I'm just missing how to divert my .com domains there.

Ideally, I'd like to have:

example.com - my website
mail.example.com - my email account via Zimbra
crm.example.com - my vtiger crm system

---

