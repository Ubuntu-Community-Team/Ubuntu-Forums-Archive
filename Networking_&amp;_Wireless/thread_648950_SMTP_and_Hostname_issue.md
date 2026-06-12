---
title: "SMTP and Hostname issue"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by unix4linux on 2007-12-24
Hello All,

First, HAPPY HOLIDAYS!!!!

Second, having smtp problems as well as a hostname ip issue which one cause be causing the other not to work properly.

Here's the thing.  I had two nics on my kubuntu machine.  eth0 (external w/ public static) and eth1 (internal w/ private static)

I install ClarkConnect on a separate machine to be my gateway/firewall.  So, I took eth0 from kubuntu out and made eth1 eth0.  In turn, eth0 is now the only nic on kubuntu with the internal static private IP.  ClarkConnect now holds eth0 (public static) and eth1 (private static).

Now, lets get ClarkConnect out of the picture since now you know what I have done with the nics.  Back to kubuntu; if I run "hostname -i", it is for some reason still showing the public static IP of the eth0 I had in the machine before taking it out and placing it on CC. This could be a problem...I don't know what problem it may cause but it's not right.

If I do "/etc/init.d/networking restart", I get the following:

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                          SIOCADDRT: File exists
Failed to bring up eth0.
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.

Buttttttt, networking is working fine.  I can communicate internally and on the internet just fine and eth0 does come up, it doesn't really fail.

If I grep for that public address that "hostname -i" is still showing "grep -nr 'public_ip_address' /dev or /etc", it won't find it.  I don't know where it's pulling the IP from unless if it's getting it from the kernel and the kernel may still thing eth0 is still that external card.

I also looked at /etc/network/interfaces and noticed:

root@www:/etc/network# cat interfaces 
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
        post-up iptables-restore < /etc/iptables.up.rules
        address 192.168.4.2
        netmask 255.255.255.0
        gateway 192.168.4.1

auto eth0

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth1

that seems completely wrong because my network is 192.168.4.0 and not 192.168.1.0.  It used to be 192.168.1.0 when both nics where in the kubunt machine but I changed it to ...4.0.

I haven't changed that yet.  I want to see if I can get some input from you guys first.

Finally, mail, if I try to telnet:
root@www:/etc/network# telnet localhost:25
telnet: could not resolve localhost:25/telnet: Name or service not known

I can't send any email out.  I am running sendmail from the repos.  I have checked my hosts files with both sysctl and hostname and /etc but everything is fine there.

I am not a noob but not a guru either.  I can defend myself pretty well so I am willing to try out any kind of stuff you guys can think of.  I don't know if me not being able to email has to do with the networking part.

What can I look into for the email problem and networking?

Thanks in advance and sorry for the long post but trying to get as much detail to you guys as possible

---

### Post by unix4linux on 2007-12-24
Ok, the telnet command had a syntax error so ignore.  I was doing telnet localhost:25 which generated the name or service not known error.

I used a space in stead and it connects fine:

telnet localhost 25

But, this still doesn't solve my problems ;-)

---

### Post by unix4linux on 2007-12-24
Ok, SMTP is working.  I can email now.  The problem was the CC was allowing port 25 traffic on external nic and not on eth1.  eth1 is my local nic so any traffic coming from any machine on the local network gets passed through eth1 hence port 25 traffic being blocked on eth1...whewwwwwwww

now, still trying to hash out the "hostname -i" issue still showing my external IP address and the weird errors when restarting networking

---

