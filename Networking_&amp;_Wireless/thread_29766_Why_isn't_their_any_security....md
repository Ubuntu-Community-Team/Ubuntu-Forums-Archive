---
title: "Why isn't their any security..."
date: 2005-04-25
forum: Networking &amp; Wireless
---

### Post by Optimal Aurora on 2005-04-25
I was running kubuntu's hoary and I started to notice some rediculous traffic on my network and it was all aimed at my Kubuntu computer... 

I solved that by going back to fedora core 3 since I had learnt how to use fedora core 1 and 2 at school... I like it for its software firewall.

I want to use kubuntu, but I still haven't seen or found anything along the lines of SE Linux or any thing resembling a firewall. 

I wanted to know what is being done or that I can do to keep these incursions on that kubuntu computer from happening (like firewall, a software firewall) or something.

Thank you
Optimal...

---

### Post by alastair on 2005-04-25
How do you know it was "aimed" at you? Please post some details of the network traffic you saw.

As far as I know, Ubuntu has no network services "open" i.e. listening on external IP's/ports. This makes it pretty safe "out of the box".

I have lots of "network attacks" on my machines all the time - it's the price of being on the internet.

If you want a firewall, then Linux is well served and very secure. Look at something like "firestarter" (GUI based) or Shorewall (config file based).

---

### Post by az on 2005-04-25
If you use kde, you may use guarddog, which is another firewall comfiguration tool.

It would seem to me that Ubuntu is more secure "out-of-the-box" than FC3?  The standard install is much leaner and as Alistair said, there is nothing listening to anything outside by default.  I beleive that Kubuntu follows the same rules.  What did you have installed?

---

### Post by LinuxDev on 2005-04-25
hi,

I'm having the same "problem" here. I installed Kubuntu yesterday and after a couple of hours using it, I saw the LED of my DSL Modem lightening without any raison, so I checked with gkrellm and saw a constant 80 kBytes/s network traffic. I didn't take the time to see if it was upload or download, I tried netstat command but didn't see anything wrong, so I switched my ISP IP and the network traffic stopped.

The only thing I was doing is listen to some music with Amarok (default Audio Player), which sometimes connects to internet to bring back some lyrics, so maybe it's it, I don't know, but it's strange...

So, I'm looking for a network monitoring tool, with GUI and a good GUI firewall. I think I'm gonna install Guarddog.

To precise : my DSL modem is a modem/router, so I don't think I was hacked or something, but I'd like to know what this network traffic was.

If you have basic commands to see network traffic, please let me know.

thanks

---

### Post by alastair on 2005-04-26
If people are worried about network traffic, then take a look at it.

The "tcpdump" program lets you look at all sorts of network packets :

man tcpdump

The program "ethereal" is a front-end GUI to tcpdump and lets you capture network traffic and inspect it. You can see what's travelling where (to and from your network devices).

Both great programs and very useful to set your mind at ease.

---

### Post by LinuxDev on 2005-04-26
Ok, thank you, alastair ;)

---

