---
title: "Get Around Lack of Port Forwarding"
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by pgn674 on 2008-02-12
I'm wondering if anyone knows of a way to be able to remote into an unmanned machine behind a router with no port forwarding?

Here's the situation: I'm living in an apartment complex, with basic internet included, through ethernet jacks installed in the walls. Thing is, I'm forced to be on a LAN behind a router that I can not configure. It seems to be more than just a router, but for my situation, saying "router" is accurate enough. It doesn't filter any traffic, it just places me on a LAN with no port forwarding. I don't want to try breaking into the thing, as it's monitored by the ISP, and I don't want to loose what internet I have :)  Oh, and we can get regular internet from a third party ISP by the way, but my roommates and I haven't sprung for the cost yet.

Anyways, I have an Ubuntu desktop in my bedroom. I also have an old Ubuntu Server edition machine on campus near by, with an external IP address (open to the internet). And, I regularly stay on campus with my laptop and wireless coverage. I want to find a way to be able to remote into my machine. An SSH bash shell terminal would be OK, VNC remote desktop would be better. My server on campus is really old and low powered, so I don't think it'd be awesome at acting as a full fledged proxy to facility traffic between my laptop on campus and desktop in the apartment.

So, what I'm thinking of is, set up something on my desktop to periodically check in with my server to see if somebody wants to VNC in. On campus, I will connect to my server using my laptop and tell it I want to VNC into my desktop. My server will then use the connection that my desktop established with my server, and send it over to my laptop. That way, my laptop is directly connecting to my desktop, and I can start the VNC connection. My apartment's router, acting as any normal router should, will keep the connection going, as it knows who on the inside to forward that particular connection's traffic to (my desktop).

I think LogMeIn, Skype, and Direct Connect all do something similar to this. Does anybody know of a free solution that will work for me, either using my own server, or some free service that works on Linux?

---

### Post by sonofusion82 on 2008-02-12
well, there is a linux version of hamachi that could probably help.

however, since u have a server. i might prefer to use OpenVPN.

---

### Post by croto on 2008-02-12
I think this could work. So you have, say, host A behind the router, and host B exposed on the internet. You want to get to port 5900 of host A from somewhere else, say host C.
What I would do is create a ssh tunneling from host A to B:
```

usera@A$ ssh  -R5902:localhost:5900 userb@B

```

That line would create the tunnel: every connection to port 5902 on host B would be forwarded to port 5900 on host A through the ssh connection.

Then from host C you can connect to host A with
```

userc@C$ vncviewer B:5902

```

You could do the same for an ssh connection:

```

usera@A$ ssh -R5910:localhost:22 userb@B

```

and then on C:
```

userc@C$ ssh -p5910 usera@B

```
which would ssh connect to host A.

I guess that should work. I forgot to mention that you have to enable the option "GatewayPorts yes" in /etc/ssh/sshd_config (or wherever it is located) on host B.

EDIT: If you change the sshd config, remember to restart sshd!

---

### Post by pgn674 on 2008-02-12
Thank you, croto, the VNC connection works. It seems kinda slow. It might be because I'm connecting from inside the apartment right now over a router I have, and the connection is going out to my ISP and beyond before bouncing back, thus going through a low bandwidth connection twice. Or, all of the traffic may be going though my very slow server (300MHz Pentium II, 128MiB RAM).

I'm not sure how SSH tunneling works, but if it's currently running all of the VNC data through my server, I imagine it might put a hefty load on it. But, in any case, it is working, so thanks.

Oh, and I didn't know what to restart after editing sshd_config, so I rebooted the machine. I don't have any other services running on it yet (though I will soon), so that works well enough :)

---

### Post by croto on 2008-02-12
Hey I'm glad it worked! You can check if the old server is slowing things down by running "top" in the old server while it's forwarding a vnc session. If the cpu usage goes up to 100%, then that may be the problem. If not, then it may be not enough bandwith, in which case you could try to improve the vnc compression. What vnc server and client are you using?

---

