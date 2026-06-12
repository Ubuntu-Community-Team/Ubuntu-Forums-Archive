---
title: "Get service list"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by iitywygms on 2006-12-20
Okay
I have been able to get bluetooth working in Edgy again. (almost)  You can see what I did to make it work (almost) by going to this thread.  [http://www.ubuntuforums.org/showthread.php?p=1909290#post1909290](http://www.ubuntuforums.org/showthread.php?p=1909290#post1909290)
The phone can see the computer and vise versa.  I can send files to the phone.  Still cant send files to the computer.  When I try to send something to the computer it says "get service list" then it says "service list not found, try again?"
What is a service list.  What is it asking for?  I never see it do this when sending to my windblows computer.
Thanks in advance.

---

### Post by iitywygms on 2006-12-20
anyone heard of this? I cant find anything on google or anywhere.

---

### Post by iitywygms on 2007-01-08
From some research I have figured out that the service list it is looking for is a list of things that can be done with bluetooth.  Such as, internet connection, wireless head set, file transfer, etc.
SO, I need to turn these things on.  Is there a place or file in edgy that has a list of thses options, and a way to enable or disable them?
Thanks.

---

### Post by zeddock on 2007-05-22
Have you found any answers?  I was kinda lurking here because I have same issue.

zeddock.

---

### Post by zeddock on 2007-05-25
Son of a gun!

I found the problem and my answer.  Actually I probably will do a bug report in LaunchPad for it.

Bluetooth was not working but I didn't know why. I decided to eliminate the variable of the physical BT adapter, by loading up a windows HD. (I knew it worked before switching to Ubuntu.)

IN BIOS of my Dell Latitude D|800, I have set to app and function-key control of bluetooth. In fact, both of those methods can work to turn the BT on and off... but there is a third way, under windows XP... you can DISABLE BT from the little BT icon in the system notification tray!

I don't know what that does. I always thought it was the same as the other switches to turn on and off... but it is not!

Once I enabled this, my lil' blue light came on in the lights of the computer, and upon booting into ubuntu again, bluetooth works nicely.

zeddock

---

