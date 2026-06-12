---
title: "Firefox error on new Xubuntu 8.10 install."
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Alfadog on 2009-04-16
DELETED.  Duplicate thread posted by mistake.

---

### Post by Alfadog on 2009-04-16
Hello.  I'm a total Linux newbie and just installed Xubuntu 8.10 on an old Dell Inspiron 1000 laptop.  I'm having trouble getting Firefox to work with my wired internet (cable modem).  NetworkManager shows that it's connected (auth0) but Firefox does not seem to be able to connect to the internet.  

I've tried to configure the connection as per p. 26 of the Ubuntu Pocket Guide with no success.  The IP address, subnet mask, and router assigned automatically are different than what shows up in my Mac system preferences for the same internet connection.  I've tried to add a new connection, but when I type in the values from my Mac, NetworkManager won't let me save them as a new connection.

Any help would be much appreciated!  Thanks in advance.

Here is the message displayed in the Firefox Error Console:

Error: [Exception... "Component returned failure code: 0x80040111 (NS_ERROR_NOT_AVAILABLE) [nsIChannel.contentType]"  nsresult: "0x80040111 (NS_ERROR_NOT_AVAILABLE)"  location: "JS frame :: file:///usr/lib/xulrunner-1.9.0.3/components/FeedProcessor.js :: FP_onStartRequest :: line 1440"  data: no]
Source File: file:///usr/lib/xulrunner-1.9.0.3/components/FeedProcessor.js
Line: 1440

---

### Post by Hospadar on 2009-04-16
Could you open up a terminal (Applications->Accessories->Terminal) and post the output of the following commands:

"ifconfig"
(like ipconfig in windows, shows network info)
"iwconfig"
(wifi specific)

Do you know if any other internet applications are working?
for example in the terminal, if you ping google, do you get a response?
"ping www.google.com"
(Ctrl-C to quit, you should see a response right away)

---

### Post by Alfadog on 2009-04-16
I cannot figure out how to cut and paste from Terminal on my laptop onto my Mac so I'm attaching a picture of the ifconfig output. (iPhone to the rescue!)  The same connection is working fine on my Mac--I'm simply pulling the ethernet cable out of the Mac and sticking it into the laptop.  

"Ping www.google.com" resulted in "unknown host www.google.com".  Not currently using wifi.

---

