---
title: "Problem with vpn configuration file"
date: 2022-04-26
forum: Networking &amp; Wireless
---

### Post by RFbD8Xy on 2022-04-26
[COLOR=#31353C][FONT=Arial]Hi, I have a problem with vpn. When I create a file and try to import it shows an error. There are no such problems when importing files from OPENVPN — only from ipfire. My osbuntu 22.04
[/FONT][/COLOR]


[COLOR=#31353C][FONT=Arial][/FONT][/COLOR]

---

### Post by TheFu on 2022-04-26
The error seems clear.  Fix that.
openvpn has an option validation which will look through the config file and say what doesn't work with a specific server. The manpage has more, but says this:```

       --opt-verify
              Clients that connect with  options  that  are  incompatible  with
              those of the server will be disconnected.

              Options that will be compared for compatibility include dev-type,
              link-mtu, tun-mtu, proto, ifconfig, comp-lzo,  fragment,  keydir,
              cipher,   auth,  keysize,  secret,  no-replay,  no-iv,  tls-auth,
              key-method, tls-server, and tls-client.

              This option requires that --disable-occ NOT be used.
...
       --tls-client
              Enable TLS and assume client role during TLS handshake.
```
The server must say --tls-server and the client must say --tls-client in the startup.  I suppose there is a way to have that inside an .ovpn config, but I think multiple options are required to accomplish the same thing that --tls-client on the command line does.

---

