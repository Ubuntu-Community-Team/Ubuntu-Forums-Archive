---
title: "SSHFS fails when port number is used"
date: 2015-10-15
forum: Networking &amp; Wireless
---

### Post by Pocc on 2015-10-15
Title says it all. Port number in sshfs can be specified with "-o port=[port number]" or "-p [port number]". Both of them produce the same error for me. I understand that sshfs is based upon sftp (i.e. if sftp works, then sshfs should work); however, I've gotten sftp to work without sshfs. The error I get is ```
read: Connection reset by peer
```, and I have used the debug option "-o ssh_debug", and the error is the second thing that comes up. The weird thing is that ssh and sftp work just fine. 

I've got it working with the default port of 22, but not 55516, which was my target. Router's port forwarding works fine, as long as external listening port is 22 and the internal port matches the listening port on the server in sshd_config.

Here's my typical sshfs command:  ```
sudo sshfs -o IdentityFile=/home/me/.ssh/eeePC_key -o allow_other me@[IP ADDRESS]:/home/me /mnt/epic -o sshfs_debug -p 55516
``` It works if I exclude the '-p 55516' (and change port forwarding in server's sshd_config and router's port forwarding accordingly). I currently have 22:22 forward to the server on my network.


Here's my sshd_config file on the server:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details


# What ports, IPs and protocols we listen for
Port 22
Port 55516
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes


# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024


# Logging
SyslogFacility AUTH
LogLevel INFO


# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes


RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys


# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes


# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no


# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no


# Change to no to disable tunnelled clear text passwords
PasswordAuthentication no #yes


# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes


X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
#Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


Subsystem sftp /usr/lib/openssh/sftp-server


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM no #yes


#My Additions
AllowUsers me
AllowAgentForwarding yes
PermitOpen any

```

I think this is all the relevant code, but I can post more as needed.

---

### Post by michi1983 on 2015-10-15
Hi,

what kind of machine are you trying to bind with sshfs? Is it a server? Might it be an iptables issue on the server?
You could check with ```
sudo nmap $IP_OF_SERVER
``` what ports are open.

---

### Post by Pocc on 2015-10-15
I didn't have nmap installed, so I apt-got it. 

Here's the relevant info:

```
Not shown: 999 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
```

---

### Post by michi1983 on 2015-10-15
okay, so this means that only port 22 is open. 
and something (maybe iptables) is blocking other ports. that's why you can't connect.

---

### Post by Pocc on 2015-10-15
So I ran 

```
netstat -ace | grep 55516
```

and got 

```
tcp        0      0 *:55516                 *:*                     LISTEN      
root       13093
```

so it's listening (I think?)
When I run ```
sudo nmap -v -p 55516 127.0.0.1
```
I get 

```
Starting Nmap 6.40 ( http://nmap.org ) at 2015-10-15 09:11 PDT
Initiating SYN Stealth Scan at 09:11
Scanning localhost (127.0.0.1) [1 port]
Discovered open port 55516/tcp on 127.0.0.1
Completed SYN Stealth Scan at 09:11, 0.21s elapsed (1 total ports)
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00015s latency).
PORT      STATE SERVICE
55516/tcp open  unknown

```

---

### Post by michi1983 on 2015-10-15
can you post the output of
```
sudo iptables -L
```

---

### Post by Pocc on 2015-10-15
```
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            


Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-logging-forward  all  --  anywhere             anywhere            
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            
ufw-after-logging-forward  all  --  anywhere             anywhere            
ufw-reject-forward  all  --  anywhere             anywhere            
ufw-track-forward  all  --  anywhere             anywhere            


Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-logging-output  all  --  anywhere             anywhere            
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            
ufw-after-logging-output  all  --  anywhere             anywhere            
ufw-reject-output  all  --  anywhere             anywhere            
ufw-track-output  all  --  anywhere             anywhere            


Chain ufw-after-forward (1 references)
target     prot opt source               destination         


Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-ns
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:netbios-dgm
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:netbios-ssn
ufw-skip-to-policy-input  tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootps
ufw-skip-to-policy-input  udp  --  anywhere             anywhere             udp dpt:bootpc
ufw-skip-to-policy-input  all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST


Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-after-output (1 references)
target     prot opt source               destination         


Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ufw-user-forward  all  --  anywhere             anywhere            


Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  anywhere             anywhere             ctstate INVALID
DROP       all  --  anywhere             anywhere             ctstate INVALID
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
ACCEPT     icmp --  anywhere             anywhere             icmp source-quench
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp parameter-problem
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     udp  --  anywhere             anywhere             udp spt:bootps dpt:bootpc
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             224.0.0.251          udp dpt:mdns
ACCEPT     udp  --  anywhere             239.255.255.250      udp dpt:1900
ufw-user-input  all  --  anywhere             anywhere            


Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         


Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         


Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  anywhere             anywhere            


Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW ALLOW] "


Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 10 LOG level warning prefix "[UFW BLOCK] "


Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type LOCAL
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type MULTICAST
RETURN     all  --  anywhere             anywhere             ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  anywhere             anywhere             limit: avg 3/min burst 10
DROP       all  --  anywhere             anywhere            


Chain ufw-reject-forward (1 references)
target     prot opt source               destination         


Chain ufw-reject-input (1 references)
target     prot opt source               destination         


Chain ufw-reject-output (1 references)
target     prot opt source               destination         


Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  anywhere             anywhere            


Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-track-forward (1 references)
target     prot opt source               destination         


Chain ufw-track-input (1 references)
target     prot opt source               destination         


Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW


Chain ufw-user-forward (1 references)
target     prot opt source               destination         


Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:55516
ACCEPT     udp  --  anywhere             anywhere             udp dpt:55516
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ssh


Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere             limit: avg 3/min burst 5 LOG level warning prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable


Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            


Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         


Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         


Chain ufw-user-output (1 references)
target     prot opt source               destination
```

---

### Post by michi1983 on 2015-10-15
okay, so you have ufw enabled.
can you please post the output of
```
sudo ufw status verbose
```
we will see to what level the logging is set.
we will then increase the log level and trace live what happens when you try to connect to the server.

could you meanwhile please also post the output of 
```
sudo ifconfig -a
```
to see how many interfaces you have and if the also need to be considered in the ufw ruleset.

---

### Post by Pocc on 2015-10-15
Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo ufw status verbose:[/FONT][/COLOR]

```
Status: activeLogging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
55516                      ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
55516 (v6)                 ALLOW IN    Anywhere (v6)
22 (v6)                    ALLOW IN    Anywhere (v6)

```

Output of [COLOR=#000000][FONT=Ubuntu Mono]sudo ifconfig -a:
[/FONT][/COLOR]```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:a6:ab:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5710 (5.7 KB)  TX bytes:5710 (5.7 KB)


wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:6a:9f:49  
          inet addr:192.168.0.200  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe6a:9f49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2763122 (2.7 MB)  TX bytes:328765 (328.7 KB)

```

As a side note, it's connected via wifi to the router. It its MAC address tied to static IP 192.168.0.200, so the rules with 22 and 55516 will always point:


Relevant line in router's address reservations:
[TABLE="width: 989"]
[TR]
[TD="class: h1, bgcolor: #66BA33"]Address Reservation[/TD]
[/TR]
[TR]
[TD="class: blue"][/TD]
[/TR]
[TR]
[TD][TABLE="width: 981"]
[TR]
[TD="class: ListTC2"]ID[/TD]
[TD="class: ListTC2"]MAC Address[/TD]
[TD="class: ListTC2"]Reserved IP Address[/TD]
[TD="class: ListTC2"]Status[/TD]
[TD="class: ListTC2"]Modify[/TD]
[/TR]
[TR]
[TD="class: ListC2"]1[/TD]
[TD="class: ListC2"]1C-4B-D6-6A-9F-49[/TD]
[TD="class: ListC2"]192.168.0.200[/TD]
[TD="class: ListC2"]Enabled[/TD]
[TD="class: ListC2"]Modify Delete[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]




Relevant lines in router's forwarding rules (NAT is enabled):

[TABLE="width: 989"]
[TR]
[TD="class: h1, bgcolor: #66BA33, colspan: 3"]Virtual Servers[/TD]
[/TR]
[TR]
[TD="colspan: 3"]**Note:    Make sure the nat is [COLOR=#FF0000]enable[/COLOR] if you want the Virtual Servers configuration take effect**[/TD]
[/TR]
[TR]
[TD="class: blue, colspan: 3"][/TD]
[/TR]
[TR]
[TD="colspan: 3"][TABLE="width: 983"]
[TR]
[TD="class: LISTB"]ID[/TD]
[TD="class: LISTB"]Service Port[/TD]
[TD="class: LISTB"]Internal Port[/TD]
[TD="class: LISTB"]IP Address[/TD]
[TD="class: LISTB"]Protocol[/TD]
[TD="class: LISTB"]Status[/TD]
[TD="class: LISTB"]Modify[/TD]
[/TR]
[TR]
[TD="align: center"]2[/TD]
[TD="align: center"]22[/TD]
[TD="align: center"]22[/TD]
[TD="align: center"]192.168.0.200[/TD]
[TD="align: center"]TCP[/TD]
[TD="align: center"]Enabled[/TD]
[TD="align: center"]Modify Delete[/TD]
[/TR]
[TR]
[TD="align: center"]3[/TD]
[TD="align: center"]55516[/TD]
[TD="align: center"]55516[/TD]
[TD="align: center"]192.168.0.200[/TD]
[TD="align: center"]TCP[/TD]
[TD="align: center"]Enabled[/TD]
[TD="align: center"]Modify Delete[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by michi1983 on 2015-10-16
Alright, could you please try to disable the ufw for testing purpose with
```
sudo ufw disable
```

After this, please backup your iptables rules with
```
iptables-save > /etc/iptables/rules.v4
```

After this, please flush all your iptables rules with the following commands. type in one by one
```

iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -t nat -F
iptables -t mangle -F
iptables -F
iptables -X

```

Now please post again the output of
```
sudo iptables -nvL
```

If the output is exactly or similar to this
```
Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
```

You can try another attempt with sshfs and see if it works.
We will then definitely know that it was a firewall issue (which I think it is)

---

### Post by Pocc on 2015-10-16
ufw is disabled.

Here's the output to 'sudo iptables -nvL':
```
Chain INPUT (policy ACCEPT 52 packets, 4229 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


Chain OUTPUT (policy ACCEPT 24 packets, 1904 bytes)
 pkts bytes target     prot opt in     out     source               destination
```

I changed /etc/ssh/ssd_config by commenting out 'port 22', so that it would be forced to use port 55516. I restarted it and sshed into it, and it works fine with the standard ssh statement with -p 55516. 


```
[COLOR=#000000][FONT=Ubuntu Mono]sudo sshfs -o IdentityFile=/home/me/.ssh/eeePC_key -o allow_other me@[IP ADDRESS]:/home/me /mnt/epic -o sshfs_debug -p 55516
```

[/FONT][/COLOR] still returns "read: Connection reset by peer" when entered on client side.

---

### Post by michi1983 on 2015-10-16
okay, now try to connect again, because now the firewall is totally **open **and nothing should block your attempt.

---

### Post by Pocc on 2015-10-16
sudo ufw status returns 'Status: inactive'. Still get 'read: Connection reset by peer' from above sshfs command.

One other thing to note was that I saved the rules with ```
[COLOR=#000000][FONT=Ubuntu Mono]iptables-save > /etc/iptables/rules.v4[/FONT][/COLOR]
``` to ~ because the folder /etc/iptables didn't exit. 

I'm not seeing this mentioned before, but this system is Ubuntu 14.04.3 server, and I installed the base system and then installed xubuntu with apt-get xubuntu-desktop.

---

### Post by michi1983 on 2015-10-16
Okay, I think we need to clarify something here I guess.

You try to bind a distant machine into your local machine.
So this means, there is a client and a server.

Are these 2 machines in the same local network?
Is your Ubuntu 14.04.3 server the server or the client?
What OS in on the other machine?

Could you maybe draw a little network plan (just with a pen or something) and post it in here, that would make things much more easier.

---

### Post by Pocc on 2015-10-17
Client is 14.04.3 Xubuntu VirtualBox VM on Windows 10 host. Server is eeePC 14.04.3 Xubuntu Server. I tried connecting with sshfs with port with above command from another computer and it worked, so I'm going to call this thread solved.

This must be an issue with the VirtualBox network interface, Windows 10's network interface, and Windows' firewall.

Thank you so much Michi1983 for your help!

---

### Post by michi1983 on 2015-10-17
that's why I asked ;-)
this seems to be a firewall issue on the windows host!

one last thing though:
you now have turned the firewall completely off on your server. you should turn it back on for security reasons and try to figure out which rules need to be adopted they your scenario works flawlessly.

cheers

---

