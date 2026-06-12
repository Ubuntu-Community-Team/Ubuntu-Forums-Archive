---
title: "Connecting to server (w/ anything but ssh) breaks network connection"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by tmcmack on 2008-05-24
Hi, all -- asking for some help troubleshooting a network connection.

I have a laptop that's my primary computer, and I am refurbing an old desktop that I'd like to use as a media server. Both have Hardy installed, though the server is server edition, command-line only. On the server I can use wget, apt-get, and ping to connect to the internet, so I know its wireless network connection works.

I set the server to a static IP and began connecting to it from the client laptop. I can SSH into the server with no problem; I can stay logged in all day, run commands (even interactive stuff like aptitude and top), no problem.

However, if I try to (A) transfer a file larger than a few KB to or from the server with SCP or (B) stream audio to it from the laptop via pulseaudio, the server loses its network connection. I get a few KB across with SCP and the command hangs; I get a few seconds of sound out of the pulseaudio server and then it falls silent. Once the server loses its network connection, not only can I no longer connect to the server with SSH anymore, it can no longer connect to the network (ping fails, etc.) until I run sudo /etc/init.d/networking restart. I can consistently reproduce the error, knocking out the network connection and then stepping back to the server's local keyboard and starting up its connection again.

To try to find the problem, I've been comparing the results of certain commands before and after I knock out the server's network connection. The output of lshw and dmesg is identical before and after the network connection goes down. There is a single line of difference between the output of lsmod before and after: before, lsmod shows that the ipv6 module is referred to ten times; after, 12 times. No clue what this means. However, there is a line in the dmesg output that says "ra0: no IPv6 routers present". ("ra0" is the name of the network interface I'm using.) Maybe it expects my router to be IPv6 (whatever that means)? I've had the router for four years; maybe it's using an older protocol.

How can I troubleshoot this further? How can I tell what's causing the network connection to go down?

---

