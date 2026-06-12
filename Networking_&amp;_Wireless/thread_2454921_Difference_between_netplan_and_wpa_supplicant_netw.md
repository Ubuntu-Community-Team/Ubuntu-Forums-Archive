---
title: "Difference between netplan and wpa_supplicant network connection"
date: 2020-12-08
forum: Networking &amp; Wireless
---

### Post by bunnyxiyo on 2020-12-08
I used Google Translator. Please point out if the grammar is weird.


I am trying to automatically connect wifi on my raspberry pi.
And there are currently three problems.


First you need to write the password in clear text when trying to configure the network in /etc/netplan/50-colud-init.yaml. I don't want this. Is this the usual way?
Second, if you look at the comments in 50-cloud-init.yaml you can see that this setting has been initialized. Initialization doesn't really happen, but when you initialize it causes big problems. If you have deployed your raspberry pi externally, is this the correct way to configure the network using netplan?
Third, if you use wpa_supplicant to connect to the network, you don't need to write the password in plain text. However, like Net Plan, I would like to use Linux's own function that is automatically connected only when information is registered.


In summary, the point is this.
I want to encrypt my password and store it on my raspberry pi while using netplan's features. And I don't want to create a separate service for it.

---

### Post by CelticWarrior on 2020-12-08
Welcome.

Which OS are you using in the RPi?

---

