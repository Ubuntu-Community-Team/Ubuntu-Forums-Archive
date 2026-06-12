---
title: "ssh tunnel collapsing for EXACTLY two hours constantly?"
date: 2016-12-22
forum: Networking &amp; Wireless
---

### Post by iammaxhailme on 2016-12-22
[COLOR=#111111][FONT=Ubuntu]I run this ssh tunneling script on my remote server (CentOS) in a terminal to get to my home computer (Ubuntu):[/FONT][/COLOR]
while true
do
  ssh -R 49666:localhost:22 (my name@ my home ip) -N
  sleep 15
done
[COLOR=#111111][FONT=Ubuntu]I have it loop (the sleep 15 part) because tunnels collapse occaisonally and when it does, somebody needs to physically be there to start it again. The loop is a workaround, although maybe not a good one...[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then from home, I can ssh to the server by ssh'ing to localhost on port 49666.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Everyone once in a while, though, I randomly just get disconnected for EXACTLY two hours and 15 seconds. I see this in my auth.log:[/FONT][/COLOR]
Accepted publickey from (work ip)
error: bind: Address already in use
error: channel_setup_fwd_listener_tcpip: cannot listen to port: 49666
[COLOR=#111111][FONT=Ubuntu]I was originally thinking that I shouldn't run the SSH -R in a loop, because it'll obviously keep trying to bind to the same port. But the thing is, the above failure happens maybe every 14 hours, not every 15 seconds, as the loop would imply. I suspect that if you try to SSH -R a connection that already exists, it just does nothing?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My next thought was that maybe some other service pops up on port 49666 sometimes and messes up the tunnel, and then when the script tries to bind to it 15 seconds later, it can't because the other service is using it. But I can't figure out what the other service, if it exists, could be. I use netstat, lsof, etc but I never see anything running on that port. I'm not sure if there is a way to see a port's history, or if you can only see things using it while they are active. But I suspect that nothing is trying to use it, but it's possible...[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After I get the "already in use" failure, I can't ssh. But then, every time, EXACTLY two hours and 15 seconds later, I get this:[/FONT][/COLOR]
Accepted publickey from (same work ip)
[COLOR=#111111][FONT=Ubuntu]but without the subsequent failures, and I can ssh as normal again. The amount of time until the next failure seems random, but from the failure until the next re-establishment of the tunnel, it's EXACTLY two hours and 15 seconds. I assume there is some kind of 2 hours cooldown firewall thing, and then the script says to wait 15 seconds, so that adds up to the time. The pattern here makes me think there is some way to config that out. The problem is I have no idea why the "address already in use" thing happens to begin with, and I don't know what side (client or remote server) the two-hour cooldown is happening on. I have pretty much all the default settings on my home computer. I don't have sudo at work (but I can get a sudo to check something for me sometimes) so I don't know what their sshd_config is like, but I imagine there is nothing weird.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Can somebody please help me identify: 1: Why the "address already in use" failure happens and what to do about it? and 2: Why the exact two hour and 15 second gap and what to do about it?

Thanks![/FONT][/COLOR]

---

### Post by TheFu on 2016-12-22
autossh? [https://linux.die.net/man/1/autossh](https://linux.die.net/man/1/autossh)

Some enterprise firewalls will close open ports after a configured period of time.  This clears their state tables and frees resources. Had a C/S program that worked perfectly for a few years, then the firewall team decided to implement a 24 disconnect policy which broke the system.  The software devs didn't implement automatic reconnection logic.

Almost every corporation where I worked, if I had done this and been caught, I would have been fired for bypassing corporate security. Guess your company is more forgiving.  Smaller companies where I worked didn't have the same controls and figured anyone smart enough to do it wouldn't introduce "bad stuff" to the corporate network.

---

### Post by iammaxhailme on 2016-12-22
It's actually a university (I'm a grad student) and if they fired everyone who did this they would lose about half the professors, and nearly all the STEM ones.

---

