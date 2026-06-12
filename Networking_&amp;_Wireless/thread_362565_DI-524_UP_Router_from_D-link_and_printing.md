---
title: "DI-524 UP Router from D-link and printing"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by the_zoor on 2007-02-15
So here is the problem. I have a router from D-Link with a printing server. Under Windows this works good with WLAN. However in ubuntu I found that the lpr option under network printing options wasn't there. Its impossible to print to lpr? Am I forced to plug it in to my usb port?

I thought I had the problem when I searched for lpr and found it. I installed it using apt-get install lpr. Worked great. But no change what so ever. The printer I'm trying to install is a brother HL-1430. I have the driver from brothers homepage and all. But still. My router only uses lpr as its system... which makes the cups alternative useless for me I guess.

Is there a way to give the Ubuntu standard printer software the ability to print to lpr?

This problem is making me crazy since I cannot just simply plug it in to my usb port since alot of other computers in my network uses it from WLAN. This was the plan for this computer aswell, but it wasn't as easy as I thought :)

Any help would be appreciated.

---

### Post by the_zoor on 2007-02-18
No one knows what to do? :(

---

### Post by bill-linux on 2007-03-01
I just posted this for another questions. The correct "lpr" packages for Ubuntu is cupsys-bsd. This installs the lpr commands for the cups system. (The default for Ubuntu is cups printing system: I assume you are using that.) Note that the Ubuntu repository also offers the package lpr -- this will NOT work with cups (at least not easily).

---

### Post by the_zoor on 2007-03-04
Ok... this is where you lost me. What does the cups driver has to do with anything? I thought I only had to install the lpr driver. I'm totally lost. Is there any step-by-step guide out there? :'(

Now I've gotten so far that the printer react and realize that it actually gets info from my computer. But thats it. I get the message "printer did not accept the info" or something similar to that. What in earth can I do to make the *#%/)%!!!! printer to work?

Best Regards, the_zoor

---

### Post by doncristobal on 2007-07-08
Maybe this can help: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)
it's how i solved a very similar problem with my siemens router and hp printer

Good luck!

---

### Post by Joe325 on 2007-08-13
I have a similar problem involving LPR.
I have a HP6180 network  printer attached wirelessly to a Billion 7300G router.
The printer installs no problem on the network but when I try and print from Quickbooks, it states it will print to HP.... on LPR..... and it just sits there.
I can print from any other app but when I need an invoice printed, It doesnt want to play.
I have an Epson CX3700 locally installed and it too, wants to print to LPR but I get nothing.\

As stated above, I also found lpr from the sources and I noticed it removed cupsys-bsd on install.... But I still have the same problem
Anyone know how to attack this one.........

---

