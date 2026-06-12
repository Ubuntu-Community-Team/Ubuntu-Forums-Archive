---
title: "how to configure ADSL on ubuntu edgy?"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by daugirdas on 2006-10-30
Hi,

I had this working with breezy. However I have upgraded and my dsl connection is now broken. I tried to configure 5.10 and 6.06 live cds but that didn't work either. So I guess I didn't do the right thing (I ran sudo pppoeconf; select eth0, enter username and password). However pon dsl-provider just gives a remote connection rejection.

So what were I doing wrong? How should I make things work?

---

### Post by mips on 2006-10-30
Why make life difficult for yourself. You say you are connecting via ethernet. You have an ethernet router, use it as such and not as a modem.

Configure the router via it's web interface. Take it out of bridged mode and into routed mode, set the encapsulaion type & VPI/VCI values, enter userid&passwd.

Configure pc for dhcp and off you go. No need for pppoe.

---

### Post by daugirdas on 2006-10-30
> **mips said:**
> Why make life difficult for yourself. You say you are connecting via ethernet. You have an ethernet router, use it as such and not as a modem.

Configure the router via it's web interface. Take it out of bridged mode and into routed mode, set the encapsulaion type & VPI/VCI values, enter userid&passwd.

Configure pc for dhcp and off you go. No need for pppoe.

I would love to be able to do this. My modem is huawei smartax mt820. I can't find out how to access its webconfig. How do I get there?


P.S. My problem with pppoe was related to an incorrect password. So now I can get connected. However it doesn't start properly during startup. I have to restart it 2ice be4 it works. Here is some console output:
```
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:38:43 localhost pppd[7071]: Plugin rp-pppoe.so loaded.
Oct 30 21:38:43 localhost pppd[7073]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:18 localhost pppd[7073]: Timeout waiting for PADS packets
Oct 30 21:39:18 localhost pppd[7073]: Unable to complete PPPoE Discovery
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:18 localhost pppd[7073]: Timeout waiting for PADS packets
Oct 30 21:39:18 localhost pppd[7073]: Unable to complete PPPoE Discovery
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:18 localhost pppd[7073]: Timeout waiting for PADS packets
Oct 30 21:39:18 localhost pppd[7073]: Unable to complete PPPoE Discovery
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:18 localhost pppd[7073]: Timeout waiting for PADS packets
Oct 30 21:39:18 localhost pppd[7073]: Unable to complete PPPoE Discovery
root@ubuntu:/home/daugirdas# poff
/usr/bin/poff: More than one pppd running and no -a option and
no arguments supplied. Nothing stopped.
root@ubuntu:/home/daugirdas# poff -a
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:42 localhost pppd[5129]: Terminating on signal 15
Oct 30 21:39:42 localhost pppd[5129]: Connect time 8.2 minutes.
Oct 30 21:39:42 localhost pppd[5129]: Sent 321 bytes, received 8978 bytes.
Oct 30 21:39:42 localhost pppd[7073]: Terminating on signal 15
Oct 30 21:39:42 localhost pppd[7073]: Exit.
Oct 30 21:39:42 localhost pppd[5129]: Connection terminated.
Oct 30 21:39:44 localhost pppd[5129]: Exit.
root@ubuntu:/home/daugirdas# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# plog
Oct 30 21:39:44 localhost pppd[5129]: Exit.
Oct 30 21:39:52 localhost pppd[7003]: PPP session is 4493
Oct 30 21:39:52 localhost pppd[7003]: Using interface ppp0
Oct 30 21:39:52 localhost pppd[7003]: Connect: ppp0 <--> eth0
Oct 30 21:39:52 localhost pppd[7003]: Terminating on signal 15
Oct 30 21:39:55 localhost pppd[7003]: Connection terminated.
Oct 30 21:39:55 localhost pppd[7003]: Exit.
Oct 30 21:39:58 localhost pppd[7216]: Plugin rp-pppoe.so loaded.
Oct 30 21:39:58 localhost pppd[7218]: pppd 2.4.4 started by root, uid 0
root@ubuntu:/home/daugirdas# poff -a
root@ubuntu:/home/daugirdas# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@ubuntu:/home/daugirdas# plog
Oct 30 21:40:47 localhost pppd[7278]: Using interface ppp0
Oct 30 21:40:47 localhost pppd[7278]: Connect: ppp0 <--> eth0
Oct 30 21:40:48 localhost pppd[7278]: PAP authentication succeeded
Oct 30 21:40:48 localhost pppd[7278]: peer from calling number 00:90:1A:42:0D:F8 authorized
Oct 30 21:40:48 localhost pppd[7278]: Cannot determine ethernet address for proxy ARP
Oct 30 21:40:48 localhost pppd[7278]: local  IP address 88.118.241.21
Oct 30 21:40:48 localhost pppd[7278]: remote IP address 213.190.60.193
Oct 30 21:40:48 localhost pppd[7278]: primary   DNS address 212.59.0.1
Oct 30 21:40:48 localhost pppd[7278]: secondary DNS address 212.59.0.2

```

---

### Post by mips on 2006-10-31
> **daugirdas said:**
> My modem is **huawei** smartax mt820.

That there is a swear word in my book.

I will look into it and get back to you.

What's your routers IP address and who is your ISP in the mean time ?

---

### Post by mips on 2006-10-31
From, [http://www.huawei.com/products/terminal/pdf/view.do?f=349&ctype=0](http://www.huawei.com/products/terminal/pdf/view.do?f=349&ctype=0)

> 
Dialing Application
Under the access mode of PPPoE, if the built-in dialing function
of MT820 is disabled, you have to install additional dialing
application on your computer that enables it to connect to the
ISP&#8217;s network.

Thats why I said 'swear word' when you mentioned Huawei, these guys make crap.

Post the Windows output of **ipconfig -a** here.


I found a Thai guide on accessing the web interface so it is possible.

Looks like the routers ip address is 192.168.1.1 and username/password is admin/admin.

If you put the 192.168.1.1 address into your web browser it should bring you to the web interface and prompt you for the username & password which is all admin but it might be different.

Lets just try and get to the web interface for now. 
If you tell me who your ISP is I will give you all the correct settings.

Some references I found:
[http://www.maxnet.co.th/images/setup/modem_old/Huawei](http://www.maxnet.co.th/images/setup/modem_old/Huawei) MT820.pdf
[http://www.tttbroadband.com/images_main/howto_setup/howto/huawei/huawei_mt820.pdf](http://www.tttbroadband.com/images_main/howto_setup/howto/huawei/huawei_mt820.pdf)
[http://forums.pcquest.com/forum/viewtopic.php?t=3700&sid=ae61101acc79b8b2c1aae27d0fc9ec49](http://forums.pcquest.com/forum/viewtopic.php?t=3700&sid=ae61101acc79b8b2c1aae27d0fc9ec49)
[http://forums.pcquest.com/forum/viewtopic.php?p=27408#27408](http://forums.pcquest.com/forum/viewtopic.php?p=27408#27408)

---

### Post by daugirdas on 2006-10-31
I managed to figure this out. I found a decent manual on a cd. The trick was to configure my eth0 so that IP was 192.168.1.x (x>=3..255) and gateway was 192.168.1.1. I added my ISP DNS as well. Then I could login onto modem at 192.168.1.1 with username admin and password admin. Then I followed the manual and i-net was up and running.

Thanks for suggestion mips!

---

### Post by Clifweb on 2006-10-31
Can you tell me step by step guide how to set my internet connection I connect the modem using Ethernet connection but I have no router. 
My ISP is MALTANET and this is the web site the give all the details how to se but on windows and MAC [http://helpdesk.maltanet.net/page.jsp?id=67&mainid=1&siteid=1](http://helpdesk.maltanet.net/page.jsp?id=67&mainid=1&siteid=1)
Thanks very much in advance

---

### Post by mips on 2006-10-31
> **Clifweb said:**
> Can you tell me step by step guide how to set my internet connection I connect the modem using Ethernet connection but I have no router.

? You use ethernet that connects to a modem but you have no router. i think you are contradicting yourself.

Please give me the brand and model of the 'modem' device ?

---

### Post by mips on 2006-10-31
I looked at the link you posted and it looks like you will neet to install pptp or l2tp.

I will get back to you later, gotto run.

---

### Post by Clifweb on 2006-10-31
I am using Alcatel 530 if I am not mistaking.

---

### Post by mips on 2006-11-01
You need PPTP (point-point-tunneling-protocol) for your internet connection, this is how your ISP has implemented it.

Look at the Mac or WinXp settings to get all the required addresses in oder to setup LAN card IP/Netmask/DNS etc but you still need to use/install pptp.

There are guides here for ppptp just do a search.

Let us know how it goes.

---

### Post by Clifweb on 2006-11-02
Can you give me a link to were there are information or give me the step on **ppptp** since till now I haven't found anything useful

---

### Post by mips on 2006-11-02
There are 100's of threads here on pptp, so i dont know why you cannot find anything suitable.

[http://www.ubuntuforums.org/showthread.php?t=28396](http://www.ubuntuforums.org/showthread.php?t=28396)
[http://www.ubuntuforums.org/showthread.php?t=287557](http://www.ubuntuforums.org/showthread.php?t=287557)
[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)
[http://www.ubuntuforums.org/showthread.php?t=151186](http://www.ubuntuforums.org/showthread.php?t=151186)
[http://www.ubuntuforums.org/showthread.php?t=41331](http://www.ubuntuforums.org/showthread.php?t=41331)
[http://www.ubuntuforums.org/showthread.php?t=91249](http://www.ubuntuforums.org/showthread.php?t=91249)

You are not going to find anything 100% specific to your situation but it will be close so you will have to change & adapt things a bit.

Have you setup you network interface as per the OSX/WinXP guides ?

---

### Post by Clifweb on 2006-11-05
Still I can't figure it out how to set my internet connection. I installed the pptp. I tried tol follow the instruction found on pptpclient.sourceforge.net ubuntu. but I couldn't follow one part because I couln't understand and second /etc/ppp/chap-secrets  I could open them. What is wrong? plese help me. I don't wish to be stuck on windows.

---

### Post by mips on 2006-11-05
Right now you are asking questions without answering those posed to you.

My adsly service is currently down 7 I'm on dialup so i cannot help you right now.

---

### Post by charles nicholls on 2006-11-05
Adsl routers should be easy tis the usb ones that give the problems 
Edgy should find the adsl router on install, then as suggested above just point your browser at 192.168.1.1 or whatever is in the handbook
that brings up the setup on the router itself, log on probably ADMIN
for log and password. in the uk select RFC 2364 PPPOA for the encapsulation
enter o in the VPI virtual path, enter 38 in the VCI , for multiplexing select VC, enter your user name (whatever@someip.com) and your password. If you pay as you go select CONNECT ON DEMAND else KEEP ALIVE for 24/7
save config and of you go. there is no need to config anything on you actual system once set up any puter with ethernet will connect to the web.

---

### Post by Clifweb on 2006-11-06
Min modem doesn't allow configuration. I have to set the networkcards and create a connection on my system in order to connect. I tried once to configure my modem but with no luck the modem restarted when I was trying the access the setup to configure the modem and telling me that there is nothing to configure. So I am still held up with the connection problem.

---

### Post by mips on 2006-11-06
> **charles nicholls said:**
> Adsl routers should be easy tis the usb ones that give the problems 
Edgy should find the adsl router on install, then as suggested above just point your browser at 192.168.1.1 or whatever is in the handbook
that brings up the setup on the router itself, log on probably ADMIN
for log and password. in the uk select RFC 2364 PPPOA for the encapsulation
enter o in the VPI virtual path, enter 38 in the VCI , for multiplexing select VC, enter your user name (whatever@someip.com) and your password. If you pay as you go select CONNECT ON DEMAND else KEEP ALIVE for 24/7
save config and of you go. there is no need to config anything on you actual system once set up any puter with ethernet will connect to the web.

Charles,

Please look at his posts and the link he provided to his ISP. His isp requires him to establish a VPN (pptp) to their network. It's not a straight forward as for most of us.

Btw, I'm still on dialup...

---

### Post by charles nicholls on 2006-11-06
My fault for not reading correctly, sorry bout that.
but I would ditch that mini modem for a full adsl router if thats an option you can take.

---

### Post by Clifweb on 2006-11-12
Error from syslog:

Nov 11 10:31:01 localhost pppd[5515]: pppd 2.4.4b1 started by root, uid 0
Nov 11 10:31:01 localhost pppd[5515]: Using interface ppp0
Nov 11 10:31:01 localhost pppd[5515]: Connect: ppp0 <--> /dev/pts/1
Nov 11 10:31:01 localhost pppd[5515]: Modem hangup
Nov 11 10:31:01 localhost pppd[5515]: Connection terminated.
Nov 11 10:31:01 localhost pppd[5515]: Exit.

or 

Nov 11 10:34:18 localhost pppd[5648]: pppd 2.4.4b1 started by clifton, uid 1000
Nov 11 10:34:18 localhost pppd[5648]: Couldn't get channel number: Input/output error
Nov 11 10:34:18 localhost pppd[5648]: Exit.

when 

2. sudo vi /etc/ppp/chap-secrets

maltanet.net\\clifaar@maltanet PPTP $PASSWORD *

My settings
1. sudo vi /etc/ppp/options.pptp
Add:
lock noauth nobsdcomp nodeflate


2. sudo vi /etc/ppp/chap-secrets

maltanet.net\\clifaar@maltanet PPTP $PASSWORD

3. sudo vi /etc/ppp/peers/maltanet

pty "pptp 10.0.0.138 --nolaunchpppd"
name maltanet.net\\clifaar@maltanet
remotename PPTP
file /etc/ppp/options.pptp
ipparam maltanet

4. sudo pon maltanet

what I did and the errors I got. Can some figure out what is wrong.

---

### Post by charles nicholls on 2006-11-12
took a look at maltanet and theres no software for Linux, but all the other downloads are standard setup's. I had this prob with a BT usb modem that needed the software loaded before connecting the modem,but as in your case they didnt support linux. however there's a list here for you to check. [http://www.qbik.ch/usb/devices/search_res.php?pattern=modem](http://www.qbik.ch/usb/devices/search_res.php?pattern=modem)

also if you can get someone to download a copy of Puppylinux livecd(50meg)
it has a pretty good setup system on the desktop to connect to the internet id it work in pup it should work in Ubuntu.its also possible to mount and edit your ubuntu system from puppy

---

### Post by mips on 2006-11-13
Clifweb,

Could I suggest you contact [http://www.linux.org.mt/](http://www.linux.org.mt/) for assistance. I bet you these guys would be able to help you faster than we could seeing they have local knowledge.

---

### Post by rksenthilkumaar on 2006-11-16
I also face a problem in connecting to internet!
Now I'm using Ubuntu 6.10
During Installation it properly detected my Eth card & I'm able to configure IP & also could "sudo pppoeconf" as well!!
When I type "pon dsl-provider" it says the connection is on.
But I'm unable to view any sites!!
Even I'm unable to view: 192.168.1.1 let alone type username & password as admin & admin!!

But I could see my modem blickering, when some data's are transferred during the time of connection!!

I'm using Huawei SmartAX MT 882 Modem.
The Connection is dataone [BSNL]

Could some body help me out??

I would be really grateful!!

---

### Post by mips on 2006-11-16
> **rksenthilkumaar said:**
> I also face a problem in connecting to internet!
Now I'm using Ubuntu 6.10
During Installation it properly detected my Eth card & I'm able to configure IP & also could "sudo pppoeconf" as well!!
When I type "pon dsl-provider" it says the connection is on.
But I'm unable to view any sites!!
Even I'm unable to view: 192.168.1.1 let alone type username & password as admin & admin!!

But I could see my modem blickering, when some data's are transferred during the time of connection!!

I'm using Huawei SmartAX MT 882 Modem.
The Connection is dataone [BSNL]

Could some body help me out??

I would be really grateful!!

Do a search here for "BSNL" as well as "Huawei 882"

---

### Post by mips on 2006-11-16
What LAN card do you have ?

lspci -v should give you details.

---

### Post by mips on 2006-11-16
[http://dataone4u.blogspot.com/2006/06/configuring-bsnl-dataone-on-smartax.html](http://dataone4u.blogspot.com/2006/06/configuring-bsnl-dataone-on-smartax.html)  IF you follow this guide you should not need to use pppoe, just enbale dhcp or use static IP parameters. Configure the device for routed mode instead of bridged mode, then specify your isp username & password.
[http://forums.broadbandbuyer.co.uk/forum_posts.asp?TID=5341&TPN=5](http://forums.broadbandbuyer.co.uk/forum_posts.asp?TID=5341&TPN=5)
[http://my.opera.com/boxopen/blog/show.dml/55566](http://my.opera.com/boxopen/blog/show.dml/55566)

---

### Post by rksenthilkumaar on 2006-11-16
What could be the problem??
The screen shot is here!!
And Hearty Thanks for all your efforts!!
Please help me out!

---

### Post by mips on 2006-11-16
I hve very little knowledge of pppoe and always advise people not to use it. Rather let the router perform that function.

It basically says your your username or password is incorrect.
Remember when entering you username you must enter the FULL username, ie. [email]username@ispdomain.xxx.yy[/email]  I dunno what your ISP domain details are but you must enter the part after the @ sign as well. Your password is just your password.

---

### Post by rksenthilkumaar on 2006-11-17
I'm unable to configure my modem as a router!
So when I type pon dsl-provider it says connected!

But When I typed "plog" in Terminal,
It says "CHAP Authentication failed"
"Connection Terminated"

Do you know what does this mean??

What I should do to correct it??

Please help me sort this out!!

---

### Post by charles nicholls on 2006-11-18
you might have luck following this link to a forum all about your modem

:-D [http://forums.broadbandbuyer.co.uk/forum_topics.asp?FID=27&PN=0](http://forums.broadbandbuyer.co.uk/forum_topics.asp?FID=27&PN=0)
hope that helps

---

