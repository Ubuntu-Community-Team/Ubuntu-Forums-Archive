---
title: "slow to print documents"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by ajdrew06 on 2010-12-07
Hi All,

I am having an issue when I print documents (to a physical printer).  When I print, I see the document in the print queue, and it stays there for 5-10 minutes before my printer actually begins to print the document.  Any ideas as to what may be causing the lag?  If I queue 2 or 3 documents, there is a 5-10 minute delay before the first document and then a 5-10 minute delay between documents.

I downloaded and installed cnijfilter-common_2.80-1.i386.deb and cnijfilter-mp210series_2.80-1_i386.deb as my "drivers" for my Canon MP210. These files have been installed for as long as I have been running Ubuntu.

When I initially installed 9.04 32 bit, I had no problem printing. Then the issue started (seemingly out of no where).  I recently did a fresh install of 10.04 32 bit, and I have the same issue. However, I have had the issue the entire time I have had 10.04 32 bit.

Any help would be appreciated.  I am happy that I have a working printer, but it is frustrating that I have to wait (seemingly) forever to print.

By the way, there is no delay if I print to file.

Thank you in advance for your help!

-ajdrew

---

### Post by elphaba on 2010-12-17
The printer I'm using is a Brother hl-2170W wireless printer.  Not sure if this will work for you but according to this guy on the blog at this link at:
[http://mikebeach.org/2010/06/ubuntu-and-brother-hl-2170w/](http://mikebeach.org/2010/06/ubuntu-and-brother-hl-2170w/)

he found that there was a fault in the cups drivers (at least for this model, maybe yours too).

He gives a very nice step by step instruction for those of us with the HL-2170W.  If you are using a different printer, you likely will need to work on step 8 in his instructions where he writes that you should enter for the field for "Model":
 Generic PCL 5e Printer Foomatic/hpijs-pcl5e

You probably need to do a forum search for "generic driver" and whatever your printer model is if you don't know what it is at this point. 

Good luck.

---

