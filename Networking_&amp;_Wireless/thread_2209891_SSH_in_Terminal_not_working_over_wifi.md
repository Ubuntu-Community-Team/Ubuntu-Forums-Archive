---
title: "SSH in Terminal not working over wifi"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by info-mbates on 2014-03-07
I have just upgraded my laptop to 13.10 and I'm having probems with ssh in the Terminal.

I can ssh fine when I have an ethernet cable plugged in, but if I am connected with wifi, the connection times out.

I've tried the "Connect to Server" option in nautilus and that works fine over wifi, using both sftp://[host] and ssh://[host]

So the problem seems to be specifically using the ssh command in the terminal when connected to my network using wifi.

I'm not sure how to go about diagnosing the actual cause of this though, so any suggestions or help would be appreciated.

Thanks

---

### Post by Hadaka on 2014-03-08
Hi, try it in this format.. 

ssh -p (port you listen on) (username@wifi card ip address)

to ssh outside your network you will of course need the ISP address
of the far end router. and can use  this same format.
have fun

---

### Post by info-mbates on 2014-03-11
-p is the port on the server, and it doesn't change if I'm using wifi instead of ethernet.

I'm not trying to ssh onto my own computer so I don't care about the ip assigned to my wifi card.

This is not to do with the format of the ssh command, it works fine when I am connected to the network using an ethernet cable. But it doesn't work when I am connected using wifi.

---

### Post by steeldriver on 2014-03-11
Have you tried connecting with verbosity turned up (ssh -vvv *user@host*) to see how  far it gets through the connection process before timing out?

In what way(s) does the interface differ between ethernet and wireless (IP / netmask / gateway etc.)?

---

