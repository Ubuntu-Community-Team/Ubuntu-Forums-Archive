---
title: "SSH local port tunnel"
date: 2019-10-20
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2019-10-20
[B]Not deleting message in case someone else looking for similar answer.

[/B]I think the following works OK;

```
ssh -L port01:localhost:port01 -L port02:localhost:port02 user@remotehost
```

Folks,

I've often set up an ssh tunnel for a secure VNC connection but was wondering; is there a way to tunnel two ports for different services with the same connection or will it have to be two separate but concurrent  connections?

Geffers

---

### Post by SeijiSensei on 2019-10-20
i recommend setting up a static tunnel in OpenVPN instead. Then you can connect securely between the machines on any port.

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by Skaperen on 2019-10-20
ssh *can* do tunnels, BTDT.  but the -L option is "port forwarding", not a tunnel.  read the man page for ssh and look at the -w (lower case) option.  i still prefer and recommend [COLOR=#0000cd][FONT=courier new]_**OpenVPN**_[/FONT][/COLOR] because it can use UDP for tunnels (the best way).  ssh only uses TCP, which means a packet loss stalls the entire tunnel until it recovers.  OTOH, if the remote host is only reachable via SSH and not reachable by IP, then SSH is your only choice.

---

### Post by TheFu on 2019-10-20
Just wanted to add that specific options can be placed in the ~/.ssh/config file for each connection using aliases, so we don't need to have scripts or aliases with different settings (though both are reasonable solutions).  The ssh_config manpage goes into all the possible options and there are many, many, of those.

I use ssh tunnels for very specific needs that only require tcp traffic.  A SOCKS proxy via ssh is a very convenient way to access internal web services on my home network when I'm away.  Quick and easy, provided no DNS is needed unless DNS over HTTPS is being used.

---

