---
title: "SSH server timeout from external client"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by 12__monkeys on 2007-06-10
Using Ubuntu 6.06 I have set up and SSH server .  Testing this I have used different clients on the local network and can connect without problem.  The problem I get is when I try to connect using a client external to my network.  'Port forwarding' has been enabled and all traffic on port 22 is forward to the SSH server.  An external client is prompted for a username, but the connection strangely times out when I type the password.

Is there a way that I can see what's happening?  How can I resolve this?

Thanks

---

### Post by Mr. C. on 2007-06-10
Look at the logs used by your SSH server.  Most likely /var/log/secure or /var/log/auth.log.

You may need to increase the verbosity of debug in your SSH server's config file and restart the SSH server.

MrC

---

### Post by 12__monkeys on 2007-06-13
Thanks for the reponse.  I tested some attempts again and monitored the file /var/log/auth.log, having made a few attempts I've posted my findings below:

Jun 13 20:53:01 localhost sshd[8227]: Connection from 84.92.106.xxx port 1034
Jun 13 20:53:21 localhost sshd[8227]: fatal: Timeout before authentication for 84.92.106.xxx
Jun 13 20:53:50 localhost sshd[8249]: Connection from 84.92.106.xxx port 1035
Jun 13 20:53:54 localhost sshd[8249]: Failed none for darren from 84.92.106.xxx port 1035 ssh2
Jun 13 20:54:00 localhost sshd[8249]: Accepted password for darren from 84.92.106.xxx port 1035 ssh2
Jun 13 20:54:00 localhost sshd[8255]: (pam_unix) session opened for user darren by (uid=0)
Jun 13 20:55:20 localhost sshd[8308]: Connection from 84.92.106.xxx port 1036
Jun 13 20:55:23 localhost sshd[8308]: Failed none for darren from 84.92.106.xxx port 1036 ssh2
Jun 13 20:55:25 localhost sshd[8308]: Accepted password for darren from 84.92.106.xxx port 1036 ssh2
Jun 13 20:55:25 localhost sshd[8312]: (pam_unix) session opened for user darren by (uid=0)

The log seems tos show that the username and password are  accepted, however once submitted the terminal remains blank until the connection times out.  Can anyone see why this is happening or can provide any pointer to check on my setup.

Thanks again.

---

### Post by Mr. C. on 2007-06-13
Make sure your DNS is working correctly.  SSH may be timing out trying to determine the hostname of the client.  The timeout period in your logs shows 20 seconds - that's close to the 15 second DNS timeout.

If your router address is listed in /etc/resolv.conf as the first nameserver line, change it to your ISPs DNS servers, or one of the dyndns servers.

MrC

---

### Post by 12__monkeys on 2007-06-14
I've checked the addresses listed in /etc/resolve.conf and can confirm that the addresses listed are for my ISP's DNS servers.  I've placed the IP address of my local router at the top of this file to see if it makes a difference but it doesn't.  I've attached below copy of my logged attempt.


Jun 14 18:24:42 localhost sshd[4727]: Server listening on :: port 22.
Jun 14 18:24:44 localhost gdm[4565]: (pam_unix) session opened for user kevin by (uid=0)
Jun 14 18:51:30 localhost sshd[6007]: Connection from 84.92.106.xxx port 1450
Jun 14 18:51:37 localhost sshd[6007]: Failed none for darren from 84.92.106.xxx port 1450 ssh2
Jun 14 18:51:41 localhost sshd[6007]: Accepted password for darren from 84.92.106.xxx port 1450 ssh2
Jun 14 18:51:41 localhost sshd[6013]: (pam_unix) session opened for user darren by (uid=0)
Jun 14 19:09:05 localhost sshd[6013]: Read error from remote host 84.92.106.xxx: Connection timed out
Jun 14 19:09:05 localhost sshd[6013]: (pam_unix) session closed for user darren

---

### Post by Mr. C. on 2007-06-15
The read error, timed out message indicates that the server received an error response when trying to read data from the client.  Some error returns are expected (as when the system call is interrupted and the server is expected to try again).

This, and that your connections work fine on the LAN, would indicate to me your firewall was causing the problems.  This can happen with packet fragmentation.

You haven't mentioned your firewall make/model; look through the various settings for an option regarding packet fragmentation; toggle it, and try again.  Also, if this is a commodity firewall, update the firmware and try again.

MrC

---

### Post by 12__monkeys on 2007-07-06
I use D-Link DSL-502T router and a Lynksys WRT54G to give me the wireless access that I need.  I have tried connecting directly to the DSL-502T via a really long RJ45 as I believe that this would receive packets first and I'm still get the problem so I think this could be where my problem is.

Thanks

---

