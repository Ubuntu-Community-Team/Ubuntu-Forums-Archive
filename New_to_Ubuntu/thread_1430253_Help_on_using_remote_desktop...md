---
title: "Help on using remote desktop.."
date: 2010-03-15
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-15
I am using **ubuntu 9.04,**i would like to use Remote Desktop feature to access my friends Desktop..But my friend is running **Windows XP**,So is it possible to access his Desktop from Ubuntu..?If so pls explain it in detail..

---

### Post by karthick87 on 2010-03-16
Bump...

---

### Post by lotharmat on 2010-03-16
go to Applications --> Internet --> Terminal Server Client (I think it is installed by default) if not use Synaptic or Software centre to locate it!

---

### Post by NickJones on 2010-03-16
[http://ubuntuforums.org/showthread.php?t=100592](http://ubuntuforums.org/showthread.php?t=100592)
Remember, search is your friend.

---

### Post by kalasoka on 2010-03-16
Use VNC client from your machine (already available with Ubuntu). Your friend probably would require to install the VNC server on his desktop. And then you can access and view his machine remotely.

---

### Post by BitJunkie on 2010-03-16
I have had success using tsclient to connect to Windows boxes.

---

### Post by CharlesA on 2010-03-16
Is it going to be accessed over the internet? That can get a bit tricky, otherwise use the TS client.

---

### Post by sikander3786 on 2010-03-16
> **getyourkarthick said:**
> I am using **ubuntu 9.04,**i would like to use Remote Desktop feature to access my friends Desktop..But my friend is running **Windows XP**,So is it possible to access his Desktop from Ubuntu..?If so pls explain it in detail..

The easiest way is to enable Remote Desktop from Windows XP and access it through Terminal Server Client installed by default in Ubuntu under the sub menu "Internet".

I have been doing this for some time. You don't need to install additional software.

Regards.

Sikander.

---

### Post by karthick87 on 2010-03-18
In terminal server client.,what should i give in computer field?And what should i give in username and password field?Which username and password?Is that windows username and password..?

---

### Post by sikander3786 on 2010-04-05
> **getyourkarthick said:**
> In terminal server client.,what should i give in computer field?And what should i give in username and password field?Which username and password?Is that windows username and password..?

In the Computer Name you can either enter the Windows XP Computer Name or its ip address. The user name and password is the same that you use to login to your XP install.

---

