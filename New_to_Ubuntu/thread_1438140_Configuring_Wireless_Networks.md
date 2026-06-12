---
title: "Configuring Wireless Networks"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by fly_boy on 2010-03-24
OK, I am now up and running with Ubuntu, and am exploring the wireless possibilities, I have a USB Based Wireless Adapter on my Ubuntu machine and have created a new wireless network (for the sake of argument we'll call it SSID "Inhouse")which my Windows 7 laptops can wirelessly connect too. This works well.

OK, I also have a wireless broadband router, (for the sake of argument we'll call it SSID "Outhouse")that I want to use to connect to the internet.

How can I bridge wirelessly between the Inhouse and Outhouse networks on the Ubuntu box.

I know that I can do this with an Ethernet cable, but how do I do it wirelessly, do I need a second wireless device in the ubuntu box, start Inhouse and then Connect to Outhouse and bridge between the 2.

Can anyone help?

Alan

---

### Post by jd65pl on 2010-03-24
Can't all machines reside on the same network? I don't see how you might get the kind of chained network you describe without two network interfaces, this seems a bit of an over engineered solution though.

---

### Post by uRock on 2010-03-24
I am not sure that Ubuntu has support for using the wireless for dual connections. I know that some machines running Windows 7 can do this, but I also think it has to do with the hardware. To use the system in the manner you are talking about, you will also have to set up your system to run DHCP on a different subnet from the one your router is using.

---

### Post by fly_boy on 2010-03-25
OK, so I have a couple of options. bridge with an ethernet cable..
 
Or just configure the AP on the ubuntu box to accept connections for my internet link, but force connection to that AP by filtering only the MAC address of the ubuntu box onto the modem....
 
I tried using the wireless bridge functionality on the router by adding the MAC address of the broadcasting network device but this didnt work. Probably because the same device cannot be logged onto 2 networks....
 
The modem/router is a belkin54g, and the AP device is a DLINK dongle based AP...
 
The ubuntu box connects nicely to the internet...
 
Just looking for some config tips on how to set this up...

---

### Post by fly_boy on 2010-03-25
Another question then, how do I configure Ubuntu to act as a proxy server for the internet, and indeed, If I do limit access to the internet t othe ubuntu box and everyhting else filters through it, will I need to set the ubuntu box up as a DNS server for the dynamic allocation of ips when a device connects.
 
If so, will I need to NAT the address outbound so when it hits the router it is identified....
 
Too many questions - not enough knowledge....

---

### Post by mcooke1 on 2010-03-25
I think you can do this with a wireless access point configured as a wireless bridge. Unusual setup but.

---

