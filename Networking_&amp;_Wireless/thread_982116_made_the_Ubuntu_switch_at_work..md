---
title: "made the Ubuntu switch at work."
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by mcorbeil on 2008-11-14
Hello everyone. I've been using Ubuntu at home for a couple years now and think it's great! I have finally installed it via dual boot on my CPU at work.
Almost everything works great but i am having trouble connecting to the internet. I can see the files and folders on the network but firefox cannot connect to the internet.

I am not sure that my CPU is being authenticated on the work network that i believe runs on windows,

I have a username, password, and domain name? Where should i enter this ? Do i need to do anything else? Thanks gang!  :)

---

### Post by anars on 2008-11-14
If you can browse the shared volumes on the network, it seems like you're correctly authenticated on that part of the network. 

But since you're not able to access the Internet, I think you have to specify a HTTP proxy or something like that. 

It all depends on your company's network policy, really. Ask your systems administrator for that information :-)

---

### Post by OMJD on 2008-11-14
"CPU" is not a term for describing a computer. 

Your CPU will resemble this:
[img]http://www.digitalworldtokyo.com/entryimages/2008/01/080130_CPU.jpg[/img]

---

### Post by superprash2003 on 2008-11-15
you might need to connect to your office proxy server.. go to edit->preferences (in firefox) and Go to Advanced, then click on Network.Then under connection click on Settings , and enter the domain name and port there.. then when you try to open a page, it would ask for the username and password.. This is only if your office has a proxy server.. in most cases, this is most likely.Cause , the fact that you are able to access network shares shows that you do have an ip address and you are able to connect successfuly to the network.. if all this doesnt work.. go to the terminal and type ping google.com and post output here.. also post output of cat /etc/resolv.conf

---

### Post by mcorbeil on 2008-11-18
Thanks Gang I'll try that and let you know if it works! Getting pretty tired of using WIN2k  :P

---

