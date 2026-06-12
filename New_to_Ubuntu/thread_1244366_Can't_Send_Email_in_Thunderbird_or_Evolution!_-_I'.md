---
title: "Can't Send Email in Thunderbird or Evolution! - I've searched here, but..."
date: 2009-08-19
forum: New to Ubuntu
---

### Post by powerfade1 on 2009-08-19
SOLVED!  Thanks everyone!


... I can't find a solution to my problem.

All my settings are correct - I've been on the phone with my ISP and everything is as it should be.

I'm running 9.04, 64 bit.

I've used Thunderbird in XP for three years and have now gone over to Ubuntu (and will have to run XP in a virtual box for certain programmes, but haven't installed XP yet).  I set up Thunderbird and tried a few configurations suggested by my ISP to get it to work, and wasn't even able to receive mail on one of my accounts. Two accounts with two identities each.  Pop protocols.  In Evolution same problem but now I can receive from all accounts.

Please give a newbie a hand here.

Thanks!

---

### Post by Merk42 on 2009-08-19
What error message are you getting?

Also, if you still have the Windows Thunderbird around you should be able to export those setting and import them into the Ubuntu version of Thunderbird.

If you don't , try installing XP in the VM and Thunderbird there.  See if it works (to make sure you aren't accidentally putting in wrong information). If it works there, then export/import to Ubuntu.

---

### Post by powerfade1 on 2009-08-19
No error message - well it does say at the bottom of Evolution that there was an error performing that operation, but no codes, etc.  They just sit in the outbox.  Sometimes the outbox has a number by it but the box is empty!  Then I try to send another email and the emails appear.

I don't have XP Thunderbird running, but I backed up all the files.  I've added a new server since then (two weeks now).

---

### Post by Merk42 on 2009-08-19
No error message at all? Never heard of that.
When you say you backed everything up, did you back up your settings from XP Thunderbird? As I said you should be able to import those settings.

Are you able to receive messages?
What sort of email is this? POP, IMAP, or web based?

---

### Post by powerfade1 on 2009-08-19
> **Merk42 said:**
> No error message at all? Never heard of that.
When you say you backed everything up, did you back up your settings from XP Thunderbird? As I said you should be able to import those settings.

Are you able to receive messages?
What sort of email is this? POP, IMAP, or web based?

Yes, backed up the settings and now have that file sitting on my desktop.

At the bottom of the Evolution screen it says error performing that operation.  I just tried to send two more emails and it says server timed out.  That's the first time that message showed up.

I can receive messages, yes.  POP.

---

### Post by Merk42 on 2009-08-19
You may have your outgoing server in wrong. Double check if you have it correct.

If you backed up the profiles alk2i7ua.default (or whatever random characters you got) you should be able to put that in ~/.mozilla-thunderbird

Since you've already started Thunderbird in Linux, you'll also have to edit the profile.ini file to point to the folder you transferred.

---

### Post by powerfade1 on 2009-08-19
Outgoing server is correct.  Transferring settings in from XP won't help because I have a new ISP now.

---

### Post by Merk42 on 2009-08-19
> **powerfade1 said:**
> Outgoing server is correct.  Transferring settings in from XP won't help because I have a new ISP now.

Have you gotten email to send/receive with this new ISP at all?
So it may not be a problem at all with Linux then?

---

### Post by ayenack on 2009-08-19
This sounds like it's an authentication error to me.

Can you tell us what email provider/s you're with?

---

### Post by powerfade1 on 2009-08-19
> **ayenack said:**
> This sounds like it's an authentication error to me.

Can you tell us what email provider/s you're with?

Two: one for work (local company that uses Bell lines), and one personal (Bell Sympatico in Ontario).

I have been able to send files with Bell but I've only used it with Linux.  I had the other one working with XP on both dialup and DSL.

What can be done about an authentication error?

---

### Post by LewRockwell on 2009-08-19
> **powerfade1 said:**
> Two: one for work (local company that uses Bell lines), and one personal (Bell Sympatico in Ontario).

I have been able to send files with Bell but I've only used it with Linux.  I had the other one working with XP on both dialup and DSL.

What can be done about an authentication error?

as long as you've got a decent internet connection you should be able to negotiate to all your accounts via a web browser at the very least

that should negate any emergency situations

we'll also assume that you will, through trial and error, be able to set up Thunderbird to retrieve your incoming email from any email provider that allows that functionality

so what we're left with is the outbound email smtp settings

your ISP will know all the exact settings that their equipment requires to relay your outgoing emails to their appropriate destinations

I have used Thunderbird for years with Windows, OSX, and Linux without any issues that I didn't create myself...

keep us posted on your progress and inform us of the solutions and corrective actions for the benefit of present and future visitors to this thread...

.

---

### Post by ayenack on 2009-08-19
Your in north America I see. I'm in UK so no knowledge on the two companies you mentioned...

Try changing Thunderbird outgoing set-up. Like this. In Thunderbird.

For sending mail. This is the tricky part. (Edited this because I had a bit for incoming set up. Which was irrelevant.)

1, Click Edit
2, Account Settings
3, Outgoing Server
4, Server Name smtp.your_provider_here.com
5, Port. (This is the tricky bit. You need to be sure you're sending on the correct port your ISP should be able to tell you this.)
6, Click **Use name and password** and SSL if supported. **EDIT:-** I think SSL may be wrong and you should try **TLS** instead.

Now when you try to send an outgoing message it'll ask you for password  enter it and tell Thunderbird to remember it and if all is working you should have outgoing mail. You can do this for both accounts but will only receive and send E-mail through one account (like a proxy) then it'll be directed to the other inbox etc.

---

### Post by ayenack on 2009-08-19
Just found some interesting info on this. Take a look at these.

This might work even though it's for Windows.

[http://www.cobolhacker.com/?p=810](http://www.cobolhacker.com/?p=810)


This will most likely concern you.

[http://forums.mozillazine.org/viewtopic.php?f=39&t=575371](http://forums.mozillazine.org/viewtopic.php?f=39&t=575371)

---

### Post by ayenack on 2009-08-19
From what I can work out you should have outgoing server set to 

Under Outgoing mail (SMTP): Check [B]This server requires a secure
connection (SSL)[/B] and ensure **25** is entered as port number.

Under Incoming mail (POP3): Check [B]This server requires a secure
connection (SSL)[/B] and ensure **995** is entered as port number. **EDIT:-** I think **SSL** may be wrong here and you should try **TLS** instead.

This seems to have worked for others.

Taken from this old post. It says to use SSL in outgoing server I think you might be better of using **TLS** in outgoing server. Give it a go.

[http://www.digitalhome.ca/forum/showthread.php?t=40582](http://www.digitalhome.ca/forum/showthread.php?t=40582)

---

### Post by mike555 on 2009-08-19
Some ISP's block port 25 , you might try a different one if you can .......

---

### Post by oldsoundguy on 2009-08-19
try port 110 .. I had to do that in order to use Thunderbird on my ISP.  25 was reserved for IE and Windows users.

---

### Post by powerfade1 on 2009-08-20
> **ayenack said:**
> From what I can work out you should have outgoing server set to 

Under Outgoing mail (SMTP): Check [B]This server requires a secure
connection (SSL)[/B] and ensure **25** is entered as port number.

Under Incoming mail (POP3): Check [B]This server requires a secure
connection (SSL)[/B] and ensure **995** is entered as port number. **EDIT:-** I think **SSL** may be wrong here and you should try **TLS** instead.

This seems to have worked for others.

Taken from this old post. It says to use SSL in outgoing server I think you might be better of using **TLS** in outgoing server. Give it a go.

[http://www.digitalhome.ca/forum/showthread.php?t=40582](http://www.digitalhome.ca/forum/showthread.php?t=40582)

Those are the settings I've been using as my ISP directed.  Started with port 25 and went to 587.  I haven't tried TLS as my ISP told me to use SSL.

Thanks for your help, I'll try it.

UPDATE: Now "send and receive" in Evolution is black and unable to be clicked.  I can't send or receive email now (except of course, online).

---

### Post by powerfade1 on 2009-08-20
> **mike555 said:**
> Some ISP's block port 25 , you might try a different one if you can .......  Did it. See post #17.

---

### Post by ayenack on 2009-08-20
That's about all the advice I can give. Should work. The only other thing is to try TLS. Maybe your ISP blocks or makes it extremely hard for Linux boxes for some reason.

---

### Post by powerfade1 on 2009-08-20
> **ayenack said:**
> That's about all the advice I can give. Should work. The only other thing is to try TLS. Maybe your ISP blocks or makes it extremely hard for Linux boxes for some reason.

I'm still working on some of the suggestions.  Thank you.  From some searching and reading, it seems Bell/Sympatico/MSN is blocking every non-Microsoft product.  My desktop at home still has XP and the kids use Outlook Express and all their addresses work fine on it.

Will update when I've tried everything.  Thanks to everyone!

---

### Post by powerfade1 on 2009-08-20
SOLVED for Thunderbird!!

The OUTGOING secure connection had to be set to TLS and I changed the port back to 25.

Thank you very much to everyone who helped me with this problem.  I have to work on Evolution now and see if I can get it working.  Integration with Ubuntu is pushing to switch to Evolution.

---

### Post by LewRockwell on 2009-08-20
> **powerfade1 said:**
> From some searching and reading, it seems Bell/Sympatico/MSN is blocking every non-Microsoft product.

If this is your ISP you should confirm this intentional blockage and request the ISP's policy which directly relates to those actions in writing

.

---

### Post by powerfade1 on 2009-08-20
> **LewRockwell said:**
> If this is your ISP you should confirm this intentional blockage and request the ISP's policy which directly relates to those actions in writing

.

It's just what I read, not what I believe.  I should have said, "may," rather than, "is."

---

### Post by cas77 on 2010-08-21
There turns out to be policy of some sort behind Sympatico's approach; I know, I know...

I used to tinker away with OS/2 before Ubuntu became the joyous-learning-curve that it is for me now.

I, too, am plugging away with trying to get Evolution to pick-up and connect with the
servers and passwords which work so well for me in WinXP and it's predecessors. 

In that, aside from searching through forums like this, I happened upon an interesting site which does have Bell Canada perspective and NorthAmerican  context.  It might help the process for you have a peek at this page:
[http://www.dslreports.com/faq/sympat/3.1_Email](http://www.dslreports.com/faq/sympat/3.1_Email)

Me, I'll go back to trying Evolution-setup and see I can get the same response as XP's Thunderbird offers.

(Just wanted to add the link to the DSL-insiders's view.)
Cass.

---

