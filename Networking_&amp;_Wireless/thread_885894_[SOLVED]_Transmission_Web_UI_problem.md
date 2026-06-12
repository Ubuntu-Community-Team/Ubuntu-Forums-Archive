---
title: "[SOLVED] Transmission Web UI problem"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by suzypeppercorn on 2008-08-10
I just installed the new version of transmission from getdeb on my desktop because i wanted to be able to control my torrents from anywhere.

I installed everything fine and i am able to connect to the web ui from my house by using the LAN IP from my desktop.

However, i cannot connect to the web ui outside of my lan. I have forwarded the default port which is 9091. And i have browsed to whatsmyip.com on my desktop to get the correct ip to try and connect to.

When i try and connect to MYWANIP:9091 i get a page load error.

Any thoughts on how to connect to the web ui from outside of my lan.

Thanks

---

### Post by omegamike3 on 2008-09-15
I seem to be having the same problem. I've setup everything networ-wise exactly the same as I have for all other torrent webui's I've tried before but for some reason I'm unable to see Transmission from the outside world. :(

---

### Post by omegamike3 on 2008-09-15
HAHA! It would seem that the Transmission daemon is not installed by default. You'll want to install the transmission-cli package from the repos:
```
sudo apt-get update; sudo apt-get install transmission-cli
```
and then start the daemon with:
```
transmission-daemon
```
Should load up for you from anywhere now and remember if you have a slower upload connection at home, it'll just take a little longer to load. :)

---

### Post by suzypeppercorn on 2008-09-18
i just found out my dsl modem is actually a router even though it only has one ethernet port on it.

so i just had to open up the necessary ports to make it work.

thanks for the suggestions

---

