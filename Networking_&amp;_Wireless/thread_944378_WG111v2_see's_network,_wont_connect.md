---
title: "WG111v2 see's network, wont connect"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by mparker81 on 2008-10-11
ive searched "wg111" and there is tons of info, it seems hit or miss..  some people plug it in boot up and it works..  others its a nightmare...  welp guess which one i am having...

anyhow it will show me the available networks but when i click on it to connect it wont connect...   

please stay with me... its going to be a PITA to help me because i am dual booting..  so when i boot to ubuntu i have no internets... well unless i go ethernet..   well anyhow i guess if there is a long step by step process ill figure something out...   


thanks guys...

---

### Post by mparker81 on 2008-10-11
back to the top

---

### Post by mparker81 on 2008-10-12
ok after searching and reinstalling...  

it will work perfect right after a freash instal, then update manager updates and it no longer will connect...  

i did however find out i have the dreaded rtl8187 chipset...   id like to avoid ndiswrapper...  sounds like that is a nightmare...

---

### Post by mparker81 on 2008-10-12
on the same note, ive found this  

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L)

supposedly a linux driver, but being a neewb i have no idea how to assign drivers in ubuntu...

---

### Post by Buster95 on 2008-10-12
RTL8187L is a challenge. You will find the researching for solutions quite a journey.

A good start is that you clearly understand that rtl8187B and rtl8187L are two very different beasts.

You probably already know that a native rtl8187 driver comes with the distro. It will work - in many, but not all cases.

I understand from this forum that the Realtek download of rtl8187L is an old, unsupported driver. I've tried it - unsuccessfully.

I have also tried some patched versions you'll find somewhere on this forum - with very limited, unpredictable and unreliable results.

I have also tried ndiswrapper. It works, but I have also found it unreliable.

All in all, I have learned that buying (as I have done) a cheap Taiwanese knockoff of a Toshiba laptop from "The Dodgy Brothers Computer Sales and Lawnmowing Company" is fraught with many challenges for wireless connectivity.

I'm loathe to suggest that you replace the crappy rtl8187 internal wireless hardware with something that works all the time, every time. That would deny you the pleasure of hours, days and months of largely fruitless, but highly entertaining fiddling around.

Good luck

---

### Post by mparker81 on 2008-10-12
i am using a netgear wg111 usb card...  i know it works.. like i said, when i first installed it worked them i updated everything and it staopped working...  is there a way i can roll back without a new install? and what gets updated that doesnt allow it to work anymore?

---

