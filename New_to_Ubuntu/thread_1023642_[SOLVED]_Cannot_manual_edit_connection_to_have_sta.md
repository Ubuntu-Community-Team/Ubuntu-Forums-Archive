---
title: "[SOLVED] Cannot manual edit connection to have static address"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by wstay on 2008-12-28
I am using ubuntu 8.10 and the manual configuration using the NetworkManager Applet 0.7.0 for network adapter to have static address cannot be edited. Where else can I edit my network adapter to have static address?

---

### Post by shrubs on 2008-12-28
I used the instructions located at [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html) under "More about the Network Manager ... " and it's working fine.

---

### Post by Dedoimedo on 2008-12-28
Well, shrubs beat me to it ... :)
Like he said ...
Dedoimedo

---

### Post by wstay on 2008-12-28
> **shrubs said:**
> I used the instructions located at [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html) under "More about the Network Manager ... " and it's working fine.

Thanks for your advice.
I have 2 more questions:
1) Why is it important to uncheck System Setting?
2) Why after filling in my gateway address 192.168.1.1 and pressing the OK button, the gateway address becomes 0.0.0.0?

---

### Post by Old Jimma on 2009-01-01
Hi Ubuntu Community:

The authors that cite the URL provide methods that did not work for me. The URL contains advice listed in 3 paragraphs after my signature. My experience with this method is that after you reboot, you don't have the static ip you hoped for!

It would be wonderful if someone could add knowledge to this thread.

Thank you!
Phil Smith
Duluth, GA

URL says:

"One of the points raised was the new Network Manager does not allow users to setup their IP address to a static value. While this claim sounds alarming, it is, fortunately, incorrect. It is possible - and quite easily, too - to change the DHCP address to a static IP address. Here's how:

Right-click on the network icon in the top panel, Edit connections. Under Wired, select one of the displayed connections and then click Edit. In the Editing <network interface> windows, click on the IPv4 Settings tab.

Under Method, change from DHCP to Manual. In the Addresses, click Add, then provide the relevant information (IP, netmask, gateway, DNS etc). Finally, most important, untick the System setting option."

---

### Post by superprash2003 on 2009-01-01
you could edit the /etc/network/interfaces file .. this should help [http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://www.prash-babu.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by Dedoimedo on 2009-01-01
Hi guys/gals,

Unfortunately, some users have problems with the Network Manager, it turns out. The method I wrote works, apparently not for everyone.

To make things clearer, I wrote that section specifically to address a point raised by a reader that it was impossible to set a static IP. It is not impossible BUT the change may not be permanent for some users. This is the actual bug, not the ability to set the static IP.

As to the two questions raised:
1) When you uncheck the system setting, this allows you to change all the necessary values for your static connection, including the dns server. This brings us to questions 2.
2) If you print out the routing table for your machine (route), you will see that the default gateway is marked by 0.0.0.0, this means that any IP address asked for and not found the destination in any of the routes before the default one, will be sent through this connection; hence the name, default gateway. In other words, 0.0.0.0 is "equivalent" to the network adapter that connects to the outside world. So the network device that connects to 192.168.1.1, let's call it eth0, will be responsible for routing all IPs (0.0.0.0), unless previously routed.

I hope this helps ...

Dedoimedo

---

### Post by Tiribulus on 2009-01-01
OK folks,
I've tried everything in this thread and I still can't get my wireless connection to work. The subnet mask somehow turns into 24 when I ok the settings.

My wap is on a different subnet from my main network because I couldn't get it to work  as a node on my main network. This has given me no problems as long as I assign static info for the main network. The clients just use the wap for wireless.

It takesthe ip address and ifconfig says it's set and even tells me the mask is correct. Net manager says it's connected, but I cannot even ping my main router address. Suse and all flavors of windows work fine this way. Only Ubuntu 8.10 seems to complain. I don't understand why the mask sets itself back inexplicably to 24, just two four bby itself, but ifconfig calls it 255.255.255.0? I suspect this may have something to do with it.

Any help would be greatly appreciated.
Thanks

---

### Post by Dedoimedo on 2009-01-01
Hello,

The netmask /24 is 255.255.255.0. The /24 is CIDR notation and tells you how many bits of the 32 the IP address has can change. In this case 32 - 23 = 8. Which is the last octet.

2^8 = 256 addresses, hence 255.255.255.0.

Dedoimedo

---

### Post by Tiribulus on 2009-01-01
> **Dedoimedo said:**
> Hello,

The netmask /24 is 255.255.255.0. The /24 is CIDR notation and tells you how many bits of the 32 the IP address has can change. In this case 32 - 23 = 8. Which is the last octet.

2^8 = 256 addresses, hence 255.255.255.0.

Dedoimedo

I didn't even think of that.

I readded the connection and now I can ping internal IP addresses, but no access to the web. No ping and "address not found" in Firefox. I have the exact same settings as my other machines. Any ideas on that?
Thanks again.

---

### Post by Dedoimedo on 2009-01-01
What does it say under /etc/resolv.conf?

```

cat /etc/resolv.conf

```

This file should have 1-3 lines like this:

nameserver xxx.xxx.xxx.xxx

This is the nameserver (DNS) your machine will contact for resolutions of names of websites (like google etc). The IP address should be the same as that you use on other machines, usually either the router IP or something given by the ISP.

Dedoimedo

---

### Post by Tiribulus on 2009-01-01
> **Dedoimedo said:**
> What does it say under /etc/resolv.conf?

```

cat /etc/resolv.conf

```

This file should have 1-3 lines like this:

nameserver xxx.xxx.xxx.xxx

This is the nameserver (DNS) your machine will contact for resolutions of names of websites (like google etc). The IP address should be the same as that you use on other machines, usually either the router IP or something given by the ISP.

Dedoimedo

Thanks for your time BTW.

I was just going to post that my resolv.conf file has only one line that says # Generated by NetworkManager though NM itlef has my dns servers in it and the net info  deal from the context menu list them as well.

EDIT: I can ping internal devices by address only, no hostname, and nothing will ping outside of my gateway. This all pints to DNS, but I'm at a loss as to how to fix it. The resolv.conf is not editable manually and every other thing says the settings are correct.

EDIT 2: I disabled IPv6 with this command   sudo sed -i -e 's/alias net-pf-10 ipv6/#&\nalias net-pf-10 off/' /etc/modprobe.d/aliases   rebooted and no change

---

### Post by Dedoimedo on 2009-01-03
Hello,

Please backup before making any change!!!

```

sudo cp /etc/interfaces /etc/interfaces-backup
sudo cp /etc/resolv.conf /etc/resolv.conf-backup

```

Under the file /etc/interfaces, under the section for the particular network inteface (let's say eth0), add the following directive:

```

peerdns no

```

Restart the computer or restart the network. Now, in the file /etc/resolv.conf, as sudo, add the line:

```

nameserver xxx.xxx.xxx.xxx

```

When xxx should be the IP of your router or the external dns that your ISP provides. The fact you can ping indicates that you have the connection, but you cannot resolve names ...

See if this helps.

Cheers,
Dedoimedo

---

### Post by Tiribulus on 2009-01-06
> **Dedoimedo said:**
> Hello,

Please backup before making any change!!!

```

sudo cp /etc/interfaces /etc/interfaces-backup
sudo cp /etc/resolv.conf /etc/resolv.conf-backup

```

Under the file /etc/interfaces, under the section for the particular network inteface (let's say eth0), add the following directive:

```

peerdns no

```

Restart the computer or restart the network. Now, in the file /etc/resolv.conf, as sudo, add the line:

```

nameserver xxx.xxx.xxx.xxx

```

When xxx should be the IP of your router or the external dns that your ISP provides. The fact you can ping indicates that you have the connection, but you cannot resolve names ...

See if this helps.

Cheers,
Dedoimedo

I really appreciate your help and should have responded sooner, but I got busy with work. Don't ask me what the difference was, but I was able to get my WAP working as a node on my main subnet and after that the wireless connection started working. I have had other Linux machines that worked fine the other way, but for some reason it didn't like the WAP being on a different subnet, or so it appears.

I also don't know why suddenly the D-Link box let me add it as a device on my main network now either. In any case it works now, but I doubt that many people will have this same issues, assuming that was indeed it.
Thanks again

---

### Post by wstay on 2009-01-08
I thought my network connection is solved when I can connect and see my xp network shared files and folders. But that was only short-live. I mean it did not last long. And moreover I can not open any of the shared files that I can see on the network. So, can we safely assume that there is a bug in ubuntu 8.10 networking?

---

### Post by Old Jimma on 2009-01-09
Hi Ubnutu Community Dudes:

I was the guy who started this tread. I like the way it is going, but I still don't have a clue about how to make an ubuntu machine to have a static IP that will stay permanently.

I say that this thread was solved, and I wondered why.:-k

Is it because it is not possible to do this as seems to be suggested?

Thank you!
Phil Smith
Duluth, GAa

---

### Post by wstay on 2009-01-14
> **shrubs said:**
> I used the instructions located at [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html) under "More about the Network Manager ... " and it's working fine.

I used your instruction given here and I can now connect my two computers.
My problem now is why on my ubuntu system I can read the shared file from my xp computer, but when I open the shared file which is a .jpg file, it won't open? 
Also when I use a Desktop Switch to connect my 2 computers, I can see shared files from both the computers. But when I use Router Modem to connect my 2 computers, I can only see the ubuntu shared files from the xp computer but cannot see the xp shared files from the ubuntu computer?

---

### Post by UNHOLYwoo on 2009-01-18
Thanks so much for the info on /etc/resolv.conf. This helped me fix my "no internet" problem on my server after removing network manager and assigning it a static ip via editing /etc/network/interfaces.

I used [http://en.kioskea.net/faq/sujet-979-having-a-static-ip-address-under-ubuntu-8-10]("http://en.kioskea.net/faq/sujet-979-having-a-static-ip-address-under-ubuntu-8-10") as a guide, for anyone else who might have a similar problem.

---

