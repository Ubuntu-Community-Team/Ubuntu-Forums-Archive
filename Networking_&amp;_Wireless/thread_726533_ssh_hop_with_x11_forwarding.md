---
title: "ssh hop with x11 forwarding"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by cnschulz on 2008-03-16
Gday, 

Ive got ssh tunelling working on my home network so i can use x apps on my windows box via a gutsy workstation. cool.

the main goal of this is to allow access from outside the home network...

windows box ==> SSH ==> internet ==> gutsy server ==> ??? ==> gutsy workstation.

i need to fill in the "???" bit!

basically what i think i need to do is ssh tunnel *twice*...(is this called an ssh "hop"?) Iive tries a few different settings but none have worked.

the gutsy server is the only machine i can access from the internet so i *must* go through that one... i can do a normal ssh to the workstation fine.

any suggestions? is this possible?

:)

---

### Post by croto on 2008-03-16
What you're trying to do is perfectly possible. But there's something I still don't understand... When you say you want to run X apps on your windows computer, do you mean that you have X11 running on your windows computer (the one that comes with cygwin for example), or you're using something like VNC?

Depending on what you're doing, the solution is different. Also could you please post the commands you're using to get the tunnel working?

---

### Post by cnschulz on 2008-03-16
sure...

i have X running on my windows machine (XMing)

from my home network i run putty with X11 forwarding turned on and log in.

then i can (for example) run "firefox &" from the terminal and firefox runs on my windows cliend under X.

when im with the same laptop but away from my home network... the only way in is via my gutsy headless (no X) server

i putty in the same way with X11 forwarding... then from that machine i issue

"ssh -Y 192.168.1.51" and log in as the same user in step 1.

i have tries setting the DISPLAY variable to many different things... localhost:10.0, <my internet ip address>10.0, 0.0 etc

ive also tried the same "hop" while on my home network just to see if NAT was an issue but it still didnt work.

so im stuck at what to supply for the second ssh and/or display variable.

cheers

c.

---

### Post by croto on 2008-03-16
It looks like the problem may be in the ssh from your windows computer (out of the home lan). You should be able to run X11 apps from your headless server. So you could try this as a test: log in to your headless server from out of the lan, and see if you can run xterm for instance (I guess it should be installed...). My guess is that it's not going to work, and if that's the case it must be related to the way putty is forwarding X11. Another thing that may be useful, please post the contents if the variables DISPLAY and XAUTHORITY when you log in to your headless server. 

I'm sorry for having you do all these things, I'm just trying to get a diagnosis of the problem...

---

### Post by cnschulz on 2008-03-16
thanks, 

just at the moment i have broken ssh at my home server (im at work) so ill have to wait a few hours to fix it. :(

however, xterm and the like are *not* installed on the headless server... it doesnt have X. it is just a gateway (passthru/server/ web host) box running ubuntu server edition.

so... i think i can eliminate the internet/nat from my problem...

192.168.1.103 (windows XMing)  Putty direct X11 forwarding ==> 192.168.1.15 (ubuntu desktop) ALL OK

192.168.1.103 (windows XMing) Putty X11 forwarding ==> 192.168.1.1 (ubuntu server) ssh -Y ==> 192.168.1.15 (ubuntu desktop)  BROKEN

ill get the other details as soon as i restore ssh.

ta

c.

---

### Post by croto on 2008-03-16
Ok, I'll wait for more details later then. For now, make sure you have enabled X11Forwarding in /etc/ssh/sshd_config in you headless box. There should be a line that looks lik this:

X11Forwarding yes

---

### Post by petesahat on 2008-05-14
Hi. Has anybody found a solution for this?
I'm trying to do the same thing.
WINBOX --ssh--> GATEWAY --ssh--> DESTINATION
The gateway is configured to support X11 forwarding. Putty exports DISPLAY=:0.0 on the winbox. And I've tried to set it on the gateway or keep it empty, .. doesn't work :(
The ouptput on the destination is:
With DISPLAY empty on gateway
```
xclock
Could not find ':' in DISPLAY:
X connection to localhost:10.0 broken (explicit kill or server shutdown).
```

With DISPLAY=:0.0 on gateway
```
xclock
connect /tmp/.X11-unix/X0: No such file or directory
X connection to localhost:10.0 broken (explicit kill or server shutdown).
```

When I'm connecting from the winbox to the destination directly, everything works just fine (through an unbelievably slow VPN-connection)

---

### Post by croto on 2008-05-16
Hi,

for the sake of troubleshooting, let's try the following. Login to the gateway, and post the result of
```

user@gateway:~$ echo $DISPLAY
user@gateway:~$ xclock

```

Then from the gateway, login into DESTINATION with
```

user@gateway:~$ ssh -Y user@destination

```

and in destination try (and please post the output)
```

user@destination:~$ echo $DISPLAY
user@destination:~$ xclock

```

---

