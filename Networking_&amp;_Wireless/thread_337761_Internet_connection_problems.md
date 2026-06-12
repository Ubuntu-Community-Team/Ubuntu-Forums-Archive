---
title: "Internet connection problems"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by geek-o-logist on 2007-01-13
Hi ... I am pretty new to linux and aim to break from Windows at the earliest. I am in the transition process and effectively using ubuntu for official purposes. I am able to connect to broadband using ubuntu. But when it comes to connecting to dail up using gnome-ppp, although it shows connected at the notification area, I'm unable to browse....I checked my browser setting and have checked directly connect to internet .... but it does not seem to work ](*,)

---

### Post by handy on 2007-01-13
Is this 2 different computers, 1 using broadband & the other dial-up?

Anyway, try typing **about:config** into the firefox address field, then **ipv6** into the now visible **Filter:** field, then double click on the line left in the firefox display window, so as to change it's boolean value to **true**.

Then restart firefox.

I must do the above to be able to browse the internet.  After having done it browsing is good.

I hope that helps?

If not I'm sure you will post more information which will make it easier for someone to help you... :)

---

### Post by geek-o-logist on 2007-01-14
Hey... thanks.... I tried using your suggestion, but it did not seem to work for me...

I have ubuntu 6.06 on my laptop. I am using it for broadband at my office and dial-up at my home. It does a fine job of identifying my usb modem, and when i dial out using gppp i am able to connect too. However, neither i can browse nor download mails... I know it must be some minor settings issue, but i am unable to resolve the same..

---

### Post by handy on 2007-01-16
Sorry I can't help you, I have been using a web based interface for my email for the last 5 years or more.  It is much safer & quicker, you manage all of your email on someone elses server, which saves lots of time, space, spam & viruses (oh! viruses, that was when I used windoze).

---

### Post by AlanRogers on 2007-01-16
> **geek-o-logist said:**
> However, neither i can browse nor download mails... I know it must be some minor settings issue, but i am unable to resolve the same..Connected but not able to browse usually indicates that you don't have DNS servers set. In initiating a dial-up connection, you should just pick these up from your ISP. However, I don't know my way round gnome-ppp.

Before you try anything else, you need to look into this. No DNS equals no web browsing or mail sending. As a test, whilst connected on dial-up, type [http://64.236.16.116/]("http://64.236.16.116/") into your browser. If that brings up the home page of a well-known television company, it's definitely (lack of) DNS.

---

### Post by handy on 2007-01-16
It may be possible that there is some help for you in this [_**how-to**_]("http://ubuntuforums.org/showthread.php?t=282034")?

---

