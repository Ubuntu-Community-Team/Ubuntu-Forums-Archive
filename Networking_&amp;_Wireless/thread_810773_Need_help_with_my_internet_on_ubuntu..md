---
title: "Need help with my internet on ubuntu."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Darzak on 2008-05-28
Hello , I installed Ubuntu a week ago and I have been trying to fix my internet connection every since. I've installed it with the "dual-boot" option so i can switch from Windows XP and ubuntu.

my problem is : I can access the google text search , I can google some words ( not pictures) but most of the sites are not working like yahoo and msn. pidgin is really slow ( but that might be normal). i view cached text after I have googled the text. some websites works also but thoose websites are of none importance to me.

i have tried : Disabling ipv6 on firefox and with the modprobe thing and blacklisted it . I've manually configured DNS servers. I've read alot of guides and followed them all but still finding that my network does not work properly... btw I got a router but I have tested to connect my internet cable directly into the socket but the problem still remains.


Thanks in advance.

---

### Post by pytheas22 on 2008-05-28
Some things to try:

If you're using some kind of encryption on your network (WEP, WPA...), try turning it off.

Do you have the same problem in different browsers?  If you haven't tried anything besides Firefox, install Opera or Konqueror and see what happens.

Please also describe more specifically what you mean by the sites "not working."  Do you get a server-not-found message in Firefox when you try to connect, or are there certain kinds of errors on the pages?  Screen shots could be helpful.

Can you give examples of websites that *do* work?  Is there anything in common about them that distinguishes them from broken sites?

---

### Post by Darzak on 2008-05-30
the computer I'm using is stationary computer which is connected to the router through cable.
 I can't really remember the error thing but it says something like this : the site seems to be alright but blablabla isnt working...

google and a ubuntu/linux site worked , but im going to try to install another web browser in the meantime please give more suggestions.

---

### Post by pytheas22 on 2008-05-31
I get errors like that sometimes ("Though the site seems valid...") when trying to access from the outside the files that I host on my computer on an Apache server.  The error happens because sometimes my router gets buggy and blocks the http port.  If I access the same files from another computer on my network, they work fine.  Check your router's settings and make sure nothing is being blocked.

In a similar vein, you could install firestarter (sudo apt-get install firestarter).  It's a GUI to configure the Linux firewall, which by default should be allowing all traffic, but maybe for some reason it's blocking certain sites.  You can experiment with the settings in firestarter to make sure the firewall is completely off.  You can also use it to see what's happening when you try to load a site--if communication is being dropped, firestarter will tell you.

You should also definitely try another browser, and it wouldn't hurt to ping the sites that you're unable to load in a web browser--do you get a response that way?

---

