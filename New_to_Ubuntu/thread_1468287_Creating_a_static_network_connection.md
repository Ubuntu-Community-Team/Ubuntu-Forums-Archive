---
title: "Creating a static network connection"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by ptm on 2010-05-01
10.04 install
Documentation says (as do several threads herein) Here is the Static Network instruction list
Static Connections

If you don't use DHCP then you can configure a static connection.

   1.Right click the NetworkManager icon in the system notification area.
   2.Click Edit Connections.
   3.Click the Wired tab.
   4.Select the connection and click Edit.
   5.Click the IPv4 tab.
   6.Choose Manual from the Method drop down.
   7.Enter your details and click OK.
   8.Click Close.

When your documentation for the "details" of item number 7 doesn't agree with the words used by the Ubuntu design who do you ask?

     My data sheet gives me the following information:
IP address nnn.nnn.nnn.nnn
Sub Mask 255.255.255.224
Default nnn.nnn.nnn.nnn
Pref. DNS nnn.nnn.nnn.nnn
Alt DNS nnn.nnn.nnn.nnn

      What Ubuntu shows 
Address
Netmask
Gateway (which resets to all 0's when you exit the window)
DNS server
Search Domains

Where is the cross translation so I know which numbers go in which spaces?

Also how do I get gateway to accept an entry instead of resetting to 0's?

---

### Post by anewguy on 2010-05-01
I think you would find the following:

address = IP address nnn.nnn.nnn.nnn
Netmask = Sub Mask 255.255.255.224
Gateway = Default nnn.nnn.nnn.nnn
DNS server = Pref. DNS nnn.nnn.nnn.nnn


I'm not sure if Search Domains = Alt DNS nnn.nnn.nnn.nnn

Dave ;)

---

### Post by ptm on 2010-05-01
Thanks, Dave, that was exactly what I needed.  Everything is up and functioning.  I'll submit your translation to the documentation project for 10.04.  

Oh, and I got the Gateway to hold the values entered by tabbing out of the field.

---

