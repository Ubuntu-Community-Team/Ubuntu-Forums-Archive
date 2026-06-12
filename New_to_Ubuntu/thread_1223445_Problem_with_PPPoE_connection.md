---
title: "Problem with PPPoE connection"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by ovroniil on 2009-07-26
I've a PPPoE connection in my home. I connected my Laptop (Dell Inspiron 6400) with that network by typing *sudo pppoeconf*. My laptop connected to the internet successfully and I can browse net smoothly. But in the top panel network connection icon shows the the network is disconnected, that it is always marked by the cross sign (though I can browse the internet). Can any one tell me what is the problem with that cross sign?

Another problem is, every time I shut down (or hibernet, or suspend) I have to run the *sudo pppoeconf* at the next openning. Otherwise my laptop can't connect to internet. Is there any scope to run this command everytime? Instead of running that command can I have a USERNAME and PASS prompt (GUI based) for connecting to internet? I mean I'll only type the username and password and then click connect button then it can austomatically connect to internet.

Thanks everybody

---

### Post by Liolikas on 2009-07-26
> Can any one tell me what is the problem with that cross sign?
I think it shows status of ethX device not pppoe device. So really no problem. You can simply remove it.

For second question read here:
[https://help.ubuntu.com/community/ADSLPPPoE#Boot%20issues](https://help.ubuntu.com/community/ADSLPPPoE#Boot%20issues)

---

### Post by ovroniil on 2009-07-28
> **Liolikas said:**
> I think it shows status of ethX device not pppoe device. So really no problem. You can simply remove it.


Actually I am quite a new one in ubuntu or linux. But what shall I do if I wanted to show the "status is connected"? 

As you say to remove it - How can I remove that?

Thanks for help!

---

