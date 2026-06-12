---
title: "Ping or Firefox before any other network activity, why is that?"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by codeandeffect on 2008-01-06
Hello all,

I have an interesting network problem - At University I can connect wired or wifi, authenticated or otherwise, and have full network access from any app - synaptic, etc.

Here at home, basic (D-Link ADSL router wired connection), and Gutsy behaves strangely: 

[LIST]
[*]I can access anything using Firefox and Evolution
[*]If I want to install something via Synaptic, it always fails when trying to get the online resource, same with ssh'ing to my server.
[*]For synaptic, I cancel the download, copy the location of the .deb, and open the url in firefox. Then cancel the download, go back to synaptic and run it again, it then works (for all dependencies too).
[*]For SSH, I normally have to to ping the server, then all will run fine.
[/LIST]

Tonight I had the same trouble as usual, but also,  I tried to use MSN thru Pidgin and nothing was allowing me to connect - I think this is because when I enter their server's into ping/firefox they don't responded like normal web urls - a security feature for the messenger service no-doubt.

I read some threads and checked that I have no proxies set up, and indeed no specialist setup. In summary, it appears only Firefox and the system has the right to access a network resource initially. Once done (if successful) then all applications can access that resource.

I cannot see what else to check (my $http_proxy value returns blank). I have no such problems with other OS's (Mac OSX, Win XP). 

I'd be grateful to hear of workarounds, or descriptions of things I could try out next.

---

### Post by codeandeffect on 2008-01-07
*bump*

I should also point out I log on as the one user I created at first install. My router allocates via DHCP, and has the mac address listed in a control list of allowed clients. Hope this helps.

---

### Post by yoghurt on 2008-01-07
I used to have similar problem in the past with my ADSL connection (and dynamic IP address). I could browse the Internet, but whenever I tried something like 
```

sudo apt-get update

```

It couldn't connect to any repositories. Then I noticed that it was using the IP addres 1.0.0.0 - which is of course incorrect. What helped me in my case was entering my ISP DNS server IP address into the Network Manager.
Problem was that each time my ADSL modem got new IP address from my ISP, this value was rewritten to the default 192.168.1.1.
I had to manually rewrite the DNS record each time I wanted to install something. I later found a script somewhere on these forums I believe that actually replaced the file with DNS records (sorry - leaking memory).
Hope this helps.

---

### Post by codeandeffect on 2008-01-08
Cheers, that worked a treat. I added their DNS, and at first it had no effect. When I removed the 192.* I had then it all worked fine. I'll try to find the script that you mentioned to make this a permanent feature and post a link in this thread.

Many thanks for your assistance.

A.

---

### Post by yoghurt on 2008-01-09
No problem mate :) I tried looking for that script myself. But I found the thread from last year:

```
http://ubuntuforums.org/showthread.php?t=206692&page=2
```.

That file you can edit directly is /etc/resolv.conf so 

```
sudo gedit /etc/resolv.conf
``` should do the trick. Too bad it gets overwritten, but it's perhaps possible to lock the file?

---

