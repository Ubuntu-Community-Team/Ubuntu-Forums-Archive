---
title: "ssh from the outside into IPv6 address."
date: 2017-06-02
forum: Networking &amp; Wireless
---

### Post by david503 on 2017-06-02
Hello, I'm running ubuntu 16.04 (unity) as my workstation, and this question probably applies to servers just as much.

I'm trying to be able to ssh into this from the outside.  So I just apt-get installed openssh and the service seems to be running fine. 

I have port forwarding configured properly to point port 22 to the right pc (this one) on the lan.  In fact it used to all work fine until my ISP gave me an ipv6 address.

I haven't changed anything in iptables so it's all the 16.04 defaults.
 


This might help:
```

oem@uvo:~/Downloads/vuze$ sudo service ssh status
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2017-06-02 07:29:44 EDT; 1s ago
  Process: 9890 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
 Main PID: 10006 (sshd)
   CGroup: /system.slice/ssh.service
           &#9500;&#9472; 9937 sshd: root [priv]   
           &#9500;&#9472; 9938 sshd: root [net]    
           &#9500;&#9472; 9939 sshd: root [priv]   
           &#9500;&#9472; 9940 sshd: root [net]    
           &#9492;&#9472;10006 /usr/sbin/sshd -D


Jun 02 07:29:44 uvo systemd[1]: Starting OpenBSD Secure Shell server...
Jun 02 07:29:44 uvo sshd[10006]: Server listening on 192.168.1.134 port 22.
Jun 02 07:29:44 uvo systemd[1]: Started OpenBSD Secure Shell server.
Jun 02 07:29:44 uvo sshd[9939]: Failed password for root from 59.45.175.66 port 54281 ssh2
Jun 02 07:29:45 uvo sshd[9937]: Failed password for root from 61.177.172.19 port 8822 ssh2

```


What's interesting to me there is that I have no idea what 59.45.175.66 or 61.177.172.19 are.  If you look at the timestamps- they happened instantly when the service starts.  Neither of those are the ip of the server i'm trying to ssh into from the outside.

So am I just getting the syntax wrong for ipv6?  I googled around for sshing to an IPv6 address but it's like clearly I'm missing something here.

I've tried:

ssh -6 oem@2604:2000:1480:c03d:4ddb:818e:ed2c:7881

returns:
ssh: connect to host 2604:2000:1480:c03d:4ddb:818e:ed2c:7881 port 22: Operation timed out

ssh -6 oem@[2604:2000:1480:c03d:4ddb:818e:ed2c:7881]

returns: ssh: No match

Also I tried changing sshd_config to specify the ListenAddress,

```
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 192.168.1.134
Protocol 2



```
What am I doing wrong?  Thanks,

d

---

### Post by SeijiSensei on 2017-06-02
Maybe someone along the way isn't routing IPv6 packets correctly?  Can you ping the machine from outside at its IPv6 address?  I cannot ping it from my virtual server at Linode:

```
$ ping6 2604:2000:1480:c03d:4ddb:818e:ed2c:7881
PING 2604:2000:1480:c03d:4ddb:818e:ed2c:7881(2604:2000:1480:c03d:4ddb:818e:ed2c:7881) 56 data bytes
^C
--- 2604:2000:1480:c03d:4ddb:818e:ed2c:7881 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9662ms

```

but since I don't use IPv6 I may have something misconfigured.  My server does have an IPv6 address.

---

### Post by david503 on 2017-06-05
Wow this is odd- 

If I go to [https://www.google.com/#q=what's+my+ip](https://www.google.com/#q=what's+my+ip)

If gives a ipv6 address.

but when I go [http://www.whatsmyip.org/](http://www.whatsmyip.org/) it gives me:

98.7.127.38

(which works when I try to ssh in, by the way!)

Why is that happening?

m

---

