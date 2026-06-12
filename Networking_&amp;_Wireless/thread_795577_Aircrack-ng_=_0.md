---
title: "Aircrack-ng = 0?"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by pmq on 2008-05-15
Hi, 

I am currently studying a model based on networking at university. One of the core topics is wireless encryption. I decided to play around with it for fun so i can get a better understanding of how things work.
I tried to use aircrack-ng on my home network. I heard that this program can crack a wep encryption in seconds, however when i do this on my own network it never happens.
Collecting packages had me up from 1am to 6am. when i finally ran the aircrack on the file storing the packet information it just kept going on for hours.

There were over 50,000 IVs and over 250,000 packets.

This makes me feel secure that my network is fine but i dont think i did things right.
Although i have started to use WPA for the moment.

Can anyone elaborate on this?

Thanks

---

### Post by chili555 on 2008-05-15
This may be helpful: [http://ubuntuforums.org/showthread.php?t=778350](http://ubuntuforums.org/showthread.php?t=778350)

---

### Post by pmq on 2008-05-18
Thanks, i didnt see that reply.

---

### Post by nicedude on 2008-05-18
50,000 IV's isn't enough you need 250,000 - 1.000,000 to ensure cracking it. sometimes over 1,000,000 wont do it.

And if you want your WPA to be safe you need to change your ssid on your router as all I need  is one encrypted handshake and with my trusty 60GB Rainbow tables and cain I can brute force your key in a matter of days more than likely all using the one encrypted handshake recorded so I don't have to even be monitoring or around your network for the actual brute forcing so you would be none the wiser. For the benefit of all here I will include a text of the top 1000 ssid values that the best WPA rainbow tables available on the net crack, If you name your network something other than is on this list it will at least force an attacker to spend time and CPU cycles to generate a custom rainbow table to attack your WPA with ( And that bumps up the trouble & Skill factor a notch ) So just grab the text below and change your ssid to something not on this list as allot of people have the same Rainbow tables I do :-)

FYI rainbow tables are precomputed variations of all passwords that greatly speed the brute force crack from years to days :-)

Hope this helps you begin your studies on this subject just don't do anything too bad to others with what you learn, PM me if you want further advice or want to know where to get some rainbow tables for yourself :-)

Nicedude

---

