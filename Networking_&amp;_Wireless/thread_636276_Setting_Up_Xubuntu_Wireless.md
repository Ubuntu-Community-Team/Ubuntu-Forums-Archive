---
title: "Setting Up Xubuntu Wireless"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by Altin on 2007-12-09
Hi

Ive installed Xubuntu 7.04 on my Toshiba Satellite laptop, and it all went much more smoothly than I had expected to be honest. Im having difficulty setting up my wireless network card now though. 

I followed the Ubuntu Docs on Ndiswrapper, and downloaded & installed it. My system was telling me though that it could not find "lpsci" so I downloaded pciutils and unzipped them. When I try to "make install" them now though I get a screen full of text and still the command will not work. When I try "find lpsci" it tell me it can not find it.

What should my next step be? I was also advised to try "lshw", and that just seems to list my hardware devices. How can I just get my wireless going?

Dermot

---

### Post by jimrz on 2007-12-09
try
```
lspci
```
in terminal and see what it says

---

### Post by Altin on 2007-12-09
Hi

lspci tells me the card is a Ralink RT2500, & lspci -n tells me the chipset is 1814:0201. From the ndiswrapper website I could only download one file, a zip file, which had four folders in it, Win2K, Win98, WinME & WinXP. Im assuming I cant use those? All the other tar.gz drivers on the site gave me a Server Failure error when I tried to download them. Google and its search results all seem to link to those files too.

Is there any where else I can get them from?

Thanks

---

