---
title: "Obtaining MAC addresses"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by tamoneya on 2008-06-26
I was curious to see if there was any way to obtain the MAC addresses of people visiting one of my webpages. Im not sure if it is even possible but I did some google searches but they werent very helpful so I thought there might be someone here with some experience.  I know a little about network protocols but not enough to know things at a packet level and such so I am not positive whether or not the MAC is physically transmitted all the way to the server.  I realize that I would probably be getting not the computers MAC but instead the router that controls their home network since these are so common currently.  

What technologies should I be looking into.  Can this be done entirely via javascript or PHP.  Should I be searching through apache logs?  Should I log the IP address and then call some server side script to ping the IP and grab its MAC?

---

### Post by jimv on 2008-06-26
The only way you're going to be able to do it is to execute some kind of code on the client's machine that pulls the mac address into the browser.

ActiveX in IE, but I have no idea for Firefox.

---

