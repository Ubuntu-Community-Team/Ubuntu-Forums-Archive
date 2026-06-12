---
title: "WebMail Addon for thunderbird"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by dragonwolf on 2009-01-11
Has anyone gotten the WebMail Addon for thunderbird along with the hotmail and yahoo addons for it to actually work in 8.10 I found some directions for 6.04 but unfortunatly due to changes made in this version they no longer work

---

### Post by Darkade on 2009-01-11
I have installed it successfully in 8.04 just following the instructions in the webmail site : [http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by dragonwolf on 2009-01-11
> **Darkade said:**
> I have installed it successfully in 8.04 just following the instructions in the webmail site : [http://webmail.mozdev.org/](http://webmail.mozdev.org/)
Think I got it now thx!

---

### Post by dragonwolf on 2009-01-12
Ok I was only partially correct using that tutorial I was able to get hotmail to work however yahoo is still not functioning keeps timing out when attempting to connect

---

### Post by Darkade on 2009-01-14
For yahoo you don't need webmail add on, you can connect to yahoo via POP3

just use this values:
> 
Incoming Mail (POP3) Server:	plus.pop.mail.yahoo.com (Use SSL, port: 995)
Outgoing Mail (SMTP) Server:	plus.smtp.mail.yahoo.com (Use SSL, port: 465, use authentication)
Account Name/Login Name:	Your Yahoo! Mail ID (your email address without the "@yahoo.com")
Email Address:	Your Yahoo! Mail address (e.g., [email]user@yahoo.com[/email])
Password:	Your Yahoo! Mail password


if plus.pop.mail.yahoo.com or plus.smpt.mail.yahoo.com don't work just try dropping the "plus" so it would be like this: pop.mail.yahoo.com

---

### Post by dragonwolf on 2009-01-15
> **Darkade said:**
> For yahoo you don't need webmail add on, you can connect to yahoo via POP3

just use this values:


if plus.pop.mail.yahoo.com or plus.smpt.mail.yahoo.com don't work just try dropping the "plus" so it would be like this: pop.mail.yahoo.com

this may sound like a stupid question to you but are you on dsl or have a paid yahoo account? the reason I ask you is that by default yahoo will not let you access your email from a client such as thunderbird, outlook, what have you unless 1- your ISP is a service that is partnered with them such as AT&T or you pay an annual fee directly to them.

---

### Post by Darkade on 2009-01-17
I don't pay for my yahoo account, and I'm in Mexico my ISP is Telmex... I really can't tell if they are partnered with yahoo but those settings work fine for me :lolflag: I would give it a shot. You have nothing to lose.

I just want to add that I have several thunderbird/evolution accounts in different computers (home, school, portableapps, laptop) and for every account in each location the ISP is different (at least 3 different ISP)

I will attach some screenshots, see if they help.

As I said, give it a shot, you have nothing to loose, but a couple of minutes

---

### Post by dragonwolf on 2009-01-24
> **Darkade said:**
> I don't pay for my yahoo account, and I'm in Mexico my ISP is Telmex... I really can't tell if they are partnered with yahoo but those settings work fine for me :lolflag: I would give it a shot. You have nothing to lose.

I just want to add that I have several thunderbird/evolution accounts in different computers (home, school, portableapps, laptop) and for every account in each location the ISP is different (at least 3 different ISP)

I will attach some screenshots, see if they help.

As I said, give it a shot, you have nothing to loose, but a couple of minutes

Just as I suspected must be a paid subscriber lol oh well worth a shot anyways

---

### Post by latinhawk on 2009-04-13
I just got both Hotmail and yahoo working. This is what I did:
change the incoming port to one higher than 1025 and the outgoing port also higher than 1025. In my case Iset it at 2500. On your account setting make sure that the username has the complete email address ie. add @ hotmail or @yahoo to the username. That is all. Hope this helps.

---

### Post by dragonwolf on 2009-04-13
I tried that back when I was actually working on the issue seems the issue is 2 fold for me as far as yahoo goes 1- I live in the US which means 2-inorder to recieve my mail from them in thunderbird or anyother client I have to be a paid subcriber that is until someone converts Ypops! email to both thunderbird and ubuntu

---

### Post by latinhawk on 2009-04-13
I also live in the Us and as you I don't pay for Yahoo mail and it's working for me.

---

### Post by BDNiner on 2009-04-13
If you live in the US then you must be a paid subscriber to yahoo mail inorder to use their POP3 service. It kinda sucks, a lot of other regions have it for free. Hotmail and Gmail should work, you don't have to pay to setup POP3 with another e-mail client.

---

