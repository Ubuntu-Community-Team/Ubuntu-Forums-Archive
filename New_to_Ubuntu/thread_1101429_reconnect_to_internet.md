---
title: "reconnect to internet"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by gkraju on 2009-03-20
hi  i am new to ubuntu
when my internet disconnects i have to go terminal and reconnect is there any way it will automatically reconnect like in Xp 
thanks in advance

---

### Post by The Cog on 2009-03-20
That's not at all clear what's going wrong or what you are doing or make it work again. But I will assume you are using wireless. You may find that wicd is a better wireless manager that the default one.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
It's what I use and I'm very happy with it.

---

### Post by gkraju on 2009-03-20
> **The Cog said:**
> That's not at all clear what's going wrong or what you are doing or make it work again. But I will assume you are using wireless. You may find that wicd is a better wireless manager that the default one.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
It's what I use and I'm very happy with it.

thanks for your reply but i am not using wireless connection 
i have connected internet through ethernet PPPoE modem
i have line problem with the service provider (will be corrected soon) but the problem is if internet disconnects i have to reconnect in terminal with command 
sudo pon dsl-provider
but in Xp it will redial automatically 
how to make ubuntu reconnect automatically once internet disconnects 
hope you undestand:P

---

### Post by 123456789123456789123456 on 2009-03-20
is the modem set to always on?  or do you need to provide it with a user name and password to get in?

If you need to enter in a username and password, I understand that Ubuntu is not fully up to date with the ability to extablish such connections, as you can do in windows.

I suggest you log into the modem, and set it to always on.  that way, all ubuntu needs to do is simply test and send a request to modem.

It will also be easier on ubuntu to detect rather or not connection has been lost.  Line problems however can cause problems, on my mac for instance, if I loose connection, it will not allways get back on, I sometimes have to force to computer to connect again.

---

### Post by gkraju on 2009-03-20
> **123456789123456789123456 said:**
> is the modem set to always on?  or do you need to provide it with a user name and password to get in?

If you need to enter in a username and password, I understand that Ubuntu is not fully up to date with the ability to extablish such connections, as you can do in windows.

I suggest you log into the modem, and set it to always on.  that way, all ubuntu needs to do is simply test and send a request to modem.

It will also be easier on ubuntu to detect rather or not connection has been lost.  Line problems however can cause problems, on my mac for instance, if I loose connection, it will not allways get back on, I sometimes have to force to computer to connect again.
thanks for your reply 
i dont need to provide username and password every time 
just sudo pon dsl-provider is enough it doesnt reconnect automatically what to do?

---

### Post by gkraju on 2009-03-20
> **gkraju said:**
> thanks for your reply 
i dont need to provide username and password every time 
just sudo pon dsl-provider is enough it doesnt reconnect automatically what to do?
any body 
please help

---

