---
title: "[SOLVED] hotmail on thunderbird client"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by downloadfreak on 2008-12-26
Hello,

I want that I can check my hotmail in my thunderbird. I did install the plugins but when I try to install the hotmail it says that the connection is refused.
What can I do?

regards,
downloadfreak

---

### Post by kellemes on 2008-12-26
Look at webmail-options in Thunderbird.. Are the 3 servers showing green?

---

### Post by downloadfreak on 2008-12-26
> **kellemes said:**
> Look at webmail-options in Thunderbird.. Are the 3 servers showing green?
yes they are, I increased them to 3000, 2000 and 4000 so they are.

---

### Post by diiphantom on 2008-12-26
downloadfreak i think the reason why you get an error with hotmail is because hotmail doesnt provide POP service anymore, for few years already, onlyway to do it is by having premium services from them. i tried it in when i used windows.

---

### Post by downloadfreak on 2008-12-26
I don't think so, because many people still get it working

---

### Post by diiphantom on 2008-12-26
if you find an answer then let me know.  :)

EDIT:

[http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html](http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html)

ALSO:
[http://ubuntuforums.org/showthread.php?t=208101](http://ubuntuforums.org/showthread.php?t=208101)

i think i found ur answer

---

### Post by downloadfreak on 2008-12-26
> **diiphantom said:**
> if you find an answer then let me know.  :)

EDIT:

[http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html](http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html)

ALSO:
[http://ubuntuforums.org/showthread.php?t=208101](http://ubuntuforums.org/showthread.php?t=208101)

i think i found ur answer
Thank you, I now still get the error that localhost is refused, if I go in and change the port and say get mail it asks for my password and after that it takes really long to load and then say "connection timed out." Do you have any ideas?

---

### Post by 2hot6ft2 on 2008-12-26
I recently had the error "negative vibes from localhost" and all I did to fix it was went to Tools>Add-ons>WebMail-Hotmail>Preferences and changed it from Hotmail Live (The new one at the bottom) to WebDav and it's working fine again so try that.

If it's already set to WebDav then switch it to Hotmail Live (The new one at the bottom).

---

### Post by downloadfreak on 2008-12-26
> **2hot6ft2 said:**
> I recently had the error "negative vibes from localhost" and all I did to fix it was went to Tools>Add-ons>WebMail-Hotmail>Preferences and changed it from Hotmail Live (The new one at the bottom) to WebDav and it's working fine again so try that.

If it's already set to WebDav then switch it to Hotmail Live (The new one at the bottom).

When I change it from hotmail live to WebDav I do get that error, so I keep it at hotmail live.

---

### Post by hyper_ch on 2008-12-27
> **diiphantom said:**
> [http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html](http://ubuntuswitch.blogspot.com/2007/09/ubuntu-how-to-get-yahoohotmail-emails.html)

this one worked for me... I first needed to install the webmail and hotmail addons and then create a new account using "webmail" option there. Then it worked like a breeze :)

---

### Post by downloadfreak on 2008-12-27
Didn't you have any errors or something?

---

### Post by downloadfreak on 2008-12-27
> **hyper_ch said:**
> this one worked for me... I first needed to install the webmail and hotmail addons and then create a new account using "webmail" option there. Then it worked like a breeze :)
Didn't you have errors or something?

---

### Post by hyper_ch on 2008-12-27
nope, worked fine... I first checked that the ports are green like in that howto... I also used 1055 and then I created a new webmail account with port 1055 and it just worked... it took a little while until logged in but then it got all the mail there (not that there was much mail anyway).

---

### Post by 2hot6ft2 on 2008-12-27
Go thru the setting for each account and check that they are still set up right. I have had mine change for some reason once.

Update the plugins mine are currently at versions WebMail is 1.3.2, and WebMail-Hotmail is at 1.2.19 and it is currently set to WebDav and is working so something in your settings is off.

For your SMTP server use your hotmail address

Server Name : localhost
User Name : [email]yourname@hotmail.com[/email]
and that port should be the same as you set the POP plugin to

---

### Post by SamNSane on 2008-12-27
You can get in touch with various people who really know the ins and outs of using this add-ons with Thunderbird at [http://groups.google.com/group/thunderbird-webmail-extension?hl=en]("http://groups.google.com/group/thunderbird-webmail-extension?hl=en").

Microsoft has been ditzing around with the interface for months and causing intermittent problems for Thunderbird Webmail users. There are additional problems for those who have free accounts that aren't older than several years of age. Those with for-pay accounts and really old free accounts are able to use WebDAV at the present time.

---

### Post by jrusso2 on 2008-12-27
I had this working for years and all the sudden one day I got the bad vibes error and it has not worked on any computer.  There must be some changes that Hotmail made because I have not made any changes and it worked for years.

---

### Post by downloadfreak on 2008-12-29
I'll use the google groups forums, probably they know all the errors over there. Many thanks for all the help everyone.

---

