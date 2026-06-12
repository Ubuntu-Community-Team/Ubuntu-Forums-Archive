---
title: "Netgear wireless router"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by ajd79 on 2010-03-23
OK so I just made the switch from windows. I run a dual boot now.  I love the interface. it runs so smoothly. I am a firefox user to begin with and the fact that it was included was nice. 

My problem, I can not for the life of me connect to the internet via my wireless router. Netgear router, blah blah blah. i tried the mac address and everything that i could but it wont show the network as available at all. Help please. I am really new here. (first 8 hours as a user)

---

### Post by Ghost|BTFH on 2010-03-23
#1: Is your wireless router broadcasting?
#2: Are you using Ubuntu 9.10?
#3: Is your wireless router open or secured with a password?
#4: When you search for available wireless connections, what is it showing?
#5: Are you sure your wireless card is being seen and is supported?  Can you tell us what the make/model is of the card, or at least the computer so we can check out who makes the wireless card for it?

When you need help, help is here...just remember to be as detailed as you can be on the problem at hand and what you're running. :)

Cheers,
Ghost|BTFH

---

### Post by Peter09 on 2010-03-23
Can you post the output of the terminal commands
```
ifconfig
```
and
```
lshw -C network
```

---

### Post by howefield on 2010-03-23
You could try connecting to the router with an ethernet cable, then in terminal, (Applications > Accessories > Terminal) type the following..

```
sudo apt-get update
```

Followed by your password when prompted, you won't see the password being entered but it will be.

Let it finish then try System > Administration > Hardware Drivers to see if there are drivers for your wireless adapter available for install.

---

### Post by ajd79 on 2010-04-23
thanks I found the issue.  My ubuntu disc was OOOOLD lol i updated and was fine. thanks

---

