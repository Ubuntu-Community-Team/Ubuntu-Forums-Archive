---
title: "Broadband Connection"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by rajaditya on 2011-03-14
Ok My PC uses one of those always on cable internet connections. It doesnt have any modems or routers in my house (customer premise) 
There is a CAT-5 cable that connects to the ethernet port(LAN card) to my computer and thats it. In windows I connect using a dialer that the broadband comapny had provided using a username password. 
Now I want to  connect my ubuntu 9.10 to the internet using it. Now my local internet guy insists that it doesnt have any support for linux. 

anyone help a poor ububtu newbie? :confused:

---

### Post by grahammechanical on 2011-03-14
When a supplier or manufacturer says that they do not have any support for Linux, it is another way of saying we do not know anything about Linux therefore we cannot advise you or support you. It does not mean that a Linux operating system will not work with their services or device.

Go to the Ubuntu Software Centre and search for Gnome PPP. It may be what you need to make the connection. It might be possible to do the same using Network Manager but I cannot tell you how to do it. It might be done through the DSL tab under Edit Connections. I do not support DSL. Do you understand? I do not have experience of making a DSL connection.

Regards.

---

### Post by sydbat on 2011-03-14
> **rajaditya said:**
> Ok My PC uses one of those always on cable internet connections. It doesnt have any modems or routers in my house (customer premise) 
There is a CAT-5 cable that connects to the ethernet port(LAN card) to my computer and thats it. In windows I connect using a dialer that the broadband comapny had provided using a username password. 
Now I want to  connect my ubuntu 9.10 to the internet using it. Now my local internet guy insists that it doesnt have any support for linux. 

anyone help a poor ububtu newbie? :confused:Unless I am misreading this, you are describing simple dial-up via your home phone line. I have never heard of any broadband service requiring a user to "dial-up", the connection is always live.

Anything to do with broadband Internet (DSL, Cable) requires some kind of modem interface between the phone line and computer...even with centralized Internet in a building served through wall connectors in each room (aka: "smart houses" that have the modem/router in the basement).

---

### Post by dineshs on 2011-03-14
Try network manager first
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

### Post by rvchari on 2011-03-14
> **rajaditya said:**
> Ok My PC uses one of those always on cable internet connections. It doesnt have any modems or routers in my house (customer premise) 
There is a CAT-5 cable that connects to the ethernet port(LAN card) to my computer and thats it. In windows I connect using a dialer that the broadband comapny had provided using a username password. 
Now I want to  connect my ubuntu 9.10 to the internet using it. Now my local internet guy insists that it doesnt have any support for linux. 

anyone help a poor ububtu newbie? :confused:

i dont think you r using dialup. it is just an interface where you click on some button to connect.

there is nothing that linux cant do and windows can. its just a matter of understanding.

when you said you are connected thru ethernet cable then you can simply right clik on the top right notifier for network and click on edit connections

create new and use it to connect. your problem should be solved. if not then give me more details of ur service provider settings...

---

### Post by Scunnered on 2011-03-14
Like you I have a password agreed with my provider.  You should use this with any request for the password with Linux.

When I initially connect with the network manager having being disconnected I am asked firstly for my Ubuntu password.  After that there is a second request which is the password that I have with my ISP.  I am from memory asked to enter it and then a second time. After that everything works immediately on login until such time as I chose to disconnect from my broadband connection.

Hope this assists

---

### Post by pricetech on 2011-03-14
Scunnered seems to be the only one who has a setup similar to yours.  I'm like the rest to whom it makes no sense for you to have a cable broadband connection and still need login credentials.

It would help if we knew where you were as different countries / regions offer different types of service.  Also, it would help to know who your ISP is.

With that information, we should be more able to assist.

---

