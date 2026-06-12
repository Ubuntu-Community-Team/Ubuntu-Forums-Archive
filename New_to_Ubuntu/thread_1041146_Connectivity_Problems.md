---
title: "Connectivity Problems"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-01-16
I would appreciate any help and/or inspiration to resolve a maddeningly annoying problem I have had for the past week.

I usually connect via Vodafone Mobile Broadband. Occasionally though, I connect via one of two wireless routers, depending upon where I am at the time and/or the signal strength available.

My problem is that when I connect, I can only sometimes keep the connection open. On other times, my system tells me I'm connected but I simply cannot browse the web or collect email. I have to disconnect and then try connecting again.

Things didn't used to be this way, and the only thing that I can imagine might be the problem is that I've clicked some option that tries to automatically connect, and my PC is now getting itself confused about which connection I'm trying to make.

Sorry to be so vague, but does this problem ring any bells with anyone? And if so, does anyone have any ideas about how I can resolve it?

(System spec is in my sig.)

---

### Post by cmnorton on 2009-01-16
On wireless/wired routers, there is usually an http-accessible admin application. If you can reach that, you probably have an ISP-related connectivity problem.

Is this happening with other systems and/or with other OSs?

---

### Post by Roger Allott on 2009-01-16
> **cmnorton said:**
> On wireless/wired routers, there is usually an http-accessible admin application. If you can reach that, you probably have an ISP-related connectivity problem.

Is this happening with other systems and/or with other OSs?

I don't have access to the router. My normal MO is to use Mobile Broadband with a dongle connected by USB.

---

### Post by cmnorton on 2009-01-16
I know it's old advice, but I would suggest that you start looking in your logs (/var/log), starting with syslog and messages.

---

### Post by Roger Allott on 2009-01-17
> **cmnorton said:**
> I know it's old advice, but I would suggest that you start looking in your logs (/var/log), starting with syslog and messages.

Thanks for the tip, but those files would make as much sense to me if written in ancient Sanskrit!

Could you (or someone) let me know if you see anything odd with the following syslog snippets?

The first snippet is when I connect and I am them able to surf the web (a BBC website page):

```
Jan 17 13:34:30 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Vodafone (contract)' 
Jan 17 13:34:30 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Jan 17 13:34:30 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan 17 13:34:30 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Jan 17 13:34:30 stuart-laptop NetworkManager: <debug> [1232199270.908432] nm_serial_device_open(): (ttyUSB0) opening device... 
Jan 17 13:34:30 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  (ttyUSB0): powering up... 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Registered on Home network 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Associated with network: +COPS: 0,0,"vodafone UK",2 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Connected, Woo! 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Starting pppd connection 
Jan 17 13:34:31 stuart-laptop NetworkManager: <debug> [1232199271.218293] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user web ttyUSB0 noipdefault usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/2 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Jan 17 13:34:31 stuart-laptop NetworkManager: <debug> [1232199271.219670] nm_ppp_manager_start(): ppp started with pid 9897 
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Jan 17 13:34:31 stuart-laptop pppd[9897]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jan 17 13:34:31 stuart-laptop pppd[9897]: pppd 2.4.4 started by root, uid 0
Jan 17 13:34:31 stuart-laptop pppd[9897]: Using interface ppp0
Jan 17 13:34:31 stuart-laptop pppd[9897]: Connect: ppp0 <--> /dev/ttyUSB0
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6 
Jan 17 13:34:31 stuart-laptop pppd[9897]: CHAP authentication succeeded
Jan 17 13:34:31 stuart-laptop pppd[9897]: CHAP authentication succeeded
Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Jan 17 13:34:35 stuart-laptop pppd[9897]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 17 13:34:35 stuart-laptop pppd[9897]: Cannot determine ethernet address for proxy ARP
Jan 17 13:34:35 stuart-laptop pppd[9897]: local  IP address 10.47.24.155
Jan 17 13:34:35 stuart-laptop pppd[9897]: remote IP address 10.64.64.64
Jan 17 13:34:35 stuart-laptop pppd[9897]: primary   DNS address 10.203.129.68
Jan 17 13:34:35 stuart-laptop pppd[9897]: secondary DNS address 10.203.129.68
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  PPP manager(IP Config Get) reply received. 
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) scheduled... 
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) started... 
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) complete. 
Jan 17 13:34:35 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started... 
Jan 17 13:34:36 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 
Jan 17 13:34:36 stuart-laptop NetworkManager: <info>  Policy set 'Vodafone (contract)' (ppp0) as default for routing and DNS. 
Jan 17 13:34:36 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) successful, device activated. 
Jan 17 13:34:36 stuart-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete. 
Jan 17 13:34:37 stuart-laptop ntpdate[9980]: adjust time server 91.189.94.4 offset -0.004204 sec
```

A short while later I try to navigate to a page on an internet forum that's powered by php & mysql (although I don't see why that should be relevant). After about a minute of just sitting there doing nothing, Firefox brings up the 'what do you want to do with this' error message such as I've attached to this post. I can no longer navigate the web. Syslog adds:

```
Jan 17 13:39:01 stuart-laptop /USR/SBIN/CRON[10186]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
```

I then have to manually disconnect and then reconnect, which is very annoying and is interrupting my work severely at the moment.

---

### Post by cmnorton on 2009-01-17
From what you've posted, you seem to be connecting.

Are you using a wireless USB device?

How old is the hardware?

I'd talk to Vodaphone support to find out what the following lines in your log mean, and if that is normal. Sometimes, you can get a "Cannot/Could not message, and you still have a good connection.

You are connecting over a VPN, and the pppd daemon is what is facilitating that.

Jan 17 13:34:31 stuart-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Jan 17 13:34:35 stuart-laptop pppd[9897]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 17 13:34:35 stuart-laptop pppd[9897]: Cannot determine ethernet address for proxy ARP
Jan 17 13:34:35 stuart-laptop pppd[9897]: local  IP address 10.47.24.155
Jan 17 13:34:35 stuart-laptop pppd[9897]: remote IP address 10.64.64.64
Jan 17 13:34:35 stuart-laptop pppd[9897]: primary   DNS address 10.203.129.68
Jan 17 13:34:35 stuart-laptop pppd[9897]: secondary DNS address 10.203.129.68

---

