---
title: "Dial-up modem help"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by geoff4376 on 2008-02-15
I'd like to start off by saying that I'm a complete amateur when it comes to linux.  I recently installed the newest version of Ubuntu on my computer and I can't get it to even recognize the modem.  Where I live, dial-up is the ONLY option, so I would really like to get this to work.  I tried going through the network settings or whatever it is to put in my u/n and p/w and such, but it would never dial out.  I did manage to get it to dial out a few times by switching the ( I think it was ) location to ttyS3, I think it was, but Firefox wouldn't connect to anything, nor would the add programs thing.  Any help would be appreciated, and again, I am a complete beginner.  I've used Windows all my life ( unfortunately ).  Thank you in advance.

---

### Post by klytu on 2008-02-15
> **geoff4376 said:**
> I'd like to start off by saying that I'm a complete amateur when it comes to linux.  I recently installed the newest version of Ubuntu on my computer and I can't get it to even recognize the modem.  Where I live, dial-up is the ONLY option, so I would really like to get this to work.  I tried going through the network settings or whatever it is to put in my u/n and p/w and such, but it would never dial out.  I did manage to get it to dial out a few times by switching the ( I think it was ) location to ttyS3, I think it was, but Firefox wouldn't connect to anything, nor would the add programs thing.  Any help would be appreciated, and again, I am a complete beginner.  I've used Windows all my life ( unfortunately ).  Thank you in advance.

Please post the output of the following command:

```
sudo wvdialconf /etc/wvdial.conf
``` 

I'll try to help you. To run the command above, go to Applications>Accessories>Terminal and just copy and paste the command above into the terminal window. You could then copy and paste whatever the command spits out into your reply.

---

