---
title: "Creating a Network Bridge with an Xbox 360"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Brad644 on 2011-04-20
Today is my first day using Ubuntu, so bare with me (I have been using Windows my entire life).  What I'm trying to do is connect to Xbox Live through the wireless connection that my laptop has with my home network.  It's probably a really simple issue, but I can't seem to figure it out.

---

### Post by iponeverything on 2011-04-20
so the you want the lap top to bridge between the wired and wireless networks for Xbox? I it not clear, you should draw a picture..

---

### Post by TheHammer23 on 2011-05-05
You want to install firestarter through the Ubuntu Software Center. It's a firewall tool that lets you easily bridge your Ethernet and wireless connections. (I happen to use the same setup for my Xbox 360). Once you install it walk through the wizard for configuring the firewall. I configured my xbox and ethernet with static IP's and used DHCP on the wireless end. This seemed to be the easiest way to configure the network. Let me know if you need more detailed instructions.

Note: One issue I have with this method is that I have to log in to the Ubuntu box for the network connection to establish. It has something to do with network manager. I used to be able to fix it by checking the "Available to all users" checkbox in the connection properties but this does not seem to work for me in 10.04. YMMV.

---

