---
title: "Using SOCAT to convert TCP to UDP"
date: 2016-04-09
forum: Networking &amp; Wireless
---

### Post by mutiny2 on 2016-04-09
Hey Everyone,


I'm currently running OPENWRT Chaos Calmer on a  Linksys WRT1900AC. My network topography is as follows: Ubuntu 14.04 RTMP streaming  server => WRT1900AC => client device receiving the streaming video


I  have a NGINX RTMP streaming server outputting audio/video to a client  device within the same LAN. My goal is to convert the RTMP TCP stream to  an RTMP UDP stream at the router using SOCAT. So far I have not been  able to get the packets to convert to UDP. Using Wireshark, I still see  TCP packet being received on the client device and at a different port  than I specified. The method I'm using is below.


SSH into OPENWRT/WRT1900AC
[FONT=tahoma]Issue the following:[/FONT]```
socat TCP4-LISTEN:1935,fork UDP4:123.456.7.8:1935
```



                     
IP: 123.456.7.8 is the client device IP. The client device connects to the video stream server with rtmp://987.654.3.2:1935. Port 1935 is set aside specifically for RTMP streaming.

Am I implementing socat wrong? Maybe I should be running socat at the server level?

Thanks in advance for any help you guys can provide.

---

