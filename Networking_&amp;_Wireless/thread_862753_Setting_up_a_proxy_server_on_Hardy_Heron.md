---
title: "Setting up a proxy server on Hardy Heron"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by KateKatja on 2008-07-17
Hi,

I have recently installed a linux distro. hardy heron for the very first time after getting frustrated from my past installation of windows vista ultimate. 

I am looking to setup a proxy server so as not to "broadcast" my ip details when I am browsing online.

I tried searching in forums for some existing documented material on the same subject but could not find anything exactly related to my issue. The closest I could find was "to setup anonymous http proxies on firefox". The problem with this kind of setup is that it won't let me enter into Java based chat rooms.

I would really appreciate if you can suggest me an online guide / tutorial.

Kate

---

### Post by diaa on 2008-07-30
As far as I understand, you want to use a proxy server to provide privacy and anonymity, well in this case you should use/connect to a remote proxy server not install one on your machine, because if you do then nothing is hidden, the requests are coming from your machine, but when using a remote proxy server, the source address will be that of the proxy.

Okay, First you have to get the address(ip address) and port of a proxy that is available to you, personally I don't know any reliable source for free proxies but you can search the web and you'll find many, probably unreliable, ones, once you get the ip and port which should look like:
158.2.150.10:3000

You should open KDE control center, navigate to Internet & Network > Proxy, and use the "Manually specify the proxy settings", and in the setup dialog, put the IP and port in the HTTP field(and the two other fields in case the proxy supports them).

This will force all KDE apps to use this proxy when connecting to the WWW.

---

### Post by dmizer on 2008-07-30
Configuring a proxy server to mask your ip address would require you to have your proxy server in a location (or on a connection) other than your own.

If you only want to mask your IP address, there are loads of tutorials out there on how to configure Firefox to do this.

Edit:
Here's a popular Firefox plugin for finding and using proxy servers: [https://addons.mozilla.org/en-US/firefox/addon/2464](https://addons.mozilla.org/en-US/firefox/addon/2464)
Here's a guide on how to configure foxyproxy: [http://foxyproxy.mozdev.org/howto.html](http://foxyproxy.mozdev.org/howto.html)

---

