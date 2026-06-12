---
title: "httptunnel doesn't work"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by NilPointer on 2014-04-15
Hello.


I'm trying to set up a HTTP tunnel to my home server using httptunnel, but it doesn't seem to work. I thought it was problem with network configuration, but later I saw that it doesn't want to work even on localhost.


I set up httptunnel server that way:


```
hts --forward-port localhost:22 80
```


Then I try to connect to it with httptunnel client:


```
htc --forward-port 5000 localhost:80
```


Apparently, if I got it right, now everything sent over localhost:5000 is supposed to go over HTTP tunnel and into SSH server. But when I try:


```
ssh -p 5000 <user>@localhost
```


It first throws this error:


```
ssh_exchange_identification: Connection closed by remote host
```


And after that, both hts and htc silently die, so if I retry - I get a connection refused error, since nothing listens to 5000 anymore:


```
ssh: connect to host localhost port 5000: Connection refused
```

Wonder what's going wrong?

---

### Post by NilPointer on 2014-04-15
Same thing happens on my Raspberry Pi, so I doubt it's broken package, probably I'm just doing something wrong.

---

### Post by NilPointer on 2014-04-17
According to Wireshark, there are only six packets sent over the wire from ssh client to htc, but none of them seem to go to the httptunnel server, after that htc quits.

---

### Post by NilPointer on 2014-04-26
httptunnel doesn't require to be run over proxy, does it? I tried to run it over unrestricted network so far and it doesn't seem to work at all.

---

### Post by NilPointer on 2014-04-28
I've just downloaded and built stable build of httptunnel, but even it doesn't work. Any ideas? I think this should virtually rule out bug as a possibility, so it's likely a wrong configuration on my part.

---

### Post by NilPointer on 2014-04-28
Apparently, when trying to connect, htc spits this into syslog, it appears it couldn't open connection, but I have no idea why.

Apr 28 21:40:01 <user> htc[5983]: http_write_request: write error: Invalid argument
Apr 28 21:40:01 <user> htc[5983]: couldn't open tunnel: Invalid argument
Apr 28 21:40:01 <user> htc[5983]: exit with status = 1

And this happens with 3.3 version

Apr 28 21:45:02 <user> hts[6001]: connection from 127.0.0.1:52575
Apr 28 21:45:02 <user> hts[6001]: connection from 127.0.0.1:52576
Apr 28 21:45:02 <user> htc[6007]: connected to localhost:80
Apr 28 21:45:02 <user> hts[6001]: couldn't connect to localhost:22: Connection refused
Apr 28 21:45:02 <user> hts[6001]: exit with status = 1
Apr 28 21:45:02 <user> htc[6007]: tunnel_in_connect: do_connect() error: Connection refused
Apr 28 21:45:02 <user> htc[6007]: handle_tunnel_input: tunnel_read() error: Connection refused
Apr 28 21:45:02 <user> htc[6007]: tunnel read error: Connection refused
Apr 28 21:45:02 <user> htc[6007]: tunnel_write_data: write error: Connection reset by peer

Apparently, now both htc and hts quit.

---

### Post by NilPointer on 2014-04-28
Case closed. I feel like a real fool for wasting so much time on something so small.

Here's what was the cause of problem - I've limited sshd to listen only on LAN subnet. It doesn't listen to localhost so it was, of course, unreachable. Replacing localhost with machine's own IP on the LAN resolved the issue.

---

### Post by Xiaomeng_Li on 2015-03-03
Hello, how did you solve the problem about "httptunnel couldn't open tunnel" finally?? I'm in trouble with it now!!!

---

### Post by NilPointer on 2015-03-24
[QUOTE=Xiaomeng_Li]Hello, how did you solve the problem about "httptunnel couldn't open tunnel" finally?? I'm in trouble with it now!!![/QUOTE]

Hello! Like I've mentioned, the problem was not with httptunnel. I've just limited ssh to listen from LAN interface only (eth0) and forgot that, so httptunnel (which I've set to connect to localhost) was not able to access the sshd and failed. So, just double-check the service and firewall configuration. And yes, httptunnel only works with TCP services. If you're sure everything works, then those steps should work:

On server:

hts -F <targetip>:<targetport> <listenip>:<listenport>

For example, establishing a connection to ssh on localhost and listening to LAN on port 8080:

hts -F localhost:22 192.168.1.2:8080

On client, do the following:

htc -F <listenport> <serverip>:<serverport>

For example, to start tunnel on port 5000:

htc -F 5000 192.168.1.2:8080

This will make HTC tunnel accessible on client like that:

ssh -p 5000 localhost

And all data will go via tunnel to the server. Hope my post is useful.

---

