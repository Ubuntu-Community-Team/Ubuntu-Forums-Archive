---
title: "Network Settings Tool messes up hosts file"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by Doncr on 2008-08-03
Greetings - I have searched but not found an answer to this. I have never had much luck using network configuration tools, but now I need it to work.

I have my machine set up as bassak.robertson.net.nz on 192.168.1.2

I also have [www.robertson.net.nz](www.robertson.net.nz) and don.robertson.net.nz as internet sites and as local development sites

In my hosts file I have:

127.0.0.1 localhost.localdomain localhost
192.168.1.2 bassak.robertson.net.nz bassak

To work on the local sites (don and www) I add

192.168.1.2 [www.robertson.net.nz](www.robertson.net.nz) www
192.168.1.2 don.robertson.net.nz don

If I use the network tool to switch between the two setups:

127.0.0.1 localhost.localdomain localhost sometimes disappears
192.168.1.2 bassak.robertson.net.nz bassak gets changed to
192.168.1.2 bassak.robertson.net.nz bassak.robertson.net.nz

and I get 
sudo: unable to resolve host bassak

anytime I try to do anything.

I have never bothered to look into it until now - just had other things to do, but I need to set up other users so they can switch between the networks. So it is annoying.

I have no local DNS, DHCP, wireless or anything. It is a very simple setup.

---

