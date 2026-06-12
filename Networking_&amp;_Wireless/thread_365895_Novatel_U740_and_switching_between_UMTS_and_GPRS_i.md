---
title: "Novatel U740 and switching between UMTS and GPRS in Ubuntu..."
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by applecookie on 2007-02-20
Hi there :)

After I got my novatel u740 merlin hsdpa card work under ubuntu, I have another little problem which I hope to get some answers here.

Because I don't find any help about the AT command set of the U740 and the at_opsys command doesn't work with this card:

How can I switch between GPRS and UMTS in Ubuntu with this card

that means, which commands will I have to send to the card to do this.

I don't want to use the winxp software dashboard to do this everytime, I need to switch.

Regards
Frank

---

### Post by applecookie on 2007-02-20
I got it myself (hurrah) :popcorn: 

Let's use a terminal program like minicom and send the following lines to the card after initializing it:


AT$NWRAT?

to see, what is the prefered network (GPRS or UMTS/HSDPA)

1,2,x = GPRS
2,2,x = UMTS

(I don't know the third parameter till now but it seems not to be very important)

AT$NWRAT = 1,2  to switch to GPRS
AT$NWRAT = 2,2  to switch to UMTS /HSDPA

Regards
Frank

---

