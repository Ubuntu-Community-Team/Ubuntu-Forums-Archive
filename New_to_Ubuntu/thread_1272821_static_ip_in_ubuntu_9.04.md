---
title: "static ip in ubuntu 9.04?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by amiacamal2 on 2009-09-22
my new college accomodation requires we set up a static ip for the broadband use, however i have no idea how to do this. i tried rightclicking on the connection thing ---> edit connections and making a new one, filling in the details i was given. it says its connected, but i still have no internet

any help greatly appreciated




:guitar:    <---- lil legend!

---amiacamal2---

---

### Post by Ocxic on 2009-09-22
[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

---

### Post by amiacamal2 on 2009-09-22
i dont understand how to acces that file to edit it....

---

### Post by Joeb454 on 2009-09-22
> **amiacamal2 said:**
> i dont understand how to acces that file to edit it....

Simply run ```
gksu gedit /etc/network/interfaces
``` Which will allow you to edit the file

---

### Post by amiacamal2 on 2009-09-22
"auto lo
iface lo inet loopback"


thats all thats in that file... shouldn't there be something more?

---

### Post by amiacamal2 on 2009-09-22
i also use a mobile broadband modem, will doin this mess with it?

---

### Post by Ocxic on 2009-09-22
add:
# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

but change the numbers to suit your needs.

network manager should allopw you to set a static address with having to edit the file.
unfortunatly if you've made a mistake with the static config in network manager it won't tell you, as it just thinks that everything is fine scince you've specified everything

---

### Post by herewasplato on 2009-09-23
> **amiacamal2 said:**
>  ... set up a static ip for the broadband use, however i have no idea how to do this. i tried rightclicking on the connection thing ---> edit connections and making a new one, filling in the details i was given. it says its connected, but i still have no internet ... I saw this post/query while hunting for a solution to my own question... then when I went to find it again a few hours later and I noticed just how far from the first page it had fallen. So, I see that this is going to be one of ***those*** forums = really active.

The stuff that I read while joining this forum said to think like a green user. Well, I'll have no problem doing that since I'm quite green to Ubuntu myself. I have however, managed to set a static IP address for the Ubuntu 9.0.4 install that I'm am learning on.

My concern with the steps that you outlined this the bold part:
*connection thing ---> edit connections and **making a new one**, filling in the details*

That step might be needed if you are talking about a wireless connection - but it is rare to have a static IP assigned to a wireless Network Interface Card (NIC).

For the hardwired "eth0" connection,  I did not make a new one; I edited the one that was there.

The steps below might help someone else - I doubt that you need the little pics.

So, like you said:
1) Right click on the connection thing (icon)...
[Upper right hand corner in a stock install.]
...and select "Edit Connections..."
[IMG]http://i33.tinypic.com/qrm82w.png[/IMG]


2) Once the next window comes up,
click on "Auto eth0" and then
click on "Edit...":
[IMG]http://i37.tinypic.com/261e05w.png[/IMG]


3) Enter your password - if need be - into the screen that may pop up asking you to "authenticate". (I'll skip that pic).


4) Select the tab labeled "IPv4 Settings"...
...and use the drop down to select "Manual":
[IMG]http://i36.tinypic.com/2qdmwc8.png[/IMG]


5) Once the "Method:" has been changed to "Manual"...
...the button labeled "+Add" should be enabled...
...and fields should appear for you to enter your info into:
[IMG]http://i33.tinypic.com/244zb03.png[/IMG]


Sidebar:
Personally, I think that the fields in the User Interface pictured above are a bit flaky when you tab to each field: [tinypic Video]("http://tinypic.com/r/xmvqlg/4") And they can still be finicky when you click inside of each field to enable it. Maybe Ubuntu 9.10 will solve same...


~Hope this helps someone~

---

