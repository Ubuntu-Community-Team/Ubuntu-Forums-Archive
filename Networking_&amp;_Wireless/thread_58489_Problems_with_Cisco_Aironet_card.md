---
title: "Problems with Cisco Aironet card"
date: 2005-08-20
forum: Networking &amp; Wireless
---

### Post by Talomon on 2005-08-20
hi there

I was playing around with my wlan and now it seemes that I broke it. 

It doesn't want to have an essid, when I type "iwconfig eth0 essid xxx" it ignores me. =) When I directly after type "iwconfig eth0" there is no change in essid. It is still "". Really strange. To sum it up, I can't use my wireless network card that worked perfectly before...

I've looked at what dmesg sais, and this is what it sais:
airo: status= 7f03
airo: Rsp0= 0
airo: Rsp1= ff11
airo: Rsp2= 0
airo: cmd= 103
airo: status= 7f03
airo: Rsp0= 0
airo: Rsp1= ff11
airo: Rsp2= 0

I really appreciate any help I can get in this matter, please tell me if you require aditional information about this matter. I don't really know if these errormessages are helpful. 

Once again, I appreciate any help I can get. Thanx all

***************************************************************************

A small update about my problem.

I finally solved it by reinstalling linux ( everything can be solved with violence and reboot, or in this case, reinstall ). After the reinstall I was in a blissfull state of having a new and fresh OS to play with. 

After testing that the wireless actually worked, which it did. I set of installing all the nice gadgeds this wonderful community had to offer. And how wonderful they were.

It was when I installed Gtkwifi, and associated packages that the wireless network died on me...again. And I got the same errors as before, I was back to square one so to say. 

What I didn't realize at the time, was that I was installing Gtkwifi when my wireless...for a lack of a better word, died on me.  (I was doing a lot with my wireless at the time.) Yet another reinstall solved that problem though. =)

Now I'm sitting here, writing on my laptop, on the wireless, but without Gtkwifi.

To me this is really strange, Gtkwifi seemes to be a wonderful applet and it seemes to work fine on most computers. I'm really wexed why it doesn't seeme to work on mine...

If you have any insight in this problem, I would be happy to hear it.

---

