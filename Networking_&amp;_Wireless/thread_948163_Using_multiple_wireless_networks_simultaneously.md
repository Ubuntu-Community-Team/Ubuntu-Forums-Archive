---
title: "Using multiple wireless networks simultaneously?"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by BrentNewland on 2008-10-14
I've discovered a wireless quirk with Windows, a feature which is very simple and obvious but not supported in any way/shape/form under the latest versions of that OS.

You see, I want to be able to connect wirelessly with a printer (in ad-hoc mode) to print while using a regular network (in infrastructure mode) to access internet. I'm told that while all hardware supports it, there is absolutely no support for that in Windows.

This might not seem to make too much sense (you might be asking why I don't put the printer on the same network that I'm on), but there are lots of scenarios where this is preferred. For example, using public wifi while having a private 802.11 printer, using your work's locked down wifi (that won't let you connect to your printer) and needing to use wireless on the printer, using a cell phone card for internet and wanting to print wirelessly to a printer... well, you get the point.

Is this currently supported via GUI with Ubuntu, or will it be with all the updates in Ibex?

---

### Post by pytheas22 on 2008-10-15
You can definitely do this in Linux if you're willing to hack stuff, but in Hardy there's no easy way to do it without some relatively serious command-line work.

I also read somewhere (can't find the source) that Network Manager in Intrepid is supposed to make it much easier to be connected on multiple interfaces at once, so that might improve things.  But for what you're suggesting (as opposed to simply connecting to more than one wireless network at once in order to get more bandwidth), you would need to figure out a way to route all printer traffic to the appropriate network, and all other traffic to the other one.  I'm not sure if Network Manager will make it easy to do this.  But you can do it on the command line using the 'route' command...

Also, if you only have one wireless card, you will need a wireless driver that would support multiple connections at once; some of the older drivers don't, so that could be another issue.  But the drivers in the new Linux wireless stack should support this, or at least it's on the roadmap.

---

### Post by BrentNewland on 2008-10-15
I figured it would be automatic (since it would be a private IP address it would search for the printer on networks of that type, or keep a list of discovered machines on each network).

Speaking of that, I remember a long time ago when setting up that it was really hard to specify which network to use for internet and which to use for private networks (say I have a cable to my router, I want to use that for internet, and I have a second nic and crossover cable to a computer, and I want to use that to communicate with just that machine, and I have a third wireless connection that I want to use to access my roommate's file server). Has that been improved?

---

### Post by pytheas22 on 2008-10-15
> I figured it would be automatic (since it would be a private IP address it would search for the printer on networks of that type, or keep a list of discovered machines on each network).

This may work automatically--I don't know enough about how networked printing is managed to be able to say.  But I suspect that it would require some work and that you'd have to write a route rule to say something like "all printer traffic (which I guess you could distinguish by port) should pass through this gateway and go to the printer with IP XX.XX.XX.XX on that network; all other traffic should go through the other gateway."  Even though the printer would have its own IP, there's no guarantee that it wouldn't conflict with an IP of a machine on the other network (e.g. they could both have IP 192.168.1.2), so I think you'd really need to route the traffic according to gateway.
> 
Speaking of that, I remember a long time ago when setting up that it was really hard to specify which network to use for internet and which to use for private networks (say I have a cable to my router, I want to use that for internet, and I have a second nic and crossover cable to a computer, and I want to use that to communicate with just that machine, and I have a third wireless connection that I want to use to access my roommate's file server). Has that been improved?

I'm not sure how hard it was a long time ago.  I don't think that this would be particularly difficult now, as long as you're comfortable with the command line and familiar with the 'route' command and other Unix networking utilities.  But as far as I know, there's still no way to do it with a nice GUI, so in that respect it's still difficult.

---

