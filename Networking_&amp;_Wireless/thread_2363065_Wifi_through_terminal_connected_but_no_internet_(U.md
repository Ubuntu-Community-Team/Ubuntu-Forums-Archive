---
title: "Wifi through terminal connected but no internet (Ubuntu Server)"
date: 2017-06-05
forum: Networking &amp; Wireless
---

### Post by arya6000 on 2017-06-05
I'm running into a weird issue with my wifi connection through the terminal I use the following command to connect to my wifi network

```
sudo nmcli d wifi connect MYROUTERSSID password MYPASSWORD
```

I successfully connect to the wifi network

I then test to see if there is internet on the wireless interface by running the following command

```
ping -I wlx74da38839273 8.8.4.4
```

Now the problem

If I connect to my home wireless router I do get internet, but if I connect to any of my Android phones with tethering enabled, it does connect, but when I ping it I get 100% packet loss. I tried the Tethered connection on 3 different laptops running Windows and it works 100% fine. What are some the things to check for so I can troubleshoot this problem?

---

