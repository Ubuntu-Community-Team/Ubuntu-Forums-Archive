---
title: "Requesting General Network Setup Advice for Virtual Lab"
date: 2017-04-12
forum: Networking &amp; Wireless
---

### Post by blogmore on 2017-04-12
Hello,
I am working on a small project, which has various legs.
[There is another thread at the Virtualisation section about this project]("https://ubuntuforums.org/showthread.php?t=2357734").
This new thread is because I would like advice in just the networking part of the setup.

The general network diagram is the following:
[IMG]http://i.imgur.com/tAGcpKw.jpg[/IMG]

My concern here is regarding: DHCP, DNS, and gateway.

I want the machine fw-ubuntu-01 to be the gateway between the internal and external network.

My question: Can I configure the fw-ubuntu-01 machine to act as a DHCP and DNS server?
I have DHCP working for the internal network...
Yet I am running into a problem when I try to the the DNS setup.
From the inside network, if I do:
ping 8.8.8.8  --- it works fine.
yet if I do
ping google.com --- it fails

Here is a [DigitalOcean HowTo on how to setup DNS on an Ubunut 16.04 machine]("https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-private-network-dns-server-on-ubuntu-16-04").

---

### Post by blogmore on 2017-04-13
DNS was setup on the Ubuntu 16.04 server VM (fw-ubuntu-01 in the network diagram above).

From fw-ubuntu-01 I can successfully ping:
ping 8.8.8.8
ping google.com

They both work.

From a machine on the "inside" network, I can only
ping 8.8.8.8  (success)
ping google.com (failure)

What could be going on?
It's like the fw-ubuntu-01 machine is not processing the DNS requests from the inside.


From the fw-ubuntu-01 machine, if we run dig google.com
```
fw-ubuntu-01:/etc/bind$ dig google.com

; <<>> DiG 9.10.3-P4-Ubuntu <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 31563
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4000
;; QUESTION SECTION:
;google.com.                    IN      A


;; ANSWER SECTION:
google.com.             298     IN      A       216.58.219.110


;; Query time: 54 msec
;; SERVER: 192.168.10.3#53(192.168.10.3)
;; WHEN: Thu Apr 13 10:03:22 AST 2017
;; MSG SIZE  rcvd: 55

```

Yet, from one of the internal VMs, if we run dig google.com, it fails with:
```
$ dig google.com

; <<>> DiG 9.10.4-P6-RedHat-9.10.4-4.P6.fc25 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 594
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 1


;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;google.com.                    IN      A


;; Query time: 1 msec
;; SERVER: 192.168.89.1#53(192.168.89.1)
;; WHEN: Thu Apr 13 10:05:00 AST 2017
;; MSG SIZE  rcvd: 39

```

---

### Post by blogmore on 2017-04-13
[Following this installation guide]("https://help.ubuntu.com/lts/serverguide/dns-configuration.html"), and I am stuck in the part that states:
> [COLOR=#333333][FONT=Ubuntu]Now that the zone is setup and resolving names to IP Adresses a [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]*Reverse zone*[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu] is also required.[/FONT][/COLOR]
Yet I am still unable to have the zone **resolving names to IP Addresses**.

Any idea what can be done/checked?

---

### Post by blogmore on 2017-04-13
Running traceroute from a machine on the "inside" network, I get the following:
```
[ipa-server0]$ traceroute 8.8.8.8traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  gateway (192.168.89.1)  0.326 ms  0.269 ms  0.204 ms
 2  192.168.10.1 (192.168.10.1)  0.484 ms  0.569 ms  0.474 ms
 3  12.207.75.55 (12.207.75.55)  1.347 ms  1.288 ms  1.186 ms
^C
[ipa-server0]$ traceroute google.com
google.com: Name or service not known
Cannot handle "host" cmdline arg `google.com' on position 1 (argc 1)
[ipa-server0]$

```

traceroute 8.8.8.8 works fine...
yet
traceroute google.com  fails.

---

### Post by blogmore on 2017-04-13
I believe I found the problem:
I was using "lab.local" as my domain... and apparently, somewhere she doesn't like "local".

So I changed to a made up domain "kkhd1234.com", and it worked fine.
Now I can ping from the fw-ubuntu-01 machine, and from the inside VMs.

---

