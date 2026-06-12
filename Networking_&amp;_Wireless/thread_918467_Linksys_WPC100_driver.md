---
title: "Linksys WPC100 driver?"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by KR4WM on 2008-09-12
I'm a clueless noob. Just getting my feet wet in Linux. My wife picked up a Linksys WPC100 PCMCIA wireless networking card for my experimental Dell Inspiron 4000 laptop. After many frustrating hours installing and re-installing Linux, it's finally ALIVE! Well- all except for the wireless networking, anyhow. I was hoping it would be as simple as plugging in the card, but alas, there must be more to installing this card than I thought. The included CD does not have a Linux driver, nor is one available on the Linksys website. How does one go about getting a wireless networking card to function in my situation? I haven't the slightest clue what chipset is in the thing. Thanks, -KR4WM

---

### Post by BillEBob on 2008-10-12
I too am new to Linux (Ubuntu) and was hoping this thread could help me out.  After several hours I kind of figured it out.  First go to "Applications" and go to "Add/Remove".  Select "System Tools" and check "Windows Wireless Drivers".  "apply" the new software.  It will be loaded under "System" and "Administration".  Open the "Windows Wireless Drivers" application.  You will need the Windows .inf file for the wireless adapter and install it.  Your wireless adapter should be recognized.  You will need to configure the adapter.  I haven't figure out how to open my locked network yet but, I can access non-secured wireless networks.  I see a place for my network key but it isn't working for me at this point.

---

### Post by Armin_Fan on 2008-10-13
ok, had a laptop with fedora 9 on it and that distro so loved to make kernel upates that would require me to find new updates for the software to run my wpc100 on it, it got so annoying becuase they wouldnt always show up in their repos, today I went back to ubuntu on the laptop. But for awhile that linksys wireless pc card worked fine in linux but had to use ndiswrapper software to load in the windows driver to get it to run. I find this procedure annoying, most of the time I got it to work. But right now I can get ubuntu to get the card online, I see the power power light is on, but cant get it to log onto my network with WEP.

this will take awhile to write about how to do ndiswrapper, especially since only got it to work 4 out of 5 times in fedora and ubuntu, today after 6 hours, I got it close working.

one thing for sure, this is annoying. its 4 am here, so I will have to really type alot of what I did that almost got there. oops, I am not using kubuntu, just regular ubuntu, so I dont know if this will be exactly the same.

---

### Post by BillEBob on 2008-10-13
After playing with the wireless adapter I lucked into the correct menu option.  I had connected to a local unsecure wireless network and then clicked on the "Wireless network connection" next to the date on the menu bar.  I selected my secured wireless network and it finally asked me for my WEP key.  I had to choose the correct format out of 3 or 4 options.  Once the correct format was selected, the wireless connection worked flawlessly.

---

