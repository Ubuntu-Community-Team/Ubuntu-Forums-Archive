---
title: "Cant Ping, Network, Router...despairing..?!?"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by gargl on 2007-08-12
Hello there.
Ive just thought that I solved the problem:
[http://ubuntuforums.org/showthread.php?p=3167921#post3167921](http://ubuntuforums.org/showthread.php?p=3167921#post3167921)

BUT I made a clean reinstall of Kubunut on my Notebook and now I got
the same Problem again...I got NO ideas left :-(


First a brief description of the problem:

My Network:


Notebook(NB).....<->.....DesktopPC(PC)....<->......Router(Internet)
ubunut 7.04..................ubuntu 7.04
..................................eth0 192.168.100.6<---->192.168.100.1
eth0<----------------->eth1 192.168.100.77
eth1 WLan

(Textual: My Notebook is connected via a cross-over cable from eth0 to the
eth1 nic in my Desktop PC. And my Desktop PC is connected via a cable to a Router, which
is connected to the Internet (broadband/DSL))

Problem:
I cant even Ping my PC!!
No MATTER WHAT I try.
Logically I cant use my PC as a router for my NB.

1. It did already worked with that Hardware, so this isn't the issue.
2. If i enter 'ping DesktopPC.local' or 'ping Notebook.local'
I recieve in both cases:
```

ping Notebook.local
PING Notebook.local (192.168.100.111) 56(84) bytes of data
ping: sendmsg: Operation not permitted

```


As you can see, the connection exists (avahi resolves the right IP (111)).

I strongly(!!) assume that avahi is the problem and also possible the solution?!

I tried sooo much  ... I got no ideas left :(.

On the DesktopPC runs dhcp and dnsmasq for automatically configuring the Notebook.


Mb worth to mention:
When it worked, I installed Ubuntu, emerging KDE later.
Now I installed only Kubuntu.

Any suggestions or ideas, plz?!

---

### Post by croto on 2007-08-12
Hi my friend,

As far as I understood, you have two NICs in your desktop computer, right? So it looks like  what you're trying to do is to create a **bridge** between the two interfaces. 
Anyways, let's try to troubleshoot your problem now. Could you please post the output of **ifconfig** and **route -n** in both your desktop and notebook? I guess there's a problem with the routing table.

---

### Post by RandomJoe on 2007-08-12
Unless you set up a bridge, as mentioned above, you need to have a different subnet for the connection between your laptop and PC from the subnet used between PC and router.  (I am assuming you haven't set your subnet masks to anything other than the default - 255.255.255.0 - for this IP range.)

So, if you change the PC to use - say - 192.168.101.77 and the laptop to use 192.168.101.111, they should see each other.  Right now, the desktop is going to try to use whichever port has been set as default route no matter what 192.168.100.x IP you try to connect to.  This is likely eth0, which means no packets will make it to the laptop.

---

### Post by gargl on 2007-08-13
Thank god, someones replying...
@croto
First I think it couldnt be a routing problem, but your assumption gave me a new idea.
I plugged my NB direct to the cable of our router (also using dhcp), and "whoups" the connection was there.
(ping/internet everything works)

Now I also assume that the problem is @myPC (routing) not @myNB am I right?!

Please stay tuned, I try reconfiguring my dhcp stuff, and reporting here my results.
But maybe tomorrow not today.

Anyway, thank you two for your help!!!

---

### Post by gargl on 2007-08-14
Hello there.
To be honest, I m not quite sure if the problem is solved at all, but at the moment I have to work and doesnt have time for configuring stuff.

Anyway what I did:
I went to /etc/dnsmasq.conf and
uncommented following line:
dhcp-range=192.168.100.100,192.168.100.150,255.255.255.0,24h

Now it works, at least when my Notebook is already on and I reboot my PC.
Strange, isnt it?

After that I figured out that I cant ping my router from my PC anymore..:confused:
Well, to be honest, Ive never got so much trouble any Linux version before regarding networking issues.

To set up my dhcp/router I followed these Instructions: (german)
[http://wiki.ubuntuusers.de/Router?highlight=%28router%29](http://wiki.ubuntuusers.de/Router?highlight=%28router%29)
Btw. I replaced the ppp0 Interface with eth0.

Maybe this could be the reason for my connection troubles to my router from my PC, because I think I defined an IPtables rule.

I now installed Firestarter to figure out whats going on there...I think Ill got it soon.
Thanks a lot for your help.

Well at the very last I am really a bit disappointed by (K)Ubuntu.
But thats another story.
One thing thats really really great is the community, and the idea a Linux for human beings, I like it a lot!
Keep on going,
Maybe Im back if I have more time again.
Thanks for your assistance.

---

