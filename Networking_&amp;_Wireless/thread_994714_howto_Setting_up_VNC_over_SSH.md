---
title: "howto Setting up VNC over SSH?"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by odinb on 2008-11-27
At my office we have an SSH-gateway to access our work-LAN.

What I am trying to accomplish is to SSH to the gateway (from my Intrepid machine at home) first, then SSH from there to my work-desktop (also running Intrepid). This I can already do using <ssh -Y "SSH-gateway-IP">, and then same thing again to my desktop <ssh -Y "work-desktop-IP">.

Is it correct to use -Y for this purpose? Any other switch I should use?

How do I now configure the VNC-client to access the desktop on my 
work-machine over this tunnel?

Have configured my work-machine in accordance with this guide to have the VNC-server running on it: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

---

### Post by doas777 on 2008-11-27
well to run vnc tunnelled via ssh, all you need is 
```
vncviewer -via user@sshserver localhost:0
``` 
to access the default ubuntu Remote desktop. 

good luck,
franklin

---

### Post by Waappu on 2008-11-27
Hi

This guide may help you
[https://help.ubuntu.com/community/SSHHowto#Tunneling%20VNC%20connections%20through%20ssh](https://help.ubuntu.com/community/SSHHowto#Tunneling%20VNC%20connections%20through%20ssh)

[http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/](http://ubuntu-tutorials.com/2007/06/12/vnc-over-ssh-securing-the-remote-desktop/)

And e.g. from Google you find lot of more

[http://www.brainonfire.net/2006/08/21/vnc-over-ssh/](http://www.brainonfire.net/2006/08/21/vnc-over-ssh/)

---

### Post by odinb on 2008-11-27
Doing:
odinb@home:~$ vncviewer -via odinb@1x8.85.197.1x5 localhost:0

Gives nothing, it just sits there.

Adding the VNC-port gave this:
odinb@home:~$ vncviewer -via odinb@1x8.85.197.1x5:5901 localhost:0
ssh: Could not resolve hostname 1x8.85.197.1x5:5901: Name or service not known
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:localhost:5900 odinb@1x8.85.197.1x5:5901 sleep 20.

Where 1x8.85.197.1x5 is my work-machine IP (The last machine I ssh to).

What am I doing wrong?

Masked out the IP a bit with x:es....

---

### Post by Waappu on 2008-11-27
Hi

Is SSH port open ?
Is SSH server on target machine running in default port ?

---

### Post by odinb on 2008-11-27
Yes, default SSH-ports used (22), and I am logged in on my work machine via SSH before issuing this command on my home machine.

In the terminal logged into my work machine via SSH, I can ls all directories, and it is the correct machine I am logged into.

Oops, patience gave this:
odinb@home:~$ vncviewer -via odin@1x8.85.197.1x5 localhost:0
ssh: connect to host 1x8.85.197.1x5 port 22: No route to host
vncviewer: Tunneling command failed: /usr/bin/ssh -f -L 5599:localhost:5900 odinb@1x8.85.197.1x5 sleep 20.

---

### Post by Waappu on 2008-11-27
Hi

Well, I'm not so good at this.

But try use small app Gnome SSH tunnel manager to create SSH tunnel between machines. It is quite handy
```
sudo apt-get install gstm
```


Edit: This guide may also help with SSH tunnel
[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

---

### Post by doas777 on 2008-11-27
have you tried dropping the :5901 ? i think it should be 22 anyway, since your tunnelling, but just remove the port and give it another try.

good luck,
franklin

---

### Post by odinb on 2008-12-01
Talked to IT today, and it seems they are not allowing port forwarding over this SSH-tunnel, which in my opinion makes it close to useless.

Thanks for trying to help out though, appreciate it!

---

### Post by HermanAB on 2008-12-01
Well, if SSH works and the distant machine is unmanned (not a training/hand-holding session), then you don't need VNC.

Just use SSH directly:
ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or if you want to be click happy:
ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by odinb on 2009-01-30
Not that I know if anyone cares, but finally got this working in mid December.

Followed this guide to set up Remote desktop using VNC on my work-desktop: [http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

Then I SSH from my home machine (on Intrepid) to the gateway and login:
ssh -Y "SSH-gateway-IP"

Then I SSH from the gateway to the work-desktop (on Intrepid) and login:
ssh -Y "work-desktop-IP"

Then on the work-desktop I start VNC:
vncviewer localhost:1

Voila! The work desktop appears on my home machine!

---

