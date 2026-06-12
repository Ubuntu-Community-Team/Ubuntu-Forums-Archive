---
title: "WUSB54GC problem with Drake"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by ruffEdgz on 2006-08-15
I have searched these forums and found 6 different posts about it and most of them said to go to the site below:

[http://www.cicerosonline.com/WUSB54GC/](http://www.cicerosonline.com/WUSB54GC/)

I went to it and followed the instructions to the 'T' but I am having problems with it connecting since it keeps freezing on me after a short time when it sees the wireless card in the Network Management section of Ubuntu (I'm a noob to Ubuntu if you don't already know). I have read the other six threads and have posted my problems in sections of this forum that I think were in the wrong ones.

If anyone could make sense of this problem or give me some reasons to why the OS could freeze up, that would be wonderful. 

I would also like to say that I am using 2WIRE DSL as my provider if that helps and I can give you any other information if you need it but I don't know what would be important to display at this time. 

Thank you to whom ever can help and take care

|2uff

---

### Post by wieman01 on 2006-08-16
Actually I have a "WUSB54G V4" and use it with "ndiswrapper" for the sake of simplicity. There are tons of posts in the forum that will help you with the setup. Try to avoid native driver, they are usually quite a hassle when your card is not recognized out of the box.

[http://www.linuxquestions.org/linux/answers/Networking/NDISwrapper_for_RTL8180_mini_HOWTO]("http://www.linuxquestions.org/linux/answers/Networking/NDISwrapper_for_RTL8180_mini_HOWTO")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#What_is_ndiswrapper.3F]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#What_is_ndiswrapper.3F")

---

### Post by ruffEdgz on 2006-08-16
I will read those sites you have listed above and get back to you if they work or any other questions about them on this post.

Thanks

---

### Post by Thyamine on 2006-08-17
I had a lot of random issues with trying to get it installed, but in the end I used ndiswrapper ( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation) ), and the drivers from the CD that came with the NIC.  

I had to install unshield ( sudo apt-get install unshield ) to extract the driver files from the data1.cab file on the CD though, since the .inf file wasn't available otherwise.  

I believe the directory needed is WINXPTarget.  

I haven't been using it all that long at this point, but I haven't seen it lock up yet.

---

