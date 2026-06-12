---
title: "Connecting to the internet at work"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by eorteg01 on 2008-02-15
My job requires me to use both Linux and XP on the same computer, however I am having an odd issue connecting to the internet.

We are behind a XP domain, and after entering seemingly all of the information into Ubuntu 7.04 I am able to access the intranet and get to all of the servers and shared folders, but I cannot access the internet.

This is pain since I have to continuously switch between Ubuntu and XP to check things on the internet. Any and all help would be greatly appreciated.

I am unsure what information to provide other than I am working behind some sort of XP domain (company.internal) and my XP login has me connect to one specific server (corporate). I have Ubuntu 7.04 installed and DHCP turned on. Through DHCP my Ubuntu automatically found seemingly all of my settings and allowed me to access the corporate shared folders right out of the box.

Again, thanks for advance for any help anyone can offer.

---

### Post by freebeer on 2008-02-15
Check your network card configuration (in Ubuntu) and see if it has been supplied with a gateway address.  If not, it will need one.  If it has one (and it's correct), then I suspect you're being firewalled somehow - possibly through the router.

---

### Post by eorteg01 on 2008-02-15
I went to "network tools" and the netstat returned this:

**Destination **--               Gateway --                 **Netmask**
**10.148.6.0**                0.0.0.0                  ** 255.255.255.0**
**169.254.0.0**              0.0.0.0                   **255.255.0.0**
**0.0.0.0**                    10.148.6.1               **0.0.0.0**

According to XP my IP address is 10.148.6.69 and the default gateway is 10.148.6.1. I can't find the 169.254.0.0 number anywhere in XP. Also, sorry for the ugly formatting.

Thanks for taking the time to respond.

---

### Post by tekguy on 2008-02-15
Usually a 169.xxx.xxx.xxx ip address indicates that the interface did not grab an IP from DHCP. Can you do an ifconfig from command line and paste the results?

Does your XP install use a proxy to connect?

---

### Post by eorteg01 on 2008-02-15
It turns out we are on a proxy server. I completely forgot to check. I entered the server name and port# into Ubuntu but that still didn't do the trick. Here if the ifconfig taken right after I entered the proxy information:

efrain@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:A2:E5:37  
          inet addr:10.148.6.69  Bcast:10.148.6.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fea2:e537/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71802 (70.1 KiB)  TX bytes:66615 (65.0 KiB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:776 (776.0 b)  TX bytes:776 (776.0 b)

Again, thanks for the help.

---

### Post by tekguy on 2008-02-15
Try this at a command line:

```
export http_proxy=http://username:password@proxyport
```

Let me know if you can get out after doing that.

---

### Post by eorteg01 on 2008-02-15
No luck running your command. Any other ideas?

---

### Post by tekguy on 2008-02-15
Sure. You might need to authenticate via domain. So you could try:

```


export http_proxy="user@domain:password@proxyport"
or
export http_proxy="domain\\user:password@proxyport"


```

Could you also try to go into Synaptic Package Manager
Go to Settings, then Preferences, and Network. 
Add your proxy settings

Try to see if Synaptic will connect. If it does, then we have to figure out why your browser won't connect.

---

### Post by eorteg01 on 2008-02-15
Neither command worked for me, and after entering my proxy settings into Synaptic it was unable to download any packages. The error said that I could not access my proxy server.

Now for some dumb questions just to make sure that I'm doing things correctly. In xp I see my proxy server address as *AB-CDE-EF01l* and my port as 80. My domain as listed by xp is companyx.internal, so the last bit of code should have looked like: 

```
export http_proxy="companyx.internal\\user:pass@80"
```

I just want to make sure I'm not missing something obvious. This is my last post of the day, I'm taking off for the weekend, but I thank you very much for your help. Any suggestions you leave I will definitely try on Tuesday when I get back. 

Again, many thanks.

---

### Post by tekguy on 2008-02-15
Try

```

export http_proxy="companyx.internal\\user:pass@AB-CDE-EF01:80"

```

---

### Post by The Cog on 2008-02-15
As far as I know, you need to put the proxy info straight into firefox: 
Edit->Preferences,
Advanced icon,
Network tab,
Connection Settings button

---

### Post by eorteg01 on 2008-02-19
A combination of entering the proxy info directly into Firefox and using the export commands has worked for me, and Firefox can now access the internet. 

Although apt-get is still not getting through the firewall, but I think I can find enough info on that by digging through the forums.

Thanks so much for all of the help guys.

---

### Post by tekguy on 2008-02-19
No problem.

---

