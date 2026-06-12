---
title: "Apt-get slow downloads but firefox fast"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by ozmaen on 2007-04-23
Hi,

New user here..so be kind please :p

Installed 64 bit Ubuntu (edgy). When downloading via firefox, speeds are fine (500-600 kb/s), utilising the availabel adsl capabilities. However, when ever I use apt-get or Syanptec, my downloads will not go faster than 20-30kb/s.

My box is connected to my network which has a ClarkConnect gateway. 

Any help on getting my apt-get etc downloads working properly will be greatly appreciated (clear instructions if possible)

Cheers

---

### Post by bionnaki on 2007-04-24
post your sources.list
maybe you're using the wrong ones for your location

---

### Post by UCAP on 2007-04-24
Or even simpler:

Go to System -> Administration -> Software Sources and choose a download mirror closer to your location.

---

### Post by Soarer on 2007-04-24
And it will even check them all to see which is quickest for you!!!!!

FYI I get about 115 kB/s on a domestic ADSL line.

---

### Post by kerry_s on 2007-04-24
Do you have ipv6 disabled?

---

### Post by ozmaen on 2007-04-24
Thanks for the suggestions. Disabled IPv6 and cleaned up my source list and only used local mirrors.

Happily upgrading to 7.04 at 600kb/s :)

---

### Post by unixguru on 2007-04-24
Can you tell me which server it is because none of my local servers or any of the servers i have tried give more than 10k. I tried the choose the best server option also but it is one of the slowest i have tried.

---

### Post by akingunay on 2007-04-25
I have the same problem. I tried many different mirrors including my local mirror, but I get at most 10-20 kB/s (my normal download speed is 150-200 kB/s). I also disabled IPv6, but it makes no difference.

any suggestions?

---

### Post by Surgeon General on 2007-04-25
How does one disable IPv6 in Feisty?

---

### Post by ozmaen on 2007-04-27
I just used this site [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/") to create my source list.

If I recall, you need to edit the alias file (can't remember where it's located) and change ipv6 to ipv6 off

---

