---
title: "Frequent internet time out"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by gtdaqua on 2007-08-20
Hi everyone!
 
 I am having a strange problem - i am an IT savvy myself but I am stumped here. 
 
 I installed Kubuntu 64bit like a month ago on an DELL Optiplex AMD64. Was surfing internet in full speed. Ran apt-get install/upgrade - no problems. 
 
 Recently, i got frequently disconnected from internet. LAN worked superfast. It always is. 
 
 Internet would just drop if i dont browse for some time. Then it would come back up after several time out issues!! 
 
 NIC cant be a problem because I am typing this post from a VM on another server in a LAN! I can get instant internet connections on any VM anytime. 
 
 But on my desktop i get disconnected every now and then!! Tried configuring OpenDNS, disabled IPv6, but no go!!
 
 So to keep continous internet, i have to leave a terminal pinging google.com always and browse in the background so that I dont lose the connection! Connected to a Gb switch and had these problems. Connected back to a 100Mbps switch - still the same issue.
 
 My Network config:
 
 Desktop IP: 192.168.6.101/24
 Gateway: 192.168.6.1 (Dell L3 switch)
 ADSL Router: 192.168.6.253
 DNS: 192.168.6.9 (all other servers are using this server) and 208.67.222.22

nslookup resolves the hostname immediately and even ping resolves - but times out. 
 
 Same configuration for VMs (Win Server 2003) but they dont have any problems!! 
 
 Can someone help me? I love kubuntu - its just the internet which is being a pain now!!
 
 Thanks!

---

### Post by will71110 on 2007-08-20
Before you assume that there is something wrong with the OS, try connecting directly to your Router.  It might be possiable that your L3 Switch is causing the issue.  

I'm no Linux expert but maybe the drivers are causing issues.  Mine, if I use the generic drives it wont detect the speed nor can I hard set it.  Still havent got that fixed either.  

Another thing you could try is hard setting the speed from auto to 100-full on the L3 switch and the NIC.

---

### Post by gtdaqua on 2007-08-20
Thanks, Will.

Maybe there is something wrong with the OS. I cant blame the L3 switch because it is the DG for all desktops/servers. I tried configuring the ADSL modem as DG - still the same issue. I have plugged a Cisco 1800 (configured cisco's DG to Dell L3 and Dell L3's DG to ADSL modem). Now my DG is Cisco and no problems so far. But really cant understand why this is happening.

I can rule out duplex setting on the NIC because I can connect and download content from all LAN servers/workstations. And no packet losses or Tx/Rx errors!!

---

### Post by will71110 on 2007-08-20
A program I'd recommand to see if you can find your problem is called Wireshark. ([www.wireshark.org](www.wireshark.org))  Could be an ARP, Broadcast, or Buffer Overflow causing issues.  Wireshark will show all these live (its a sniffer).  Now, I havent installed it on linux but I do know there is a version for it.  You also have to have winpcap installed to make it run.

ARP could be timming out too soon on the box and when you goto connect maybe ARP isnt working right off the bat. Type ARP in the Terminal, see how long ARP table keeps your gateways IP. (CTRL C to exit it)  If ther is a way to set it, might need to increase the timeouts on ARP.

---

### Post by gtdaqua on 2007-08-20
ARP is a good point to look at! How to determine the duration of gateway IP held in ARP?

---

### Post by will71110 on 2007-08-20
Not sure.  I'd have to google it. LOL. Let me know if you figure it out though if I havent already.

EDIT:Another thought would be maunally put in in ARP so it dosent disapear.  Still reading up on the command. If you "man arp" in terminal, there are instructions on how to do this.

---

### Post by gtdaqua on 2007-08-20
Ok - this is what happened. I didnt browse the internet for sometime and tried ubuntuforums.org - no response. I cancelled immediately and opened terminal and typed 'arp'. After the result displayed, I went to browse back again and I got connected immediately.

So probably, add a permanent entry in the arp ?

---

### Post by will71110 on 2007-08-20
>  cancelled immediately and opened terminal and typed 'arp'

That command only shows info about ARP if ran by itself.  One thing that command helps with is to see if your NIC is accepting ARP requests.  It should have addresses with MAC addresses beside them,  if not there is an ARP problem.  or you'll run into alot of issues.

> So probably, add a permanent entry in the arp ?
That sounds like it'll fix it.  I havent figured out the syntax.  It say to do

> arp -s hostname hw_addr

---

### Post by gtdaqua on 2007-08-20
yeah - i added the Dell L3 switch's MAC to arp and configured it as my gateway.

No problems so far - but let me wait for a while! Thanks for ur support! Really appreciate it. 

Is Ubuntu going to fix this permanently (coz i know several users had the same problem and there quite a few posts in this fourm before)?

EDIT: Btw, "info arp" shows it all. Just like any other 'info <command>'...

---

### Post by will71110 on 2007-08-20
ah...that is what I was missing

arp -i eth0 -s *IP* xxx.xxx.xxx *HW address* xxxx: xxxx: xxxx

---

### Post by gtdaqua on 2007-08-22
> **will71110 said:**
> ah...that is what I was missing

arp -i eth0 -s *IP* xxx.xxx.xxx *HW address* xxxx: xxxx: xxxx


It is definitely ARP!!! 

Two of my machines are having the same ARP entry!!! This happens often!!

192.168.6.1 (L3 Switch & Actual DG) - this MAC is pointing to 192.168.6.3 (Ubuntu Server) - so when I accidentally ssh'd to 6.1, i was presented the logon screen for 6.3! now I double checked ARP and 6.3 has 6.1's MAC address. So no routing happens! 

Can someone help here? I am concerned if this is a MITM Attack!

---

### Post by will71110 on 2007-08-22
When you show ARP on the L3 switch, does it show these both with the right address?  Also check the physical MACs using ifconfig on both machines and make sure you dont have duplicates.  I have seen that before.

EDIT:  When you manually put the MAC address in ARP in 6.1to point to 6.3, did you put in the MAC of 6.3 and not the MAC of 6.1?  If you did put in the MAC of 6.3 with 6.1s MAC then that is why when you log into 6.1 it shows up as 6.3.  Also you dont need to edit the l3 switches ARP table, only the host.  So I'd clear the manual tables in the switch and only put the manual entry in your host.

---

### Post by gtdaqua on 2007-08-24
Thanks, Will.

I do the ARP clearing in my desktop. I dont do anything on the switch. The L3's arp and the server's ARP are not the same. Only in my (dekstop) ARP entry - L3's MAC is shown as the server's MAC. All other desktops are showing correct ARP entries.

---

