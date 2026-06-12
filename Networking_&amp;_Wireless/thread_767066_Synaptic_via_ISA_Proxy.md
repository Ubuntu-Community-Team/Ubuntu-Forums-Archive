---
title: "Synaptic via ISA Proxy"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by pgmmike on 2008-04-25
Good afternoon,

I've recently setup an a system with 8.04 and have been having some difficulties trying to get synaptic through our ISA proxy.

I've added http_proxy to my environment and have configured firefox to authenticate through the proxy and have managed to get both working correctly.

When attempting to configure synaptic however it appears that the credentials are only partially being passed along.
Upon trying to refresh the repositories my NT account gets locked out. The odd thing is that the proxy logs show this connection attempt as coming from 'anonymous'.

Clearly it wasn't an anonymous attemp if it was able to lockout my NT account...

In any case, I've checked the uname/pass many times and can safely say that this isn't a case of bad typing.

Configs I've tried include the GUI config within synaptic as well as adding 01proxy file in /etc/apt/apt.conf/ with the following contents.
Acquire::http::Proxy "http://username:password@proxyFQDN:proxyPort";

Has anyone else had a problem with synaptic's proxy config locking out the NT account used in the config?

---

### Post by barts2108 on 2008-06-10
Same thing here. Ubuntu 8.04 LTS. Firefox works through proxy, Add/Remove programs and/or Synaptic.... no way to get it work not with NTLMAPS, nor with manual configurations in /etc/apt/apt.conf

---

### Post by MaikoID on 2011-04-06
Same problem here =|. Any one knows the solutions ? I can use Firefox (it ask me about my user and password) but I can't use apt-get or snaptic

---

