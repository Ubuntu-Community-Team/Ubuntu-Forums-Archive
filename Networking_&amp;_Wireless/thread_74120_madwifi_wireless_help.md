---
title: "madwifi wireless help"
date: 2005-10-10
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2005-10-10
I would really like to try ubuntu.  I tried the live CD's for 5.04 and 5.10.  The live CD for 5.10 works with my wireless card out of the box.  I was really impressed.  The only problem is that I also need to install ubunut on an external USB hard drive.  I tried using a step-by-step how to that someone wrote for 5.04, but it didn't work.  So, I thought I would try 5.04.  My wireless card seems to be detected, but it cannot find my router (iwlist shows nothing).  The card shows up and is more or less working correctly in ifconfig and iwconfig.  I am running WEP with an open key and that is listed as working on the Supported hardware wiki page (I also tried turning the encryption off).  The card is a Dlink DWL-G650.  Like I said, I want to try ubuntu but I don't want to spend a ton of time wrestling with the wireless stuff (and I would gladly use 5.04 or 5.10 as long as I can get them installed on my usb hard drive).

I also tried a dmesg | grep ath_pci and got a driver number of 0.9 something experimental.

How can I know if wireless is going to work if I go through the trouble to install ubunut?

Thanks,

Ryan

---

### Post by firecat53 on 2005-10-11
Hmmm...two options as I see it:

1. Wait until the 13th and download the final installable version of Breezy (5.10) which sounds like it already works with your card.

2. Download the most recent madwifi source and compile it. It's not too difficult, and there's a few how-to's floating around that cover it. That's what I did a few months ago and it worked great!

Good luck!

Scott

---

### Post by RyanGT on 2005-10-18
For the sake of completeness if anyone stumbles onto this thread,  I did get my wifi card working with both hoary and breezy without very much trouble.  I have a Dlink DWL-G650 madwifi card and it is very well supported.  I have never tried WPA, but WEP works very well.

---

