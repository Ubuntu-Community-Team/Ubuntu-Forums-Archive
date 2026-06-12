---
title: "Netowking from a second connection on my Windows XP machine?"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by telliott on 2006-08-05
I had networking running fine on both systems when they were both connected to the router.  I have a second (gigabit) connection on my Windows machine so I unhooked my Ubuntu machine from the router and connected it to the gigabit port on my Windows machine to take advantage of the higher speed.  My Ubuntu machine has a gigabit card.  Both systems used DHCP for file and unternet sharing.

Now, networking and internet isn't working on my ubuntu system.  What do I need to do?  I'm still a Linux noobie.

Thanks,
Tim

---

### Post by ylixir on 2006-08-05
basically, you need to turn your windows system into a router.  you need your windows system to share it's internet with your ubuntu system, or route the internet to your ubuntu system, just like your router routes the internet from the modem to your windows system.

instructions for that are a little beyond this forum imho, but i don't remember it being too terribly difficult.  the option is called internet connection sharing, or something like that iirc.

---

### Post by telliott on 2006-08-06
I got my main computer connecting to my Ubuntu computer.  I gave each computer a static ip address.  I can copy files to and from my Ubuntu computer (only using the main computer).

I still can't connect to any network resource from my Ubuntu computer.  The first time, everything worked without additional setup.

I ran the network setup wizard in Windows and the Ubuntu computer shows both systems under MSHOME but can't connect to my main computer.

I mainly use my Ubuntu computer to watch videos from my main system so the extra speed using the gigabit connection would come in handy

Thanks,
Tim

---

### Post by ylixir on 2006-08-07
[this page]("http://www.practicallynetworked.com/sharing/xp_ics/serverbroadband.htm") has some information on setting up what you need.  you'll have to enable dhcp on your ubuntu box. iirc correctly there is no way to shut off dhcp when winxp is sharing a connection.

---

