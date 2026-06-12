---
title: "Limit wireless networks based on user"
date: 2020-08-23
forum: Networking &amp; Wireless
---

### Post by Sam_Williams on 2020-08-23
Hi,
I've got a situation where a Ubuntu laptop is used for both household and business use. We have two wireless networks set up, one for business devices (radius) and one for IoT / kids devices (WPA personal). Our firewall prevents any new connections from the IoT devices to the business network.
Is there an easy way to configure the ubuntu laptop so that when one of the kids logs in it uses the IoT wireless network, but when my wife or I login it uses the business network (and uses our login details for the radius auth etc.)?
Thanks in advance!

---

### Post by CelticWarrior on 2020-08-23
You all have different user accounts, don't you?

Typically it should connect to the last used access point per account.

---

### Post by Sam_Williams on 2020-08-23
Hi,
Yes, separate user accounts for each user. But not sure how to limit certain SSID's to certain users? Do I need to define a group for the business network users, add the group to the users, and then chown the network definition to that group?

---

### Post by SeijiSensei on 2020-08-23
How about as a simple kludge you first change the SSID of the business network in your router, then turn off SSID broadcasts? That would require you to enter the SSID, but it wouldn't appear in the list.

---

