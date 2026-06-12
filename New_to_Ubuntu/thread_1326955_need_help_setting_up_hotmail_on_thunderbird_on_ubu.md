---
title: "need help setting up hotmail on thunderbird on ubuntu"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by zacker02 on 2009-11-14
Whew...... so i installed Ubuntu and its pretty good so far.. 
first question: does windows live mail work on this? if so, how do i install it?

Second: if the above isnt possible, i have thunderbird all set to go, but i cant seem to set up my hotmail on it.. even following the directions and tutes on the mozilla forums.

third: I really wanna DL and install and use "Live Mesh" on this laptop.. can it be used with this OS? 

fourth: the desktop.. when i save something like a photo off the net, why doesnt it show on my desktop, same with programs, if I click to send to desktop.. it says its there but i dont see it.

can anyone help me?
thanks!

---

### Post by nitstorm on 2009-11-14
i dunno about the other questions, but the windows live mail.. u mean the messenger? pidgin works well, but aMSN gels well with those who have windows live messenger... 

hope i wasn't completely useless, cheers :)

---

### Post by zacker02 on 2009-11-14
thanks nitstorm.. Windows Live Mail is actually the new Hotmail.. but now its a downloadable program.. its kinda like Outlook Express.. or thunderbird.. I used it to read email on my windowz machines and it works great. I have three different gmail accts, two different accounts through my provider and my hotmail addy..  and I had all of them running through Live Mail and it was great. If i can get them all to work in thunderbird, fine but id much rather have my livemail.

---

### Post by nitstorm on 2009-11-14
i think evolution mail should work,people say its good, but i have never used it... obviously i dont lots of mail  :P

---

### Post by chriscross93 on 2009-11-14
I do not believe that POP3, IMAP, or SMTP access was allowed by hotmail.  Your best bet may be to make another Gmail account and have all your live/hotmail forward to it.  You can then configure an email client (ex. thunderbird (+1, love it)) to revieve/send mail using the Gmail account. Heres a guide to configure thunderbird with gmail.  [http://mail.google.com/support/bin/answer.py?hl=en&answer=38343]("http://mail.google.com/support/bin/answer.py?hl=en&answer=38343")

---

### Post by steve161 on 2009-11-15
Have you tried using the webmail extensions. My apologies if this is too obvious.

[http://webmail.mozdev.org/]("http://webmail.mozdev.org/")

---

### Post by zacker02 on 2009-11-15
thanks guys... according to all the tutes i have seen for getting thunderbird to mesh with hotmail say hotmail (now called windows live mail) is pop3 .. and that it works well w/ thunderbird.. but not for me..lol im wondering, is it hotmail, thunderbird or, Ubuntu thats making it not work? 

i will check out the links you provided and see what they are.. thanks.

---

### Post by zacker02 on 2009-11-15
> **steve161 said:**
> Have you tried using the webmail extensions. My apologies if this is too obvious.

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

none of these extensions are installing because it says they arent compatible.. here i go again...lol

---

### Post by RJ12 on 2009-11-15
> **zacker02 said:**
> thanks guys... according to all the tutes i have seen for getting thunderbird to mesh with hotmail say hotmail (now called windows live mail) is pop3 .. and that it works well w/ thunderbird.. but not for me..lol im wondering, is it hotmail, thunderbird or, Ubuntu thats making it not work? 

i will check out the links you provided and see what they are.. thanks.

The answer is  Hotmail. A while back ago M$ stopped delivering pop3 and SMTP access (it was reserved for paying customers). Then with the switch to Windows Live Mail (And the whole Live suite) they got something called DeltaSync which only right now the webmail hotmail and Windows Live Mail is compatible with. Im sure theres a way but I just cant figure it out.

Anyway I hope that clears some of it up!:D

---

### Post by ktmom on 2009-11-15
It works on my Jaunty install, using Thunderbird 2.0.0.23

Use [these instructions]("http://email.about.com/od/mozillathunderbirdtips/qt/et_free_hotmail.htm") adjusting for the Linux version of T-bird (e.g. instead of *Tools | Account Settings* use *Edit | Account Settings*).  Make sure you use the full [email]username@hotmail.com[/email] or [email]username@live.com[/email] for the username entries and make sure the POP security is set to SSL (port 995) and the outgoing security is set to TLS.

---

### Post by ktmom on 2009-11-15
> **zacker02 said:**
>  
first question: does windows live mail work on this? if so, how do i install it?

Windows Live Mail is for Windows operating systems

> **zacker02 said:**
>  
third: I really wanna DL and install and use "Live Mesh" on this laptop.. can it be used with this OS? 

Live Mesh is for Windows and Mac based OS.  I don't think there is anything for linux (yet).

> **zacker02 said:**
>  
fourth: the desktop.. when i save something like a photo off the net, why doesnt it show on my desktop, same with programs, if I click to send to desktop.. it says its there but i dont see it.

Help me understand better here, what browser and what steps are you taking to save to the desktop?

---

### Post by qwerty2009 on 2009-11-15
HI :)

im nt sure but i think this should work with thunderbird (i use evolution )

hotmail setup-

receiving mail - 

[LIST]
[*]select pop from the drop down box
[*]server is pop3.live.com
[*]username is [email]blank@hotmail.com[/email] (or whatever u use)
[*]security is ssl
[/LIST]
sending mail

[LIST]
[*]sever is smtp.live.com
[*]encryption is ssl
[*]username is [email]blank@hotmail.com[/email] (or whatever u use)
[/LIST]

go here to set up ur gmail  - [http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)

if u just use livemesh to download music try using frostwire instead :P

im not sure bout ur desktop im sure u will find out why :P have u tried looking at ur desktop by clicking on ur desktop in ur home folder

---

### Post by steve161 on 2009-11-15
> none of these extensions are installing because it says they arent compatible.. here i go again...lol

I'm able to check my hotmail account with Thunderbird in Karmic.  You need to right click and save as for the webmail and hotmail extensionns.  Then go to tools-addons-extensions and install webmail.  Restart TB, check to see, under preferences, if the webmail addon is running (you may have to use a port above 1024).  Then install the hotmail addon the same way.

---

