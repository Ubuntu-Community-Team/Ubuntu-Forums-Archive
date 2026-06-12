---
title: "Creating IP sec tunnel"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by gijs007 on 2015-07-06
I'm trying to setup a VPN/Tunnel between three(3) Ubuntu 15.04 servers. I've googled and it seems that I can use IPsec tools for this.


  I've only found the following tutorial:[https://help.ubuntu.com/community/IPSecHowTo](https://help.ubuntu.com/community/IPSecHowTo) and can't seem to generate and keys by running:
  dd if=/dev/random count=16 bs=1| xxd -ps
  in SSH, it just continues to run until I end it with ctrl + C and it doesn't generate any key..
How can I generate the keys I need?


  My second question is if there are any other tutorials on how to  setup the IP sec tunnel with the IPsec tools, I don't find the one that I  mentioned above very useful. I couldn't find any tutorials with Google  for the IP sec tools.
  My final question is how I can use a private range address that isn't  routable over the internet for use inside the tunnel. (So that if the  tunnel fails the applications that make use of the IP of the other  server can't send unencrypted data over the internet)

---

### Post by Anakondarh on 2015-07-15
Are your sure you're typing that command right? Check for typos. It works perfectly on my ubuntu server over SSH...

---

