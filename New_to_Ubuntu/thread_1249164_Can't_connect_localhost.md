---
title: "Can't connect localhost"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Zeck on 2009-08-25
Hi all,
I have a problem. When my internet connection broken i can't connect localhost. And when i connect internet my localhost is working fine. This is a my problem. How to solve this problem. Please help me ?

---

### Post by credobyte on 2009-08-25
Connect .. from where to what ? *localhost* is an alias, not an application. Have you tried *127.0.0.1* ?

---

### Post by Zeck on 2009-08-25
Yes, i'm tried.

---

### Post by zeroseven0183 on 2009-08-25
***localhost*** is equivalent to ***this computer*** and 127.0.0.1 is your default IP address _without_ network connection.

Now, you don't want to connect to yourself, right? What you need to determine is the issue on your network connection.
Are you using wireless or cabled connection?

---

### Post by credobyte on 2009-08-25
> **Zeck said:**
> Yes, i'm tried.

You still haven't answered my main question. Is it Firefox ( eg. Apache ) or something else that doesn't let you in ( where ? ) ?

---

### Post by zeroseven0183 on 2009-08-25
Give us more information about this issue so we can troubleshoot it easier.

I assume that when you type **ifconfig** in the Terminal, the IP address reflected is **127.0.0.1**.

---

### Post by Zeck on 2009-08-25
I'm using Firefox and my internet connection is dial up.

---

### Post by zeroseven0183 on 2009-08-25
Were you able to successfully install the modem before?

Here are two links you can check to install the hardware:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/DialUpSupport](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/DialUpSupport)

---

### Post by credobyte on 2009-08-26
Firefox can be tricky sometimes. Check if [COLOR=Gray]File / Work Offline[/COLOR] ( Offline mode ) is selected - if it is, deselect it and you should be fine.

---

### Post by r3bol on 2009-10-14
> Firefox can be tricky sometimes. Check if File / Work Offline ( Offline mode ) is selected - if it is, deselect it and you should be fine.A million thanks. It took me 6 hours to find this answer. So obvious when you think about it :D

---

