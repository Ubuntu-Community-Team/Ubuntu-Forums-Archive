---
title: "RTL chipset Drivers?"
date: 2016-04-01
forum: Networking &amp; Wireless
---

### Post by ken0069 on 2016-04-01
First let me say that WIFI driver support in Ubuntu and Mint has been EXCELLENT over the past few years and so much so that I'd forgotten what a pain not having the correct drivers in the install could be.  

I recently purchased two N300 USB wireless adapters from Ebay, one for a laptop for a friend I'm introducing to Mint and the other for a desktop in my bedroom.  That bedroom system is running Ubuntu 14.04 with the Mate desktop and the laptop is running Mint Mate 17.3, which was a clean install last week.  

Problem is neither system will recognize the rtl8192**EU** chipset in these new WIFI dongles??  Looking at another system here it seems those USB WIFI dongles have the rtl8192**CU** chipset instead and they are recognized in most anything I plug them into??

Meanwhile, I did find this site [https://sites.google.com/site/easylinuxtipsproject/reserve-7](https://sites.google.com/site/easylinuxtipsproject/reserve-7)  and did get the **EU** driver installed on that Mint 17.3 laptop, but, unfortunately that didn't work with Ubuntu Mate 16.04 as it showed errors during the install.  Bad thing about it though is if a kernel update is done, then they say these drivers won't work afterwards.  

Which begs the question of why isn't support in 16.04 for this "new" **EU** chipset, and, will drivers for it be there in the 16.04 release later this month?

---

### Post by chili555 on 2016-04-01
I haven't any idea when rtl8192eu will be included by default. If you simply want to install the driver, check here: [http://askubuntu.com/questions/741559/wireless-adapter-realtek-0bda818b-problems-used-to-sometimes-connect-now-n](http://askubuntu.com/questions/741559/wireless-adapter-realtek-0bda818b-problems-used-to-sometimes-connect-now-n)

---

### Post by ken0069 on 2016-04-02
IT WORKED!  Thanks for the link, which I seemed to have missed in my searches?  

Next question, does this driver still stay loaded with new kernel updates?  And if so, should I do this install on that Mint 17.3 laptop before I give it back to my friend?  Mint doesn't do kernel updates like Ubuntu so it "may" never be a problem for him?

---

### Post by chili555 on 2016-04-02
>  does this driver still stay loaded with new kernel updates?Yes.

I don't know much about Mint, aside from Julep, so I can't say with certainty what will happen. Since it is based upon Ubuntu, I suspect you'll be just fine.

I'm glad it's working.

---

### Post by ken0069 on 2016-04-02
I guess I better just leave well enough alone on that Mint laptop since it's working OK like it is.  Mint doesn't do kernel updates like Ubuntu does.  You have to go looking for that update and it's not likely my friend will be doing that.  This is a laptop that belonged to his Dad (deceased now) that had Windows Vista on it.  He wanted something more modern so I talked him into trying Mint.  

Thanks again for the reply.

---

