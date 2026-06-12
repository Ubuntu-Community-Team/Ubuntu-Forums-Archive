---
title: "Problems displaying web pages"
date: 2007-11-10
forum: Networking &amp; Wireless
---

### Post by bobthebullet990 on 2007-11-10
Hi all,

I have an active network connection to my router. However, i'm getting a very strange result in that I cannot get firefox to display any webpages from the internet!

however, If from the command line I do:

ping [www.google.com](www.google.com)

I get a response from google, so my initial thought of a problem with the nameserver cant be the problem!

can also login to my ftp location from the command line!


Anyone got any ideas??? thanks

---

### Post by Peter09 on 2007-11-10
This is due to you not having any DNS name servers allocated. If you have a DHCP router then try putting that IP into your network manager DNS tab. Otherwise put the DNS servers supplied by your ISP. Any other free DNS server ip will do though.

---

### Post by ankur_gupta10 on 2007-11-10
Had it been a DNS problem then from the command line also there should not have been any response.

try checking the network connection settings in the firefox. Try some other browser like Opera etc.

---

### Post by Peter09 on 2007-11-10
Sorry, but perhaps I have misunderstood, pinging by IP address does not need any DNS server involvement. DNS servers are there to resolve host name --> IP address .

Did I misunderstand the problem?

---

### Post by Peter09 on 2007-11-10
Sorry, I misread your post, I realise now that you were pinging google by host name, and yes that means that you have DNS servers :)

---

### Post by vpjr on 2007-11-10
have you checked in firefox: Edit -> Preferences -> Advance -> Network -> Connections?
firefox is by default set to connect directly to the internet. you are using a router? perhaps you can try setting firefox to automatically detect the proxy settings of your network.

---

### Post by Mitcal on 2007-11-10
I am also having these same problems.

I am trying to switch to Ubuntu from Windows on my home Desktop.

I can ping google.com or ubuntu.com with Network Tools but I cannot use Firefox, email or any other internet stuff.

The PC is directly plugged into the router via a network cable and the internet works under Windows.

It seems very strange to me that it doesn't just work - like it says it should.

I have fiddled with a lot of the settings to no avail and it's driving me a little mad.

Anyone know how to fix this?

---

