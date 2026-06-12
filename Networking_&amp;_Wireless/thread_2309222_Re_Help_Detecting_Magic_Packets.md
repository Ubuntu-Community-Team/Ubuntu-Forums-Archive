---
title: "Re: Help Detecting Magic Packets"
date: 2016-01-08
forum: Networking &amp; Wireless
---

### Post by robo731 on 2016-01-08
I'm trying to set up Wake on Lan for a laptop running Ubuntu Server. I'm trying to troubleshoot why it's not working. My first thought is that it is not receiving the magic packets that are being sent to it. I've tried detecting them using wireshark, but I'm new to Ubuntu and I cannot get it to work. Since I am running Ubuntu Server, I am restricted to the CLI. Is there any way to detect if the laptop is receiving the magic packets? Either through wireshark or some other means?

I followed the steps someone suggested in an old post. I ran: ```
sudo    tcpdump -i eth0 port 9 -vvvv -s0 -n
``` which returned output that    was similar to that of this [post]("http://ubuntuforums.org/showthread.php?t=1807768&p=11064495#post11064495").    According to the person in that thread, this indicates that the    computer is receiving the packets. I'm assuming that person is correct    and that the machine is at least receiving the packets. This is the closest thing to a solution I could find.

---

