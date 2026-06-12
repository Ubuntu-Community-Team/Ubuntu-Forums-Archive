---
title: "Using a Specific Network Interface For Application Through Terminal"
date: 2016-09-30
forum: Networking &amp; Wireless
---

### Post by linux.l0v3r on 2016-09-30
Basically is there a command to force connections through a specific network interface?
Like

terminal>firefox --use-net-inter=eth0

or

terminal>set network-interface=eth0

The problem is I setup a new Ubuntu server with a VPN and had to add another network interface for it.  Now I want to run a media server but the connection doesn't use the default interface because it fails to bind to the port.  So, is there some way that I could force it to use a network interface by launching it with the terminal?

---

### Post by SeijiSensei on 2016-10-01
If I understand what you're asking, and I'll admit it isn't very clear what that is, what you're asking for is usually handled by routing. There is no method to do what you describe.

Try describing more carefully what you're trying to do.  How many network adapters are in the machine?  How are they connected to your network(s)?  When you say "another network interface" do you mean something like tun0 over which the VPN operates?  Or did you add a second network card to the machine?

I especially don't understand the comment about not binding to the port.  Which port on which interface?

Does the machine have a firewall?  If so, is the port in question open, or is the firewall blocking traffic to it? Sometimes a service cannot bind to a port because it is blocked by a firewalling rule.

---

### Post by linux.l0v3r on 2016-10-01
This post is what I was looking for, but I can't get it to work.

[http://superuser.com/questions/271915/route-the-traffic-over-specific-interface-for-a-process-in-linux](http://superuser.com/questions/271915/route-the-traffic-over-specific-interface-for-a-process-in-linux)

It explains what I'm looking for better I think.

---

### Post by SeijiSensei on 2016-10-02
Did you try using the script mentioned at the bottom of that page: [https://gist.github.com/level323/54a921216f0baaa163127d960bfebbf0](https://gist.github.com/level323/54a921216f0baaa163127d960bfebbf0)

It might make things easier.

I haven't used cgroups, so I'm afraid I can't help with this.

---

