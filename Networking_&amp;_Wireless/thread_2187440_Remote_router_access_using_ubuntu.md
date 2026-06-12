---
title: "Remote router access using ubuntu"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by conradjgodfrey on 2013-11-12
Hi,

I've just set up an old laptop of mine to run ubuntu, and have installed openSSH on it, and configured it so that I can now SSH into it from anywhere. It is currently sitting at home in my lounge doing not much.

Is it now possible for me to access my home router settings remotely? Like the page you get when you find at 192.168.0.1 when at home normally? Can I setup my new laptop's network settings so that it requests traffic via my old laptop, so I could type 192.168.0.1 into my new laptop, and it would send the request to my old laptop, and then send the result back?

Thanks

---

### Post by Lars Noodén on 2013-11-12
You could SSH into your remote machine and have it forward X11 and then run Firefox (or whatever browser). That would give you access but the display would be on the machine in front of you.

```

ssh -X xx.yy.zz.aa /usr/bin/firefox

```

That's one option. Another would be to run lynx remotely but your router might have javascript or other problems with lynx.

---

### Post by conradjgodfrey on 2013-11-12
Yeh, tried elinks and that didn't work due to javascript, so I imagine lynx wouldn't either. This x11 stuff is working, thanks! Just out of interest, is there anyway that you can just automatically set it to route traffic through your server? like a proxy? or tunnelling or something... I'm just making up terms here

---

### Post by Lars Noodén on 2013-11-12
Using a SOCKS proxy would be more responsive than tunneling X.  You'd connect using ssh, then point your local browser at the proxy.

The option -D will set up a SOCKS proxy.  

```

ssh -D 8081 xx.yy.zz.aa

```

Then in Firefox, go to Edit->Preferences->Advanced->Connection->Manual proxy connection, and set

SOCKS Host: 127.0.0.1, port 8081

As long as the SSH connection is open, the proxy works.  Remember to unset the proxy information in Firefox when you are done or you won't get anything to load.  That's a few more steps to set up and tear  down than just tunneling X.

---

### Post by conradjgodfrey on 2013-11-12
Some minor heresy here, but I'm trying to connect from a windows machine, do you know what the equivalent of the SOCKS thing is in Putty?

---

### Post by Lars Noodén on 2013-11-12
I wouldn't know about Windows.  Putty is available on Ubuntu though and these instructions work with it:

[http://www.adamfowlerit.com/2013/01/05/using-firefox-with-a-putty-ssh-tunnel-as-a-socks-proxy/](http://www.adamfowlerit.com/2013/01/05/using-firefox-with-a-putty-ssh-tunnel-as-a-socks-proxy/)

---

