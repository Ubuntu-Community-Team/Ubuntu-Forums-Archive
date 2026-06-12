---
title: "SSH from outside LAN doesnt work but webserver does?!? Ubuntu 14.04 64"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by tylersprice84gmai on 2014-07-16
Been searching as much as im able to and can not fix this issue, I am very new to linux so please bring lube, lol.

I setup 14.04 server fresh on a dedicated machine with AMP, postfix, dovecot etc, it has 2 connections 1 being wired eth0 and 1 being wifi wlan0, i have this set up and working beautifully i used a couple route add commands to do it and will list them.
I can view my webserver remotely/locally on port 80, if i try and ssh in from android i get a host terminated connection (connection reset by peer), if i ssh from a diff comp using my external IP (using putty) it doesnt say anything than times out.
If i ssh in locally all is well, I have my router port forwarding correctly and confirmed from a remote port scan.
openssh-server is installed.
havnt touched sshd_config (did view it to see if anything messed up)

here is my /etc/network/interfaces setup

auto eth0
iface eth0 inet static
address 192.168.1.2
up ip route add 192.168.1.0/24 via 192.168.1.1 || true
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameserver 192.168.1.1 (resolve.conf head is set up with 8.8.8.8 8.8.8.4)
dns-search <DOMAIN>
-----------------------------
here is my rc.local which has been chmod +x 'd

sudo ifconfig eth0 down
sudo ifconfig wlan0 down
sudo ifconfig wlan0 192.168.0.3 netmask 255.255.255.0 broadcast 192.168.0.255 up
sudo route add default gw 192.168.0.1 dev wlan0
sudo wpa_supplicant -B -D wext -i wlan0 -c <CONFIG FILE>
sudo ifup eth0
sudo ifconfig eth0 up
exit 0
-------------------------------
i can ping google.com, 192.168.0.1, 192.168.1.1 and all computers on my internal LAN on both networks.
i can SSH IN using 192.168.0.3 from inside my network, works great.
i can not SSH IN using <EXTERNAL IP/HOST NAME FROM DDNS>
i can locally view my web server, i can remotely view my web server using <EXTERNAL IP/HOST NAME FROM DDNS>
ports 22 is confirmed open from a remote port scan.
router is port forwarding properly as well.
rebooted router and LAMP server.
made sure sshd is turned off on all other computers (windows so no sshd) routers (main router cisco, have a ddwrt repeater setup running flawlessly)
netstat confirms tcp:ssh *.* LISTEN
nmap <LOCAL IP> -p 22 returns 22/tcp open ssh (0.000094s latency) 1 IP address (1 host up)
nmap <EXT IP> -p 22 returns 22/tcp open ssh (0.010s latency) 1 IP address (1 host up)
--------------------
ipv6 is disabled from GRUB
ndiswrapper bcmn43xx64 : driver installed device (0846:9011) present
DDWRT repeater router is set up perfect no issues whatsoever, even did a port 22 forward in there just to make sure, that changed nothing.
-----------------------------------------------------------------------
Seriously got me scratching my head, any help would be much appreciated, Thanks in advance!

---**-- EDIT --**---
edited sshd_config
bind sshd to 192.168.0.3
commented out X11 forward
---------------------------------------
I believe its an issue with my routing table, if anyone can enlighten me i would appreciate it.

tcpdump -v -n -nn -tttt -i wlan0 port 22
<attempt to ssh from 4G>
returns:
2014-07-16 04:03:48.595659 IP (tos 0x4, ttl 52l id 41938 offset 0, flags [DF], proto TCP (6), length 60)
209.91.x.x.<port number> > 192.168.0.3.22: Flags [S], cksum 0x0064 (correct), seq xxxxxx, win xxx, options [mss xxx,sacOK,TS val xxxxxx ecr 0,nop,wscale 6], length 0
<This following line is my server replying to request so all pretty well the same except ....
192.168.0.3.22 > 209.91.x.x<port number> >

few more lines similar to that, so what i gather is my server is receiving these ssh requests than attempting to reply but does not know how to route it properly?

am i correct in my assumptions? and how can i remedy this?

---

### Post by tylersprice84gmai on 2014-07-16
After alott of playing around i finally found a solution that is working, it is related to having a HOST router than using a DD-WRT router to repeat (client bridge (routed)) the host signal, the trick is to forward all your ports properly on the **[COLOR=#800080]HOST[/COLOR]** router, which I had done, THAN put the **[COLOR=#0000ff]LAMP/SSH/FTP/xxxxxxx server(Internal IP)[/COLOR]** into the _**[SIZE=4][COLOR=#ff0000]DMZ on your DD-WRT router[/COLOR][/SIZE]**_.

I have been able to ssh,http,https,ftp,sql,etc into my server from the www successfully.

Hope this can help someone in the future, in my searches i found a few similar posts with this problem.

---

