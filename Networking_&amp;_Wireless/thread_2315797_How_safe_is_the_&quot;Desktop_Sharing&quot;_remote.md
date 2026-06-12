---
title: "How safe is the &quot;Desktop Sharing&quot; remote access protocol?"
date: 2016-03-02
forum: Networking &amp; Wireless
---

### Post by lakeshore2985 on 2016-03-02
So how safe is sharing your desktop computer using Ubuntu's default remote access app if only inside a local network? And does it use some kind of encryption for more protection?

---

### Post by newbie-user on 2016-03-02
Desktop sharing uses VNC. Only the username and password used to make the connection are secured, the rest of the session is not. If you trust all your users on the local network, then it's fine to use. Otherwise, you'd be better off security-wise tunneling it over SSH.

---

### Post by Irihapeti on 2016-03-02
If you're using remote desktop within a local network - and here I'm thinking about a LAN at home - you're probably OK. If it's a bigger network, such as a company intranet or something at a dorm, I'd be wary.

Activating remote desktop and using it on the internet is one of the most common ways that I've seen of getting hacked. (The other one is setting up an SSH server with password access.)

---

### Post by lakeshore2985 on 2016-03-02
Thanks. But if it uses VNC protocol, then how come it won't connect via either VNC Viewer or androidVNC for example? All clients from Android of course. Output error reads "authentication mechanism requested cannot be provided by the computer".

---

### Post by lakeshore2985 on 2016-03-11
Up. Anyone?

---

### Post by steeldriver on 2016-03-11
I think what you're seeing is an incompatibility between the type(s) of encryption supported by the vino server and your client - AFAIK the only workaround currently is to disable encryption on the server side, either using the GUI dconf editor or

```

gsettings set org.gnome.Vino require-encryption 'false'

```

See [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1281250](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1281250)

---

### Post by lakeshore2985 on 2016-03-12
> **steeldriver said:**
> I think what you're seeing is an incompatibility between the type(s) of encryption supported by the vino server and your client - AFAIK the only workaround currently is to disable encryption on the server side, either using the GUI dconf editor or

```

gsettings set org.gnome.Vino require-encryption 'false'

```

See [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1281250](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1281250)

Heck, it works now (but unencrypted)...  Thanks for the hint! :D

```
sudo apt-get install dconf-tools
dconf write /org/gnome/desktop/remote-access/require-encryption false
/usr/lib/vino/vino-server --sm-disable start
```

[http://www.bonusbits.com/wiki/KB:Fix_VNC_Desktop_Sharing_on_Ubuntu_Desktop_14.04](http://www.bonusbits.com/wiki/KB:Fix_VNC_Desktop_Sharing_on_Ubuntu_Desktop_14.04)

---

