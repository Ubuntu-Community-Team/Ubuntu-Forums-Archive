---
title: "Wireless not strong enough"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by airbornemist6 on 2008-05-09
Is there any way to pretty much force my wireless card to boost it's signal? I know in windows you can make one extend it's range by editing the driver and SLIGHTLY overvoltaging it. Is there any way to do anything similar in linux?

---

### Post by BallsOfSteel on 2008-05-09
I've personally never heard of this... but why don't you just grab a higher dbi gain antenna?  Possibly a Cantenna?  You could use either on your router or your wireless card.

Brandon

---

### Post by airbornemist6 on 2008-05-09
I want to, but frankly I don't have the money and don't want to lug it around. much less, go through hell trying to get it to work in linux.

As far as the process, I didn't know it was possible either until my girlfriend showed me how to do it. Evidently it voids your wireless card warranty, but it doesn't damage it... if you don't overpower TOO much.

---

### Post by tashmooclam on 2008-05-09
Get an Intel wireless card.

---

### Post by BallsOfSteel on 2008-05-09
Get what trying to work in linux?  A Cantenna or higher gain dbi antenna are just that... antenna's.  No configuration is needed to use them in Linux.  As long as you have a wireless card that has an external antenna, you can hook it up to the rpsma connector.  

You can probably find a Cantenna in Circuit City for $50 if you want that.  For another antenna that isn't large, but gets the job done, you shouldn't have to spend more than $30 at a Radio Shack.  

Keep googling for a hack on increasing the voltage.  I imagine it would require some altering ofthe driver for your wireless card.  Find the driver your system and look into it.  See if there is anything you can decipher from it.  I'd be interested to know if you get anywhere.

Brandon

---

### Post by airbornemist6 on 2008-05-10
My problem is, it's an internal antenna. This is a laptop I'm talking about, so I don't have the luxury of an external, it would take a card to interface with the internal. As far as modifying drivers, I just remembered I'm using NDISwrapper so I should be able to alter the driver without much trouble.

---

### Post by BallsOfSteel on 2008-05-10
I'm guessing just modify the driver first and THEN install it using ndiswrapper.  Let us know what you do and how it goes.  That could be beneficial to some people here.

Regards,

Brandon

---

### Post by airbornemist6 on 2008-05-11
heh it appears my card doesn't like that, it just turned off. i tried it in windows and it did the same thing, so oh well there goes that idea.

---

### Post by chili555 on 2008-05-11
From *man iwconfig*:> txpower
              For cards supporting multiple transmit powers, sets the transmit
              power in dBm. If W is the power in Watt, the power in dBm is P =
              30 + 10.log(W).  If the value is postfixed by  mW,  it  will  be
              automatically converted to dBm.
              In  addition,  on and off enable and disable the radio, and auto
              and fixed enable and disable power control  (if  those  features
              are available).
              Examples :
                   iwconfig eth0 txpower 15
                   iwconfig eth0 txpower 30mW
                   iwconfig eth0 txpower auto
                   iwconfig eth0 txpower offWhen I run *iwconfig eth1* I see the txpower is already at the max, in my case, 27 dBm. I have no trouble adjusting down, but I haven't found a way to go over the maximum.

You might also see if the router (my WRT54G does) allows you to adjust the transmit power up. You might also select a less noisy channel, say channel 1 or 11.

---

### Post by airbornemist6 on 2008-05-11
oh cool, i didn't know that command... i'm still somewhat new at many aspects of linux, evidently that's one of them, thanks

---

