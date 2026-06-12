---
title: "Public IP address"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by mofire on 2010-08-19
Hi guys

I have a problem with using public IP address on my ubuntu server which is working perfectly on the LAN,but once i change private IP to public IP i can communicate with the server. here is how my interfaces looks like

iface eth0 inet static
        address 178.xx.xx.xx
        netmask 255.255.255.xx
        gateway 178.xx.xx.xx

and my resov.conf having DNS

nameserver 178.xx.xx.xx
nameserver 178.xx.xx.xx

am trying to connect to the internet through a router whose public IP is the one am using as my gateway. So guys wat am i not doing or am I doig wrongly ? Any help will be highly appreciated.

---

### Post by Bachstelze on 2010-08-19
Don't put your public IP there.  What are you trying to do?

---

### Post by NCLI on 2010-08-19
> **mofire said:**
> Hi guys

I have a problem with using public IP address on my ubuntu server which is working perfectly on the LAN,but once i change private IP to public IP i can communicate with the server. here is how my interfaces looks like

iface eth0 inet static
        address 178.xx.xx.xx
        netmask 255.255.255.xx
        gateway 178.xx.xx.xx

and my resov.conf having DNS

nameserver 178.xx.xx.xx
nameserver 178.xx.xx.xx

am trying to connect to the internet through a router whose public IP is the one am using as my gateway. So guys wat am i not doing or am I doig wrongly ? Any help will be highly appreciated.

When inside your own LAN, you have to use your the local IP-address assigned to your server by your router.

When outside, accessing it from the internet, you need to use your public IP, and configure your router to forward the ports you need to be able to be able to access from outside to your server.
Forexample, if you want to be able to use SSH from the internet, you'll have to forward port 22 to your server.

---

### Post by mofire on 2010-08-19
@Bachstelze, thanks for the reply,am trying to have a site I have created accessed through the internet which am serving from my server. so where do i put the public IP then if not there ?
@NCLI ,thanks for the reply. would you mind guiding me on how to do that port forwarding on Ubuntu am a newbie here. 
thanks again guys.

---

### Post by lisati on 2010-08-19
Most of the time, with the default settings for your web server, you won't need to put the public IP address anywhere: it is usually set by your ISP. If you have a dynamic IP address, it can change, which will mean tinkering with your settings if you have a need for your server to know it. 

The specifics of setting up port forwarding on your router will depend on the make and model router you are using: it's normally done through your router's browser-based control panel.

---

