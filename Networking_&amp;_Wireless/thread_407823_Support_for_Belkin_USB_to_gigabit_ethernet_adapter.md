---
title: "Support for Belkin USB to gigabit ethernet adapter?"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by Peepsalot on 2007-04-12
I am thinking about getting this product or something similar: 
[http://catalog.belkin.com/IWCatProductPage.process?Product_Id=281799](http://catalog.belkin.com/IWCatProductPage.process?Product_Id=281799)
Part number F5D5055

I was just wondering if anyone knows if this is supported under linux?

And yes, I realize USB 2.0 doesn't even go up to 1gigabit of bandwidth, but with any luck I think it should be 3-4 times faster than standard 100Mbit LAN.

---

### Post by Peepsalot on 2007-04-13
I actually ended up getting a different but very similar product.  
[Linksys USB1000](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1124916753255&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5325522279B18)

I wil return it if I can't get it running in the next few days.  I am currently trying to get it working with ndiswrapper, but running into some problems.  It will not load the kernel module, and gives an error saying "Invalid Argument".

---

### Post by Peepsalot on 2007-04-14
Got the Linksys working today. I did a couple tests to measure the max speed.

Using netcat, I sent a 100MB file full of random data over my gigabit LAN and measured the speed.  I did each test once sending the file one way then again sending it the other direction.

Control group onboard 100Mbps link:
87.9Mbps up / 94.2Mbps down
USB1000:
216Mbps up / 270Mbps down

I wonder if the Belkin would fare any better.  Also, i'm not sure if the hard drive that stores the 100MB is the bottleneck in this test.  I would like to load the file completely into RAM before running the test, but I have yet to figure out how to do that.  I think Linux should automatically cache it in ram anyways, but maybe that is unpredictable.

I read somewhere that the maximum speed in the specification for USB is 480Mbps, but in practice the best you can get is about 320Mbps.

---

