---
title: "Sendmail won't send from my local mail client"
date: 2013-12-31
forum: Networking &amp; Wireless
---

### Post by hojkoff on 2013-12-31
I've been playing with send mail for a bit now and I've managed to get the vast majority of things setup how I want them with the main exception of one. 

I can't get sendmail to send an email from my remote sever when using my local machine.

I can however receive mail on my local machine and send and recieve mail when I log in remotely from the box itself, just not send from my home computer. When I try to send an email it comes back with

```
Mail was unable to connect to server "*XXX.XXX.XXX.XXX*&#8221; using SSL on the default ports. Verify that this server supports SSL and that your account settings are correct.

Select a different outgoing mail server from the list below or click Try Later to leave the message in your Outbox until it can be sent.
```
I have a feeling that this maybe to do with the access table not being set up correctly to relay the email from my home machine, but I'm not 100%. It may also be worth mentioning I've changed the SSH post from the default 22, no idea if that's going anything to do with it. 

I'd also like to reject any mail being sent from an external source to the root user. Any help with that'd be appreciated too. 

(Also, would anyone like to volunteer to check that I haven't got an open relay? I've had a check myself but if someone else with a bit more knoledge could double check it for me I'd really appreciate it!)

Thanks!

---

