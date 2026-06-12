---
title: "Enable wireless from wired"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by hocvol1 on 2010-11-22
I have been using wireless on this HP G60-447CL Notebook with no issues to date.  I have temporarily moved to a wired connection and that went smoothly.  Now I wish to go back to wireless and cannot. I click on the connection icon and I see that the wireless connection is greyed out and wireless is disabled. I disconnected my wired connection and rebooted but still no wireless.

How do I get my wireless back?

Thank you.

---

### Post by DogMatix on 2010-11-22
Can you not right click on the wireless icon and select 'enable wireless'?

---

### Post by hocvol1 on 2010-11-22
No, I cannot right click on "enable wireless".  It is greyed out and nothing happens.  BTW, I am running Ubuntu 10.10.

---

### Post by DogMatix on 2010-11-22
How about trying System > Administration> Network Tools. Then see what network device is selected in the drop down menu.

---

### Post by hocvol1 on 2010-11-22
"Loopback interface (Lo)" is selected.

---

### Post by DogMatix on 2010-11-22
Loopback interface is how my default is too. But, is there an option for wireless can you select that click configure and then select the wireless tab to view your wireless connections.

---

### Post by hocvol1 on 2010-11-22
Thanks and I tried that as well.  No local wireless connections are listed.

---

### Post by spikoley on 2010-11-22
Maybe your wireless is turned off on the laptop.  Some laptops have a switch to turn off wireless and other use a key combo.  You also should check the BIOS to see if the wireless is active.

---

### Post by DogMatix on 2010-11-22
You may also find the info. at the following link worth reading:

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by hocvol1 on 2010-11-22
"Maybe your wireless is turned off on the laptop. Some laptops have a switch to turn off wireless and other use a key combo. You also should check the BIOS to see if the wireless is active."

I suspect the above may be close to the answer.  when the tech came in to install the cable connection, and the laptop booted, the wireless came on. He pressed the wireless button and the cable connection came on with no further problem.  I have tried to reverse the procedure but nothing's happened so far.

---

### Post by spikoley on 2010-11-22
> **hocvol1 said:**
> "Maybe your wireless is turned off on the laptop. Some laptops have a switch to turn off wireless and other use a key combo. You also should check the BIOS to see if the wireless is active."

I suspect the above may be close to the answer.  when the tech came in to install the cable connection, and the laptop booted, the wireless came on. He pressed the wireless button and the cable connection came on with no further problem.  I have tried to reverse the procedure but nothing's happened so far.

There is a quote button in the lower right hand corner of each post that will give you the pretty quoted box like above.

Search for your laptop model and wireless switch on your favorite search engine.  You should be able to find a diagram that will point it out.

---

### Post by hocvol1 on 2010-11-22
Thank you.  Apparently this is an HP phenomenon.  Not resolved but I will keep on trying.

---

### Post by hocvol1 on 2010-12-31
Thanks for everyone's input.  The issue was the wireless switch. It was defective. I worked around it by installing a Belkin BASIC (f7d1101) USB wireless adaptor.  Works great.

---

### Post by RichieB07 on 2010-12-31
> **hocvol1 said:**
> Thanks for everyone's input.  The issue was the wireless switch. It was defective. I worked around it by installing a Belkin BASIC (f7d1101) USB wireless adaptor.  Works great.

How did you get that adaptor to work?  I've been trying to for the past 6 hours and can't.

---

### Post by hocvol1 on 2010-12-31
> **RichieB07 said:**
> How did you get that adaptor to work?  I've been trying to for the past 6 hours and can't.

I downloaded addon "Ndiswrapper" from repository.  using this program and the CD that came with your adaptor, install driver from the file XPK2 or something like that.  Once installed, your adaptor should light up.  Mine had a conflict with the installed wireless card (wireless switch won't work on my HP), so I removed the wireless card and got connection with the Belkin.  I connect with open and WPA connections. WEP does not work for me.

---

