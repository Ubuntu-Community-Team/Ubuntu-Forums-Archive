---
title: "Needs some guidance and DHCP and PXE"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by ylafont on 2013-10-20
I set up a PXE server the other day on Ubuntu 12.10. Form reading some post, i was under the impression that i could have two DHCP servers on the same network. One for just PXE clients and another all remaining client.   I have set up the PXE server to  give addresses  between 192.168.1.200 and 192.168.1.225  and reserved those address from the first DHCP server.  I was going to read up on how to turn off DHCP ports 67 and 68, but then realized that the PXE server will be unable to assign ip address if i did that.   Is there a method of having the PXE server responds to PXE requests only?  


some logs entries on the pxe server.
Oct 20 19:20:58 PlexOne dhcpd: DHCPREQUEST for 192.168.1.6 from 3c:43:8e:e7:65:74 via em1: unknown lease 192.168.1.6.
Oct 20 19:31:54 PlexOne dhcpd: DHCPREQUEST for 192.168.1.10 from 00:24:d7:d4:c4:64 via em1: unknown lease 192.168.1.10.

Thank you.

---

### Post by jantoniou on 2013-10-24
> **ylafont said:**
> I set up a PXE server the other day on Ubuntu 12.10. Form reading some post, i was under the impression that i could have two DHCP servers on the same network. One for just PXE clients and another all remaining client.   I have set up the PXE server to  give addresses  between 192.168.1.200 and 192.168.1.225  and reserved those address from the first DHCP server.  I was going to read up on how to turn off DHCP ports 67 and 68, but then realized that the PXE server will be unable to assign ip address if i did that.   Is there a method of having the PXE server responds to PXE requests only?  

What you want is something called a ProxyDHCP server.  Trying to run two DHCP servers on the same network will create a huge amount of headaches that frankly you don't need to deal with.  It certainly won't consistently deliver what you want.

dnsmasq is the only reliable/functional ProxyDHCP server I am aware of.  Here is an example ProxyDHCP server config in dnsmasq that has worked for me: 

port=0
log-dhcp
enable-tftp
tftp-root=/tftpboot
pxe-service=x86PC, "Boot from local disk"
pxe-service=x86PC, "Install Linux",pxelinux
dhcp-range=192.168.0.0,proxy,255.255.0.0

dhcp-range=10.0.0.0,proxy,255.0.0.0
dhcp-range=172.16.0.0,proxy,255.255.0.0


I generically include all the private IPv4 networks here as you can see since there's no real harm in doing this - dnsmasq won't really work as a proxyDHCP server unless you have an existing DHCP server running.  Obviously this example is using pxelinux though normally I work with iPXE.  Example iPXE boot options look like:

dhcp-match=ipxe,175
dhcp-option=175,8:1:1
dhcp-boot=net:ipxe,[http://yourserver.com/boot.ipxe](http://yourserver.com/boot.ipxe)
dhcp-boot=tag:!Iipxe,ipxe.0



Anyway once you have it configured, fire up dnsmasq on the same logical or physical LAN as whatever devices you're trying to netboot - along with any existing DHCP server to hand out the actual IP addresses and logical network config to DHCP clients - and you should be good to go.  And yes you can also configure the dnsmasq server to be an added ip helper (DHCP relay) if you have a multi-subnet environment.

---

