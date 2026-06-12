---
title: "Understanding iptables, firestarter etc etc"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by elpuerco on 2006-09-18
OK when it comes to these I know jack and am trying to learn.

I have looked at iptables.....:confused: 

I have looked as firestarter.....:confused: 

Is there an idiots guide to understanding these and how to configure them?

For example 

blocking or enabling ip addresses?  How does one know what are allowed and disallowed before even going to said ip addresses in the first place?  

How do you know what ports to enable disable?

thnx

---

### Post by tagra123 on 2006-09-18
Trail and error is usually what ends up working.

Firestarter edits the iptables and even when the firestarter GUI isn't running the iptables are.

Others may disagree but for a home network.

Allow lan connections (Your numbers here may be different)

192.168.1.0\24   (Allows all LAN connections)

192.168.1.10     (Allows connection from only 192.168.1.10)


Some common ports to allow:

443  (Microsoft-ds) I needed this one for VMWare to work properly
631   (CUPS)
67    (DHCP)
111 2049 (NFS)  File sharing
137-139 (SAMBA) File sharing

When using firestarter if a port is blocked it should be listed in the events. To allow a block connection right click on the event in the event tab.

---

### Post by tbonius on 2006-09-18
[http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables](http://www.section6.net/wiki/index.php/Setting_up_a_Firewall_NAT_using_IPTables)

:-)

T

---

### Post by elpuerco on 2006-09-18
Thanks for the advice and the URL, some good reading for me there =D>

---

### Post by elpuerco on 2006-09-19
Tbonius, thanks for the link which I have duly read.

However it still leaves me virtually in the dark as I dont understand what it all means?

Also at the end you state it is not the most secure and needs further filtering?

Like I say I know jack about this sort of this thing but want to learn and to ensure I am secure.

I did a hacker test on my Kubuntu box last night from some website which reported all my ports are secure and invisble to the outside world.

Can I assume therefore that I really need not be worrying about configuring a firwall?

Thnx

---

### Post by tbonius on 2006-09-19
Not quite that simple.. I am not sure what you do and do not understand therefore I do not know whwere to begin in helping you.  Try using a small utility called "nmap" to scan the the external IP of your firewall in order to see what ports are open.  Make sure you do this from a computer outside of your network.

Read lots of books about IP and IP based firewalls.  Thats about my only advice.

T

---

### Post by elpuerco on 2006-09-21
HI,

OK at home I have a Netgear ADSL modem/router.

I undertsand that this connects to the outside world and internally I connect to the router via wireless.

So are you saying I should use nmap against the ip address which my PSP has assigned to my modem/router to see how secure that is?

If so do you know of a Windoze tester as as yet I am unable to get internet access from my Linux setup when connected at work, something to do with proxies or whatever but so far no luck.

Therefore I would have to run the test fom Windows XP at work 

Thnx for any help....;)

---

### Post by elpuerco on 2006-09-21
I have spent most of tonight reading the FireStarter documentation which I had to go to manually as for some reason the link from within FireStarter does not work.

Rather sad I had not realised to do this before:rolleyes: 

The guide makes for a good read and I am starting to understand more about the program :D 

Anyway, I cannot stay here all night, erm all morning chatting for there is reading to be done.....;) 

l8r

---

### Post by elpuerco on 2006-09-21
Still here, match sticks holding my eyelids up!!!

One thing whilst reading about FireStarter that was puzzling me was how to identify ports.

The help for me can from Shields UP! web site as recognized by the FireStarter home page.

This web site not only confirm again that my PC is secure but also provides this nifty tool to check out what the given port number does :D 

[https://www.grc.com/PortDataHelp.htm](https://www.grc.com/PortDataHelp.htm)

---

