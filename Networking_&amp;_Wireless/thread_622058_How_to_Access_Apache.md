---
title: "How to Access Apache?"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by garyed on 2007-11-24
I'm using Apache to work on my web pages & test them before I upload them to my Web Host.
I have Apache loaded on 1 computer & can access its web pages through any of my other computers hooked up to the same router by typing the correct IP address in a web browser or "localhost" on the Apache computer. I want to view the Apache computer web pages from the 
internet from anywhere.
Can anyone tell me how?

---

### Post by kelbizzle on 2007-11-24
sure you just have to goto your router configuration page and forward port 80 to the computer with apache on it.  If you don't know how [http://www.portforward.com/](http://www.portforward.com/) this site will help you.

---

### Post by garyed on 2007-11-24
Thanks,

So after I set up port forwarding I assume all i need to do is enter in my ip address into a browser from anywhere & it should connect to my Apache server.

---

### Post by kelbizzle on 2007-11-24
Yes...Unless you have a Dynamic ip address. It could get pretty annoying when you need to connect to your computer only to find your ip address isn't correct. Depending on your router. You may be able to setup a dynamic dns service like dyndns to update your ip to a web address. I know my linksys has a place where I can put in my dyndns username and password. If not you can use this [http://ddclient.wiki.sourceforge.net/](http://ddclient.wiki.sourceforge.net/) to update the dns name.

---

