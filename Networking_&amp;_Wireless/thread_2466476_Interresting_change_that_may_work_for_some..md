---
title: "Interresting change that may work for some."
date: 2021-08-28
forum: Networking &amp; Wireless
---

### Post by sanman770 on 2021-08-28
OK I’m a beginner novice at best and I just had to publish what I found which was unusual.  I was having the WiFi slow issue, tried most of the things I found on the web and Ubuntu forum and nothing happened.  So I noticed that at every point it was Realtek as the main culprit.  Some insight. I have an old Asus P7H55-M PRO with an on board.

 
 
 Realtek ® 8112L Gigabit LAN controller
 Realtek ® 8-channel High Definition Audio  
 
 
 I had installed the Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter.

 
 
 ALL Realtek chips.
 
 
 So thinking all these devices are battling for the same thing, memory, cycles or ,what have you,  I decided to change my WiFi card for one I had laying around.   A TP-Link TL-WN88IND PCI express 300 wireless adapter which has a Anteros chip.  I used an old SSD I had laying around which had Ubuntu 18.04 on it.  I didn’t want to use my 20.04 because I didn’t know how it was going to react to the change in WiFi cards.  FYI the 18.04 drive was originally built with the Realtek card and  having the same issue.

 
 
 Low and be hold the speed was where it should be for my internet link.  I couldn’t believe it. So I reversed everything I did.  Put the everything back the way it was.  Ubuntu 20.04 with the Realtek card and low an behold, I’m running the speed of my internet connection.  
Like I said I’m a novice at best but I think Anteros uses something different like address or memory and changed the bios on the MB.  

  I’m sure some readers may think I’m nuts, but I was just looking for some feedback and what some may think of this.   

Thanks

---

### Post by mikewhatever on 2021-08-28
Seems bizzare and  irrelevant to me, but I hope it keeps working well.

---

