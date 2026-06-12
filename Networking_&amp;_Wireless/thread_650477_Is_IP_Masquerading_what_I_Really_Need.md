---
title: "Is IP Masquerading what I Really Need?"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by prodonjs on 2007-12-26
I am trying to configure an FTP server using Ubuntu Server Gutsy and ProFTPD. In the process, I have also created a machine that I can create SSH tunnels through in order to route BitTorrent traffic (since our university network blocks all torrent traffic). Anyways, I have gotten the FTP server to work successfully from inside my network, and it also works fine from outside the network if I used the command-line based FTP tools.

But when I try to use a browser and passive FTP mode, the connection hangs. I have enabled Masquerading in my proftp.conf file (using the WAN address for my router assigned by my ISP). I have also configured the appropriate ports in my router for forwarding to the local IP address of the Ubuntu machine. However, I am still unable to get anything to work from outside the LAN if I use a web browser.

I saw an article about IP masquerading using iptables on the Ubuntu Server Guide section of the site, but I'm not sure if that's really what I want. I'm not planning on using the Ubuntu Server as a NAT device, in fact it's actually a virtual machine that is very lightweight and really is only going to be used to host files and to act as a proxy for torrent connections. How can I configure things so that an external user can connect via a web browser with my FTP server using passive FTP? What am I missing besides the configuration file in ProFTPD, opening the ports in my router's configuration page, and configuring iptables to allow input from those ports?

---

