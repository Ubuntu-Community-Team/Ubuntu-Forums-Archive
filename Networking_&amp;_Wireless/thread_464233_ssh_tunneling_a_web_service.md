---
title: "ssh tunneling a web service"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by littlephil56 on 2007-06-04
Hello everyone!
I use utorrent a lot to download torrents.Today I tried it's web UI feature and it worked perfectly.I then port forwarded my router and was able to access the web interface as intended.

Now the problem is that it uses basic http digest authentication over http.I read a lot about ssh tunneling and I would like to access utorrent's web UI over an ssh connection.I have never done this kind of a thing before .So,if some one could help me out in setting it up! Any help appreciated. :) 

utorrent's web UI is located at http://<External-ip>:62402/gui/

regards,
phil

---

### Post by jro on 2007-06-04
Check out the -L flag for SSH:
[-L [bind_address:]port:host:hostport]

Make sure utorrent is running on your host machine. Then go to your client machine and issue this command at the command prompt:

ssh -L 62402:localhost:62402 host

Then you should be able to point your browser at localhost:62402 and your utorrent GUI should show up. You can change the second port to what ever you want, then just change the port you connect to locally in your browser.  And, don't for get to change 'host' to what ever your IP or hostname is of the machine you have running utorrent. Let me know if you get that to work.

---

### Post by littlephil56 on 2007-06-04
So ssh tunneling has nothing to do with http ?I mean, even with the current setup as you mentioned ,everything will occur over http but encrypted?utorrent runs all the time and so does it's web UI service.:p

also.what command should I run on my side(host) .Do I have to forward any other ports in my router other than 62402 ?

---

### Post by jro on 2007-06-04
You can essentially forward anything over SSH that uses TCP. I have a Dante socks server on my home machine that I SSH to when I get to work and hook my web browsing and instant messing up to so everything is encrypted.

Just remember that only the port you specify will be forward over SSH. If the web gui to use services on any other port they will most likely 404.

You don't have to run anything else on the host, that is what make SSH port forwarding so cool. All you need is the service you want to forward and and OpenSSH server. The SSH client opens a socket that you connect to that then forwards your request to the host. If you are on a *nix machine remember that only root can open sockets on privileged ports (less than 1023).

Check out the man page on ssh, specifically the section under 'TCP FORWARDING'

---

### Post by littlephil56 on 2007-06-04
Another silly doubt:How am I supposed to run this openssh server that you talk about?Do I have to download something?:(

Also,do I have to port forward any ports other than 62402 ?My friend on IRC tried executing the above command but he couldn't connect to.

PS :Also ,say I get connected via ssh ,will it prompt for a password?
PS2:My IP got changed to 59.93.114.0 .
PS3:I got a dyndns account.Can you suggest some auto ip updater for dyndns on linux ?

---

### Post by jro on 2007-06-05
Well, setting up an ssh server on Ubuntu is cake. Just:

```
apt-get install openssh-server
```

Then you will need to open a port in your firewall (port 22) so you can get to your server. As for the dynamic IP, here is a link to scripts that they list as usable with their service: [http://www.dyndns.com/support/clients/unix.html](http://www.dyndns.com/support/clients/unix.html)

Honestly I don't know anything about the utorrent web gui. So I am not sure if it requires any additional ports to be opened for use, I suspect not.

The SSH session will open normally, you will get a username/password prompt then you will be logged in. You can even use the shell normally while using the tunnel.

Was your friend able to connect to your SSH server, or was there a problem establishing the tunnel?

---

