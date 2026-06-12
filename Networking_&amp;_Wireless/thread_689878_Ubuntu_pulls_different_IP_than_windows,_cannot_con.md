---
title: "Ubuntu pulls different IP than windows, cannot connect"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by maxxum on 2008-02-06
I am facing a very strange issue with my internet connectivity. Last night I suddenly got disconnected from the internet while using Ubuntu. I connected through a router to the cable modem. My laptop (running XP at the time) also got disconnected (it was using wireless). I have been using Ubuntu like this for a year now. I reset the cable modem, the router and everything. When nothing worked, I removed the router and connected directly. Ubuntu is able to get an IP address which is a valid IP (roaming mode on in network manager). But I cannot get to any webpage. I booted into XP on the desktop and I am able to get on to the internet. The only strange fact is that Ubuntu is pulling a slightly different IP from the ISP than windows is. The last three digits are different, Ubuntu is getting 165 while windows is getting 230. 

I talked to my ISP and they said the IPs should be the same. The dynamic IPs remain same for up to a certain period of time and should not change with OS. Everything else seems normal, Ubuntu displays the gateway, DNS etc information correctly and has the same hardware address as the windows has. I have an onboard Intel PRO1000 network controller. If I connect through the router, I cannot get to the internet either in Ubuntu or on XP even though the ISP says that the router is also pulling the 230 IP similar to XP. 
Are there any settings in Ubuntu that I can play with? is the ISP server seeing my machine differently when I am booting Ubuntu than it does when I am on XP?
I'm totally stumped!:confused:

---

### Post by Jaiinus on 2008-02-07
Since you're posting I'm going to assume you somehow have internet connectivity (unprotected wireless lan's rock!). I'd recommend getting wireshark which is a packet capturing utility and it will let you see exactly what's transposing between your computer and the rest of the world. What I'm going to suggest will help you get information and you don't' necessarily have to use wireshark while performing the commands but it would definitely be helpful. 


You said you are getting an IP address from your ISP, so that means you have some connectivity. Issue the route command (vanilla on ubuntu and route print on XP) and see what router you're pointing at, and issue a tracert to that IP. Traceroute will show you exactly what steps you're taking to the router. This should work. Next do a nslookup google.com which should give you a IP. If that command fails then you're problem is that you can't resolve names. Find a working dns server and set it (/etc/resolv.conf or under tcp/ip -> properties).

---

### Post by joebeasley on 2008-02-07
You are getting different ip addresses because the mac address on each card is different.  You could "clone" the ip of the machine that works on your router if that option is available.

---

### Post by roachk71 on 2008-02-07
Another DNS option is OpenDNS. This service is fast, and even helps protect your computers and users against phishing sites, etc. The addresses are:

208.67.222.222 and
208.67.220.220

Maybe this info can help you out a bit... :)

By the way, this service is also free.

---

### Post by maxxum on 2008-02-07
Probably I was not clear enough in the first post.

1) I have connectivity to the internet when I boot into XP as long as I don't use my router. Lets put the router aside for the moment and just talk about direct connectivity to the cable modem.

2) I have verified the MAC id is the same in XP and Ubuntu. When I was connecting through the router, I did clone the mac id otherwise the belkin router setup page would show 'not connected'. It shows 'connected' after cloning but internet does not work, even with XP. So router is set aside for now.

3) Jaiinus, I will boot back into Gutsy now and try what you said and report back soon.

4) roachk71, if I am to use those DNS servers in Ubuntu, I need to specify a static IP in the network manager and those DNS, right? I am not sure if my ISP will let me specify a static IP but I will try this solution.

be back soon guys! thanks for the help so far!

---

### Post by patryk77 on 2008-02-07
add the lines:

nameserver 208.67.222.222
nameserver 208.67.220.220

if you just wanna use the other DNS servers... no need to set a static IP

Also, while the internet works, try to ping [www.yahoo.com](www.yahoo.com), and write down the IP address

Then also retry it while the internet is not working, and see if you can ping it by the IP address

```
$ ping www.yahoo.com
$ ping 69.147.114.210
```

---

### Post by roachk71 on 2008-02-07
Patryk77, I've tried entering the nameservers both in the Network Management dialog and into /etc/resolv.conf. Still, the DNS servers revert to the servers used by my ISP after reboot. Do you know of a way to make it more permanent?

I ask this because I'd like to reduce the DNS load on my ISP's servers to let other users benefit from it.

---

### Post by maxxum on 2008-02-07
Came back after trying on Ubuntu. 
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.4     *               255.255.255.255 UH    0      0        0 tap0
172.16.52.0     *               255.255.255.0   U     0      0        0 vmnet1
192.168.2.0     *               255.255.255.0   U     0      0        0 tap0
172.16.112.0    *               255.255.255.0   U     0      0        0 vmnet8
24.38.244.0     *               255.255.254.0   U     0      0        0 br0
24.38.244.0     *               255.255.254.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0

```
I figured the one to try would be eth0, so I tried to tracert to it.
```

tracert 24.38.244.0
Result: The program 'tracert' is currently not installed.  You can install it by typing:
sudo apt-get install traceroute
bash: tracert: command not found

```
Since I have no connectivity, I cannot install traceroute. :mad:
Then I tried nslookup
```

nslookup google.com
;; connection timed out; no servers could be reached

nslookup www.google.com
;; connection timed out; no servers could be reached

```

patryk77, I did try to add the nameserver in that file. It seems that the two DNS servers were added to the list in network manager but I could not get connection.
When in windows, I did ping [www.yahoo.com](www.yahoo.com) in the command prompt and it replied from 69.147.114.210 four times. I am almost certain it will not work in ubuntu since the google.com thing didn't work. 
I have tried connecting unsuccessfully from two different installations of ubuntu gutsy in two different hard drives. This means there is no problem with my ubuntu installation.

---

### Post by mozetti on 2008-02-07
> **roachk71 said:**
> I ask this because I'd like to reduce the DNS load on my ISP's servers to let other users benefit from it.

It's a nice thought, but it won't matter. Those servers are robust enough to handle everything, I'm sure.

**maxxum** The reason for pinging Yahoo from Windows and getting the IP address is so we can diagnose where your problem is. When you ping yahoo.com, you still need to hit a nameserver to get the IP. Now that you have the IP, you don't need a nameserver to help you fine the site. 

Ping 69.147.114.210 -- if you get a response, then we know the problem lies with DNS. If you don't get a reply, then we know you're not getting out to the internet.

---

### Post by maxxum on 2008-02-07
I went into ubuntu and tried the ping.
$ ping 69.147.114.210
connect: Network is unreachable

$ping [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)

So apparently I am not getting out into the internet with the IP I am getting in ubuntu (xx.xx.xxx.165).

---

### Post by mozetti on 2008-02-07
Are you using network-manager to handle your networking? If so, what are the different network interfaces that are in your routing table.

For example, eth0 is your NIC, vmnet1 & vmnet8 are probably for virtual machines, and br0 is probably the bridge between your NIC & your vmnet* interfaces. But, what is the tap0 device?

---

### Post by maxxum on 2008-02-07
tap0 is something I must have created while following a howto on creating Samba networking with the XP virtual machine I have inside Ubuntu. I did not make any changes to the networking before I suddenly got disconnected last night. So I wouldn't assume it would be a problem. If it is a suspect, could you tell me how to get rid of it? sorry, I am not very knowledgeable on this.

---

### Post by maxxum on 2008-02-07
Update: I got another router and I still cannot connect through that (even after cloning the mac address). The cable modem will not give connectivity to anything that is not a physical computer running windows, it seems. I am only online when I connect the  PC directly to the modem and boot into windows. I know it is not an issue with Ubuntu but is has me and my cable company baffled. Tomorrow I am going to go to them and get another cable modem. Will update after that.

---

### Post by Jaiinus on 2008-02-08
Ubuntu doesn't have traceroute installed by default, and it's not in the default package list either. I've been trying to find a source for it but no luck so far. What Ubuntu does come with is tracepath which is puported to perform the same basic functions. You can try that. Hopefully you are at least getting to the router (otherwise you're getting phantom DHCP packets).

---

