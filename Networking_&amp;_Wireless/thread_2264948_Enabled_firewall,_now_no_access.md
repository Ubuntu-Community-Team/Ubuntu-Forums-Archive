---
title: "Enabled firewall, now no access"
date: 2015-02-11
forum: Networking &amp; Wireless
---

### Post by musicweb on 2015-02-11
I enabled the linux firewall, and now the only ports open are 22 and 53.

The rest of the ports say they are "filtered"

How do I get my ports unfiltered so they accept connections? Especially 80.

I've been trying to figure out why our email is not working because when trying to
send a test message, it says "all network protocols are disabled". So I thought enabling the 
firewall would help. Made it worse....

I'm running 14.04 LTS on a Lenovo server.

---

### Post by The Cog on 2015-02-11
Can you explain how you enabled the linux firewall? There are many different ways that would meet that description.

The easiest way to unfilter the ports is to turn the firewall off again.

I don't know about mail servers (and you don't say what software), but I think it's possible that  "all network protocols are disabled" means that the mail server has not been configured correctly - no network protocols have been configured.

---

### Post by musicweb on 2015-02-11
I enabled the linux firewall through the Webmin interface.
I chose "allow all traffic" in the options.
I can get in via SSH. Not sure how to turn the firewall off....

Using the mail software shipped with Ubuntu.... Postfix and Dovecot

---

### Post by musicweb on 2015-02-11
I disabled ufw, and also stopped iptables and ip6tables usin commands from [here]("http://www.cyberciti.biz/faq/ubuntu-start-stop-iptables-service/").

Still no access.....

Results from nmap:

```
Host is up (0.00065s latency).
Not shown: 987 closed ports
PORT      STATE    SERVICE
21/tcp    filtered ftp
22/tcp    open     ssh
23/tcp    filtered telnet
24/tcp    filtered priv-mail
53/tcp    open     domain
80/tcp    filtered http
81/tcp    filtered hosts2-ns
110/tcp   filtered pop3
143/tcp   filtered imap
8080/tcp  open     http-proxy
10000/tcp filtered snet-sensor-mgmt
10001/tcp filtered scp-config
20000/tcp filtered dnp

```

---

### Post by kpatz on 2015-02-11
Post the output of **sudo iptables -n -L**

Are you accessing these services from the internet?  Through a router?  You may need to forward ports there.

---

### Post by musicweb on 2015-02-11
After a while the sites came back up.... not sure why.... unless it takes a while for changes to take affect
when stopping the firewall? My next question would be.... If I enable the firewall again, will I have the same problem?
Going to disable the Linux firewall right now.

Now nmap shows this:

```
Host is up (0.00067s latency).
Not shown: 991 closed ports
PORT      STATE    SERVICE
22/tcp    open     ssh
23/tcp    open     telnet
53/tcp    open     domain
80/tcp    open     http
110/tcp   open     pop3
143/tcp   open     imap
8080/tcp  open     http-proxy
10000/tcp open     snet-sensor-mgmt
10001/tcp filtered scp-config

```

Output from iptables -n -L:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD_IN_ZONES (0 references)
target     prot opt source               destination

Chain FORWARD_IN_ZONES_SOURCE (0 references)
target     prot opt source               destination

Chain FORWARD_OUT_ZONES (0 references)
target     prot opt source               destination

Chain FORWARD_OUT_ZONES_SOURCE (0 references)
target     prot opt source               destination

Chain FORWARD_direct (0 references)
target     prot opt source               destination

Chain FWDI_public (0 references)
target     prot opt source               destination

Chain FWDI_public_allow (0 references)
target     prot opt source               destination

Chain FWDI_public_deny (0 references)
target     prot opt source               destination

Chain FWDI_public_log (0 references)
target     prot opt source               destination

Chain FWDO_external (0 references)
target     prot opt source               destination

Chain FWDO_external_allow (0 references)
target     prot opt source               destination

Chain FWDO_external_deny (0 references)
target     prot opt source               destination

Chain FWDO_external_log (0 references)
target     prot opt source               destination

Chain FWDO_public (0 references)
target     prot opt source               destination

Chain FWDO_public_allow (0 references)
target     prot opt source               destination

Chain FWDO_public_deny (0 references)
target     prot opt source               destination

Chain FWDO_public_log (0 references)
target     prot opt source               destination

Chain INPUT_ZONES (0 references)
target     prot opt source               destination

Chain INPUT_ZONES_SOURCE (0 references)
target     prot opt source               destination

Chain INPUT_direct (0 references)
target     prot opt source               destination

Chain IN_dmz (0 references)
target     prot opt source               destination

Chain IN_dmz_allow (0 references)
target     prot opt source               destination

Chain IN_dmz_deny (0 references)
target     prot opt source               destination

Chain IN_dmz_log (0 references)
target     prot opt source               destination

Chain IN_external (0 references)
target     prot opt source               destination

Chain IN_external_allow (0 references)
target     prot opt source               destination

Chain IN_external_deny (0 references)
target     prot opt source               destination

Chain IN_external_log (0 references)
target     prot opt source               destination

Chain IN_home (0 references)
target     prot opt source               destination

Chain IN_home_allow (0 references)
target     prot opt source               destination

Chain IN_home_deny (0 references)
target     prot opt source               destination

Chain IN_home_log (0 references)
target     prot opt source               destination

Chain IN_internal (0 references)
target     prot opt source               destination

Chain IN_internal_allow (0 references)
target     prot opt source               destination

Chain IN_internal_deny (0 references)
target     prot opt source               destination

Chain IN_internal_log (0 references)
target     prot opt source               destination

Chain IN_public (0 references)
target     prot opt source               destination

Chain IN_public_allow (0 references)
target     prot opt source               destination

Chain IN_public_deny (0 references)
target     prot opt source               destination

Chain IN_public_log (0 references)
target     prot opt source               destination

Chain IN_work (0 references)
target     prot opt source               destination

Chain IN_work_allow (0 references)
target     prot opt source               destination

Chain IN_work_deny (0 references)
target     prot opt source               destination

Chain IN_work_log (0 references)
target     prot opt source               destination

Chain OUTPUT_direct (0 references)
target     prot opt source               destination

```

---

### Post by The Cog on 2015-02-11
It seems that the firewall filters pop3 and imap which are common email ports. Ideally, you should try to find out how to enable those ports in the firewall.

---

### Post by musicweb on 2015-02-11
So after I got all my ports back for some reason, I installed Citadel hoping to
get email that was easier to set up.
Well.... it did the same thing to me again and set most of the ports as "filtered"
and left ports 22, 53, and 8080 open.
Guess I need to do a lot more research on this problem.

---

### Post by musicweb on 2015-02-11
Finally removed the Citadel suite and re-installed Postfix and Dovecot.

Still no access....

Output from nmap:

```
Starting Nmap 6.40 ( http://nmap.org ) at 2015-02-11 19:23 EST
Nmap scan report for wm-mw.org (209.222.239.101)
Host is up (0.00067s latency).
Not shown: 987 closed ports
PORT      STATE    SERVICE
21/tcp    filtered ftp
22/tcp    open     ssh
23/tcp    filtered telnet
24/tcp    filtered priv-mail
53/tcp    open     domain
80/tcp    filtered http
81/tcp    filtered hosts2-ns
110/tcp   filtered pop3
143/tcp   filtered imap
8080/tcp  open     http-proxy
10000/tcp filtered snet-sensor-mgmt
10001/tcp filtered scp-config
20000/tcp filtered dnp

Nmap done: 1 IP address (1 host up) scanned in 93.58 seconds

```

Anyone got any ideas for me on how to fix this?

---

### Post by musicweb on 2015-02-11
Come to find out, and remember, that I also installed firewalld.
After I removed it, all the ports came back.

---

