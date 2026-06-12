---
title: "oidentd / xinetd problems."
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by nazrm on 2007-05-30
Setup:

Ubuntu feisty with oidentd and xinetd. I've been googling like a maniac the past few days, but I just can't get oidentd to work. Port 113 is forwarded in the router and all.. 

/var/log/syslog:
> 
May 30 11:14:41 scaryfish xinetd[9427]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9428]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9429]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9430]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9431]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9432]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9433]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9434]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9435]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9436]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9437]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9438]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9439]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9440]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9441]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9442]: warning: can't get client address: Transport endpoint is not connected
May 30 11:14:41 scaryfish xinetd[9443]: warning: can't get client address: Transport endpoint is not connected


that's when I try to connect to a IRC server.

/etc/xinetd.d/auth:
> 
service auth
{
disable = no
socket_type = stream
protocol = tcp
wait = yes
user = nobody
server = /usr/sbin/oidentd
server_args = -F -i -u nobody -g nobody
nice = 10
}


Any help is greatly appreciated.

---

