---
title: "SSH HTTP Port forwarding"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-06-06
Question, I have the router at 192.168.1.1, which I can configure via a browser, from intranet.
I have a ssh server at 192.168.1.2

It's not possible to configure the router from outside 192.168.1.*, but I would like to be able to do so. I don't want to change the router config to allow external access, though.

So... can I forward/tunnel my firefox/GoogleChrome connection somehow via ssh ? So that from outside, I login on 192.168.1.2 via ssh, and then forward the browser request to 192.168.1.1 + forward back the routers answer ?

---

### Post by bodhi.zazen on 2010-06-06
Yes it can be done, tunnel http over ssh.

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

There are many tutorials on how to do this if the one above does not work for you.

From Windows clients, use Putty.

---

