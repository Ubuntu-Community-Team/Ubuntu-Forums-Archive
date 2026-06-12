---
title: "[SOLVED] School's Network Giving Me Trouble"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by ghindo on 2007-08-25
I have a Dell Inspiron 1420n with Ubuntu preloaded on it.  I have never had any trouble with connecting to the internet before, whether wired or wirelessly - it has worked flawlessly.

I recently began university, however, and for some reason their networks, wireless and otherwise, has been giving me a lot of trouble.  I simply can't connect to them.  When you open a browser on my school's network, it's supposed to bring up page for registration.  When I try a browser, however - both Firefox and Konqueror - it gives a blank page.

The weird thing is that I can see other computers via DAAP on Rhythmbox.  Given, I can't access the music, but I can at least see the playlists and know that they're there. 

I took it in to my university's help desk, but they were largely baffled that I did not have a Mac or Windows, so they could not help me a great deal.  One of the guys said something about a DNS server, but I am not very familiar with most of these terms.

Help please?

---

### Post by Darkhack on 2007-08-25
DNS stands for Domain Name System.  Basically all servers and websites have a unique IP address.  When someone visits a website like google.com, the computer must know its IP in order to connect.  Your ISP (or in this case the university) has a DNS server that converts the human readable domains into IP addresses for the computer to connect to.

In fact, [http://google.com]("http://google.com") and [http://64.233.167.99/]("http://64.233.167.99/") are the same thing.  The only reason that the IP version of the website says "English" under the logo is because Google has their servers setup so that all the different languages that Google search engine is translated in reside on the same server and when you visit the IP it doesn't know if you came from google.com or google.jp (japan).  So rather than detecting location based off of the domain name, they just use a script to detect what language your browser is configured to (en-US for me) and then return that page where they specify to you what language was chosen.  Other than that, it is the same website.

The reason you can connect via DAAP but not get online is because you know the IP already with DAAP.  Try going to the IP address version of Google I gave on your Inspiron and you'll be surprised to find that it works, but google.com doesn't.

Ask the help desk for the DNS Server's IP address and you can configure your system to use it.  Then you can visit pages that use domains instead of being restricted to IPs only.

---

### Post by ghindo on 2007-09-11
That worked superbly.  Thank you!

---

