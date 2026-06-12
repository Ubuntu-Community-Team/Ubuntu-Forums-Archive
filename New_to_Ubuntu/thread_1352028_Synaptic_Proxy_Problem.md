---
title: "Synaptic Proxy Problem"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by SyntaxError77 on 2009-12-11
Hi,
 
I am trying to use synaptic package manager by proxy. I have set the http proxy address, port and user/pass in System-->Administration-->Network Proxy.
 
I can browse the web with FireFox, though the user/password request box appears.
 
When I try to update the package list in Synaptic, I get authentication errors in the log?
 
Am I missing something?
 
Thanks
 
Paul
 
PS: Ubuntu version is 9.10 Koala

---

### Post by rustutzman on 2009-12-11
Is it Microsoft's ISA proxy? If it is you need to install ntlmaps. Download the .deb from Ubuntu packages. packages.ubuntu.com and then follow the installation instructions.

edit: Here's a link on one of the US servers:
[http://mirrors.kernel.org/ubuntu/pool/universe/n/ntlmaps/ntlmaps_0.9.9.0.1-10ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/n/ntlmaps/ntlmaps_0.9.9.0.1-10ubuntu1_all.deb)

Russ

---

### Post by ukripper on 2009-12-11
> **SyntaxError77 said:**
> Hi,
 
I am trying to use synaptic package manager by proxy. I have set the http proxy address, port and user/pass in System-->Administration-->Network Proxy.
 
I can browse the web with FireFox, though the user/password request box appears.
 
When I try to update the package list in Synaptic, I get authentication errors in the log?
 
Am I missing something?
 
Thanks
 
Paul
 
PS: Ubuntu version is 9.10 Koala





 go in synaptic, settings-->Preferences-->Network set proxy there

---

### Post by Ivo Jesus on 2009-12-11
Hi,

I'm also having some problems with synaptic and a proxy..  I usually work at my company headquarters and in order to access the web I need to config the proxy on my Ubuntu. And so I did and all as gone ok. But now, I'm at home and I can't seem to be able to make the proxy configuration go away. I've already tried to choose the "direct connection" setting on the network proxy "thingy" but no matter what I do, synaptic keeps trying to access the web through the proxy...

Is this normal?

---

### Post by leonbravo on 2009-12-13
Hi ivo,

I have the same problem. It works only in the configured proxy. I tried removing it, somehow it keeps trying to find the old entry. 

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_AU.bz2)  Could not connect to xxxxxx.xxx.edu.au:80 (130.56.71.50). - connect (113 No route to host)


I tried in console with same results.

Seems a bug to me, which files may content proxy info?? :(




> **Ivo Jesus said:**
> Hi,

I'm also having some problems with synaptic and a proxy..  I usually work at my company headquarters and in order to access the web I need to config the proxy on my Ubuntu. And so I did and all as gone ok. But now, I'm at home and I can't seem to be able to make the proxy configuration go away. I've already tried to choose the "direct connection" setting on the network proxy "thingy" but no matter what I do, synaptic keeps trying to access the web through the proxy...

Is this normal?

---

### Post by SyntaxError77 on 2009-12-14
Hi, thanks for the info on ntlmaps.
 
I installed ntlmaps, and a configuration window appeared asking for server details, username etc. But still no connection.
 
Am I supposed to put the data in ntlmaps and the proxy settings, or just ntlmaps?
 
Also, I cannot bring up the ntlmaps interface anymore. There is no entry for it in the applications/system menu, and sudo/gksu ntlmaps is no good.
 
Thanks

---

### Post by ukripper on 2009-12-14
ok if it doesn't work via GUI you can try below in terminal:

```
export http_proxy=http://username:password@proxy-server:port/
```

and if you don't have username or password for your proxy simply do this
```

export http_proxy=http://proxy-server:port/
```

after this run this comamnd and see if it is using your proxy:
```
sudo apt-get update

```
If any of the above works then you can make it permanent adding it to your .bashrc

---

### Post by rustutzman on 2009-12-15
> **SyntaxError77 said:**
> Hi, thanks for the info on ntlmaps.
 
I installed ntlmaps, and a configuration window appeared asking for server details, username etc. But still no connection.
 
Am I supposed to put the data in ntlmaps and the proxy settings, or just ntlmaps?
 
Also, I cannot bring up the ntlmaps interface anymore. There is no entry for it in the applications/system menu, and sudo/gksu ntlmaps is no good.
 
Thanks

You put your proxy info into the ntlmaps config file, /etc/ntlmaps/server.cfg. Then you set your machine proxy to IP 127.0.0.1 port 5865. Then you can use the Network Proxy Preferences and the "Apply System-Wide" button to switch between proxy and no proxy.

```
gksudo gedit /etc/ntlmaps/server.cfg
```


I had to go into the config file and remove spaces between the colen( : ) and the setting. These are the settings you need to check:
```
PARENT_PROXY:your.proxy.server
PARENT_PROXY_PORT:8080
NT_DOMAIN:yourdomain
USER:domain\username
PASSWORD:XXXXXXX
```

It does store your password as plain open text so if others have access to your computer you might want to let it prompt you for your password.

HTH
Russ

---

### Post by torgrot on 2009-12-15
On the system menu select Synaptic Package Manager Settings Preferences network then enter your proxy information on that tab.  Update Manager uses this proxy info.

torgrot

---

### Post by rustutzman on 2009-12-15
Make sure you're using the "Apply System-Wide" button and then you need to logout and then log back in at a minimum.

Russ

> **leonbravo said:**
> Hi ivo,

I have the same problem. It works only in the configured proxy. I tried removing it, somehow it keeps trying to find the old entry. 

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_AU.bz2)  Could not connect to xxxxxx.xxx.edu.au:80 (130.56.71.50). - connect (113 No route to host)


I tried in console with same results.

Seems a bug to me, which files may content proxy info?? :(

---

### Post by rustutzman on 2009-12-15
> **torgrot said:**
> On the system menu select Synaptic Package Manager Settings Preferences network then enter your proxy information on that tab.  Update Manager uses this proxy info.

torgrot

For some reason this doesn't seem to work with Microsoft's ISA proxy server. The ntlmaps route was the only solution I found that works.

Russ

---

