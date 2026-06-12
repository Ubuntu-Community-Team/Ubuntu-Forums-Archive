---
title: "Why doesnt my Ubuntu Setup Not Finding DHCP Server"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by kustomjs on 2007-11-11
Hi Guys
I need to know why when I do the setup through the cd the DHCP server isnt finding it? I am behind a linksys router and I got DHCP server enabled what else can it be?

---

### Post by scrooge_74 on 2007-11-11
Is your network card been detected? What model do you have?

---

### Post by kustomjs on 2007-11-11
detectes it and the onboard lan is innet/stewart onboard lan card

---

### Post by SpiritIsReality on 2007-11-11
howdy
I don't know for sure, but while we're waitin for somebody to come up with the right answer, here's some links that might help
[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
trails
can you ping the router? if you run the live cd ?
have you tried cancelling the dhcp detect network step and give your pc a static ip address?

will the live cd run on your computer? 
do you have a microsoft os on your computer we can use?
if the live cd will run, you click on Applications > Accessories > Terminal
you type at the command line
ping your_router's_address
press the enter key
it will show your computer sending signals to the router
press and hold down the ctrl key, and press the c key. , then release the ctrl key. that stops the pinging., and tells you with a message
whether the signal  reached your router.
ping 192.168.0.1
or
ping 192.168.1.1
will usually work, if you don't know what your router's address is, or check the manual for the router or the manufacturer's web page by 
typing your router's make and model in the box here [http://www.google.ca/](http://www.google.ca/)
hope all goes well. If not, you can post back here with a question.
trails

---

### Post by Peter09 on 2007-11-12
I think the problem is not that your machine does not find the DHCP server, my DHCP server list all my current machine and they are allocated IP addresses by it. The problem is that Name Resolution (part of the DHCP service) does not work. This means that you cannot access machines by Host Name.

If this is your problem you will be able to ping machines and mount shares by IP address. Pinging by host name will not work.

---

