---
title: "can't get my dlink dwl-122 to work with ubuntu"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by linuxman94 on 2008-03-16
I can't get the dlink dwl-122 wireless usb adapter to work on ubuntu.  I have tried everything I could find and it got me nowhere.  If someone has any help I would very much appreciate it.

Evan

---

### Post by gordintoronto on 2008-03-16
Did you look at:


[https://help.ubuntu.com/community/WifiDocs/Device/DWL-122]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-122")

Good luck,
Gord

---

### Post by linuxman94 on 2008-03-17
yep i tried that and it still won't work

---

### Post by ala.frosty on 2008-03-18
I have the same problem. Unable to get the ndiswrapper working with the .INF either. Gives me an error.

I think the problem is with the configuration. I notice that the iwpriv commands are different for the rt2570 than for the rt2500 and rt73.

```
$ iwpriv rausb0
rausb0    Available private ioctls :
          auth             (8BE0) : set   1 int   & get   0     
          enc              (8BE1) : set   1 int   & get   0      
          wpapsk           (8BE2) : set  64 char  & get   0      
          psm              (8BE3) : set   1 int   & get   0      
          adhocmode        (8BE4) : set   1 int   & get   0     
          get_adhocmode    (8BE5) : set   0       & get   1 int  
          rfmontx          (8BE6) : set   1 int   & get   0     
          get_rfmontx      (8BE7) : set   0       & get   1 int  
          forceprismheader (8BE8) : set   1 int   & get   0    
          get_prismheader  (8BE9) : set   0       & get   1 int 
          get_rtpriv       (8BEB) : set 2047 char  & get 2047 char
```

Now, I'm way too noobie to know what to do with all of this, but I think what generally needs to happen is:

Download the SeaMonkey gz
Remove the offending rt2500usb
blacklist the rt2500 and rt2500usb
fix etc/network/interfaces so that the settings are correct for the rt2570 iwpriv commands. This is the piece that I don't know how to do because I don't know what all those things are. What I do know is that if you use "set WPAPSK=... " like with the rt2500, you get an error but if you use 
```

iwpriv rausb0 wpapsk "yadda yadda yadda"
```

you do not get an error. The only gets that work are "get_adhocmode" "get_rfmontx" and "get_prismheader" .. 

Is there documentation about these somewhere? I'm not sure it would help me. Does anyone know how to use them all? 

Is there one of these that gets the lights on the DWL-G122 B1 to turn on?

Inquiring minds want to know ....

And if we can get to the bottom of this, I promise to put together a "real" step-by-step of how to get the DWL-G122 working with WPA because right now, there's a ton of disinformation about it floating about that just wastes everyone's time.

---

### Post by acad1 on 2008-03-18
Which version of Ubuntu are you using? I am using 7.04 with WEP encryption and the USB device is working OK, but with 7.10 I cannot get it to connect at all.

---

### Post by ala.frosty on 2008-03-18
Version 7.10. Gutsy. WEP worked readily in 7.04. Feisty. Looks fine in Gutsy, but I didn't test it. Unfortunately, my network is WPA-PSK. 

So .. anyone running WEP .. this thread should serve to tell you, "it works" but for those attempting to run WPA, people have reported getting it running, but there are no reliable instructions and a TON of people who have not been able to get it running (from what I've read). If we can put together something that steps through how to get it running from install to Internet, I know this would help a lot of people out.

---

