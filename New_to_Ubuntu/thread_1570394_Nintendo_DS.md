---
title: "Nintendo DS"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by olddai on 2010-09-08
I have just bought my daughter the latest Nintendo DS and now she wants me to configure the DS so that she can get online using my Internet connection. Is this possible and if so how would i accomplish this anyone please. I am running Ubuntu 10.04 (Lucid Lynx).

---

### Post by bredman on 2010-09-08
A Nintendo DS needs access to a WiFi router, and the WiFi router needs access to the internet. In most cases, the router is connected directly to your phone line or cable, so there is no need to have your Ubuntu machine involved in the solution.

Please let us know more about your internet connection. Do you use phone/cable/3G/WiMAX etc?

Do you have a WiFi router in your house?

---

### Post by olddai on 2010-09-08
My Broadband Internet connection is provided by TALKTALK via a telephone line and router.

---

### Post by Mammut1492 on 2010-09-08
do you have wireless access to your router (can you connect to the internet without plugging in a cable?)

---

### Post by cbctechhead on 2010-09-08
If you do have wireless and you use security make sure it is only WEP type otherwise the Nintendo DS can not connect.

---

### Post by olddai on 2010-09-08
I am using an ethernet cable connected to my router and computer to get online because i wasn't sure how to set up a wireless connection.

---

### Post by bredman on 2010-09-08
Can you tell us the model number of the router? It should be on the bottom of the router.
There is a chance that it supports WiFi and you didn't know it.

---

### Post by olddai on 2010-09-08
HUAWEI EchoLife HG521
Broadband Wireless ADSL2+ Router

---

### Post by bredman on 2010-09-08
Is looks like you have a wireless router after all...

You should be able to tell the NDS to scan for WiFi, and then connect to the network.

However, this may not work if your router has not been set up correctly, or if wireless has been turned off. To check the settings on the router, check the user manual for the router.

If you don't have the router user manual, your best bet is to open a web browser on your Ubuntu machine and type one of the following on the browser address line
192.168.0.1
192.168.1.1
and you should see a configuration page for your router.

The above examples are the common addresses used by routers. There is a chance that your router uses something different. In this case, enter the following command on your Ubuntu machine
route

and look for the address in the gateway column. There is a very good chance that the Ubuntu machine is using the router as its gateway to the Internet.

---

### Post by olddai on 2010-09-08
I  typed 192.168.1.1 and the HUAWEI interface opened up asking for a password so i typed admin twice and got in. Now i've got to change the username and password before i do anything else. Thanks for all the help

---

