---
title: "vpnc can't ping vpn network"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by lee_connell on 2005-07-27
hey guys,

i got vpnc installed i setup my config using example.conf (made changes as appropriate) and i am asked for username and password and it says it connected and puts the process in memory.

i check ifconfig and there is an ip assigned to me from the pix using tun0 interface.

however i cannot ping any ip or connect to any ip on the network im connecting to which is 192.168.0.0.

I am not allowed to ping any host names like [www.google.com](www.google.com) as i can see there was a route added to my table which throws all traffic to tun0 which would be the answer to this.

my concern and main question here is why can't i ping any 192.168.0.0 network?  the error it gives me is this:  

/etc/vpnc$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

---

### Post by gruepig on 2005-07-27
Two questions:

1. Do you have any firewall rules in place (iptables)?

2. What does your route table look like?  (Run 'route -n' and post the results.)

---

### Post by lee_connell on 2005-07-28
hey,

im not at that computer right now so i can't give u the routes but their is a default route 0.0.0.0 to tun0.  i'm not running iptables.

i did install firestarter but i didnt start it up, maybe i should look at that.

I did install cisco client 4.0.5 and it did work.  However when i make rdp or vnc connections to the remote computer it connects but it does not give me any desktop interface, it's like it fails sending the rdp data and i get just a black screen on both vnc and rdp?

A different site i connect to i can log in with cisco client and i can ssh into the box and everything with no problems.  When i load web page on the intranet it's really really slow compared to when in windows.

Kind of a bummer having these issues, as i have to use windows at work because of this :(

vpnc doesn't even pass the authentication process on one of my sites.

I would like to try cisco client 4.6 but it wont compile on hoary?

---

### Post by lee_connell on 2005-07-29
does anyone know of vpnc 0.3.3 version in deb format that works in hoary?

---

### Post by lee_connell on 2005-07-30
I compiled 0.3.3, you just need libcrypt-dev installed.

Another question, i got cisco 4.6 compiled and working, however i dont see any route from 4.0.5 or 4.6 on my system, is this normal cisco behavior?  No extra routes after cisco connection.

---

