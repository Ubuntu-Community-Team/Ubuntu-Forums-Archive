---
title: "Ports not open, firewall disabled"
date: 2018-02-02
forum: Networking &amp; Wireless
---

### Post by kirk_grem on 2018-02-02
Learning Linux networking, and created an "iRedMail" server as a VirtualBox.  OS is Xubuntu 16.04 hosting the VM which is Ubuntu server, 16.04 with all updates offered.

After installation, the RoundCube webmail, and iRedAdmin pages seemed to work well.  I got an email to the postmaster with the following:
> POP3 service: port 110 over TLS (recommended), or port 995 with SSL.
* IMAP service: port 143 over TLS (recommended), or port 993 with SSL.
* SMTP service: port 587 over TLS.

So, I just tried forwarding that mail to my external email account (gmail) but RoundCube balked, giving me this:
> SMTP Error (-1): Connection to server failed.

Now, I've been chasing my tail on this, but I think THAT problem might be a bad install, so I'm going to start from scratch.

However... I thought at first that the problem might be that port 587 was being blocked.  So I ensured the firewall was off:
> sudo ufw disable

My thoughts were that all ports should now be open...right?  Wrong.
running (from another machine):
> nmap my.ip.ad.dress 
Starting Nmap 7.01 ( [https://nmap.org](https://nmap.org) ) at 2018-02-02 14:52 PST
Nmap scan report for my.ip.ad.dress
Host is up (0.00052s latency).
Not shown: 991 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
110/tcp open  pop3
139/tcp open  netbios-ssn
143/tcp open  imap
443/tcp open  https
445/tcp open  microsoft-ds
993/tcp open  imaps
995/tcp open  pop3s

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

My question is: _** Why are not ALL ports open with UFW disabled?**_

I also mucked about with iptables, used a script I found at [http://electron.mit.edu/~gsteele/firewall/firewall](http://electron.mit.edu/~gsteele/firewall/firewall) but no matter what ports I opened using that script, the results of Nmap did not change.

Someone had written elsewhere in these forums that a port is only opened once a service is registered to use that port.  So I took a look inside /etc/services and found this segment is the only one mentioning port 587:
> submission    587/tcp                # Submission [RFC4409]
submission    587/udp

So now my question is also:  [B][U]Who is "Submission"?  and what will happen to it if I succeed in installing the SMTP service that iRedMail package wants to install?  But mostly...why do I have any blocked/closed ports if the firewall is disabled?


[/U][/B]Thank you all for your help...if you can...
-Kirk

---

### Post by kirk_grem on 2018-02-02
Reinstalled iRedMail package, and all works as expected now.  However, I think I need to dig into the whole "register a service that uses that port" thing.

---

### Post by SeijiSensei on 2018-02-02
There are 65,535 ports.  nmap scans only a limited number of them by default.  You can force it to scan all the ports using the TCP protocol with 
```
sudo nmap -sT -p 1-65535 ip.address
```

It took about 30 seconds for one of my machines to scan my server with that nmap command. Limiting it to TCP scans will make it go faster; you're much less likely to be running UDP services unless you have DNS or NFS servers running.  You can run it again with -sU if you want to see if any UDP services are listening.

As for what makes a port "open," yes, there needs to be some program listening on that port.  IP packets addressed to ports with no software to handle them are ignored.   So a machine like yours running openssh-server has a "daemon" program /usr/bin/sshd that "binds" itself to port 22 when it starts up during boot.  Any IP packets addressed to port 22 on that server will be handled by the sshd program.

A firewall stands between servers like sshd and the network.  You could have sshd listening on port 22, along with a firewalling rule blocking access to that port from some or all external locations.  I have iptables rules on my remote servers that limit access to port 22 to just a couple of client machines I control.  I allow those few IPs and block the rest.

---

### Post by kirk_grem on 2018-02-07
Thank you!  After a full rebuild of the iRedMail server, and adding a routing rule for ports 81->80 and 444->443 (because I already had a web server and I've not yet added a reverse proxy...next project)  Using the suggested nmap command, I now get this:

> Starting Nmap 7.01 ( [https://nmap.org](https://nmap.org) ) at 2018-02-07 12:34 PST
Nmap scan report for my.ip.ad.dress
Host is up (0.0011s latency).
Not shown: 65526 filtered ports
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
110/tcp open  pop3
143/tcp open  imap
443/tcp open  https
587/tcp open  submission
993/tcp open  imaps
995/tcp open  pop3s


Still don't know what "submission" is.  Will post more as I make progress.

---

### Post by The Cog on 2018-02-07
> IP packets addressed to ports with no software to handle them are ignored. I have to disagree here. Packets addressed to ports that have no service listening for them are rejected by the OS. For TCP, a SYN (a connect request) will elicit a RST (reset, reject) packet. For most other protocols the OS will send an ICMP port unreachable response. I would call a port that has a listening software attached to it **open**, and one that does not have listening software **closed**.

When there is a firewall complicating things there are other possible states. The usual one is for a firewall to simply ignore the packet. I would call that port **blocked**, however lots of people like to call such blocked ports closed (grsecurity call it **stealthed**). This introduces confusion as they then refer to unblocking the port in the firewall as opening it but this is nothing to do with whether the port is open in the OS. A port that is "open" through the firewall will be visible to callers in that a response can be received from it, but that port may well be closed in which the case will be an RST (connection refused) or a port unreachable message. To add further confusion, a firewall can be configured to send its own unreachable messages instead of simply dropping the packet, making it difficult to tell whether it is a firewall or the OS that is sending the rejection message.

You can see if the OS is listening for incoming packets with the command ```
sudo netstat -lntp
```If a port is listed, it's open. If it is not listed, it is closed. Either way for TCP calls at least (other protocols may choose to ignore input) a caller should get a response.

---

