---
title: "How to share internet connection using my wireless card?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-23
I've internet connection through ethernet cable, also i have a wiress card up and running,
what i need is how to share my broadband connection so other laptops can access the web
thanks in advance

---

### Post by Isyaltut on 2010-07-23
Just click network icon and create new wireless connection. Your other computer should detect that network and can surf the internet from there.

---

### Post by hhh on 2010-07-23
Short answer, use a wireless router...
[http://en.wikipedia.org/wiki/Wireless_router](http://en.wikipedia.org/wiki/Wireless_router)

Long answer...
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by uRock on 2010-07-23
> **Isyaltut said:**
> Just click network icon and create new wireless connection. Your other computer should detect that network and can surf the internet from there.
It isn't that easy. You would have to install DHCP server to give the other hosts an IP to connect with. You are basically setting up your PC to work as a router for the other hosts. There may be more to it than this. I haven't actually set it up yet, though I have been pondering it.

Edit: hhh's link [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) explains it very well.

---

### Post by Isyaltut on 2010-07-23
> **uRock said:**
> It isn't that easy. You would have to install DHCP server to give the other hosts an IP to connect with. You are basically setting up your PC to work as a router for the other hosts. 

Wow, you make it sounded harder. My method above is actually really work for me and I've done it almost everyday to share internet connection with my sister's laptop. I use open (no password) when I make new wireless connection. WEP or WPA doesn't seems to be working, at least in my experience.

---

### Post by uRock on 2010-07-23
> **Isyaltut said:**
> Wow, you make it sounded harder. My method above is actually really work for me and I've done it almost everyday to share internet connection with my sister's laptop. I use open (no password) when I make new wireless connection. WEP or WPA doesn't seems to be working, at least in my experience.
Is your sister's PC the one with the connection?

---

### Post by Bachstelze on 2010-07-23
> **uRock said:**
> It isn't that easy. You would have to install DHCP server to give the other hosts an IP to connect with.

Wrong.  DHCP is not required, the other hosts can be configured with static IPs.

---

### Post by uRock on 2010-07-23
> **Bachstelze said:**
> Wrong.  DHCP is not required, the other hosts can be configured with static IPs.
That is why I seconded hhh's link. It shows how to do it without DHCP server, but if your want it to issue IPs the way a router does, then it will be needed.

---

### Post by Grenage on 2010-07-23
> **Isyaltut said:**
> Wow, you make it sounded harder. My method above is actually really work for me and I've done it almost everyday to share internet connection with my sister's laptop. I use open (no password) when I make new wireless connection. WEP or WPA doesn't seems to be working, at least in my experience.

I have found the same, and that caused me to bail on the task.  The hotel only had cabled internet, and my wife has an iphone; it wasn't worth spending too much time on the problem.

---

### Post by Isyaltut on 2010-07-23
> **uRock said:**
> Is your sister's PC the one with the connection?

Nope, my Ubuntu box is the one which is connected to internet cable. It's one more reason to love Ubuntu, it is so easy. In Windows you have to create a new ad-hoc connection to share internet everytime you shutdown the computer, while in Ubuntu you do not need to. 

It is not hard, but I'm too lazy to do that. ;)

>  The hotel only had cabled internet, and my wife has an iphone; it  wasn't worth spending too much time on the problem.

What is the problem really? I also have an iPod Touch and it detect my Ubuntu shared internet connection just fine to surf the internet. Why you need to do that though? It's an iPhone. It surely can surf the internet without wifi. Now my iPod Touch, that's different of course.

---

### Post by Grenage on 2010-07-23
> **Isyaltut said:**
> What is the problem really? I also have an iPod Touch and it detect my Ubuntu shared internet connection just fine to surf the internet. Why you need to do that though? It's an iPhone. It surely can surf the internet without wifi. Now my iPod Touch, that's different of course.

I wasn't willing to use it without encryption.  We were in America, and the roaming data charges were ridiculous.

---

### Post by MBG1987 on 2010-07-23
> **Isyaltut said:**
> Just click network icon and create new wireless connection. Your other computer should detect that network and can surf the internet from there.

It works very nice and clean, thank you
but will you please show me how to do it via terminal 
also much depreciation to all of you

---

### Post by uRock on 2010-07-23
> **Isyaltut said:**
> Nope, my Ubuntu box is the one which is connected to internet cable. It's one more reason to love Ubuntu, it is so easy. In Windows you have to create a new ad-hoc connection to share internet everytime you shutdown the computer, while in Ubuntu you do not need to. 

It is not hard, but I'm too lazy to do that. ;).
I guess I stand corrected then. I will have to give it a try. I have a netbook that has to be within 10 feet to connect to anything. I'll never buy another Asus.

---

