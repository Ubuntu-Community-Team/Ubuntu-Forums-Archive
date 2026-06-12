---
title: "Unable to install Cairo comosite manager ?"
date: 2011-06-02
forum: New to Ubuntu
---

### Post by SACHINVD on 2011-06-02
Hi
My pc has some proablem with compiz so its not working.
I am trying to install alternative composite manager Cairo composite manager.

I followed steps given in cairo compmgr website to install it but its not working

Followed steps below.

updated sources.list

```
sudo apt-get update 
```
After above get error 
> 
"GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
"

then tried command
```
sudo apt-get install cairo-compmgr cairo-compmgr-plugins
```
got following output
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cairo-compmgr : Depends: cairo-compmgr-core but it is not going to be installed
 cairo-compmgr-plugins : Depends: libcairo-compmgr0 but it is not going to be installed
                         Depends: libvala0 (>= 0.7.10) but it is not installable
                         Depends: cairo-compmgr-core but it is not going to be installed
E: Broken packages


By looking at list above list I tried following
```
  sudo apt-get install libcairo-compmgr0 
```
output of above is
>  The following packages have unmet dependencies:
 libcairo-compmgr0 : Depends: libvala0 (>= 0.7.10) but it is not installable
E: Broken packages


then i tried to install libcairo-compmgr using synaptic manager and got popup "first fix broken packages".

I install libvala-0.10-0 from synaptic but still problem doesn't solve ?

How do I fix above problem ?

Thanks in advance

---

### Post by SACHINVD on 2011-06-18
Problem solved after manually downloading and installing libvala0 from site [https://launchpad.net/ubuntu/maverick/i386/libvala0/0.8.0-0ubuntu1](https://launchpad.net/ubuntu/maverick/i386/libvala0/0.8.0-0ubuntu1)

---

### Post by Gaygerbil on 2012-12-06
I've been looking for a 64 bit version of this library, can't find it. Oh well. :\

Nvm I'm dumb lol:
[https://launchpad.net/ubuntu/+source/vala/0.8.0-0ubuntu1/+build/1687316](https://launchpad.net/ubuntu/+source/vala/0.8.0-0ubuntu1/+build/1687316)

---

