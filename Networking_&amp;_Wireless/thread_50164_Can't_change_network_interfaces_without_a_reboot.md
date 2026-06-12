---
title: "Can't change network interfaces without a reboot"
date: 2005-07-19
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-07-19
So the wireless network I have really sucks. It continually goes down, and while I have the option to use the wired ethernet, I prefer just to keep it deconfigured since as of yet, I have found no way around the whole trying to configure both interfaces at boot (so if I am on a wireless network, that gets configured, then I have to sit around for a while while it tries to use eth0, the wired ethernet).

Anyway, when wireless (eth1) goes down, I want to be able to just plug in my ethernet, reenable eth0, and get going. This doesn't work, though. Even if I desable eth1, run /etc/init.d/networking restart, I can't connect to anything. If I try to ping anything, I get "ping: uknown host anything". Similarly, I get host not found errors in Firefox.

Running route shows that everything is setup for eth0, with no eth1 to be found, so that is working properly. But obviously, SOMETHING is not.

Restarting makes everything work, but I absolutely don't want to do this. There is NO reason I should have to restart just to switch interfaces. Any ideas as to what the deal is here?

---

### Post by souki on 2005-07-19
try to stop the network *BEFORE* modifying the interfaces
my guess is that you have a dhclient process running for the first interface

if that does not work, try to ping an ip address to see if it's a resolver issue

---

### Post by Strife on 2005-07-19
I doubt the first possibility is really the problem. If it is, something is not designed very well. Besides, I try stopping and starting so many times that if that were the problem, it would be undone.

It is quite possible it's a resolver issue, but if that is the case, then what can be done about it?

---

### Post by souki on 2005-07-19
well, I don't know, I just talk about my own experience

the /etc/init.d/network script call ifup/ifdown and from the ifdown man page:
>        The  ifup  and  ifdown  commands  may be used to configure (or, respec&#8208;
       tively, deconfigure) network interfaces based on interface  definitions
       in the file /etc/network/interfaces.

this means that, if you remove an interface definition entry *BEFORE* stopping it, it won't be stopped.
I would not say this is a bad design, the network script is just supposed to act based on what is found in the /etc/network/interfaces file

you can check that a dhclient process is running with:
```
ps awx|grep dhclient
```
you can check that what I say is true simply by removing an active entry in /etc/network/interfaces and then stop the network: you will see that the interface will still be active, and, if it is a dynamic interface, you will see a dhclient process still running in the background

---

### Post by gruepig on 2005-07-19
[QUOTE=Strife]It is quite possible it's a resolver issue, but if that is the case, then what can be done about it?[/QUOTE]

It sounds like a resolver (DNS) issue.

What are you using for DNS servers?  You can find (or edit) your DNS servers in the file /etc/resolv.conf or through the Network settings program in Gnome.  (To view the contents of /etc/resolv.conf, run 'cat /etc/resolv.conf' at the command line.)

From the command line, you should be able to lookup hostnames/IPs using the standard Unix/Linux DNS utilities nslookup, host, dig, etc.  Try 'host www.google.com'.  If you get back a response, you have working DNS.  If not, you should get an error.  (Alternately, you can see whether your problem is a DNS resolution problem by pinging an IP  address.)

You'll want to make sure you are using the correct DNS servers.  If you are getting your IP settings by DHCP, most likely you should be getting your DNS servers by DHCP as well.  If you are not able to get your DNS servers by DHCP, you can enter them manually either by editing /etc/resolv.conf or through the Network settings program.

---

### Post by Strife on 2005-07-20
First off, I did try explicitly to disable eth1 first. That did not help.

So it looks like it's a DNS issue (I pinged an IP, and got an "operation not permitted" error instead of a "host not found" error... Usually I have to authenticate with the network first, which obviously I can't do without being able to connect to the host). What I don't understand is this though: Why is it that setting up the nameservers doesn't work when I switch interfaces, but it does when I reboot?

That is what makes no sense to me.

---

### Post by souki on 2005-07-20
that why I was mentionning the dhclient problem: if there is a dhclient running in the background you will keep the previous resolv.conf

to avoid this, you should stop the network first, then change your settings, then start the network again

sorry to repeat that, but did you try ? did you check there is no dhclient running?

---

### Post by gruepig on 2005-07-20
One other thing to check ... did you configure a firewall?  (Run 'iptables -L' to view firewall rules.)

---

### Post by Strife on 2005-07-22
I tried stopping the network and then restarting it. That did nothing. The last time I checked, I had forgotten to see if there was a dhclient running, so I'll try that.

But that leads to the next obvious question, why are dhclient processes not killed when running /etc/init.d/networking stop? That would seem to make the most sense to me if this is what is causing the problem.

gruepig - I'm not sure what having a firewall would have to do with this. I have firestarter to configure the firewall for me, and it is setup only to protect eth1 (wireless). It doesn't even touch eth0.

---

### Post by Strife on 2005-07-23
All right, it's official. It just plain doesn't work.

Stopping the network before bringing up eth0 doesn't work. There is no leftover dhclient process running. The only thing I can do to get DNS working when switching the interface is to restart.

There has to be something else I can do!

---

### Post by gruepig on 2005-07-24
The reason I asked about a firewall was to rule out one more variable (especially if it was the cause of the "operation not permitted" error).

Are you sure you are having a DNS problem?  That is, can you ping hosts and/or access services by IP address?

If everything works except DNS, it sounds like a matter of the DNS servers not getting set.  Check the contents of /etc/resolv.conf ('cat /etc/resolv.conf').  Does it change when you change interfaces?  What error do you get when you run 'host www.google.com' (or some other hostname)?

---

### Post by Strife on 2005-07-26
So I got it to work by manually clearing /etc/resolv.conf and then starting eth0. The really strange part? It looks exactly the same both with eth1 and eth0.

And yes, it was definitely a DNS issue. I couldn't really ping IPs either, because I have to web authenticate with the network first, so I would always get "destination unreachable errors" unless I used the hostname, in which case I would get "unkown host" errors.

---

### Post by gruepig on 2005-07-26
Ah.  Glad it works.

---

### Post by Strife on 2005-07-27
Hrmph. I hate inconsistency.

I tried it again, and now I get the DNS issues again. Another (slightly less) odd thing is that when I restarted, both interfaces were working, but I got "host not found" errors. Running sudo ifdown eth0, everything magically worked.

I just don't get it.

---

### Post by JayCnrs on 2005-07-27
Have you tried ifplugd? If not you should give it a try see if it helps with your issue. First you will need to install ifplugd

apt-get install ifplugd

Then you will need to edit a couple of files the first one is, I am assuming you have setup your network interfaces through System-->Administration-->Networking, edit the file /etc/network/interfaces, remove all lines that say auto eth0 and auto eth1.

Next you will need to add the interfaces into the /etc/defaults/ifplugd file add this line:

```
INTERFACES="eth0 eth1"
``` 

Now you can try rebooting your PC, ifplugd should look after your interfaces, you just have to plug in the cable for the wired ethernet or you put in your wireless.

If this doesn't work take a look at the man page **man ifplugd and man ifplugd.conf** 

Let us know if this works for you that way if somebody does a search they know this worked

Good Luck  :smile:

---

### Post by souki on 2005-07-27
I suspect that if you have a dhclient running on eth0 then you cannot get a new resolv.conf for the other interface.

ifdown does a clean shutdown of you interface: it kills the running dhclient
I know 3 ways to avoid messing with dhclient processes:

- ifdown eth0
- /etc/init.d/network stop
- killall -9 dhclient

if you comment the eth0 interface and then stop the network, it wont work: the network script does not shut any running interface but only the interfaces described in /etc/network/interfaces (any comment is skipped)

please, check again for running dhclient processes

---

### Post by Strife on 2005-07-28
Jay, I tried ifplugd, and I still get the same issues (although interestingly, running ifplugstatus after I've turned off the wirless card with my laptop's function key, it still says  "eth1: link beat detected"). Seems like an interesting tool, and if I could get this network issue fixed, it would be great.

souki, yes, I have done all of that multiple times already in the appropriate order.

---

### Post by Strife on 2005-08-03
Does no one still have a solution to this problem?

It's very frusterating that everything appears to be working, but when I try to go and connect to, say, google.com, I can't because it can't resolve the hostname... Even though resolv.conf is correct.

Really, there has to be an answer to how I can switch interfaces without restarting, because that's just a pain in the neck.

---

