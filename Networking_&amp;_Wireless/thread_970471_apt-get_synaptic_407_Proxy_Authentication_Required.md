---
title: "apt-get synaptic 407 Proxy Authentication Required"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by robertoaguiarlima on 2008-11-04
Hi!

I have trouble when using apt-get or synaptic package manager. When I type apt-get update, the system show me some messages like: 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  407 Proxy Authentication Required

I already try to configure apt.conf, http_proxy variable, gnome Network Proxy, Synaptic manual proxy configuration and NTLMAPS. I made thats configuration following other threads in this forum. Inside firefox, this configurations run without troubles, including NTLMAPS (with firefox proxy configuration pointing to NTLMAPT).
I am using a Windows proxy that needs authentication in a Domain.

Could someone please help me?

---

### Post by nixscripter on 2008-11-04
I'm afraid I don't know much about proxies, but I would offer a workaround.

If you download the files with Firefox, you can stick them in **/var/cache/apt/archives** and it won't try to fetch them. You can do this with anything aptitude tries to fetch.

---

### Post by stubbz on 2008-11-04
Are you trying to connect through a Microsoft ISA server?  If so, can you or you administrator set your machine up as a securenat client?

---

### Post by Olaf123 on 2008-11-12
If you are in an all MS windows domain I found that NTLMAPS is the only thing that works. However the standard settings as recommended in the /etc/ntlmaps/server.cfg file are not always sufficient because windows 98 compatibility on some networks has been disabled. What works for me (I am using Ubuntu 8.10) is:

(Note the NT support!! I had to edit out all the coments to fit in this window. Leave them in your original file!, Dont forget to set the proxy in Synaptic)

#================================
[GENERAL]

LISTEN_PORT: 5865


PARENT_PROXY: YOUR_PROXY_SERVER
PARENT_PROXY_PORT: YOUR_PROXY_SERVER_PORT

PARENT_PROXY_TIMEOUT:15

ALLOW_EXTERNAL_CLIENTS:0

FRIENDLY_IPS:

URL_LOG:0

MAX_CONNECTION_BACKLOG:5

#=====================================
[CLIENT_HEADER]

# for windows 2000 emulation ;)
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows NT5)

Accept-Encoding: gzip, deflate

#===================================
[NTLM_AUTH]

NT_HOSTNAME: YOUR_WINDOWS_PC_IDENTIFIER

NT_DOMAIN: YOUR_WINDOWS_DOMAIN

USER: YOUR_USER_NAME_ON_NETWORK

PASSWORD: YOUR_PASSWORD

LM_PART:1
NT_PART:1

# Highly experimental option. See research.txt for details.
# LM - 06820000
# NT - 05820000
# LM + NT - 07820000
NTLM_FLAGS: 07820000

NTLM_TO_BASIC:0

#================================
[DEBUG]

DEBUG:0

BIN_DEBUG:0

SCR_DEBUG:0

AUTH_DEBUG:0

---

