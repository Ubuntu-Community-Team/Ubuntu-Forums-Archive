---
title: "Ubuntu 20.04 not using first DNS Server listed, 18.04 however does."
date: 2020-04-23
forum: Networking &amp; Wireless
---

### Post by egandt on 2020-04-23
So I have installed 20.04LTS works, but it is not using the first (internal DNS) first, while 18.04LTS does so.  hence my overrides for testing are being ignored

```

root@ubuntu2004lts:~# nmcli dev show ens33 | grep -i dns
IP4.DNS[1]:                             10.120.25.1
IP4.DNS[2]:                             1.1.1.1
IP4.DNS[3]:                             8.8.4.4
IP4.DNS[4]:                             XXXXXX
IP4.DNS[5]:                             8.8.8.8
IP4.DNS[6]:                             XXXXXX

```
So the first listed DNS is 10.120.25.1

Now this DNs over-rides a number of addressees from external to internal for testing and other reasons.

```

root@ubuntu2004lts:~# nslookup mughi.XXX.XXX 10.120.25.1
Server:         10.120.25.1
Address:        10.120.25.1#53

Non-authoritative answer:
Name:    mughi.XXX.XXX
Address: 10.120.25.62

```

So 10.120.25.1 returns what I want, but running nslookup returns:
```

egandt@ubuntu2004lts:~$ nslookup mughi.XXX.XXX
Server:         127.0.0.53
Address:        127.0.0.53#53

Non-authoritative answer:
Name:   mughi.XXX.XXX
Address: 100.38.XXX.XXX

```

So the external facing IP, which is wrong.  Since 10.120.25.1 is first it should be used and hence resolve an internal IP, but while this works on Windows and Ubuntu 18.04, it is not working on 20.04LTS.  I can not say what DNS it is using by default, but it is not the correct aka first one listed.

Why is 127.0.0.53 not using the first DNS set by the adapter? in this case 10.120.25.1, how do I get it to do so?


```

Link 2 (ens33)
      Current Scopes: DNS                    
DefaultRoute setting: yes                    
       LLMNR setting: yes                    
MulticastDNS setting: no                     
  DNSOverTLS setting: no                     
      DNSSEC setting: no                     
    DNSSEC supported: no                     
  Current DNS Server: 1.1.1.1                
         DNS Servers: 10.120.25.1            
                      1.1.1.1                
                      8.8.4.4                
                      XXX       
                      8.8.8.8                
                      XXX           
          DNS Domain: ~.                     
                      <removed> 

```
So based on "systemd-resolve --status" it is clear that it did not use the first entry but the second which is incorrect, but why is it ignoring/skipping the first entry?

18.04LTS looks the same but the order is correct with 10.120.25.1 showing up first.
```

Link 2 (ens33)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 10.120.25.1
                      1.1.1.1
                      8.8.4.4
                      xxxx
                      8.8.8.8
                      xxxx
          DNS Domain: ~.
                      <removed>


```
Correct server is being used.

ERIC

---

### Post by egandt on 2020-04-23
Tracked down the issue the Network Manager is not fully initialized before the "systemd-resolve" is started, as a result it seems to pick 1.1.1.1, if I restart it after networkmanager is started then it will pick the first IP from the list of DNS servers.   For now I set a rc.local script with a 60 second delay as a hack to ensure it works.

ERIC

---

### Post by egandt on 2020-04-24
New issue to run this on login I need to use sudo, but creating a file in /etc/sudoers.d does not work, but adding a line to /etc/sudoers does, for example:
echo "
egandt ALL = (root) NOPASSWD: /etc/restart_systemd-resolved.sh
" > /etc/sudoers.d/98-restart_resolved.conf
 chmod 0440 /etc/sudoers.d/98-restart_resolved.conf 
the file is never picked up or used, as if it is not present

But simply adding the line:
```

egandt ALL = (root) NOPASSWD: /etc/restart_systemd-resolved.sh

```
right before the #include to /etc/sudoers does work

However the correct way is a new file, it i has the proper format and correct permissions 0440, but it is simply ignored and there is no way to debug well, at least none I've found.  None of this is needed in 18.04LTS something to do with networking in 20.04LTS is a serious pain as it sets the wrong default DNS unless I restart systemd-resolved after I login.

ERIC

ERIC

---

### Post by TheFu on 2020-04-24
Why not just list the internal DNS and nothing else?  Also, you can disable systemd-resolved and simply modify the /etc/resolv.conf file manually to make this solution trivial.

Of course, if the system moves (i.e. is portable/laptop), then some other solution will be needed.

Internally, we have a pi-hole setup, running on an LXD container.  Works well. Seeing plenty of bandwidth to that container and zero performance issues. Other systems only point at the pihole for DNS ... except the laptops which use DHCP reservations and get the Pi-Hole for DNS through DHCP settings when on our network. The Pi-Hole also runs a weenie internal DNS server, so we had to ensure FQDN were included in the records and the search settings in each resolv.conf were set to check local domains then external domains first.  Sometimes it is handy to connect to systems through external ports from inside the LAN.

---

### Post by egandt on 2020-04-24
So it is a laptop, actually more than, one on teh desktop I'd just set a manual list, so in teh end I did this for now, (talk about nasty):

```

echo"
#!/bin/bash
/usr/bin/systemctl restart systemd-resolved
exit 0
" > /etc/restart_systemd-resolved.sh
 chmod +x /etc/restart_systemd-resolved.sh
 
echo "egandt ALL = (root) NOPASSWD: /etc/restart_systemd-resolved.sh
" > /etc/sudoers.d/98-restart_resolved.conf
 chmod 0440 /etc/sudoers.d/98-restart_resolved.conf 
echo "#!/bin/bash
/usr/bin/sleep 30
sudo /etc/restart_systemd-resolved.sh" > /home/egandt/restart_systemd-resolved.sh
 chown egandt:egandt /home/egandt/restart_systemd-resolved.sh
 chmod +x /home/egandt/restart_systemd-resolved.sh
reboot

```

However it is working and switching the DNS properly I then trigger it on login.

---

### Post by TheFu on 2020-04-24
Seems like a hack.

In the old days, we'd use use a post-up section of the interfaces file to restart the resolver code and be done.  There has to be a more elegant way. 

Some googling ... 
[https://unix.stackexchange.com/questions/442598/how-to-configure-systemd-resolved-and-systemd-networkd-to-use-local-dns-server-f](https://unix.stackexchange.com/questions/442598/how-to-configure-systemd-resolved-and-systemd-networkd-to-use-local-dns-server-f) 
Is it possible the nsswitch.conf doesn't have the correct order?  *files resolve dns*?

I don't see the need to touch anything related to sudoers. I'm probably missing some very important aspect.
I don't use network-manager.  It is the 2nd thing I purge from my systems, after nano.  ;)

---

