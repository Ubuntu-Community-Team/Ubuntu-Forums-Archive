---
title: "How can I establish wireless connection..?"
date: 2009-05-28
forum: New to Ubuntu
---

### Post by eatyourvegetables on 2009-05-28
I just had Ubuntu 9.4 installed today. I am very new to Ubuntu, and have been messing around with it to try to get the hang of it. No matter how much I do, however, I cannot establish a wireless signal from my router, though I had no problem with that when I was using Windows XP. Any suggestions on how I can get this connection? I feel like I've tried everything! :confused:

---

### Post by vejan on 2009-05-28
need info on your wireless card

list what lspci says here- to see if ubuntu finds your card

---

### Post by raymondh on 2009-05-29
Hello Eatyourvegetables,

As Vejan had mentioned, we need to see what your wireless card is to get us pointed in the right direction.

You will need a TERMINAL (applications > accessories) and type (or copy&paste) this command

```
lspci -v | less
```

This will print out the PCI cards in your system. Kindly post back the output.

Some basic troubleshooting (this may sound silly but it'll help if we know what you have done so far with regard to your issue):

1.  On the network icon (top right of your desktop), if you right click, is ENABLE NETWORKING ticked?
2.  Same icon > edit > wireless ... have you added your router and password (if any)?  Is the password WPA, WEP??
3.  Have you enabled/installed the necessary drivers for your hardware? Though I'm thinking we need to find drivers ...
4.  Did you try out the LiveCD?  If so, did you try out wireless and did it work then?

Here is a link for the supported wifi card list for your reference

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Regards,

---

