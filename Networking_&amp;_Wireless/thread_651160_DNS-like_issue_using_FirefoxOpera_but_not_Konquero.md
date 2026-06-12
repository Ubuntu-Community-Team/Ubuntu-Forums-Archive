---
title: "DNS-like issue using Firefox/Opera but not Konqueror"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by james_mcl on 2007-12-27
I am having a rather unusual problem with Gutsy which is not unlike the IPv6 problems some people have reported, and is also similar to a DNS resolution problem. Basically, whenever I try to access any websites in Firefox (and Opera - but for brevity, I'll just present the Firefox error messages here), if I use the site's name, eg [www.bbc.co.uk](www.bbc.co.uk), I get "Server not found" - and it gives me this extremely quickly (in fact, this may have gotten faster since I disabled IPv6, but I can't be sure.) If I use an IP address, sometimes it works (I can access the router at 192.168.0.1, and Google at 216.239.59.104, for instance), but occasionally not (for instance, I did a DNS lookup using my router on metro.co.uk, got 195.234.240.212, entered this into Firefox's address bar, and watched as dailymail.co.uk appeared in Firefox's address bar and the server wasn't found.)

However, Konqueror does not have these problems, Sound Juicer was clearly able to get the data it needed from whichever site it uses when I ripped a CD earlier, Update Manager and Synaptic have no trouble getting the packages, and wget and nslookup were also OK.

I have been googling for people with similar problems, and have tried everything suggested to disable IPv6 (setting network.dns.disableIPv6 to true in Firefox's about:config, replacing the IPv6 line in /etc/modprobe.d/aliases with

alias net-pf-10 ipv6 off
alias net-pf-10 off #ipv6
alias ivp6 off

creating a file, /etc/modprobe.d/bad_list, containing the line alias net-pf-10 off, removing the IPv6 lines from /etc/hosts - I've since put them back, out of desperation - adding blacklist ipv6 to /etc/modprobe.d/blacklist, and if there's anything I've forgotten to mention here I've still probably done it.)

Trying to troubleshoot this as a possible DNS issue, I've added my ISP's DNS server addresses to /etc/resolv.conf and edited /etc/dhcp3/dhclient.conf to make sure they'll stay there, and I've also tried entering them directly into Network Manager.

When I reboot into Windows, I don't have any of these problems in either Firefox or Opera. I have also been using another router (same model - a Netgear DG834N) at a different address via Ethernet, and although I haven't tried that one again yet since setting up wireless, I didn't have any problems there either.

Finally, in case this is relevant, the wireless network I'm using uses WPA2.

So, there you are! Does anyone have any idea what's going on and what I can do about it?

Thanks,

James McLaughlin.

---

### Post by p_quarles on 2007-12-27
I'm curious to know what happens if you try disabling ipv6 from within Firefox itself. Here's how:
1) Type about:config in the address bar
2) In the "filter" input box, type "network.dns.disableIPv6"
3) Change the value to "true." 

You may have to restart Firefox, I can't recall. 

Anyway, I'm not sure that's the issue, since as you say you've already disabled ipv6 lookups at the kernel level. 

As for the address of your router, I think it's possible that you obtained the address of a gateway, and that there are no forwarding settings that would allow people to access your LAN from that gateway.

---

### Post by james_mcl on 2007-12-27
If you take another look at my original posting, you'll see I already did disable IPv6 using Firefox's about:config exactly as you describe.

As for the address of the router, I don't really understand the point you're trying to make there, but as Konqueror isn't having any problems it seems a bit unlikely - could you explain?

---

### Post by p_quarles on 2007-12-27
> **james_mcl said:**
> If you take another look at my original posting, you'll see I already did disable IPv6 using Firefox's about:config exactly as you describe.
Ah, yes, in the middle of the long parenthetical. I see it now.

> As for the address of the router, I don't really understand the point you're trying to make there, but as Konqueror isn't having any problems it seems a bit unlikely - could you explain?
What I mean is that the IP address you claim to have found for your personal router points to the Daily Mail. I tried this with both Firefox and Konqueror, and got the same page both times. The host listing for that address points to [http://www.you.co.uk](http://www.you.co.uk), which is on the same top-level domain as the Daily Mail. 

My assumption was that perhaps you were talking about a router that is somewhere within the co.uk domain, and that when you looked up its IP address, you received the gateway rather than the specific NAT address assigned to that router. Without knowing anything about your setup, or what you were expecting to see when you typed that address into Firefox, this is just a guess.

---

### Post by james_mcl on 2007-12-27
"the IP address you claim to have found for your personal router points to the Daily Mail."

No, the IP address for my router is 192.168.0.1. What I was trying to say is that using my router to do a DNS lookup of metro.co.uk gave me an IP address which, when entered into Firefox's address bar, resolved itself to dailymail.co.uk. The fact that it resolved to dailymail.co.uk instead of metro.co.uk wasn't what surprised me; rather the fact that the IP address I'd typed in automatically resolved itself into a domain name (and then, of course, failed to find the server) when I pressed Enter.

---

### Post by p_quarles on 2007-12-27
Here's my best (sorta wild) guess based on the information you've given: it could be that either your router or your ISP's DNS server are responding too slowly for the defaults present in Opera and Firefox. In my experience, Konqueror takes a bit longer to timeout, so it's possible that it's able to get get the resolved hostname from the server before giving up, where Firefox and Opera are not.

Of course, you also said that Firefox and Opera both work fine in Windows, and while I haven't checked every aspect of their setups, I believe the defaults are very similar for both OSes. This, to me, points to how Ubuntu is handling networking. And, it's an unfortunate fact that some wireless cards see lower performance in Ubuntu than they do in Windows. 

Anyway, one possibility, if you haven't tried it already: in Firefox's about:config page, use these two settings:
```
network.http.proxy.pipelining      true
network.http.pipelining.maxrequests         8
```
If you see a change (for better or worse) after changing those settings, then there might be something to my guess.

Another thing you can do to diagnose the problem: run this in a terminal
```
sudo tcpdump -i eth0 -n
```
where "eth0" is replaced with the actual name of your main interface. This will record network activity while it's running, including attempts at DNS resolution. With this running, browse to a few pages with Firefox or Opera, using domain names rather than IP addresses. The output could point to the problem.

---

### Post by james_mcl on 2007-12-28
Thanks for that last posting - the results were very interesting! Using tcpdump to record network activity on eth1 showed up plenty of activity when I browsed about a bit with Konqueror, but nothing at all when I used it to try to monitor Firefox and Opera. The settings changes in about:config didn't make a difference, but since it looks from the tcpdump experiment like FF and Opera thought there wasn't an Internet connection, I guess that was only to be expected.

Any idea how to proceed from here?

---

### Post by p_quarles on 2007-12-28
> **james_mcl said:**
> Thanks for that last posting - the results were very interesting! Using tcpdump to record network activity on eth1 showed up plenty of activity when I browsed about a bit with Konqueror, but nothing at all when I used it to try to monitor Firefox and Opera. The settings changes in about:config didn't make a difference, but since it looks from the tcpdump experiment like FF and Opera thought there wasn't an Internet connection, I guess that was only to be expected.

Any idea how to proceed from here?
That's pretty puzzling. The output you got suggests that FF and Opera are somehow failing to even attempt to connect to a DNS server (which certainly explains why DNS doesn't work). 

I haven't seen exactly this error before, but I recall someone having a similar DNS problem with the Ubuntu repositories, and part of the issue was that APT was using the localhost as its interface. This had to do with a misconfigured proxy. I'd check to see if there's a similar issue here:
```
sudo tcpdump -i lo -n
```As for how to proceed, I can only say what I'd do in your situation: start scouring about:config in Firefox and look for any potentially related settings. I'd start by searching for DNS and proxy.

---

### Post by james_mcl on 2007-12-28
Thanks p_quarles - I've now been able to work out what was going on and fix the problem! (I also found that button that actually adds to your "Thanks" total, hope you noticed you got another one!) I suspect you'll find the below explanation goes into a bit too much detail, but this is partly for the benefit of anyone else who encounters the same problem:

I tried tcpdump on lo as you suggested, and as before it showed quite a bit of activity for Konqueror but none for Opera or FF. I then did a bit of googling for apt and localhost, which gave me the idea of taking a look in /etc/hosts. I have been using it to block tracking cookies, fake anti-spyware software sites, web bugs etc, so quite a lot of stuff's directed to 127.0.0.1. Usually the file looks a bit like this:

127.0.0.1 localhost

127.0.0.1 thisnastydomain.com
127.0.0.1 [www.thisnastydomain.com](www.thisnastydomain.com)

127.0.0.1 webbug.otherwisereputablesite.co.uk

(etc)

127.0.1.1 name_of_my_laptop

(I deleted the IPv6 entries that would have been here again, btw)

This time, it looked like:

127.0.0.1 localhost thisnastydomain.com [www.thisnastydomain.com](www.thisnastydomain.com) webbug.otherwisereputablesite.co.uk fakesecuritysoftwaresite.biz (etc without any line breaks until)

#
#all the comments I'd had on lines
#beginning with hash signs
#throughout the file

127.0.1.1 name_of_my_laptop

I'd used Network Manager instead of gedit when deleting the IPv6 entries - I'd done that before the problem started because I remembered from a previous Ubuntu Dapper install that IPv6 caused problems, and realised it must have changed the formatting. After I wrote a small C++ program to put the file back the way it was (well, except my comments, it wasn't going to be possible to find where they'd all been and put them back, I just deleted them.) and tried again, all was well! Firefox, Opera, and Konqueror are all online, and I'm thinking about downloading epiphany-browser in case I need another spare.

Thanks again PQ,

James.

---

### Post by p_quarles on 2007-12-28
So it was Network Manager that messed up /etc/hosts ? That's good to know. I'm going to add that to my list of things to look for with similar problems. Glad you got it working.

---

### Post by spicedreams on 2008-02-16
Thanks, that also killed a very vexing problem for me. I had the same trick of a list of ad sites redirected to 127.0.0.1 in my hosts file, and I share the same hosts file (by sneakernet) among all my machines. One one ubuntu machine where I have switched between wireless and wired networking, I must have used the Xubuntu graphical tool to set up the wired network settings, and that must have munged the hosts file as you describe.
So the problem is not limited to one Ubuntu network config tool, but probably exists in the library they all call to read/write the hosts file. It doesn't like multiple lines starting 127.0.0.1 (it probably hates any multiple lines with the same IP address) and tries to merge them, resulting in a single huge line which overflows some buffer in Firefox and Opera.

---

