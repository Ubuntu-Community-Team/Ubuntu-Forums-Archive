---
title: "No Internet Connection with new Kubuntu installation"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by ianp5a on 2007-08-20
A new install of Kubuntu Feisty does not SEEM to connect to the internet. As Konqueror reports 'site not found' with every web address.
My spec is:
Wireless Fritz Stick and Wireless Fritz Box Router/Modem. This is all working in Windoes XP. So the ISP and PPPOE are presumably all ok.
The KDE "Network Manager" reports the wireless stick is OK and 'enabled' and shows a IP address automatically assigned. WEP is off for the moment. The Router address is entered under Gateway address.
Is there a way to tell if the wireless is working? What are the steps to check if each step is working? Maybe it already is and I just have to set something?
Thanks

---

### Post by ajgreeny on 2007-08-20
Try to, ping a site, eg. google.com.  In a terminal type:-
ping -c 5 [www.google.com](www.google.com)
and it should get contact 5 times and then stop.  If you get an error message, then you have no connection and need to look further.

---

### Post by ianp5a on 2007-08-20
Thanks. I'll try that when I boot back into Kubuntu. (I have to go into XP to use the internet remember.)
But I have to pass a technique onto my other users, so I really need tool to do it comfortably. There must be a GUI version.
Edit: I've just found **Kping** via google. I'll try that.

---

### Post by ianp5a on 2007-08-20
Ping reported no host found. Much the same as Konqueror.
I'm beginning to feel I'll never get Ubuntu to connect to the internet. Which would be the end of it for me.
And in my searches fo a solution, it seems that huge numbers of people have had similar troubles.

---

