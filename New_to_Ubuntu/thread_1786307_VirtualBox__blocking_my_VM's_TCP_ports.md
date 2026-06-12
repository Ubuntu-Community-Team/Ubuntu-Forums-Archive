---
title: "VirtualBox  blocking my VM's TCP ports"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by cwmoser on 2011-06-19
I have VirtualBox VM running Windows XP.
My XP client does not have a firewall nor even antivirus.

Something is blocking the TCP Port I am using.  I can successfully test my software inside the VM client but all attempts from the host or outside my LAN fail.

I have my VM in Bridge mode networking.

I suspect its the VirtualBox software that is doing the blocking of TCP ports.  Any help is appreciated.

Thanks

Carl

---

### Post by GWBouge on 2011-06-19
Try using NAT instead of Bridged.

---

### Post by crispy_420 on 2011-06-20
The problem with going NAT would then be that the client/guest would then be on a different network all together. 

What is the IP and subnet of each PC, host and guest? 

XP does have a firewall by default. Did you disable that or open the appropriate port?

---

### Post by cwmoser on 2011-06-20
Windows Firewall on the XP VM is turned off.
No other firewalls.
No Antivirus either.

My host and my VM are using IPs on my LAN 192.168.0.xxx

Carl

---

### Post by crispy_420 on 2011-06-20
Why not include the whole IP? But I'm assuming there is no conflicts in address and they are in the same subnet.

Can each system ping the other? 

Do you want to let us know what software you are testing?

---

### Post by cwmoser on 2011-06-20
Both the host and the VM can ping each other.

From the host, I test the port and get this:

$ telnet 192.168.0.202 20666
Trying 192.168.0.202...
telnet: Unable to connect to remote host: Connection refused

The listener is running on the Windows XP VM.


Within the VM, I can go to the command prompt and similarly use telnet and test the port and it connects and works like this:
C>  telnet  127.0.0.1  20666

but I get connection refused if I do this:
C>  telnet 192.168.0.202  20666



This is some software that I am writing.  Its purpose is to collect data from a number of remotely located PC's.  The server is to be an Ubuntu Linux box running a VM - Windows XP or Server 2003.

My software works when I test within the VM but I get "Connection refused" when I test from the host machine.  

There is something inside Ubuntu or Virtual Box that is blocking this port.

Any insights are appreciated.  Thanks.

Carl

---

### Post by crispy_420 on 2011-06-20
I think it is unlikely it is Ubuntu or Virtualbox blocking this port. My next guess would be your networking hardware is causing the issue.

As there a functional difference between if connect via 192.168.0.202 and 127.0.0.1 that gets me thinking infrastructure issue. If you use the localhost address it does no get routed where as the IP address uses the router/switch. So the limiting factor has to be the router because once you remove it your connection is fine.

So what is your router make/model?

---

### Post by cwmoser on 2011-06-20
I have a TP-Link router TL-WR541G.

I have Forwarding set to allow the port to the VM IP address 192.168.0.202.

I set up a test to see if I can communicate outside to the host Ubuntu box and it works. 

I think its got to be something in VirtualBox or something to do with the VM's virtual NIC interface.  I can't find any firewall within the XP VM at all.

Stumped :-(


Carl

---

### Post by cwmoser on 2011-06-20
My software is based on .NET 2.0.
I wonder if there is a security policy that is causing the TCP port to be blocked?

Carl

---

### Post by GWBouge on 2011-06-20
I've had this issue before using 'Bridged' in VirtualBox on an Ubuntu Server VM, and using NAT fixed it.  With Bridged, the VM seems to share the host's interface, so I gathered that the *host* was swallowing up requests, not VirtualBox.  With NAT the VM gets to do its own thing outside of the host, and appears as any other machine on my internal network.

No, I'm no network expert, so I really don't know the specifics of what's going on, but after spending a couple days fighting a Bridged setup not accepting requests from anything outside of itself, a simple switch to NAT solved it.  Now, on any VM I set up that is intended to listen for requests (or anything I want to exists as a 'true' machine, directly connected to the network), I use NAT, and have no issues.

---

### Post by crispy_420 on 2011-06-20
You shouldn't need forwarding if you are working locally but since you have set it up try using your external/WAN IP address instead of local.

Are working on wireless? I have seen routers that block types of traffic locally if the source is wireless as some attempt at security.

Do you have any security related feature enabled on router? Are you using their DMZ function?

Lastly I am convinced that it is your router if you have not noticed. Would you be willing to reset to factory defaults if it comes to that? If you have a complex setup and don't want to that's cool.

---

### Post by cwmoser on 2011-06-20
I changed my VM's NIC adapter from Bridged to NAT and it got a 10.0.2.15 IP addres.

Within my Windows XP VM, my software responds properly when I issue:
C>  telnet  127.0.0.1  20666


But, within my VM, it will not respond with I issue:
C>  telnet 10.0.2.15  20666

Windows Firewall is OFF.

In Virtual Box Network Adapter settings, I have:
Protocol    Host IP   Host Port  Guest IP   Guest Port
TCP        127.0.0.1  20666      10.0.2.15   20666

That is kinda interesting - the 127 address works but not the 10 address.  

Looks to me that something is blocking the port 20666.

Any ideas?

Thanks

Carl

---

### Post by crispy_420 on 2011-06-21
On you XP machine try the following command to verify it is really listening:

netstat -an |find /i "listening"

[http://www.petri.co.il/quickly_find_local_open_ports.htm](http://www.petri.co.il/quickly_find_local_open_ports.htm)

Maybe also running a port scanner from the linux machine to see if the port is listening and open.

---

### Post by cwmoser on 2011-06-21
I ran netstat -an |find /i "listening" in my XP VM and this is what I got:

```
C:\>netstat -an |find /i "listening"
  TCP    0.0.0.0:135            0.0.0.0:0              LISTENING
  TCP    0.0.0.0:445            0.0.0.0:0              LISTENING
  TCP    10.0.2.15:139          0.0.0.0:0              LISTENING
  TCP    127.0.0.1:1027         0.0.0.0:0              LISTENING
  TCP    127.0.0.1:20666        0.0.0.0:0              LISTENING

```

Should it show the IP address (10.0.2.15) of the VM?

Carl

---

### Post by gmargo on 2011-06-21
> **cwmoser said:**
> 
```

  TCP    127.0.0.1:20666        0.0.0.0:0              LISTENING

```

There's your problem.  Whoever is listening on port 20666 is only listening to the localhost interface. 
--unix info removed--
How does one configure the telnet daemon on Windows?

Are you running "unix services for windows"?
According to this: [http://support.microsoft.com/kb/324077](http://support.microsoft.com/kb/324077) which I am not sure applies,
the telnet daemon is launched from an xinet daemon confgured in /Etc/Inetd.conf.
Check that file - it probably specifies which interface(s) to listen on.

This page: [http://technet.microsoft.com/en-us/library/bb463201.aspx](http://technet.microsoft.com/en-us/library/bb463201.aspx) says the config file is $INTERIX_ROOT/etc/inetd.conf

---

### Post by cwmoser on 2011-06-21
Gmargo, you solved the problem I was having - thanks.

Here is my code fragment:
```
 
       'Dim localAddr As IPAddress = IPAddress.Parse("127.0.0.1")
        Dim localAddr As IPAddress = IPAddress.Parse(IPaddrs)

```


I had **127.0.0.1** thinking that it would be IP address independent.  You called out that in your prior post.

So, I changed it to the actual IP address of my VM.  I changed Virtual Box back to Bridge Mode to get a local LAN address.  Changed my routers Port Forwarding rebooted the Router.  At first the Router did not work properly and a reboot got it working as it should.

Thanks again.  Now that I have the core TCP/IP plumbing working between my Remote client and the Server, I can go on and sling some more code.  Thanks much.

Carl



> **gmargo said:**
> There's your problem.  Whoever is listening on port 20666 is only listening to the localhost interface. 
--unix info removed--
How does one configure the telnet daemon on Windows?

Are you running "unix services for windows"?
According to this: [http://support.microsoft.com/kb/324077](http://support.microsoft.com/kb/324077) which I am not sure applies,
the telnet daemon is launched from an xinet daemon confgured in /Etc/Inetd.conf.
Check that file - it probably specifies which interface(s) to listen on.

This page: [http://technet.microsoft.com/en-us/library/bb463201.aspx](http://technet.microsoft.com/en-us/library/bb463201.aspx) says the config file is $INTERIX_ROOT/etc/inetd.conf

---

### Post by crispy_420 on 2011-06-21
So is it solved for now? Or did you already mark it as and I'm just not paying attention to titles anymore?

---

### Post by cwmoser on 2011-06-21
> **crispy_420 said:**
> So is it solved for now? Or did you already mark it as and I'm just not paying attention to titles anymore?


Yes, it was a programming issue - not anything to do with Virtual Box.  I hard coded 127.0.0.1 as the IP address of the VM thinking that it would work.  I replaced 127.0.0.1 with the actual IP address of the VM and it fixed it.

Thanks for helping.

Carl

---

### Post by crispy_420 on 2011-06-21
I almost blamed a VM I had for an issue I was having just now, turned out it the firewall I forgot I installed. So it happens.

But on a side note wouldn't it be better to avoid a single IP address if possible?

---

