---
title: "Ubuntu internet not working"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by GBurr on 2009-05-24
I just picked up a EEE PC by ASUS. I loaded Ubuntu through Wubi because there is no optical drive. I've got everything set up fine but I can't get my wireless internet to work. I connect to my linksys homenetwork and Ubuntu shows me I have a connection with 3 bars. I open firefox but can't display anything. 

Any help would be appreciated. I'm new to linux.

---

### Post by LubindaMaim on 2009-05-24
don't own a netbook to know for sure but did you try looking in System -> Administration -> Hardware Drivers. Also did you try the netbook remix? and to install it when you don't have a optical drive is via usb stick using [Unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by GBurr on 2009-05-24
My problem seems to be with just the internet connection. I'll try to look for the drivers. It is just weird that I can connect to the router and it says I have 3 bars but the browser won't work.

---

### Post by GBurr on 2009-05-24
The hardware drivers says no proprietary drivers are in use on the system

---

### Post by LubindaMaim on 2009-05-26
Does it work over ethernet?

---

### Post by alphacrucis2 on 2009-05-26
Type the following command and post output:


```
ifconfig
```

---

### Post by 3rdalbum on 2009-05-26
If you can connect to your network and access network resources, then you have the correct driver. If you cannot receive web pages, then it sounds like a DNS problem.

Right-click the network manager, go to Edit Connections...

Click the Wireless tab and then click on your SSID. Click Edit.

Click the "IPv4 Settings" tab, change the method to "addresses only", and put your DNS server as "208.67.222.222". (This is the free OpenDNS server, in case you were wondering). Otherwise if you know your ISP's DNS server address, you can put that in.

You may need to turn off wireless and then turn it back on again, or connect to a different network and then connect back. See how that goes.

---

