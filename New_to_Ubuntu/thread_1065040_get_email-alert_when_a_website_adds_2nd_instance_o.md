---
title: "get email-alert when a website adds 2nd instance of a phrase into a webpage"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by hanzj on 2009-02-09
Hello.


 I need to be able to track when a website adds a phrase onto one of its pages, the home page. The thing is, the phrase (e.g. Hello World) is already on the page. So I need to be able to receive an alert when an ADDITIONAL copy of the phrase is added to the page. How can I do this? I don't want to have to keep checking the site every 5-10 minutes manually. Thanks.


The number one important thing is SPEED. I need to receive an ALERT as soon as webmaster adds that additional "Hello World" phrase onto his website's homepage.


Thanks.

---

### Post by LowSky on 2009-02-09
I dont think this is possible, at least from an Ubuntu standpoint. Not to mention this isnt something an Absolute Beginner would need to do.

Also your request might not work if the wording is put up as an image or with flash.

---

### Post by niteshifter on 2009-02-09
Hi,

[http://www.changedetection.com/](http://www.changedetection.com/)

May work for you. Other than that you'd need to program a solution for this.

---

### Post by kellemes on 2009-02-09
There are all kind of alerts possible, but they will alert you only when the website is checked for changes..
One of many examples would be.. [Firefox Update Scanner]("https://addons.mozilla.org/en-US/firefox/addon/3362")
A service like this will need to know how often you want it to scan for changes.. I hardly think it's reasonable (possible?) to have it scan every second or so.. ;-)

What you need is for the serverside to alert you when the phrase is added.
Like have some script send you an email (or SMS) when things have changed..
Is this a server you controle? Guess not..
In this case I can't think of a solution to be honest.

---

### Post by kellemes on 2009-02-09
> **niteshifter said:**
> Hi,

[http://www.changedetection.com/](http://www.changedetection.com/)

May work for you. Other than that you'd need to program a solution for this.

From there own FAQ
Typically pages are checked **once per day** for changes.

---

### Post by hanzj on 2009-02-09
> **kellemes said:**
> From there own FAQ
Typically pages are checked **once per day** for changes.

Once per day checking is not often enough for my needs. If I leave my computer on, can there be some sort of program made (I'm NO programmer at all) that can check as frequently as I choose? If so, can someone help?
Thanks.

---

### Post by hanzj on 2009-02-09
> **kellemes said:**
> There are all kind of alerts possible, but they will alert you only when the website is checked for changes..
One of many examples would be.. [Firefox Update Scanner]("https://addons.mozilla.org/en-US/firefox/addon/3362")
A service like this will need to know how often you want it to scan for changes.. I hardly think it's reasonable (possible?) to have it scan every second or so.. ;-)


Kellemes, thanks for your post. Unfortunately 

Update Scanner plugin, which I've just downloaded, will alert me when ANY change is made on the page. i don't want to be alerted when just ANY change is made. I would like to receive an alert when a second instance of a phrase "Hello World" is added to the page.

---

### Post by hanzj on 2009-02-09
> **kellemes said:**
> 
What you need is for the serverside to alert you when the phrase is added.
Like have some script send you an email (or SMS) when things have changed..
Is this a server you controle? Guess not..
In this case I can't think of a solution to be honest.
No, it's not a server or a website I control.

---

### Post by kostkon on 2009-02-09
There is [*Specto*]("http://specto.sourceforge.net/") that can check for changes on a page.

---

### Post by hanzj on 2009-02-09
> **kostkon said:**
> There is [*Specto*]("http://specto.sourceforge.net/") that can check for changes on a page.
Thanks. Downloading now to try it out.

---

### Post by hanzj on 2009-02-09
Specto does not allow selective monitoring of a webpage. If ANY part of the webpage changes, it will alert you. But I need to get alerted/updated only when the phrase HELLO WORLD is ADDED to a site's homepage.

---

### Post by G|N| on 2009-02-10
> **hanzj said:**
> Specto does not allow selective monitoring of a webpage. If ANY part of the webpage changes, it will alert you. But I need to get alerted/updated only when the phrase HELLO WORLD is ADDED to a site's homepage.

If i understand correctly you want to be notified if the phrase HELLO WORLD is added a second time to the site?

Indeed this is not possible with specto although specto 0.3 gives you a little difference view from what is changed.

And if this is still not what you want, give me a good example and i will create a custom watch especially for you :)

---

### Post by hanzj on 2009-02-10
Dear G|N|,
Thanks for the reply.

The reason why I don't want to get an update every time there is a change in the website is because the website changes quite often, and I don't want to receive "false positives" every time there is a difference. 
Therefore, Specto 0.3(rc1)'s difference view isn't really what I need.


Thank you for offering to create a custom watch. So there's a website (let's call it XYZwebsite.com for now. If you need to exact URL, let me know and I'll PM you.) that will add to their website homepage (a second instance of) the phrase "HELLO WORLD".  Currently on the homepage the phrase "HELLO WORLD" is in plain text. I do not know whether the second re-occurence of the phrase "HELLO WORLD" will be in plain text or will be in a jpg. If in a jpg,  its URL will be, I gather, in somewhere in xyzwebsite.com/* (in other words, the image will be hosted internally by the website). Currently, the website homepage seems to have a stable number of a few jpgs. And I don't know whether the jpg containing the phrase will have alternate text. So I don't mind receiving an alert anytime a new jpg or png is added to the site. 

By the way, G|N|, how can I get specto to send me an email via the command line? I see in the Advanced Options tab that we can run a custom command "when this watch has changed", but I don't ever use command line email. I have a gmail account. Is there an easy way to get an email to my gmail (or cellphone) when watch has changed?
Thanks.

---

### Post by hanzj on 2009-02-10
I found a way to get an email sent to my email box and my cellphone using sendemail.


The command I used was:

Command used was:
> 
sendEmail -f [EMAIL="thisisthesender@emailaddress.com"]thisisthesender@emailaddress.com[/EMAIL] -s mail.emailcompany_realemailaccount.com -xu [EMAIL="realemailaccount@email.com"]realemailaccount@email.com[/EMAIL] -xp password_ofrealemailaccount -t [EMAIL="torecepient@email.com"]torecepient@email.com[/EMAIL] -u email_subject_line_here -m Hello World. This is where message goes!

---

