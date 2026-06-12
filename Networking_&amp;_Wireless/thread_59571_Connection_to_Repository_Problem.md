---
title: "Connection to Repository Problem"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by ccm030 on 2005-08-24
First off let me say that I am very new to Linux (Ubuntu). I am trying to load a package (dsniff) using the synaptic package manager onto my ubuntu machine. I have added a repository to the list of repositories. Now listed as repositories are:

CD Ubuntu 5.04 Hoary 
Ubuntu 5.04 Hoary (archive.ubuntu.com/ubuntu/)

My problem is when I try to reload the packages I get an error "407 Proxy Authentication Req'd". I have added the correct proxy info into the preference settings under synaptic manager. I have also set the proxy settings under System->Administration->Network Proxy and included my proxy authentication credentials. 

I am am able to surf the web through the proxy, but the first time I go to an external website I am prompted for a user name and password, then it works. Synaptic never prompts me, so I get the error above.

Anyone have any ideas?
Thanks
ccm030 ](*,)

---

### Post by s_p_a_r_k_y on 2005-08-24
in synaptic, Settings->Preferences then network

---

### Post by cwaldbieser on 2005-08-24
[QUOTE=ccm030]First off let me say that I am very new to Linux (Ubuntu). I am trying to load a package (dsniff) using the synaptic package manager onto my ubuntu machine. I have added a repository to the list of repositories. Now listed as repositories are:

CD Ubuntu 5.04 Hoary 
Ubuntu 5.04 Hoary (archive.ubuntu.com/ubuntu/)

My problem is when I try to reload the packages I get an error "407 Proxy Authentication Req'd". I have added the correct proxy info into the preference settings under synaptic manager. I have also set the proxy settings under System->Administration->Network Proxy and included my proxy authentication credentials. 

I am am able to surf the web through the proxy, but the first time I go to an external website I am prompted for a user name and password, then it works. Synaptic never prompts me, so I get the error above.

Anyone have any ideas?
Thanks
ccm030 ](*,)[/QUOTE]

It helps to know what kind of proxy authentication your proxy is using.  If it is basic authentication, then it is probably something like this:

With no authentication:
```
http://proxy:port
```
With authentication:
```
http://username:password@proxy:port
```

---

### Post by ccm030 on 2005-08-24
cwaldbieser

The proxy asks for a username and password, so I would assume that I should use the second line of code, but where do I put the code? (forgive me, I'm very new to Linux).  Would I put it in the network settings in synaptic or in the Source.list file??

Thanks
ccm030

---

### Post by s_p_a_r_k_y on 2005-08-25
ccm, synaptic uses its own proxy settings not gnome's

enter it in here
in synaptic, Settings->Preferences then network

---

### Post by ccm030 on 2005-08-25
[QUOTE=s_p_a_r_k_y]ccm, synaptic uses its own proxy settings not gnome's

enter it in here
in synaptic, Settings->Preferences then network[/QUOTE]
 Thanks for the help!!! 

That worked great. 
ccm030

---

