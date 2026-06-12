---
title: "Hosting Own Website with Apache"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by trstowell on 2010-10-31
In the coming months I intend to launch a web service using the LAMP suite/service/what-have-you. 

I have familiarized myself with the basic workings/configurations of Apache, but am still missing the big picture. What I mean by missing the big picture is I am unsure how to associate my paid domain name with the site files I create in my Apache directories. 

Basically, how can I design my website (as I can easily do with localhost) then publish it to users outside of my network with Apache.

Thank you.


EDIT:   I have scoured the Apache2 Documentation but have not found quite what I'm looking for.

---

### Post by cj13579 on 2010-10-31
Once you have created your site and you are happy with it and you can access them from either localhost and/or other machines on your network you will need to do 2 things:

1) Forward port 80 on your router to the box which you are going to be hosting the site from. 

2) Edit the DNS record for your domain to point to your IP address. You can find out your public IP by going to [www.whatsmyip.org](www.whatsmyip.org). Depending upon your ISP and your connection speeds this may or may not be static. You'll want to find that out.

---

### Post by trstowell on 2010-10-31
When port forwarding with my router I am allowed to enter the last digit to the IP dot operator (i.e.  192.168.0. [ ENTER ]).

On another page of my router config labeled "LAN IP" I have a Starting/Ending IP Address of 192.168.0.[10]/192.168.0.[19] respectively. When port forwarding must I enter an address within or outside of this 10-19 block?


I have my IP address and have registered it, along with my domain name, with [www.no-ip.com](www.no-ip.com). AFAIK I have enabled the Pseudo-static IP service where it updates if my IP changes.

---

### Post by cj13579 on 2010-10-31
You will need to make sure that the box from which you are hosting the site has either got a static IP address or an address that is reserved in your DHCP server. 

Whether it is inside or outside of that range is irrelevant if you are using a static address, it sounds like that is the range that your DHCP server is giving out.

You should be able to find a section in your router about reservations easily. On mine it is the on a similar page to what you were describing.

For setting a static IP may I refer you to here: [https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.10/serverguide/C/network-configuration.html)

---

### Post by HermanAB on 2010-10-31
Howdy,

You won't find any DNS information in the Apache documentation, since it is not an Apache issue.

Configure Apache to listen on whatever IP address the box has, then configure the DNS to point to it.

---

### Post by trstowell on 2010-10-31
EDIT: This problem has been resolved. AFAIK my website [www.StowellSolutions.com](www.StowellSolutions.com) is readily accessible from outside of my network. Hopefully I can hone my skills in this area and become a valuable member of this board. I sincerely appreciate your time.

---

### Post by cj13579 on 2010-10-31
Glad everything is working for you. To keep the moderators happy and to keep the place looking tidy you should mark this thread as solved.

---

