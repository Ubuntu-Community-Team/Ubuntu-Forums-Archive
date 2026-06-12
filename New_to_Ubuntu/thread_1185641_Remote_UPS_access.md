---
title: "Remote UPS access"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-06-12
I can get information about how my UPS is acting by starting the software & then going to 127.0.0.1:8080/sms in a browser. There's also a command line utility that lets me work with it.

I think I'd be able to use the command line utility by ssh'ing into the UPS connected computer, then running the utility since it doesn't require me to mess around with addresses.

I'm curious to know how I might get the browser view from another computer. I've kinda figured out 192.168.x.x is for local network, & 127.x.x.x works for local devices (?) but how do I go though 102.168.1.100 to get to 127.0.0.1:8080/sms ?

Thanks,

---

### Post by Hospadar on 2009-06-12
Well you have a couple options:

Run a browser on the remote machine with X11 forwarding (slow)

if you're on the same network as the server, you can probably just point your browser at the ip of the server/sms and see the status, although I think port 8080 may be blocked as it is often used by web servers as their admin page (i.e. not safe to be public)
But give it a try

If it's not blocked, but you need external access, you'll need to forward port 8080 to the server on your router (if you're behind a router) and then point your browser at <external ip of your server>:8080/sms
If you don't know the external ip of the server, try doing "curl checkip.org" while ssh'd in the server, you'll see it in there.

If you don't want to forward 8080 (you shouldn't if you run apache for example) forward port 80 (the standard http port) and then set up a reverse proxy in apache (or whatever) so you can point your browser at the newly proxied location.

Google if you need info on setting up a reverse proxy, it's not too tricky.

---

