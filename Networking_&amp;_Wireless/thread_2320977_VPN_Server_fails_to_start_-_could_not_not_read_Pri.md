---
title: "VPN Server fails to start - could not not read Private Key password from stdin"
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by May_Masters on 2016-04-19
Hi all,

I recently got a new image for my Raspberry-Pi. I got it flashed to the SD-Card and after the initial config task I installed the openvpn package.
I followed the [instructions]("https://wiki.ubuntuusers.de/OpenVPN/") to setup the server and did: sudo service openvpn restart
To be save I issued a reboot afterwards and when the system was back 'systemctl -status openvpn' shows everything ok 

Now I tried to connect with the Android OpenVPN Client (with the newly created mynetwork.ovpn file) but the connection fails with: Connection Timeout.
So I checked the openvpn server lock and saw:

[B]Mon Apr 18 15:03:53 2016 us=304445 ERROR: could not not read Private Key password from stdin
Mon Apr 18 15:03:53 2016 us=304671 Exiting due to fatal error

[/B]So the VPN server tries to read the private key password from stdin ? 
The previous Pi-Ubuntu didn't had that issue!

How to solve this probelm ?

---

### Post by May_Masters on 2016-04-25
Ok, so I gonna answer my own question.

When this error occures you either have a broken ssl-lib or - more likely - a misconfigured system.
In other word's: the error mentioned above should not appear.

When creating a new Server cert/key, make sure you set no passphase. For running the VPN Tunnel it's not needed anyway. Only for creating more cert's
Make sure the paths to the cert and keyfiles within the server.config ar correct:
```

ca ./easy-rsa2/keys/ca.crt
cert ./easy-rsa2/keys/server.crt
key ./easy-rsa2/keys/server.key    # Diese Datei geheim halten.
dh ./easy-rsa2/keys/dh1024.pem     # Diffie-Hellman-Parameter
```

... sounds profan, but that's what caused my issue ...

And last but not least - take your time and build everything from scratch ! 
CA, server and client cert/keys plus Diffie-Hellman stuff.

---

