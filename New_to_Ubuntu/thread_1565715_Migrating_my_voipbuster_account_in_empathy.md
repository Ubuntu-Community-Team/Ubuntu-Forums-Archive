---
title: "Migrating my voipbuster account in empathy"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by yoramdavid on 2010-09-01
I don not know what I do wrong...
I tried with Empathy, Limphone and now Ekiga.

I prefer Ekiga, so here are my settings:
Name: my name
Registar: sip.voipbuster.com
User: The username I use in Voipbuster
Authentication User: The username I use in Voipbuster
Password: The password I use in Voipbuster
Timeout: 3600

Problems: I do not see my contact list, my friends do not see me on-line (they all use voipbuster).
Error message at bottom of Ekiga window by the connection icon: could not register sip:myusername@sip.voipbuster.com

Anyone can help, please?

---

### Post by yoramdavid on 2010-09-27
Any body, please?

---

### Post by smileone on 2011-01-03
HI,
I try this configuration, works!!
First step install 
```
sudo apt-get install telepathy-sofiasip
```
Open empathy application and add SIP account:
username : [email]nickname@sip.voipbuster.com[/email]
your password *****
Advanced option
select:
[INDENT][x]Discover the STUN server automatically[/INDENT]
[INDENT][x]Discover Binding[/INDENT]
don't fill field  Server but select Port 5060

Keep-Alive Options
[INDENT]Mechanism : Auto[/INDENT]
[INDENT]Interval 0[/INDENT]

Miscellaneous Options
[INDENT]Authentication username nickname[/INDENT]
[INDENT]Transport UDP[/INDENT]

If you have any problem contact me.):P

---

### Post by yoramdavid on 2011-01-03
> **smileone said:**
> HI,
I try this configuration, works!!
First step install 
```
sudo apt-get install telepathy-sofiasip
```
Open empathy application and add SIP account:
username : [email]nickname@sip.voipbuster.com[/email]
your password *****
Advanced option
select:
[INDENT][x]Discover the STUN server automatically[/INDENT]
[INDENT][x]Discover Binding[/INDENT]
don't fill field  Server but select Port 5060

Keep-Alive Options
[INDENT]Mechanism : Auto[/INDENT]
[INDENT]Interval 0[/INDENT]

Miscellaneous Options
[INDENT]Authentication username nickname[/INDENT]
[INDENT]Transport UDP[/INDENT]

If you have any problem contact me.):P

Hi and thank you!
Unfortunately I get a "connection error"
Below are my setting, I did like you said.
There is one more option at the bottom about "Flexible routing" ?

[IMG]http://img253.imageshack.us/img253/9478/empathyandvoipbuster.png[/IMG][/URL]


Thank you again.

Yoram

---

### Post by chandu870114 on 2011-06-14
HI
Am new to ubuntu.
Am trying to setup my fastvoip sip account in empathy but I hadn't succeeded yet.

username: [email]user123@fastvoip.com[/email]
password:xxxxxx
Dopublish ?  Port 5060
Udp ?
Use proxy sip.fastvoip.com
Authuser  [email]user123@fastvoip.com[/email]
Authdomain fastvoip.com

These are details which I enterd in SIP account. Then also I didn't get any result

Later I executed below commond
sudo apt-get install telepathy-sofiasipthen also I didn't get anything.

Anyone who understand this problem,please help..

Thanks in advance 
chandu
sweden

---

### Post by chandu870114 on 2011-07-08
> **chandu870114 said:**
> HI
Am new to ubuntu.
Am trying to setup my fastvoip sip account in empathy but I hadn't succeeded yet.

username: [EMAIL="user123@fastvoip.com"]user123@fastvoip.com[/EMAIL]
password:xxxxxx
Dopublish ?  Port 5060
Udp ?
Use proxy sip.fastvoip.com
Authuser  [EMAIL="user123@fastvoip.com"]user123@fastvoip.com[/EMAIL]
Authdomain fastvoip.com

These are details which I enterd in SIP account. Then also I didn't get any result

Later I executed below commond
sudo apt-get install telepathy-sofiasipthen also I didn't get anything.

Anyone who understand this problem,please help..

Thanks in advance 
chandu
sweden

Ya I got it
First I **removed previous SIP account**.

Next  **sudo apt-get install telepathy**

Next **add new SIP account** as shown in above reply(SMILEONE)

Thanks and regards
Chandu  :p

---

