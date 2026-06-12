---
title: "Wireless static ip??"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by dannyo616 on 2009-01-19
I am trying to forward a port in order to download and seed torrents.From what I know about port forwarding in windows, I need to set up a static ip. 

However I am using Ubuntu 8.10 and there seems to be a bug where the static ip is ignored or overwritten or something after restarting. I have found several guides telling how to fix this problem, but none dealing with a wireless connection.

Once I get the static ip situation figured out I can get the rest by myself. So if anybody else knows how to fix this problem, please help a brother out.

---

### Post by hyper_ch on 2009-01-19
I prefer WICD as network manager now and it is simple to set there a static lan ip.

Have a look at the repo gen in my signature, WICD is also listed there or do a google search for WICD.

---

### Post by mcduck on 2009-01-19
The best way is to configure the DHCP server on your wireless router to always use same IP address for your Ubuntu machine. This way you can leave network settings on Ubuntu to automatic..

Most routers allow you to do this, and since you either need to configure the IP in both router and the computer, or just in the router, this would be the easiest solution. ;)

---

### Post by dannyo616 on 2009-01-19
Thanks for the help guys, but I think I've figured it out. I went ahead and tried setting up a static ip and it looks like the aforementioned bug either isn't affecting me or doesn't affect wireless connections.

---

