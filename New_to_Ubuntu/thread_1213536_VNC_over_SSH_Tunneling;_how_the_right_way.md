---
title: "VNC over SSH Tunneling; how the right way?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by lovswr on 2009-07-14
Ok from reading other threads here I thought I understood this but I don't think I have the slightest clue.


What I am doing now is starting up my putty client on my XP laptop at work & ssh'ing to my ubuntu desktop at home.  I then log in.

Next I fire up tightvnc on that same XP laptop & put in the same ip address that I just ssh'ed to (using session 1) & vnc comes right up.

Now I **thought** that the above was using vnc via the SSH connection, BUT if I remove the port forwarding rule for vnc from my firewall, the above does not work (the ssh rule is still allowed).

That would suggest to me that I am NOT getting the vnc session over the SSH.  Could some kind soul enlighten me on how to get this working?  I would be much abliged.

---

### Post by cybergalvez on 2009-07-14
> **lovswr said:**
> Ok from reading other threads here I thought I understood this but I don't think I have the slightest clue.


What I am doing now is starting up my putty client on my XP laptop at work & ssh'ing to my ubuntu desktop at home.  I then log in.

Next I fire up tightvnc on that same XP laptop & put in the same ip address that I just ssh'ed to (using session 1) & vnc comes right up.

Now I **thought** that the above was using vnc via the SSH connection, BUT if I remove the port forwarding rule for vnc from my firewall, the above does not work (the ssh rule is still allowed).

That would suggest to me that I am NOT getting the vnc session over the SSH.  Could some kind soul enlighten me on how to get this working?  I would be much abliged.


you need to set up a tunnel in putty and then vnc to localhost
take a look at [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi) the site does a nice job explaining it

---

### Post by glennric on 2009-07-14
In order to vnc through ssh you have to set up a tunnel and connect with vnc through that tunnel.  I don't know how to do that with putty, but here is a link for doing that in linux:
[VNC Accessing your PC over the Internet]("https://help.ubuntu.com/community/VNC#Accessing%20your%20PC%20over%20the%20Internet")
In brief:  ssh into the remote host with
```
ssh -L 5900:localhost:5900 user@remote_host
```
Then on the local computer run
```
vncviewer localhost
```

I think that putty has port forwarding (tunneling) capabilities, so you will have to figure this out for putty.  Maybe someone else here can help you.

---

### Post by Hospadar on 2009-07-15
+1 for putty tunnel.  I think that's a good way to do it.  I think it's also possible to have ssh on the server do some kind of port forwarding business for you (basically the same deal as the putty tunnel but set up on the server)

Anywho, I've set up putty tunnels before and it's not bad, that's the route I'd take.

For that matter, how bad do you really need vnc?  If you just need specific applications, it'd be a lot faster and simpler to use X11 forwarding through putty with a windows xserver like xming.

---

### Post by lovswr on 2009-07-15
> **cybergalvez said:**
> you need to set up a tunnel in putty and then vnc to localhost
take a look at [http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi) the site does a nice job explaining it




Ok this works I think.  Even though I followed the instructions at your link, I still had to allow port 5901 through my firewall.  I would think that as long as the SSh 'tunnel' is working, then my firewall would not actually "see" the vnc protocols.  Is that not the case?

---

### Post by lavinog on 2009-07-15
> **lovswr said:**
> Ok this works I think.  Even though I followed the instructions at your link, I still had to allow port 5901 through my firewall.  I would think that as long as the SSh 'tunnel' is working, then my firewall would not actually "see" the vnc protocols.  Is that not the case?

I don't think you did it right if you still had to open a port.

in putty set the source port to something like 9999
and set the destination to ###.###.###.###:5900     The # signs are the network ip address of the remote machine as seen from the ubuntu box. In your case since you are trying to vnc to the ubuntu box, use localhost or 127.0.0.1
after connnecting to the ssh server, run the vnc client and connect to localhost:9999

Use localhost and not the ip address of the remote machine for the vnc connection

Using X11 forwarding is much nicer because you don't have to draw the whole desktop to use one app

---

### Post by thingswelostinthefire on 2009-07-18
In addition, pay attention to this: [http://ubuntuforums.org/showthread.php?p=7635847#post7635847]("http://ubuntuforums.org/showthread.php?p=7635847#post7635847")... that happened to me! :)

---

