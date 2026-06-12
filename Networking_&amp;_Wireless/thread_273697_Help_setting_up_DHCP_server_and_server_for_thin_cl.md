---
title: "Help setting up DHCP server and server for thin client"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by GargoyleMusic on 2006-10-08
What I want to do is this:

Our home gets internet via roadrunner, and we share that connection with a router.

I want to use a computer as a server, and I want it too to act as a router (I want to connect a hub to this computer).

I then want the computers that are connected to the hub to act as thin clients from the server.

I want it to look like this:

```


[FONT="Courier New"]Cable Modem
  |
  |
  --- Router (192.168.0.1)
         |
         |
         --------------
          |     |     | (eth0: 192.168.0.125)
         Sam   Bob   Server
                       |  (eth1)         
                      Hub
                       |
                      Mary (10.229.2.24)
[/FONT]

```

In this example, Sam and Bob are connected to the router (with their 192.168.0.x IPs). The Server also has a 192.168 IP.

But I want eth1, then, to assign 10.229 IP addresses to computers that are connected to that hub (say Mary). I want Mary to be a thin client that is getting the kernel, etc from Server.

I want this:[IMG]https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring?action=AttachFile&do=get&target=ltsp_inet2.png[/IMG]
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring)

That said, I'm having a bit of trouble. First, different dhcpd guides give different ways of configuring the interfaces. Is there any one guide that will do the trick? Or does anyone know how I should edit my dhcpd.conf file?

Once I do that, then I'll worry about trying to get the thin-client mechanism to work - though help with respect to that would be appreciated as well. I know edubuntu is supposed to configure all of that for you in advance - but I just want to use vanilla Ubuntu (because the purpose of the thin client isn't for educational stuff at all.)

Another option is to use a boot-cd to tell Mary where to find the kernel. Might that be a better/easier option to explore?

I appreciate your help in advance!

---

### Post by gperk on 2007-10-30
Worked out a solution yet? 
I am a little new to all this myself but why bother with DHCP at all? You can just assign static IPs to all the computers. It is not like you have hundreds of them. 
Also, why not just use 192.168.0.x with all the machines?

---

### Post by soapyfish on 2007-12-04
Following these instructions here got the dhcp server and the terminal server going nicely 

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

So I hope those help. 

I am trying to configure the dhcp server so that it will only service requests that match a list of mac addrresses. We already have one dhcp server and I cannot use that. I  also do not want to make a mess of the IP address allocation we already have. I figured if I was to configure my dhcp server to only hand out leases to machines with specific MAC addresses that would solve the problem ??

---

