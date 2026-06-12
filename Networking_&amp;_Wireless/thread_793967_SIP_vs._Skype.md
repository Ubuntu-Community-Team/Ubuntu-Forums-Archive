---
title: "SIP vs. Skype"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by rykel on 2008-05-14
Hi,

I have accounts with Gizmo5, Ekiga, GoogleTalk and WengoPhone.

However, I do NOT seem to understand SIP at all, even after reading all the userguides and wikis. In fact, the more I read, the more overwhelmed I am with all the technical details.

I am currently using Skype with SkypeIn, SkypeOut and Skype-to-Skype on both PC and Nokia 6121 mobile phone (via Fring.com), and so far so good. I tried using Gizmo5-to-Phone (SIP) but usually the call quality is worse than SkypeOut.

OK, assuming SIP=Skype, my questions are:

[INDENT][LIST=1]
[*]How do I set up a proper SIP account on my Nokia phone? (It already has a built in section for SIP set up.)
[*]What is the format of a SIP phone number? (ie. XXXXXXXX or [email]XXXXXXXX@someSIPprovider.com[/email]?)
[*]How do I make SIP-to-Phone, Phone-to-SIP and SIP-to-SIP** calls?
[/LIST][/INDENT]

Thanks for helping!

** I mean Gizmo5-to-Ekiga, Ekiga-to-WengoPhone, WengoPhone-to-GoogleTalk etc.

p/s. My apologies if this thread is posted in the wrong category!

---

### Post by loell on 2008-05-14
SIP != skype to begin with.

1. check this sip app for mobile phones [http://www.talkonaut.com/]("http://www.talkonaut.com/") , might be easier to set up.

2. usually the generally accepted format on any sip sof phone is,

sip:XXXXXXXX@someSIPprovider.com


3. if you paid for an account, then sip to phone is most probably  just the phone number, someone correct on this.

intl code + area code + phone number

phone to sip is still a normal phone number that is if you bought one.

sip to sip is the same as no. 2

---

### Post by rykel on 2008-05-17
Hey,

Thanks for the note about Talkonaut... it set me off on 2 days of hunting in the wonderful forests of VoIP, and I found that Skype is nothing when it comes to the possibilities (FREE calls) available with SIP!

Anyway, right now I am using VoIPdiscount (1 of the Betamax companies) via Ekiga to make PC-to-Phone calls (FREE unlimited to more than 30 countries with just about US$16 for 120 days) and the quality is very clear! In fact, they even provide a way to call 2 phone numbers for FREE - just like Jajah does. (but Jajah is chargeable)

OK, now my question is, *is there a SIP softphone on Ubuntu that can connect to **ALL** SIP providers, MSN/Yahoo/GTalk/ICQ/AIM/Jabber/whatever, send SMS etc. like Talkonaut does?*

Ekiga is OUT because it only connects to SIP (and if the SIP service has disconnected itself, Ekiga does not seem to try to reconnect anymore)... Gizmo5 and Wengo are OUT because they are trying to lock in users to their own "network", like Skype does, without adequately educating users about the existence of SIP. (although Wengo is VERY close to what I am looking for) Twinkle is also OUT because it is a KDE program and I prefer a GNOME one (just a personal preference!)...

Any suggestions?

UPDATE 1: Alright, I am giving Wengo a 2nd try... will let you guys know if it is the best of open source desktop IM/SIP/Skype? program...

UPDATE 2: Wengo fails to register to VoIPDiscount SIP service just like Ekiga would fail if I disconnect it. Gizmo also allows itself to use another SIP service, but the options to control the functions are either mostly hidden or missing.

NEW QUESTION: Do you know how I may receive SMS in Gmail, and send SMS to mobile phones from Gmail - without using an actual PSTN SIM card?

---

