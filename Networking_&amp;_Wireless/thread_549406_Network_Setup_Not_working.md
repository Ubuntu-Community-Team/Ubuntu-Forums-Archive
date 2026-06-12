---
title: "Network Setup Not working"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by andthereitgoes on 2007-09-12
Ok here is my twisted problem.

I have a router. To which i have 1 machine connected. This machine runs Windows XP Pro SP2
On this machine i have VMWare Server installed. Ubuntu (7.04 )  is installed on VMWare.

Now the network is set for DHCP. But i cannot connect to internet in Ubuntu.
I have tried dhclient to release and acquire a new address. I have checked the router logs, which shows that a new IP address has been acquired. Both the IPs are same.

But still cannot connect to the internet. Any ideas?

---

### Post by noob12 on 2007-09-13
Make sure you've followed the VMWare  notes on installing Ubuntu as a guest OS.  The instructions include disabling IPV6, and installing VMWare tools (which includes some drivers). Also, I would use bridged networking mode in the VM initially.

---

### Post by andthereitgoes on 2007-09-13
ok cool thanks.. will do that and get back..!!

---

### Post by andthereitgoes on 2007-09-13
ok i installed the tools.

I changed the network setting to bridge connection instead of NAT
but now when i start Ubuntu its says..

The network bridge on device VMNet0 is not running. The Virtual Machine will not be able to communicate with the host or with other machines on the network. Virtual device Ehternet0 will start disconnected

---

### Post by noob12 on 2007-09-13
Check your VM configuration.  Make sure that VMnet0 is defined to be bridged to a physical interface on the Windows side that is actually connected.  

If your VM configuration says VMnet0 is being mapped automatically, first try setting the mapping manually to the wired interface and making sure the Host OS has an established wired connection.  You can then try the fancy automatic mapping once you have that working.

If you are sure everything is right, you can also try restarting vmware-tools: **sudo /etc/init.d/vmware-tools restart** and see if that helps at all.

You should also try the VMWare forums and support FAQs.

---

### Post by andthereitgoes on 2007-09-14
hey.. ok i sorted the problem and i am able to access the connection.
the problem was really silly, i had my host computer and the guest computer ( Ubuntu ) named
with the same host name. so once i changed that i could access the network.

there one small problem though.

i have a firewall on my host computer ( Windows XP ) . I am using Outpost. Now when i disable the firewall the connection works. but i when i enable it, the connection doesnt work.
i have allowed connection for the following processes
vmware-vmx.exe
vmserverdwin32.exe
vmware-authd.exe
vmware.exe

also it would help if anyone could tell me what connections should be allowed ( if anything in particular )

PS- i have also posted this in vmware forum. no reply yet.

---

### Post by noob12 on 2007-09-14
I'm glad you found your issue.  I am not very familiar with this problem and it's again an issue that's not really on the Ubuntu side, so I hope you can get more help from the VMWare forums.  Here are the only things I can think of:

When you say the connection doesn't work, do you mean that no traffic from the guest Ubuntu VM can get through?

Do you have control of the firewall on a per-connection basis?  Can you turn off the firewall only on the bridges?  If so, try that.

If you can't do that, there might be another approach open now that you have gotten networking working on the guest OS side.  You could try going back to your original private NAT-ed virtual net setup.  (Yes, I know I told you to go bridged earlier --that's because it's less complicated to get that working initially.)  This would have the advantage that you could probably configure your firewall to let traffic in and out based on the address range you choose for that NAT-ed virtual net.

---

