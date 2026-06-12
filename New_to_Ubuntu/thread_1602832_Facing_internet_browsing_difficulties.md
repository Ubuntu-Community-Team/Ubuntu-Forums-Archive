---
title: "Facing internet browsing difficulties"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Rushyang on 2010-10-21
Hey guys,

I am on ubuntu 10.10 (Normal Installation). From last 2 days, I'm facing problem that I just can't open YouTube, Wooledge, github sites. They are the top sites, obviously there's no way their server are down. 

When I open them, My page just keep loading but nothing shows.. I deleted all of my FF cookies. But no luck. I can instantly browse into other sites, there is no problem with my internet connectivity. Please Advise. 


Regards

---

### Post by JustinR on 2010-10-21
Hi,

Can you go to **Applications > Accessories > Terminal**
and type this:
```

sudo apt-get install flashplugin-installer

```

---

### Post by Rushyang on 2010-10-22
> **JustinR said:**
> Hi,

Can you go to **Applications > Accessories > Terminal**
and type this:
```

sudo apt-get install flashplugin-installer

```


It's already installed.. I followed some after installing 10.10 essentials.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
flashplugin-installer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


---

### Post by wojox on 2010-10-22
Try this [Preferences Tweaks]("http://firefox-tutorials.blogspot.com/2010/05/preferences-tweaks.html").
Scroll down to disabling ipv6.

---

### Post by Rushyang on 2010-10-22
I'm stuck! Am I the first one to face this?

---

### Post by Paqman on 2010-10-22
Are other machines on the same network having the same problems? Do other sites load ok? Do you just use the standard DNS provided by your ISP?

---

### Post by TeoBigusGeekus on 2010-10-22
Also, have you tried with another browser?

---

### Post by MattBD on 2010-10-22
If you disable IPv6 in FF, does that solve the issue? You can do this by entering about:config in the address bar, clicking through the warning, entering IPv6 in the Filter bar, and where it lists network.dns.disableIPv6, right-click it and toggle the value from false to true.

If that is the problem, you may be able to fix it more permanently by upgrading your router's firmware to the latest version or using an alternative DNS provider. Google's public DNS (8.8.8.8 and 8.8.4.4) is good, as is OpenDNS (208.67.222.222 and 208.67.220.220).

I've had a similar problem in the past and I found upgrading my router's firmware was the only permanent fix.

---

### Post by Rushyang on 2010-10-24
When I'm in my another operating system - Windows 7 x64 Ultimate, I can easily browse all sites. So I doubt there is no problem with my router's firmware.

Yes, I have tried different browser (Chrome) and I'm pretty sure there is some problem regarding "Maverick Meerkat"..

I can remember now, when I installed full updates in my ubuntu.. after that Im' facing problems.

Yes, I'd already disabled IPv6 through my FF. Enabling it also doesn't work. So far, I have found no solution to over come this problem......

---

### Post by MattBD on 2010-10-24
> **Rushyang said:**
> When I'm in my another operating system - Windows 7 x64 Ultimate, I can easily browse all sites. So I doubt there is no problem with my router's firmware.

That doesn't necessarily mean that it won't fix the issue. I had a similar issue in Edgy and Feisty, while at the same time Windows XP was unaffected. It was resolved by upgrading the router's firmware. Don't forget, router manufacturers are probably less likely to care if their products don't play nice with Linux.

You might want to read [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) which explains the issue in more detail. It sounds like your issue could be something like that.

Also, can anything else access the internet? For instance, can you ping Google, or install software via apt-get or Synaptic?

---

### Post by Rushyang on 2010-10-29
> **MattBD said:**
> That doesn't necessarily mean that it won't fix the issue. I had a similar issue in Edgy and Feisty, while at the same time Windows XP was unaffected. It was resolved by upgrading the router's firmware. Don't forget, router manufacturers are probably less likely to care if their products don't play nice with Linux.

You might want to read [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) which explains the issue in more detail. It sounds like your issue could be something like that.

Also, can anything else access the internet? For instance, can you ping Google, or install software via apt-get or Synaptic?

Sorry for late reply, I've almost given up for this matter.

Yes, I can browse ubuntuforums without any hassle through the same operating system. Thanks for the above link, but I'd already disabled IPv6. My terminal can ping to all sites... 

Here is my traceroute of youtube..
> 
                             rushyang@Maverick_Meerkat: ~ $ traceroute [www.youtube.com]("http://www.youtube.com/")
traceroute to [www.youtube.com]("http://www.youtube.com/") (209.85.231.91), 30 hops max, 60 byte packets
 1  117.198.192.1 (117.198.192.1)  37.575 ms  41.530 ms  43.505 ms
 2  218.248.169.230 (218.248.169.230)  47.486 ms  49.462 ms  51.438 ms
 3  115.113.128.17.static-mumbai.vsnl.net.in (115.113.128.17)  61.415 ms  63.402 ms  67.372 ms
 4  59.163.25.242.static.vsnl.net.in (59.163.25.242)  69.352 ms  69.333 ms  71.380 ms
 5  121.240.0.10.static-Mumbai.vsnl.net.in (121.240.0.10)  77.279 ms  79.262 ms  81.237 ms
 6  216.239.43.214 (216.239.43.214)  83.215 ms  43.363 ms  57.580 ms
 7  72.14.232.100 (72.14.232.100)  79.544 ms  81.615 ms  85.496 ms
 8  72.14.238.90 (72.14.238.90)  89.476 ms  89.458 ms  103.426 ms
 9  maa03s01-in-f91.1e100.net (209.85.231.91)  107.404 ms  111.389 ms  111.359 ms                      
One more thing I would like to draw concern to..
**I was able to browse all sites before some days through same operating system (ubuntu 10.10), & under Same router. & now, I am not able to open some of them like I listed above. **

List of Sites which are not opening, are getting bigger and bigger day by day...

---

### Post by primaxx on 2010-10-29
Could your /etc/hosts file be messed up somehow?

I am by no means an expert, but what does your hosts-file look like?

```
gksudo gedit /etc/hosts
```

---

### Post by Rushyang on 2010-10-29
> **primaxx said:**
> Could your /etc/hosts file be messed up somehow?

I am by no means an expert, but what does your hosts-file look like?

```
gksudo gedit /etc/hosts
```

Wooa!! Did you mean changing the hostname can trouble me for the internet? 
Because I changed my hostname and yes! May be after that I faced problems..

I will be back after restoring old hostname and reply soon.

---

### Post by Rushyang on 2010-10-29
Nopes, Still sites are not opening..

Here is my /etc/hosts

> 117.198.201.243    rushyang-MS-7519    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    rushyang-MS-7519    localhost6.localdomain6    localhost6
127.0.1.1    rushyang-MS-7519

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Verbeck on 2010-10-29
could you open the sites from a live cd?

---

### Post by Perseverance on 2010-10-29
If your look up at other pages is slow too it must be DNS issue. Try changing it. I found my best here [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/).

---

### Post by tajiknomi on 2010-10-29
[SIZE=2]*I thing *[/SIZE]**IPV6** [SIZE=2]sittings are enabled...check it out...and if you find it as enable..just select ignore option and try again...[/SIZE]

---

