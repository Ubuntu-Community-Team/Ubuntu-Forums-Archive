---
title: "Vpn client problem on ubuntu 20.04 with PEM certificate"
date: 2020-05-10
forum: Networking &amp; Wireless
---

### Post by tuliete on 2020-05-10
I'm using the new versión of UBUNTU, la 20.04, I was using 16.04. With that version  I was using VPN  client with my PEM  and key certificate. With the lclient VPN and the CA certifcate was working ok. But in UBUNTU 20.04 doesn't work. I tried with cisco anyconnect for ubuntu creating the folders:

sudo mkdir /opt/.cisco/certificates/client

sudo mkdir /opt/.cisco/certificates/client/private

sudo mkdir /opt/.cisco/certificates/ca

then I moved my *.pem  certificate inside the folder  /opt/.cisco/certificates/client

and my *.key  certificate on the folder /opt/.cisco/certificates/client/private

also the CA certificate.

I imported the certificates with Firefox.

And still don't work.

Anyone can tell me the solution? Thank you.

---

