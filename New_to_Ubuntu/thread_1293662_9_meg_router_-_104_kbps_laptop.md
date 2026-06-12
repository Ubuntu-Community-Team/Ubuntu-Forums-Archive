---
title: "9 meg router - 104 kbps laptop"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2009-10-17
Hi All,
I have a Dell Inspiron pre-loaded with Ubuntu and a Linksys AM200 router as recommended by someone on this forum. My connection was never very fast, but has got slower and slower over a couple of years. Now, as part of a 2 month broadband problem with Virgin I have finally discovered that the router is registering over 9 megs, but my computer struggles to get 104 kbps. I also have a Vaio dual booting with XP and Ubuntu and the speed is the same. To confuse things (for me at least) I am using my upstairs neighbour's wireless broadband and am getting over 6 megs, according to an online speed test. 
The question is: does the router download speed of over 9 megs mean that it is receiving 9 megs and somewhere between it and my computer I am losing most of it or is the 9 megs some sort of potential, but the router isn't really getting it, so nor am I? Can I assume that the speed I am getting on me neighbours wireless means that there is nothing fundamentally wrong with my browser settings, certainly not enough of a problem to explain the massive differences in speeds?
Thanks for any help.

---

### Post by pbrane on 2009-10-17
When you say that your router is "registering over 9 megs" do you mean it is trained up at over 9M or that the actual through-put is over 9M? Typically when an ADSL router is trained up at a certain speed that IS your bandwidth. And the down stream speed is faster that the up stream speed. (Asymetrical DSL). So to answer your question, if the ADSL modem is trained up at over 9M then that is your actual bits per second. But if your throughput is only about 100K then it sounds like you LAN has a problem. I assume this because both your computers do the same thing. Is your AM200 the only device in your network? If you also have a switch or router the trouble may be there. I have 6M DSL here and I get about 5.9 to 6.2 megs throughput to various speedtest sites. Even over wireless (802.11g - 54M).

The other thing is to look at the "actual" downstream speed in the router status page and make sure it is 9M or so. Your SNR margins should be greater than 6 db too. And really should be better, like 12 or higher.

If you are using the AM200 router for VoIP too then this could be your problem, VoIP sets the TOS byte to 255, meaning it's packets go first, then data. VoIP is a type of real-time protocol and can severly impact your LAN. Maybe this is just a provisioning issue.

---

### Post by LewRockwell on 2009-10-17
issues of data transfer rates differ widely

our broadband transfer rates routinely vary as much as 2 megs during normal daytime hours

perhaps you could compare local ping timing between your various pieces of equipment for a better understanding of the performance of your local devices

there are also various websites available when you can go to test your specific upload and download rates

here is a piece of random commentary on interweb speed:

[http://torrentfreak.com/optimize-your-bittorrent-download-speed/](http://torrentfreak.com/optimize-your-bittorrent-download-speed/)

as always, your mileage will vary...

.

---

### Post by Dermot Doyle on 2009-10-17
Hi, I was probably a bit vague and I'll try to answer your points:
PBRANE
1 I'm really not very computerate, but when I get into my router settings, under DSL it says downstream rate 9427, upstream rate 1020. I don't know what 'trained' or 'throughput' means so I can't say which it is.
2 I thought LAN was something to do with wireless internet, I don't think I have a problem with that or have I missed something.
3 I just have my laptop connected to the router and that's it.
4 Under the DSL settings I have downstream margin 12db, upstream margin 2db. Is that what you were talking about?
5 I'm afraid I don't know what VoIP means.
LEWROCKWELL
How do I check the ping timing between the laptop and the router?
The download speed of 104kbps came from various attempts on various websites. Though I understand these can be far from accurate at times they consistantly show roughly the same slow speeds.
Thanks for the help so far. Any more thoughts or clarifications would be welcome.

---

### Post by pbrane on 2009-10-17
your actual trained speeds are as you said 9M down and 1M up. If you only get 104K at your computer then the issue is between the AM200 router and your computer. But this could still be a configuration issue. VoIP is Voice over IP and I thought the AM200 has a VoIP setup but I may be mistaken. 

To check ping times to your router you need to know the IP address of the router. It defaults to 192.168.1.1 so if you haven't changed it that should work. 

from a terminal in Ubunutu (Applications -> Accessories -> Terminal) type:
**ping 192.168.1.1**

you should see some short pings times. for instance...

[I]$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.36 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=6.18 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.21 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.32 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=1.29 ms
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 1.292/2.477/6.184/1.885 ms[/I]

my average ping to my router is 2.477 milliseconds. Yours should be in that range too.
You can also ping a site like yahoo.com to compare times. I get about 50ms to yahoo from here.

one other thing to try to narrow down your bottleneck is to run the command
**mtr 192.168.1.1** in a terminal. YOu will most likely have to install mtr. this will trace the route to each network device and display ping times continuously. mrt is available in the Synaptic Package Manager. You really should only have one network hop from your laptop to the router and this may not be much help, but may show something you're not aware of.

In case you don't already have it:
[http://www.linksysbycisco.com/UK/en/products/AM200]("http://www.linksysbycisco.com/UK/en/products/AM200")

this is a link to the router page that has the user guide on it.

Not sure where you are located but have you tried calling your DSL helpdesk? They should be able to help you out.

---

### Post by Dermot Doyle on 2009-10-17
Hi, thanks for the reply.
Did a ping test as you explained and got speeds of around 0.330 ms - I don't know how many you need to let it do before you get an average, I stopped at 100 - but from what I could see the average was something a little lower than that. The router is currently offline which is the ongoing problem I'm having with Virgin, but I assume I was only checking the link between the computer and the router. Not knowing exctly what I'm checking, does the ping demonstrate the speed of the connection between the computer and the router? If so, mine seems faster than yours or again, have I missed something?

---

### Post by Paqman on 2009-10-17
EDIT: Nevermind, must learn to read posts better...

---

### Post by pbrane on 2009-10-17
Yes, by pinging the router (192.168.1.1) you just tested your link between the router and your computer. My ping times may be more because I am running wireless to my router. It would seem that the throughput problem is in the router itself. By throughput I mean the actual rate of flow of the data through the entire network and computer. Being connected at 9Megs does not ensure a constant 9Megs of data from a server to your computer. Many things affect this. But you should be getting much better than 104K. That's for sure. If Virgin is sure their network is not causing problems and that your modem is operating okay then you may need to look at the user guide and make sure the configuration is correct. Maybe Virgin can help.

---

### Post by Dermot Doyle on 2009-10-17
I don't believe for a second there isn't a problem with Virgin's network and I find them as much use a a chocolate fireguard, but thanks for the help. I'll look further into the router settings or maybe try another make.
Cheers

---

