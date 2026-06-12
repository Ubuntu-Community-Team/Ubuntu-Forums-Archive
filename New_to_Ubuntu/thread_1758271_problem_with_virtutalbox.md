---
title: "problem with virtutalbox"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by karthik.k.nair on 2011-05-14
[SIZE=2]hi sir how r u. i m karthik form india. sir i m using super OS 10.10 as my mother os. i m using wireless usb modem for internet conectivity wihch uses  ppp0-Link encap:Point-to-Point Protocol for internet conectivity . 

now i will come to the problem. i hav installed virtualbox in which i have installed backtrack4 distribution and windows xp. i hav configured network adapter as NAT in both xp and bt and is able to get internet conetivity in both os.
i noticed tat both the os is having same ip adddress (10.0.2.15) but different netmask (255.255.255.0 for xp and 255.0.0.0 for bt) and both is having same gateway (10.0.2.2). i was not able to ping each other.

 so i changed the netmask and ip of bt to 255.255.255.0 and 10.0.2.16 respectively and tried ping each other but still unsucessful.my objective was to sniff the internet traffic of xp in bt. since its not able to ping each other inspite of having same netmask(255.255.255.0) and gateway (10.0.2.2). i m not able to ping each other.

 pls help sorry my english is not so good i hope u understand. thank you.[/SIZE]

---

### Post by Habeouscorpus on 2011-05-14
I understand what you're trying to do. I'm not sure that the Virtual machines can see each other. There is a program called Wireshark that can sniff traffic. Maybe you should look into that instead of Virtual Box?

---

### Post by karthik.k.nair on 2011-05-14
sir i m not able to ping each other from either side

---

### Post by wildmanne39 on 2011-05-14
> **karthik.k.nair said:**
> sir i m not able to ping each other from either side

Hi, I have been using virtualbox for about 3 years now, I do not know if I can help or not but I will try.Also if you go to virtualbox home page they have a forum just about virtualbox. You say you can connect to the internet is that right?, if so is it a really matter whether you can ping or not? I am not sure what it would accomplish being able to ping.:)

---

### Post by karthik.k.nair on 2011-05-15
> **wildmanne39 said:**
> You say you can connect to the internet is that right?, if so is it a really matter whether you can ping or not? I am not sure what it would accomplish being able to ping.:)


thank you but sir my objective is to sniff internet traffic of xp from backtrack. since i m not able to  even to ping xp an backtrack, how can i sniff xp traffic from backtrack..

---

### Post by duke.tim on 2011-05-15
You could sniff traffic using wireshark. I don't think that you will be able to sniff the internet traffic from the virtual machine unless you forward xp's internet traffic to the virtual machine.

---

### Post by karthik.k.nair on 2011-05-15
both xp and backtrack are virtual machines. i have created a virtual network in which there are 2 machines- xp and bt. i know wireshark is used to sniff and analysis the traffic. but since two virtual machines in the same virtual network is not able to see each other how can i sniff the traffic of one with other.

this problem occurs only when i use pppd in my mother OS for internet conection. but whn i use normal adsl modem i m easly able to sniff the traffic of virtual xp in virtual backtrack.

and for ping issue i ping not to sniff traffic but to see weather both the virtual machines (xp and backtrack) are able to see each other. only if they are able to see each other then only we think of sniffing the traffic of one from another.. i use wireshark only to sniff the traffic but my problem is if the two machines r not able to see (ping) each other then how the wireshark installed in one machine sniff the traffic of another?

---

### Post by Skorzen on 2011-05-15
@karthik.k.nair,

Have you tried setting up both VM's network adapter in Bridged Mode? Since you're using a 'special' connection (PPP), I don't know if it will work.

Also, both VM's may be configured to not respond to ICMP traffic (ping). Isn't this the case? Even if you're not being able to ping each other, turn Wireshark on to see if it can detect other types of network traffic.

Best regards,

Bruno Martins

---

### Post by karthik.k.nair on 2011-05-15
> **Skorzen said:**
> @karthik.k.nair,

Have you tried setting up both VM's network adapter in Bridged Mode? Since you're using a 'special' connection (PPP), I don't know if it will work.

Also, both VM's may be configured to not respond to ICMP traffic (ping). Isn't this the case? Even if you're not being able to ping each other, turn Wireshark on to see if it can detect other types of network traffic.

Best regards,

Bruno Martins
  yes sir when i connect using normal adsl i used bridge mode in virtual machine. my wireless internet uses ppp and i hav tried bridg mode to connect to virtualmachine but it does not work. i m using NAT network adapter. and it works fine with ppp connection. both the machines are able to conect to internet. the problem both virtual machines are not able to see each other .

ya i have tried sniffing the traffic through wireshark. still unsuccessful.

---

### Post by wildmanne39 on 2011-05-15
> **karthik.k.nair said:**
> yes sir when i connect using normal adsl i used bridge mode in virtual machine. my wireless internet uses ppp and i hav tried bridg mode to connect to virtualmachine but it does not work. i m using NAT network adapter. and it works fine with ppp connection. both the machines are able to conect to internet. the problem both virtual machines are not able to see each other .

ya i have tried sniffing the traffic through wireshark. still unsuccessful.
Hi, have you tried the virtualbox.org forums? :)

---

### Post by wildmanne39 on 2011-05-17
> **karthik.k.nair said:**
> yes sir when i connect using normal adsl i used bridge mode in virtual machine. my wireless internet uses ppp and i hav tried bridg mode to connect to virtualmachine but it does not work. i m using NAT network adapter. and it works fine with ppp connection. both the machines are able to conect to internet. the problem both virtual machines are not able to see each other .

ya i have tried sniffing the traffic through wireshark. still unsuccessful.
Hi, if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:D

---

### Post by karthik.k.nair on 2011-05-17
somebody help to solve the problem.. the thread is still open

---

