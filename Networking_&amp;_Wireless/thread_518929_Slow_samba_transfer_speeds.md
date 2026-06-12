---
title: "Slow samba transfer speeds"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by jd65pl on 2007-08-06
I have already posted this question to the beginners forum but I've not had any useful answers as I think it is out of the scope of that forum. [URL="http://ubuntuforums.org/showthread.php?t=508408"]Link to original thread. 
[/URL]
I have a file server and an apache web server running on the same machine. When I transfer files via http the data rate is good (6000kbs +) however when transfering files through samba the data rate is appalling (90kbs). The same file is transfered in both cases. Both were going slow until I forced the card to 100T full duplex using ethtool.

Anyone know how I can fix this or what is causing the problem?

Thanks

J

---

### Post by jnorth on 2007-08-06
> **jd65pl said:**
> I have already posted this question to the beginners forum but I've not had any useful answers as I think it is out of the scope of that forum. [URL="http://ubuntuforums.org/showthread.php?t=508408"]Link to original thread. 
[/URL]
I have a file server and an apache web server running on the same machine. When I transfer files via http the data rate is good (6000kbs +) however when transfering files through samba the data rate is appalling (90kbs). The same file is transfered in both cases. Both were going slow until I forced the card to 100T full duplex using ethtool.

Anyone know how I can fix this or what is causing the problem?

Thanks

J

Been there before.  There's a good chance it can be fixed with your config options.

I would recommend posting your smb.conf here so people can take a look.

Other things - try adding this to your smb.conf file also, somewhere near the top in the global section.
```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```

Restart samba and see if that helps.
```
sudo /etc/init.d/samba restart
```

Also, let us know if you have multiple network interfaces - you may need to specifically identify it in the conf.

Edit - just read your original post - I see why you made a new one :)

---

### Post by sfarber53 on 2007-08-06
I wish I had an answer for you.  I guess I'm writing to provide moral support.

My Feisty box has a similar setup and transfers 4.35 GB in under an hour on a 100 base-T LAN which seems to be pretty fast to me.  Are you certain that you have all of the parameters for Samba defined correctly?

Cheers!

Steve

---

### Post by Nythain on 2007-08-07
im starting to think we arent going to get any help in this department.
maybe we can troubleshoot things we've each tried.
first my specs:
Ubuntu Box (The Server)
     Linksys Wireless G PCI Adapter WMP54G ver 4.1
XP Machine
     Linksys Wireless G USB Adapter WUSB54GC ver unknown
Router
     Linksys Wireless G Router WRT54G ver 8.0

i would like to mention that the problem also occured with a different setup, not sure of all the model numbers but it consisted of
Ubuntu Box
     Davicom 10/100 Wired Ethernet Adapter
XP Machine
     Onboard Wireless Adapter (not sure of make or model since its not here right now
Router was the same (Though the problem DIDNT occur before switching to a wireless router and the xp machine going wireless)

And now the Problem... horribly slow and inconsistant speeds... i mean it fluctuates between 0 and 600k via Samba. Everything else is great, just not samba.

Now my smb.conf (full of just about every tweak i could find, some adding a little stability and some not making any difference at all)
```

[global]
netbios name = SWINEBOX
workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

security = share
restrict anonymous = no
domain master = yes
preferred master = yes
os level = 35
name resolve order = hosts wins bcast

wins support = yes

[stuff]
case sensitive = no
guest ok = yes
path = /data/
read only = no
available = yes
share modes = yes
locking = yes

```

A few other solutions i've tried were
Upgrade or buy different hardware - well as you can see i have bought TWO new Wireless Adapters, one for Ubuntu machine AND one for the xp machine
Install correct Drivers - Currently working on this one... the router is at the latest firmware release now 8.0.2 or whatever... the XP machine is using the latest drivers i could find for its adapter... Ubuntu machine is a bit trickier since im STILL trying to figure out if i need the RT2500 or the RT61 drivers since lspc -v says both like this RT2561/RT61

Hope some of that helps you (mostly the smb.conf... not sure how many edits you have in yours)
Like i said, some of it has helped a little bit, but most of it had no impact on the actuall problem yet

---

### Post by noob12 on 2007-08-07
My guess is that you are seeing this with Samba transfers in Nautilus or Konqueror.  I still haven't figured that one out.  Have you tried testing with smbget or smbclient?  I see very different behavior with those.

I see the same problem just at 10x scale on my gigabit/jumbo-frame network.   Here smbget runs at 500+mbps, ftp at 700+mbps, while Samba in Nautilus (comparitively) trickles at about 90mbps.  Everything being bumped up a factor of 10 keeps it tolerable, but the ratios sound roughly the same.

If you see the same, you'll conclude like me that isn't server configuration per se, but some oddness in the interaction of the Nautilus Samba client.  Haven't had time to trace this further.

---

### Post by Nythain on 2007-08-07
i dont use nautilus or konqueror... and the problem persists going ubuntu to windows and windows to ubuntu... thanks for the info though, good to know that certain file managers just dont play nice with thier samba plugins

---

### Post by noob12 on 2007-08-07
Ok.  Different problem then.  With the non-gui Samba clients, I get fast transfers 400-500+mbps.

---

