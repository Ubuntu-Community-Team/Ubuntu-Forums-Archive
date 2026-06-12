---
title: "VNC Lubuntu From OutSide Home Network"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by bigpappajohn1984 on 2014-09-13
I have Lubuntu running on my machine.  How can I set up VNC on this machine so that I can VNC into this machine from anywhere with Internet access?  I know my home networks WAN IP and this machine has a static IP so that is not a problem either.  Just not sure how to set things up?

---

### Post by weatherman2 on 2014-09-13
You can do this easily if you don't care about security.  All you have to do is forward port 5900 through your main router/firewall to the IP of your box running Lubuntu.

However, VNC is not secure - only the password is sent securely over the internet.  All other VNC traffic you do is visible to switches and routers your traffic passes over on the internet.

People secure VNC in several ways.  One is to use ssh over VNC (google for "ssh over VNC").  That pushes all the traffic over an encrypted ssh connection.

Another way would be to setup a VPN on your home network or even on the Lubuntu, then connect to your VPN.  Then you can get to any resource on your home network, not just your server.  If you setup the VPN server on your router, not on your Lubuntu box, then you'd also have the ability to connect to your VPN, then wake up the Lubuntu box remotely using Wake-On Lan (WOL).  This is what I do, with OpenVPN.  Get a router for your main home network/firewall that is capable of running OpenVPN - using say DD-WRT or TomatoUSB firmware - and you'd be able to achieve this.

Another approach would be to use some other remote desktop access instead of VNC.  For example, you could use Teamviewer or Google Chrome's remote desktop app (assuming you have Chrome up and running on the Lubuntu box).

---

### Post by bigpappajohn1984 on 2014-09-13
@weatherman2 - I only need to access the files on this server while away from my home.  No need to access any other network resources (as there shouldn't be any other shares, lol).  Thank you for letting me know the data is insecure, I wasn't aware of that.  I will look into the "SSH Over VNC" that you recommend above and see what information I can discover regarding this.


EDIT ---
Does this pretty well describe the SSH over VNC you were referring to?

Also, I will be attempting to VNC the Lubuntu machine from a Windows 7 machine...if that throws any kinks into it.

I use Ultra VNC & VNC on my Windows machine - I think these commands are for Linux machines, can you decipher into a Windows command for me:
```

 ssh -L 12345:localhost:5900 you@1.2.3.4

```

---

### Post by weatherman2 on 2014-09-13
I haven't done this in a long time.  However, here's a tutorial you can try to follow:

[http://lyle.smu.edu/support/contents/index.php/tutorials/49-remote-access/46-tutorialvncwin](http://lyle.smu.edu/support/contents/index.php/tutorials/49-remote-access/46-tutorialvncwin)

FYI, this uses a well-regarded Windows ssh client called Putty to create the ssh tunnel.  

The part left out of this tutorial (because they already assume working Linux machines at the university) is to install ssh (ssh server) on the Lubuntu box so you can connect to it via ssh.  Plus you'll need to install the vncserver.

I'd get this to work first on your local network: first make sure you can connect via ssh from a Windows machine locally to your Lubuntu machine using Putty.  Then, make sure you can connect locally to the vncserver you start via ssh.

To connect from the outside, you're going to open port 22 on your local network and forward it to your Lubuntu machine, then connect via ssh with Putty from the Windows machine, then start the vncserver and create tunnel in Putty as they describe.

---

