---
title: "modem doesn't connect"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by new_foo on 2006-11-05
I am using dapper drake, and now when I try to dial out with my modem, it won't connect.  It dails, talks to the isp modem, and according to firestarter, it starts up a ppp connection.  But then it drops or perhaps doesn't actually start a ppp connection.

Here's the weird part.  It used to connect.  I am using a pcmcia modem, and it works since I can connect using it in windows. 

Any ideas on what's going on? Or any ideas on how to track it down?

Thanks in advance.

---

### Post by A. J. Rimmer on 2006-11-05
How are you initiating the connection?  You might try setting up the dial-up connection by running sudo pppconfig, then initiating the connection with pon.  After you do that, you can type in plog and get a report on what the modem is doing and the "conversation" it is having with the ISP's modem.  That might help you with your troubleshooting.

For example, the output of plog might show that you are sending the wrong user ID or password, or that the ISP's modem is hanging up on you (GSTN Cleardown), or some other problem.

Just keep issuing plog over and over again as the handshaking process proceeds and maybe you will see something that will be helpful.

Good luck!

---

### Post by new_foo on 2006-11-05
Thank you, I will try it when I get to a phone.

If only I could get one of my modems to work with ubuntu, I'd spend far less time using windows.  I was playing with my gprs modem using edgy, it seemed to be more reliable than with dapper.  I am going to reload edgy again later to test some more.

By the way, could it be my megahertz modem is just somehow not compatible?

---

