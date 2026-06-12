---
title: "Evolution imap password problem"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by capnthommo on 2009-03-17
hi (tired sigh)
i have been using evolution with my 2 gmail accounts with no problems so far. yesterday ONE of the accounts started to request authorization when SENDING mail 
> please enter SMTP password for (user) on host smtp.googlemail.com
when i enter the password i have always used and never had a problem with i get the following
> unable to authenticate to SMTP server.  Bad authentication response from server (there is then a repeat of the password enter box)  
i have made no changes to the setup except that first time it happened i went into gmail and was forced to make my password longer by gmail.  but this worked for a while and then it started again for no apparent reason.  and the other gmail account that i access from the same evolution screen is unaffected - it sends and receives with no problem.
this only affects when i try to SEND mail from one particular account - it receives fine.
i am using intrepid 64bit
any thoughts, anyone?
is anybody else having similar issues?
cheers
nigel

---

### Post by gandaran on 2009-03-17
> unable to authenticate to SMTP server. Bad authentication response from server (there is then a repeat of the password enter box)
check smtp settings
server: smtp.gmail.com
use SSL encryption
authentication=plain

sorry, these settings are for pop3 sever not imap.

---

### Post by sgosnell on 2009-03-17
Yes, it sounds like something in the settings got munged, probably the smtp settings.  Check both accounts, and see what is different between them.

---

### Post by capnthommo on 2009-03-17
hi there.  i think i agree, having given it a little more thought.  i know i haven't changed anything but thought i'd check in case it was a more general problem than just me.
i think what i might do is delete both from evolution, make sure they are both right as far as gmail settings are concerned, and then set up and configure the accounts in evolution from the start again.
serve me right, i was getting a bit bored so now i have a little project to occupy myself with.
one last point, does anybody know of a better how to than the guide to configuration in gmail settings, cos that is a little unclear, i feel.  it has to be, necessarily, vague about how to reset ports and suchlike and i am a tad unclear on that subject.
cheers anyway, i shall attend to this one later on, after i have considered whether i might like to give thunderbird or some other mail/calendar client a try.
any suggestions there would be appreciated.
cheers
nigel

---

### Post by sgosnell on 2009-03-17
I follow the instructions on the Settings page of GMail, for other clients.  It has always worked for me.

---

