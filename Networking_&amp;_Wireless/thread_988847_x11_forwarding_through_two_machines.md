---
title: "x11 forwarding through two machines"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by sripplinger on 2008-11-20
I have been ssh'ing from my home machine (ubuntu) to my mac on campus, and then from there to a cluster computer.  When I try to run any programs that require x11 forwarding I am told the program is unable to connect to the x server.  Will I even be able to do this through two machines, the middle one a mac?  Currently I am using both the -X and -Y options in my ssh command.

---

### Post by beren.olvar on 2008-11-21
If the cluster is configured to allow X forwarding through ssh, then the easiest way, I know, is using ssh tunneling, that means you use a ssh session just to map a remote port in your own computer. use it like this:

```

   ssh  -l username -L 7777:cluster.ip.here:22  mac.ip.here  cat -

```

where the username is the one needed to log at mac.ip.here. This will:
log at mac.ip.here
map the cluster address (a subnet ip) at port 22 into 127.0.0.1 (localhost) at port 7777, and will take over your terminal (cat -) so you will have to open a new one.
This is done in order to mantain the connection active between both machines.

so, to access the cluster you have to do

```

   ssh -X -l username -p 7777 127.0.0.1

```
(username for the cluster) in a new terminal.

once logged in, it acts like a direct connection, so X forwarding should be enabled.

to close the session just hit Ctrl-c at the tunnel terminal.

Hope it works.
cheers

(sorry if the explanation is too cumbersome. anyway you should google for ssh tunneling)

---

