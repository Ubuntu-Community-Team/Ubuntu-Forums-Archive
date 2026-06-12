---
title: "How to restrict internet data usage when on payed WiFi"
date: 2018-04-25
forum: Networking &amp; Wireless
---

### Post by ward388 on 2018-04-25
Hi,

I want to know how I can (easily) restrict internet data usage by switching on some kind of data saver option.
Sometimes I use WiFi's with a limited data plan. In that case I want to make sure that the minimum amount of data is used (only the data that I use for webbrowsing).

What applications could use (large amounts) of internet data in the background?
How can I monitor internet data usage?
How can I restrict internet data usage when I'm using a WiFi connection with limited data plan?

I'm looking for an as simple and quick option as possible. A system tray widget from where I can switch data restriction on and of by a click of a button and that shows me if data usage restriction is on or off would be ideal! And if the data saver app would remember which WiFi network has limited data plans and would switch on and off automatically, would be even better!!! :D 
Because I don't want to forget to switch off the data saver when I'm on an unlimited WiFi connection. 

Thnx,

Ward

---

### Post by TheFu on 2018-04-25
I have some ideas for how to accomplish what you seek, but they aren't using a GUI and are fairly non-trivial to setup. I couldn't imaging any end-user would be able to accomplish it.
[https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/](https://www.tecmint.com/command-line-tools-to-monitor-linux-performance/) has network monitoring tools.

To limit bandwidth used across the entire system isn't too hard.
* wondershaper
* iptables (limiting and blocking of all ports, in/out, except those used by the specific programs you want)
* tc - traffic control; probably want to use wondershaper instead

For limiting which programs can use the network, you'd want to run them inside some kind of container/sandbox that prevents network access completely.  firejail, with custom settings, or normal lxd/lxc Linux containers can do this.
If you disable automatic things that use networking, like automatic APT updates and upgrades, then those won't abuse your connection.  It would probably be best to setup network monitoring and watch how things are used, when for a few weeks to get an idea of where the effort to restrict network access is most important.  Web browsers, email and backups is where I'd start.

Of course, maybe my google-fu is weak and I missed a took that does exactly what you seek. Hopefully, someone else will post, if that is the case.

---

### Post by ward388 on 2018-04-28
Thnx!
I'm gonna experiment with GUFW (graphical tool instead of iptables).
I hope it works!

---

### Post by ward388 on 2018-04-28
Thnx!
I'm gonna experiment with GUFW (graphical tool instead of iptables).


[LIST]
[*]Install Graphical Uncomplicated Firewall
[*]Created a profile called: Payed
[*]Incomming: deny
[*]Outgoing: reject (you could choose for deny as well)
[*]Add one of the preconfigured rules for everything that doesn't work and you would like to allow internet access, like:
[LIST]
[*]HTTP
[*]HTTPS
[*]And more to follow...
[/LIST]
[/LIST]
 
I hope it works!

---

### Post by TheFu on 2018-04-28
If gufw does what you seek, then I totally misread the question.

---

### Post by ward388 on 2018-04-28
GUFW only allows the traffic that I want to allow, and blocks everything else. So that saves data usage.

With your tools I could make it even better: Not only allowing or denying, but if I allow it also manage how much bandwidth it may use at max.

---

### Post by TheFu on 2018-04-28
But if you allow outbound http/https, then 50 different programs can still suck bandwidth when you only want the current web-browser to have that access.   For example, ubuntu updates happen over http/https. Most webapps that are used today use a REST interface over HTTPS as the protocol.  Every android app that "phones home" goes over https too.  They do this to get around corporate firewalls and corporate proxies.

---

