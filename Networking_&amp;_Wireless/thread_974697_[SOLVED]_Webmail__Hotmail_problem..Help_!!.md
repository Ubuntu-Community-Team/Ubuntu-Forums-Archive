---
title: "[SOLVED] Webmail / Hotmail problem..Help !!"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by edgaruy1980 on 2008-11-07
:( I have installed Kubuntu 8.10 and in general works fine..
But.. I can not compose in Hotmail, running Firefox 3.03
javascript is enable, JRE6-10.
I tried to trick live.com using "user agent plug in" which has IE7 mode..
Well, maybe somebody knows about the issue I request support to hotmail as they recommend Internet explorer and firefox...

thanks guys..

---

### Post by Idefix82 on 2008-11-07
I don't use Hotmail but there have been numerous threads here today. They seem to have introduced an inconsistency with Firefox and/or Linux. The universally agreed best solution is to open a gmail account and to set up email forwarding and to tell your friends about your new email address. Porting contact lists is easy, since you can export them as a cvs file from hotmail and import them into gmail. You can also have a look at this thread: [http://ubuntuforums.org/showthread.php?t=973876]("http://ubuntuforums.org/showthread.php?t=973876")
Hope that helps.

---

### Post by calisun on 2008-11-08
Doing as described below in the quote Works!
Oh my god, so there is no comptibility issue, they are just blocking Ubuntu. 
Someone needs to sue the hell out of Micro$oft, that is not right.
How can they get away with that?
Someone needs to contact open source foundation about this so they can start the legal process. This is not right, that is bunch of b.s.

> **blazerw said:**
> To get Hotmail to work, apparently, you can change your "vendor" value to "Firefox" and it lets you in and works fine.

Here's how:
type "about:config" into the Awesome Bar, press enter.
In the filter, type "vendor"
Double click on "general.useragent.vendor" and change the value to "Firefox".
Click OK, try Hotmail.

Don't forget to change it back for visiting other sites. Give Ubuntu credit.

---

### Post by edgaruy1980 on 2008-11-08
Thanks so much , it worked..

:guitar:

---

