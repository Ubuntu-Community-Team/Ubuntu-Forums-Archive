---
title: "Need help ubuntu and Linksys wireless router"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by katherine48 on 2009-11-03
I recently downloaded Ubuntu on my laptop and now am unable to get a connection to my Linksys wireless router.  I know the problem is not the router because I have another laptop with a Windows O/S which is working just fine;  that's why I am able to type this note right now....

I went to the help page to troubleshoot the wireless router connection and first step is to make sure it is on, second step is to enter a command which tells you if the system is disabled, etc.  My router shows up as "disabled" on this exercise, and I am directed back to step 1 to make sure the router is on.   I already know the router is on because it is working fine with my other laptop.  

There is no other explanation of why I might get "disabled" status on my laptop using Ubuntu when the router is working fine with Windows.  Help?

---

### Post by The Funkbomb on 2009-11-03
Welcome to Ubuntuforums and the Ubuntu Operating System.

If I am correct, I think there is some bad communication.  It isn't your router but your wireless networking card.

What is the command you put in to check your wireless card?  iwconfig?

What wireless card are you using?

---

### Post by katherine48 on 2009-11-03
I went to 5.2.2 of Unbuntu help, and in step 2 it instructs to open a terminal and enter

sudo lshw -C network

when I do that, i get a lot of stuff including the word "disabled."  The help instructions then tell me to go back to step 1 and make sure the router is on, which it is.  It is an endless do loop.  There is no alternative for the situation where you check the router and it is on but you get the message "disabled."

I don't know what wireless card I have, how would I find out?   Sorry for my ignorance.

Thank you.

---

### Post by jimmy the saint on 2009-11-03
can you please open a terminal Programs>Accessories>Terminal and type in 

```
lspci
```

Then copy and paste the results here?  This will list all of you PCI devices and allow us to help you more.

---

