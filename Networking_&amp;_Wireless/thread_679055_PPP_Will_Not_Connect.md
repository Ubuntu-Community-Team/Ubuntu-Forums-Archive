---
title: "PPP Will Not Connect"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by arettinger on 2008-01-26
I am using an HSF Conexant modem on a Dell Inspiron 1525 laptop under Ubuntu 7.10. 
I installed the Linuxant 56K driver via a DEB as normal. It appears in the restricted drivers manager. I attempted to form a connection through the network manager. The modem dials, and appears to succeed; however, I am unable to connect to any web pages. I cannot even ping. It is literally as though the connection never existed. I have edited resolv.conf, as is often necessary under other distributions, to no avail. I have no firewall installed. Please note that the connection functions normally under the terminal wvdial; I would like to continue use of the network manager.
Here is the output of 'tail -35 /var/log/messages':
```
root@arettinger:/home/arettinger# tail -35 /var/log/messages
Jan 26 14:32:12 arettinger chat[15897]: abort on (NO DIALTONE)
Jan 26 14:32:12 arettinger chat[15897]: abort on (NO DIAL TONE)
Jan 26 14:32:12 arettinger chat[15897]: abort on (NO ANSWER)
Jan 26 14:32:12 arettinger chat[15897]: send (ATZ^M)
Jan 26 14:32:12 arettinger chat[15897]: send (AT&FH0M0^M)
Jan 26 14:32:12 arettinger chat[15897]: expect (OK)
Jan 26 14:32:12 arettinger chat[15897]: ATZ^M^M
Jan 26 14:32:12 arettinger chat[15897]: OK
Jan 26 14:32:12 arettinger chat[15897]:  -- got it 
Jan 26 14:32:12 arettinger chat[15897]: send (ATDT18475897883^M)
Jan 26 14:32:13 arettinger chat[15897]: timeout set to 75 seconds
Jan 26 14:32:13 arettinger chat[15897]: expect (CONNECT)
Jan 26 14:32:13 arettinger chat[15897]: ^M
Jan 26 14:32:13 arettinger chat[15897]: AT&FH0M0^M^M
Jan 26 14:32:13 arettinger chat[15897]: OK^M
Jan 26 14:32:13 arettinger kernel: [ 5834.936000] sky2 eth0: enabling interface
Jan 26 14:32:13 arettinger kernel: [ 5834.944000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 26 14:32:16 arettinger kernel: [ 5836.988000] sky2 eth0: disabling interface
Jan 26 14:32:18 arettinger kernel: [ 5839.132000] sky2 eth0: enabling interface
Jan 26 14:32:18 arettinger kernel: [ 5839.140000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 26 14:32:18 arettinger kernel: [ 5839.232000] sky2 eth0: disabling interface
Jan 26 14:32:22 arettinger kernel: [ 5843.296000] sky2 eth0: enabling interface
Jan 26 14:32:22 arettinger kernel: [ 5843.304000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 26 14:32:42 arettinger chat[15897]: ATDT18475897883^M^M
Jan 26 14:32:42 arettinger chat[15897]: CONNECT
Jan 26 14:32:42 arettinger chat[15897]:  -- got it 
Jan 26 14:32:42 arettinger pppd[15877]: Serial connection established.
Jan 26 14:32:42 arettinger pppd[15877]: Using interface ppp0
Jan 26 14:32:42 arettinger pppd[15877]: Connect: ppp0 <--> /dev/modem
Jan 26 14:32:47 arettinger pppd[15877]: CHAP authentication succeeded: 
Jan 26 14:32:47 arettinger pppd[15877]: CHAP authentication succeeded
Jan 26 14:32:47 arettinger pppd[15877]: local  IP address 4.142.132.94
Jan 26 14:32:47 arettinger pppd[15877]: remote IP address 209.247.5.15
Jan 26 14:32:47 arettinger pppd[15877]: primary   DNS address 209.244.0.3
Jan 26 14:32:47 arettinger pppd[15877]: secondary DNS address 209.244.0.4
```

---

