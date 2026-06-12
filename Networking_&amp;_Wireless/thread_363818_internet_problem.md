---
title: "internet problem"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by esacre on 2007-02-17
Hello everybody,

I'm pretty new to ubuntu and I'm now facing a problem I cannot resolve.

I hava a pc under windows connecting perfectly with an adsl router dlink dsl-g604t.
I decide to install ubuntu to go for linux and avoid using windows anymore.

I install ubunto 6.10 2 days ago, everything goes fine behalve a connection problem to internet : unable to surf. I can ping my router, dhcp is enabled on both side, the router is connected to my isp, my pc gets a ip adress...so everything seems to be correctly working.

My first action was to replaced the dns server defined for eth0 192.168.1.1 (my router adress) by the 2 dns provided from my isp. After that I can surf but a little bit later no more surf. IO go back to the network properties and the 2 dns servers are replace by 192.168.1.1. OK It seems normal because I have dhcp enabled and my router sends back the dns adress

I was presuming a problem with my router which cannot correctly do the dns relay to the outside. My firmware was old so I flashed the router with the latest firmware I had found.
The problem is still the same.

I reboot, go back to windows -> It's working -> reboot -> ubuntu

I search a little bit on the net and I found cases with firefox problem and ipv6. So I disable ipv6 in firefox ([http://about:config](http://about:config) -> ipv6 disabled). OK It is working ;-)

After that I try to launch automatic update and I get a connection problem -> search on the net -> I disable ipv6 on the whole machine
I modify /etc/modprobe.d/aliases in such a way
alias net-pf-10 off
alias net_pf-10 ipv6 off
alias ipv6 off

I reboot the box but it's still not working.

So now:
1.dhcp enabled
2.dns server is 192.168.1.1
3.ipv6 disabled in firefox and on the whole box

And 
1.I can surf
2.I'm not able to update

If I put back the dns server from my isp in place of 192.168.1.1, the update works.

So now I don't have any idea of how to solve the problem.

Some tips ?

Thank you in advance

---

### Post by solar george on 2007-02-17
In the network manager disable DHCP and give yourself a static ip setup.
You will need to choose an ip that is in the same range as the router:
e.g.  192.168.1.123
set the gateway address to 192.168.1.1
set the netmask to 255.255.255.0

Then update the DNS addresses to the ones given to you by your isp.

Hope this works.

---

### Post by esacre on 2007-02-17
Thank you for the answer. 
But I know it's working because when I put the 2 dns in place of 192.168.1.1 it is working, then after the dhcp overwrites the config.

Actually I already use you proposition as a workaround but what if I want to keep dhcp on my box ?
Is there any solutions ?
What is the root cause of the problem ? software bug ? If it's the case it can be transferred to development team or support guys.

---

### Post by Floppyjoe on 2007-02-17
> **esacre said:**
> Thank you for the answer. 
But I know it's working because when I put the 2 dns in place of 192.168.1.1 it is working, then after the dhcp overwrites the config.

Actually I already use you proposition as a workaround but what if I want to keep dhcp on my box ?
Is there any solutions ?
What is the root cause of the problem ? software bug ? If it's the case it can be transferred to development team or support guys.
This may help you with your dhcp problem:
> Using OpenDNS with DHCP

If you assign your computer's IP with DHCP, it probably overwrites your /etc/resolv.conf. Here's how to fix that:

   1.

      Run: sudo gedit /etc/dhcp3/dhclient.conf
   2.

      Change the prepend line to read:

      prepend domain-name-servers 208.67.222.222, 208.67.220.220;

      This will prepend the OpenDNS addresses to the top of the list. (You can also use "supersede", which will just use them.) You don't have to worry about the DHCP client overwriting settings on each reboot or lease cycle, and your ISP nameservers will still be used as backup.
   3.

      Run: sudo /etc/init.d/networking restart
   4. Using Ubuntu? Check "Networking" to see if the changes applied correctly.
      Go to "System &#8211;> Administration &#8211;> Networking" and click the DNS tab.

You could susbstitute your ISP DNS servers for the OPENDNS servers above but either should work fine.

---

### Post by koenn on 2007-02-17
> What is the root cause of the problem ? software bug ? If it's the case it can be transferred to development team or support guys.
The cause seems to be that your router (actually the dhcp service running on your router) configures your pc to use the router address as DNS server - but apparently the DNS service running on the router does not work very well.

---

### Post by esacre on 2007-02-18
It can be possible.
But I think it's normal that the router sends 192.168.1.1 as dns server to ubuntu. The router is also configured to passthrough the dns request to the 2 dns outside the lan discovered during connection with my isp.

---

### Post by handy on 2007-02-18
The problem is apparently caused by cheap windoze centric router/modems.  The good quality hardware is quite expensive.

---

