---
title: "Two Problems - Internet Connection and Open Office"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by kb88 on 2010-03-09
Hi. I am an absolute beginner to Ubuntu. I no longer have access to a Windows computer. I like the operating system a lot but I am having two problems that need to be resolved. (I am not a computer programmer so I don't know how to go into the terminal and just start turning wrenches like a mechanic).

Problem 1. .wps files:

How do I get Open Office to read .wps Microsoft Works files? How do I convert them to something that can be read by OO?

Problem 2. Wireless Internet Connection with the KDE Desktop:

I installed the KDE Desktop but I can't connect wirelessly. The map detects my wireless network and I enter the information like the wepkey but there is no button to actually make the connection and it will not automatically connect. What do I do?

Thank you.

---

### Post by gmjs on 2010-03-09
> Problem 1. .wps files

OpenOffice doesn't have a built-in ability to open Microsoft Works files, so your best bet is to convert them online (I've been told that [http://www.zamzar.com/]("http://www.zamzar.com/") is a good site for this).

There is a library called libwps (available from sourceforge.net) for converting .wps files, but I haven't tried it and it would involve some software compilation (a bit mean if you're new to GNU/Linux).

Perhaps someone else has had success with libwps?

> Problem 2. Wireless Internet Connection with the KDE Desktop

I'm not too hot on KDE4 and wireless, but perhaps you would try the following command in a 'Konsole' window and post the output:

```
~$  **iwconfig wlan0 essid *<your WLAN name>***
```

It should either set the wireless network going, or report a (perhaps useful) error!

---

