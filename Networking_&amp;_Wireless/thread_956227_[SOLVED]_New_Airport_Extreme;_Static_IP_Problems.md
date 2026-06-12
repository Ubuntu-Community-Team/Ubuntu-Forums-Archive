---
title: "[SOLVED] New Airport Extreme; Static IP Problems"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by ryharv on 2008-10-23
Hello all,

My networking setup used to work fine.  I had a Ubuntu box plugged into an Airport Extreme with a physical cord.  The Ubuntu box had a static internal IP as 192.168.1.200.  All other clients that connected with a wired or wireless connection to the Airport Extreme used a DHCP lease.

The Airport Express crapped out and I had to get a new one.  Now, I have an interesting problem.  All is working fine except:

The Ubuntu box will not open outgoing connections.  

I can SSH to it from another computer via "ssh 192.168.1.200".  No problem there.  But I cannot open a web page, or ping google.com from Terminal.  

When I switch the networking on the Ubuntu box to use DHCP, everything works fine.  But I don't want to have it set up this way.  

The problem must be with a setting on the Airport Extreme, I am thinking.  I have it set so that the DHCP leases run from 192.168.1.02 through 192.168.1.199, so it's not interfering that way.  

Any ideas?  Thanks for your help.

---

### Post by ryharv on 2008-10-23
Hello all,

My networking setup used to work fine. I had a Ubuntu box plugged into an Apple Airport Extreme with a physical cord. The Ubuntu box had a static internal IP as 192.168.1.200. All other clients that connected with a wired or wireless connection to the Airport Extreme used a DHCP lease.

The Airport Extreme crapped out and I had to get a new one. Now, I have an interesting problem. All is working fine except:

The Ubuntu box will not open outgoing connections.

I can SSH to it from another computer via "ssh 192.168.1.200". No problem there. From another computer, I can also open a web page at [http://192.168.1.200](http://192.168.1.200).  But from the Ubuntu box, I cannot open a web page, or ping google.com from the terminal.

When I switch the networking on the Ubuntu box to use DHCP, everything works fine. But I don't want to have it set up this way because I have several backup scripts set to see it as 192.168.1.200.

The problem must be with a setting on the Airport Extreme, I am thinking. I have it set so that the DHCP leases run from 192.168.1.02 through 192.168.1.199, so it's not interfering that way.

In Ubuntu's "Network Settings / eth0 properties", I have:

Static IP Address
IP: 192.168.1.200
Subnet Mask: 255.255.252.0 (matches what I see in the Airport config)
Gateway address: 192.168.1.1

Any ideas? Thanks for your help.

---

### Post by ryharv on 2008-10-23
Update: I have no idea how it happened since I didn't make any changes, but everything is working fine for me now.  Just as I typed the post, I returned to the computer and was able to get a connection.  Thanks for looking!

---

### Post by bapoumba on 2008-10-24
Threads merged.
Nice to see you got it to work, BTW :)

---

