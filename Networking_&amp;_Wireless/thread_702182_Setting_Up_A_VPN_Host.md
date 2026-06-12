---
title: "Setting Up A VPN Host"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Eschguy on 2008-02-20
Alright so I installed Ubuntu 7.10 on an old Dell I got from my old man. I want to turn it into a host server for all my movies, music, etc. That part I can do, but I also want to set it up as a VPN host so I can access it wherever my travels take me, rather than trying to guess what I'll want on the trip.

Thanks!

---

### Post by The Cog on 2008-02-20
I would recommend OpenVPN. 
**sudo apt-get install openvpn**
You will need to read the howto at [http://openvpn.net/](http://openvpn.net/) - it's a litle long winded but just follow the instructions step by step. It's secure, using encryption and X509 certificates, and it works through NAT gateways. You'll need to arrange for your router to pass one UDP port through to your VPN server. It's popular here where I work because it's so reliable and performs well.

---

### Post by mo0on on 2008-02-20
OpenVPN suits best for you I think. It's easy to set up and very safe. You only have to configure a few config files.
I recommend you to use certificates for the authentication it's the most safe way.

---

### Post by Eschguy on 2008-02-20
So I was going through the HOWTO and got to the part where I had to edit the vars, after I edit it and do the ./clean-all it says I haven't defined the KEY_DIR. Thoughts?

---

### Post by Rogers on 2008-02-20
I'm lazy, VPN is  a pain in the neck and if you just want to be able to access your data forward port 22 and use SSH. You can portforward is you must but SSH offers SFTP/SCP.  In regular ubuntu you can "Connect to Server" and login to an SSH server for movies like it's a regular windows share or NFS.

FYI:* I wrestled with open VPN and it's WAY overkill for what your doing. Hamachi is also a good solution...*

It's pretty sweet really, and if you need to access a machine inside the network just use port forwarding and forward port 3389 or forward VNC(5900).  I use SSH internally and externally to use my videos/music internally and externally.  Also, SSH supports a REAL VPN setup with little configuration. [https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN")

**SSH FTW :-)**

---

### Post by The Cog on 2008-02-20
> **Eschguy said:**
> So I was going through the HOWTO and got to the part where I had to edit the vars, after I edit it and do the ./clean-all it says I haven't defined the KEY_DIR. Thoughts?

Sorry, it doesn't do that for me. But is see in the vars script that it sets up the KEY_DIR variable, in this line:
port KEY_CONFIG=$D/openssl.cnf

Maybr you didn't succesfullt execute "**. ./vars**" before "**./clean-all**"? Notice the dot-space-dot before vars.

---

### Post by Eschguy on 2008-02-20
> **Rogers said:**
> 
**SSH FTW :-)**

Would this work if I'm a) On the internet from a different network (for example, campus), and b) From a Windows or Mac?

---

### Post by Eschguy on 2008-02-20
> **The Cog said:**
>  Notice the dot-space-dot before vars.

Yep, I'm a fool, didn't have the space. However, I get this:

```
austin@ServOS:/usr/share/doc/openvpn/examples/easy-rsa$ . ./vars
NOTE: when you run ./clean-all, I will be doing a rm -rf on /usr/share/doc/openvpn/examples/easy-rsa/keys
austin@ServOS:/usr/share/doc/openvpn/examples/easy-rsa$ ./clean-all
mkdir: cannot create directory `/usr/share/doc/openvpn/examples/easy-rsa/keys': Permission denied

```

---

### Post by The Cog on 2008-02-21
Get yourself a root command prompt by opening a console and using the command
**sudo -i**
and try again. Also note the HOWTO's suggestion to copy the easy-rsa folder somewhere else to avoid having it overwritten by later software updates.  (You can do this with a nautilus that you launch from your root command prompt, or by running
**gksudo nautilus**
from a normal prompt.

---

### Post by Eschguy on 2008-02-22
Alright, so I've gone through and generated my Hiffie Hellman parameters. But I get really confused when it comes to the config files. Do you think it's possible to dumb the directions down? Some of this stuff is completely foreign to me.

---

