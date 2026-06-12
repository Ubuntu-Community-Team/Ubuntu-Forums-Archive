---
title: "Problem in connecting to WEB pages past my Home Page"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Kevin Funnell on 2006-12-17
Good Day All, 

   I have also posted this Thread on Absolute Biginners Talk but the repllies i received were helpful but did not help me to correct the following problem

[COLOR="Red"]I NEED HELP IN SETTING-UP MY EXTERNAL MODEM SO I CAN CONNECT TO THE WEB AND UPDATED PACKAGES.[/COLOR]

I still having problems with my connection to the Internet and therfore are unable to use eith of the update managers or Download Package Information.

I am able to log-in to my Mail program where I can Receive & send mail I can also log-into my ISP /Home page but can not connect to any other Web page/Site. Which makes it impossible to use Ubuntu 

I used PPPconfig to configure the modem and that is wher I probable have made some minor errors in my selection of options available.

My System P4 Intel computer
Modem: External -  Hayes Accura 56K + FAX

I Can ping my ISP/Home page but no othe valid WEB sites.

If any one has a working copy of PPPconfig could you send it to me via this Forum or e-mail.

I want to use Ubuntu/Linux but without a working Internet connection in is impossible and I have to go back to Windows to connect to theis Forum or other sites.

Old Kevin

---

### Post by ESPOiG on 2006-12-17
dns servers you have to put them in, im with AMCOM and i have to use dns servers

---

### Post by Littleweseth on 2006-12-17
A couple of probing questions so we can help you more;

Firstly, does your dialup work normally under windows? (i.e. you still have internet quota if you're on one of those by-megabyte monthly plans.)

If you do indeed have some quota left in the tank, you may have faulty DNS settings. Try this command in a terminal :

ping 66.249.89.99

then this one :

ping [www.google.com](www.google.com)

In both cases, you should get a scrolling list of lines looking like '64 bytes from 66.249.89.99 : icmp_seq=1 ttl=232 time=235ms'. Hit Ctrl-C to make it stop. If it works for the first one and doesn't for the second, then you have an error in name resolution (faulty DNS settings) - 66.249.89.99 and [www.google.com.au](www.google.com.au) are one and the same.

If the second command didn't work but the first one did, type cat /etc/resolv.conf and paste the results here.

---

### Post by ESPOiG on 2006-12-17
i still think it is ur dns servers, i had the same problem when i started with ubuntu i couldnt connect to web pages, and if i did they were very slow, but i could use irc and i belive im.

in the end i email my isp and askd what the problem could be, but because there linux wasnt up to scratch they just gave me about 20 options :D, luckly dns servers were the first thing i tried and it worked

/etc/resolv.conf

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

---

### Post by Kevin Funnell on 2006-12-18
Good Day Littleweseth & ESPOiG,

Your post got the grey matter working, originally I got my DNS settings from Bigpond so I checked again this morning and got a different set of DNS figures Ooriginal one were for Broadband).  Now I am a happy old vegemite, everything sppears to be running like clock works, currently updating with Update Manager all 140MB so I'll be on the net for sometime tonight.

Your help has got me on the Net and the help from you and other Ubunto Forum members is what I like about Ubuntu always willing to help.

Regards & Thanks again,
Old Kevin

---

