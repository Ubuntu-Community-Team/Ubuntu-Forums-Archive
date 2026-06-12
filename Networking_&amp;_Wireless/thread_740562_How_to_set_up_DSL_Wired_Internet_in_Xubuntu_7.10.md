---
title: "How to set up DSL Wired Internet in Xubuntu 7.10"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by noobuntu7 on 2008-03-30
Hey,
I had a computer with Xubuntu 7.10 on it, it worked great with my broadband high-speed cable internet (it was plug-and-play, I could just plug the Ethernet cable in and Xubuntu automatically recognized the network and I could browse with Firefox immediately). I gave the computer to my friend who has a slightly different internet setup (it's DSL from Mediacom) and he tried plugging his Ethernet cable from his modem into the computer and the computer acted like it recognized the network (the little computer network icon did it's spinning thing and had a green check mark on it). But when he tries to launch Firefox and go to a website it gives him the error message:

[B]Firefox can't find the server at [www.example.com](www.example.com).


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.[/B]


He called me and I tried to help but I don't know what to do. The computer has no firewall or proxy settings on it. Can anyone give me some ideas of what might be wrong and what he could do to fix it? Thanks!

---

### Post by Iowan on 2008-03-30
Modems sometimes "lock in" on MAC address.  Try resetting (power cycling?) the modem.

---

### Post by superprash2003 on 2008-03-30
well to make sure the computer is getting an ip.. please go to the terminal and type ifconfig and post results here

---

### Post by noobuntu7 on 2008-04-01
I talked to my friend today and he said that he called a Mediacom representative who was not familiar with either Linux or Firefox, but told him to try power-cycling his modem (which he did) and it didn't work. I asked him to start a terminal and run ifconfig and the computer gave him a long list of numbers and letters with colons in between. What should he specifically be looking for in the ifconfig command results? Please help out because I'd like to get his computer running with the internet. Thanks for all the help!

---

### Post by superprash2003 on 2008-04-02
well in the output he should see ETH0 and an ip next to it.. if the ip is similar to that of the modem i.e. if the modem ip is 192.168.1.1 and his ip is 192.168.1.x then its setup right.. if hey cannot see any ip .. or if he sees an ip like 169.x.x.x then he has a problem with his ip setup and needs to set a static ip or configure the eth0 card properly

---

