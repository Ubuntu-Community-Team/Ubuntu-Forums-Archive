---
title: "problems with synaptic and iternet"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by 3ws on 2007-10-22
I am having a number of problems with 7.10. 

After installation I could access my home network but could not get an internet connection. I also couldn't get synaptic to work - message saying that the repositories were out of date and that I need to update. I tried to download the 6 or 7 additional files but was unable to do so, not even 1 KB, as if synaptic could connect to the servers.

I did some research and found a possible solution to the internet/Firefox problem - setting IPv6 to false. I checked my Firefox configuration and found that the value was already set to false. So I set it to true and got internet access.

However, Synaptic still says that I don't have an internet connection. After several reinstallations and more research I tried

sudo apt-get update

every connection timed out.

I have also tried a different NIC but had the same problems. I really have no idea what to do next. Any ideas?

---

