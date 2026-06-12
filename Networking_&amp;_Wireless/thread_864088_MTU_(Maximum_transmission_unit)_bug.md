---
title: "MTU (Maximum transmission unit) bug"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by fib1807 on 2008-07-19
Can anyone help me with a command-line for changing/setting MTU 

Any help will be appreciated.

---

### Post by bab1 on 2008-07-19
```
ifconfig -mtu [COLOR="Magenta"]nnnnn[/COLOR][COLOR="Blue"] eth0[/COLOR]
```

Where nnnn is your MTU size and eth0 is your interface.  Don't go above 1500 MTU.

---

### Post by ModelM on 2008-07-19
For the folks on dialup reading this thread: the Maximum Transmission Unit (MTU) & the Maximum Receive Unit (MRU) values can be changed within the file:

/etc/ppp/options

---

### Post by fib1807 on 2008-07-21
Thanks friends. I've been using lo (I honestly dunno why ?) My MTU was  16000 so I cut it down to 9500.1500 ain't working on lo is it different for different devices ?
lo,pppo,etho ?

Thanks again.And if it's a wrong way of asking just Kick my *** and please enlighten me with the real concept behind MTU. I will be thankful fo' dat too coz I'm an absolute noob.:)

---

### Post by fib1807 on 2008-07-21
And also I wanted to know if I could save the settings..you knw....err..each time I need to set that MTU thing.So could u ppl please temme a CL fo' saving my MTU config ?

---

### Post by ModelM on 2008-07-21
The lo interface is called the "local loopback". It does just that - loops from one port of the computer back into another port.

There are many processes running in your computer and many of these need to communicate with each other. To each process the communication path "looks like" a network interface. The lo interface is what is used for this process intercommunication.

Since this phantom interface does not handle any packets leaving or entering the computer, only within it, changing it's configuration will have no effect on Internet speed or local LAN performance.

In other words, there's no need to mess with the lo interface.

---

### Post by fib1807 on 2008-07-23
Thanks for that info and Do you mean to say that lo has nothing to do with internet ?

---

### Post by ModelM on 2008-07-23
That's right. The lo interface has nothing to do with the Internet.

---

### Post by fib1807 on 2008-07-29
The window of my Firefox used to change from orange to Grey (It used to get crashed) within no time.When I changed MTU of lo (by default 16000 circa) to 9500,10000,10500 etc my net seemed to be running smoothly so I was wondering if it had changed all the problem I was facing and so I put up that lo question.Even if it didn't have any effect on internet would changing the MTU would change overall MTU or something ? Please :D help me.

---

### Post by ModelM on 2008-07-29
My advice would be to put lo & all the other interface settings back to normal and only then work on your Firefox problem. I think you're looking in the wrong place.

---

### Post by fib1807 on 2008-08-01
Ohh! I'm sry that I'm troubling u a lot but..Can u please suggest me another fix ? Firefox crashes in every 15 min and after that no net.

---

### Post by Basildon John on 2009-11-01
> **bab1 said:**
> ```
ifconfig -mtu [COLOR=magenta]nnnnn[/COLOR][COLOR=blue] eth0[/COLOR]
```
 
Where nnnn is your MTU size and eth0 is your interface. Don't go above 1500 MTU.
 
I live in the UK and use a broadband provider called talktalk. Their MTU rate is 1430 instead of the normal 1500. I have had to adjust my other computers to run at this lower MTU speed, otherwise it takes ages for even one page to load.
 
I would now like to make a similar change on my Acer netbook. Since loading Ubuntu 9.04 it is running much better than the factory loaded linux but when using talktalk it cannot play music (but it can play music when I am visiting my son in Spain)
 
So how do I make the change? I can see the advice above but how do I find the part of the programme where I need to make a the change and/or insert new instructions? change. I am a silver surfer, not a geek, so the simpler the advice/instructions, the better!

---

### Post by Basildon John on 2009-11-01
In case others are interested I have found instructions which have enabled me to solve my problem of pages loading very slowing and music not playing 

[http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

I found that an MTU setting of 1430 is giving the best results - my broadband supplier being talktalk and my test item being organ music by Handel81 on You tube

My Acer netbook is now fully functional !!

Basildon John

---

