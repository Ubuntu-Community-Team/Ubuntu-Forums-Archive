---
title: "I can't surf from my university wifi!"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by PsychedelicReaction on 2007-11-12
I study at the Bocconi University in Milan, Italy. Here we have a wifi connection for students. It's a open connection and not cripted but I had to register my mac address at the ict department of the university. with windows i can connect to the network, then, when i open my browser (firefox too), i have to accept a certificate and then it automatically redirects to the login page of the network. finally i can access to internet with every application.
with linux i can connect, it recive the ip address i think correctly, but then when i open the browser nothing happens like there's no connection. i also tried to go manually to the login page (that is something like [https://1.1.1.1/login](https://1.1.1.1/login)) but it didn't work. so maybe it's a problem of the gateway but i don't know what to do. that's the screenshot from windows.

[IMG]http://img216.imageshack.us/img216/2552/reteuniqu9.png[/IMG]

thank you!

---

### Post by Fire_Chief on 2007-11-13
According to the screenshot you sent, that IP configuration should not even work. The Gateway IP address must be on the same subnet as your assigned IP address. The information listed really does not make any sense.

This is the info from a working Windows PC?

---

### Post by PsychedelicReaction on 2007-11-13
yes, it has been taken on my windows installation, where that network works.

while this has been taken on ubuntu

[IMG]http://img403.imageshack.us/img403/8894/screenshotmp8.png[/IMG]

---

### Post by Fire_Chief on 2007-11-13
I don't suppose the ICT dept. has any info or suggestions for getting linux on the network?

---

### Post by PsychedelicReaction on 2007-11-13
only a couple of how-to on the site to make it works on win and mac...

---

### Post by Farhaad on 2008-04-16
Hi

I have a similar problem. I have problem connecting to internet after I connect to free wifi in a coffee pub. In windows, when you connect and open your browser, you will be directed to a page which you must accept some terms and after that you have access to internet. It works for me using windows but in Ubuntu, firefox doesn't auto direct me to that login page, thus I cannot use internet. Anybody know how I can fix that?

---

### Post by jonallport on 2008-04-17
That subnet mask is wrong!

I see a 24-bit mask (255.255.255.0) but the broadcast address (10.6.127.255) indicates an 18-bit mask (255.255.192.0).  It looks like someone's tried to supernet an older, smaller broadcast domain without knowing what they're doing.

Either:
-Manually correct the subnet mask with ifconfig
-Contact the IT department and ask them to configure the DHCP server correctly

That may help, it may not, but it'll be one thing that's been eliminated.

Jon

---

