---
title: "Ubuntu Vserver as Proxy to connect to home network (avoiding DynDNS)"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by social2 on 2013-11-04
Hi,

i've recently setup a NAS with a webserver in my home network and thought it would be nice to have access to it's content from outside of my home network as well. As the public IP of my router changes over time, I first thought of using some kind of DynDNS service to have a static URL pointing to my home network. But on second thought I came up with the idea of using my vserver (which has a static public ip that is already linked with my own domainname) as some kind of proxy which redirects a user to my home network.
I thought about the following configuration:

user ---my.domain.com/homenetwork----->Vserver (with webserver) redirect according to current ip of homenetwork-----IP-OF-HOMENETWORK:80/webservice---->Home-Network-Router forwards port--->NAS (with webserver) behind router

There are two questions I'm asking myself:

1. Does it even make sense to do this kind of redirection thing
2. assuming my nas runs on linux, what would be the best way to communicate the current IP to the vserver?

regards, janis

---

### Post by urapain on 2013-11-04
Try this script that wiil send you an email each time your external IP changes.

---

### Post by social2 on 2013-11-05
Thank you very much for the script. E-mail is indeed a nice solution but are there any alternatives, probably a solution which involves some kind of authentication. I thought of using scp?

regards, janis

---

