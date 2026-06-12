---
title: "PPPOE issue"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by Jay-D on 2007-01-28
Hey there everybody, i was wondering if i could get sum help on this issue. My only way to connect to the internet is through a PPPOE connection. And since Ubuntu doesn't support this out of the box i've been struggling to get this to work, remember i cannot connect to the online repositories since PPPOE is my only way to connect, so my guess i would have to download the packages from windows and copy them to ubuntu and then install them. but how do i do that and what packages and software do i need? Oh yes and i need to know how i can change my MAC address as well.
Thank You

---

### Post by tagginannie on 2007-01-28
> **Jay-D said:**
> Hey there everybody, i was wondering if i could get sum help on this issue. My only way to connect to the internet is through a PPPOE connection. And since Ubuntu doesn't support this out of the box i've been struggling to get this to work, remember i cannot connect to the online repositories since PPPOE is my only way to connect, so my guess i would have to download the packages from windows and copy them to ubuntu and then install them. but how do i do that and what packages and software do i need? Oh yes and i need to know how i can change my MAC address as well.
Thank You

Hi Jay,

Bear with me because I have not used Gnome in 4 years I am  kde gal . First 
You don't need to download PPPoE because it come with Ubuntu. just  click 
System—>Administration —>Networking and click on the type of connection
 you use and enter your ISP information. If you have dialup click on "Enable
 this connection" As for changing your MAC IP address try this site
_[Mac OS X Server 10.2: How to change the IP address]("http://docs.info.apple.com/article.html?artnum=107637")_

Suzy:KS

---

### Post by imihai on 2007-01-28
ubuntu has a pppoe-client . just do in a terminal sudo pppoeconf and answer some questions!

---

### Post by pyrofire on 2007-01-28
> **imihai said:**
> ubuntu has a pppoe-client . just do in a terminal sudo pppoeconf and answer some questions!

dont work for me.

---

### Post by ushaba on 2007-01-28
sudo pppoeconf should bring up the ubuntu version of roaring penguin. this will basically ask you a number of questions you probably don;t understand the answers to,b ut all you really need is the user name and the password for your ISP. i've had quite a bit of experience getting pppoeconf to work if you need and more specific tweaks. the defaults are usually pretty good, but if you need to do anything unusual, that's possible too. :D

---

### Post by Jay-D on 2007-01-28
Thanks Guys It Worked Perfectly!!! I'm posting from my laptop right now where Drapper Drake is up and running!!!!!!! Love Ya!!!!!

---

### Post by pyrofire on 2007-01-28
> **ushaba said:**
> sudo pppoeconf should bring up the ubuntu version of roaring penguin. this will basically ask you a number of questions you probably don;t understand the answers to,b ut all you really need is the user name and the password for your ISP. i've had quite a bit of experience getting pppoeconf to work if you need and more specific tweaks. the defaults are usually pretty good, but if you need to do anything unusual, that's possible too. :D

do i use it for connecting to my local area network?

---

### Post by TheWizzard on 2007-01-28
> **pyrofire said:**
> do i use it for connecting to my local area network?
no. pppoe id for connecting directly to your isp. 
if you have lan, you can just plug the pc into the router.

---

