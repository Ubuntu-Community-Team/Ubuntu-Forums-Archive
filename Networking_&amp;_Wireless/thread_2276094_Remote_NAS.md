---
title: "Remote NAS"
date: 2015-04-30
forum: Networking &amp; Wireless
---

### Post by max94 on 2015-04-30
Hello,

I am wanting to build a NAS that can be accessed from anywhere.

I have looked into using samba and NFS but both are designed for local networks...

NFS doesn't have any sort of password protection so that is definitely off the list. 

Samba does have some password control but is designed for local use (Should I just ignore that?)

Any tips would be greatly appreciated!

Thanks

---

### Post by michi1983 on 2015-04-30
Hi,

*... can be accessed from anywhere* is always a security risk.
I would suggest to set up a VPN connection to the location where your NAS stands and then accessing the NAS.

Or you give ***owncloud ***a chance. I set that up in a VM at home and have my own personal cloudservice.

---

### Post by max94 on 2015-04-30
Oh thank you! I am already using owncloud but I would rather an external harddrive kind of thing than a dropbox kind of thing... if that makes sense :D.

So do you know how I would set up the VPN as a mount?

Thanks

---

### Post by michi1983 on 2015-04-30
Yeah I know what you mean :-)
I am not very sure if that is even possible. All I know is that you would have to first connect to your VPN server at home (from your mobile phone, your laptop or whatever) and then you are "*physically*" connected to your LAN and can access all your network storages you have.

---

