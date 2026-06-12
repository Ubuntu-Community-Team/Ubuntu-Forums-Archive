---
title: "the command line list for ubuntu server edition"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by karthik8585 on 2010-09-18
is there any one stop destination for all the ubuntu server commands?? I jus managed to install ubuntu server edition with great difficulty.... 

and i'm also facing the network problem . I'm not able to use internet in ubuntu server,even though there was a complete functioning ethernet cable.

I'm complete newbie in  linux....

Suggestions and comments would be appreciated

---

### Post by candtalan on 2010-09-18
Welcome!

The server guide is available from the basic page
[http://www.ubuntu.com/server](http://www.ubuntu.com/server)

and also a pdf version of a previous release form various places including
[http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CB0QFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2F6.10%2Fpdf%2Fubuntu%2FC%2Fserverguide.pdf&rct=j&q=ubuntu%20server%20guide%20download%20pdf&ei=eKSUTM_FFIGn4AaE9qmQBA&usg=AFQjCNG0910khtLi8Mk6wQCPqH0xki7VPQ&cad=rja](http://www.google.co.uk/url?sa=t&source=web&cd=2&ved=0CB0QFjAB&url=https%3A%2F%2Fhelp.ubuntu.com%2F6.10%2Fpdf%2Fubuntu%2FC%2Fserverguide.pdf&rct=j&q=ubuntu%20server%20guide%20download%20pdf&ei=eKSUTM_FFIGn4AaE9qmQBA&usg=AFQjCNG0910khtLi8Mk6wQCPqH0xki7VPQ&cad=rja)

If I were to start off with the server edition I think I would consider to also install the desktop gui (!) so I could also see what was happening at least to start with....

I would maybe install the package ubuntu-desktop using apt

hth

---

### Post by CharlesA on 2010-09-18
If you aren't able to get to the internet, can you post the output of these commands:

```
ifconfig
```
```
cat /etc/resolv.conf
```


> **candtalan said:**
> If I were to start off with the server edition I think I would consider to also install the desktop gui (!) so I could also see what was happening at least to start with....

I would maybe install the package ubuntu-desktop using apt

There are a [few reasons]("https://help.ubuntu.com/community/ServerGUI") for not using a GUI on a server, but if you really want to install Gnome, then just install Ubuntu Desktop instead of Ubuntu Server. You can set up a server just fine using either one.

---

### Post by nothingspecial on 2010-09-18
> **karthik8585 said:**
>  

and i'm also facing the network problem . I'm not able to use internet in ubuntu server,even though there was a complete functioning ethernet cable.


Hi


```
sudo ifconfig eth0 up
sudo dhclient
```

Will get you connected

```
sudo apt-get update && sudo apt-get upgrade
```

To get yourself updated.

---

