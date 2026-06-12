---
title: "static IPs and evolution settings"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by hcsvespa7 on 2008-05-04
[SIZE="3"]Hello from hcsvespa7 down here in New Zealand. 

I am now (with Ubuntu 8.04 available and easy as to install) seriously interested in learning lots of it for my future in the world of IT. I can now install updates that do not kill off the system like Ubuntu 7.10 did to me a number of times and I had to reinstall from the beginning each time and lost interest then. I have quite a number of years in the IT trade and know quite a bit without blowing my trumpet too loudly. 

I have a large home windows based network that is my base for my work. I have an email server running all the time and my windows systems work really well overall. I have one vista machine running, but ask myself why did Microsoft do this at all…???

I have a couple of immediate questions with Hardy Heron that I need to resolve in order to carry in with my exploration of this remarkable operating system. 

I have a SMC router with a normal IP range of 192.168.2…..n for the range of machines up to n =254.My subnet mask is 255.255.255.0 and my gateway is 192.168.2.1. My ISP DNS settings are 60.234.1.1 and secondary DNS is 60.234.2.2 That is in the IPv4 system. 

My Hardy Heron computer that I installed the desktop version onto automatically connected itself via my SMC router to the internet just fine, which is truly remarkable.

However I want to set it to have static IP address in line with my SMC router and when I do set this the internet is no longer available. My LAN computers are on the same workgroup name but I don’t as yet see any way that Hardy Heron will allow me to connect it to my windows workgroup. My question then is how can I set a static IP address and still connect the internet like it did automatically when first installed. 

I have been exploring Evolution email and I cannot find any place where I can insert my login name my password and the equivalent of the windows pop3 and smtp servers for Evolution to drag email off my local LAN email server. How can I access the settings page is my simple question. It may be tied up with accessing my local windows Lan. 

I also have a networked Kyocera printer that is one of the best one can use by the way in my opinion. I manage to get Hardy Heron to access this printer and use it as the default printer no problems with a bit of fiddling around. So the network must be working for that to happen. 

I also see that Ubuntu is maybe using IPv6, which I know is coming to our industry sooner than later.

I feel like a child learning something really new but exciting at the same time. 

Kind regards hcsvespa7   [/SIZE]

---

### Post by Iowan on 2008-05-04
Did you manually set the gateway address?  Perhaps posting your **/etc/network/interfaces** file and results of **ifconfig** would be helpful.

---

### Post by hcsvespa7 on 2008-05-07
Hello again folks. 
I feel a total dummy on this one. 
I need to type in a command and I cannot find anywhere in Hardy Heron where I can do so. An example is 

sudo apt -set install gparted 

Kind regards and your patience with me in advance. 

One more thing. I have a windows XP email server running Mdaemon post office software. It works a treat, but the Evolution Linux programme will not pull email from the server via the pop3 and smptp server names like Windows machines do...??? 

Thanks muchly if you can take a moment or two to put me on the right path. Cheers Henry.

---

### Post by Iowan on 2008-05-07
In Gutsy, a Terminal is available under Applications>Accessories. You can also use CTRL-ALT-F1 (through CTRL-ALT-F6) to get a command line.  To return to the Desktop, use CTRL-ALT-F7.

---

