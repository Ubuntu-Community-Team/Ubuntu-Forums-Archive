---
title: "Setting up fully-qualified domain name"
date: 2007-10-10
forum: Networking &amp; Wireless
---

### Post by jon_gunnar on 2007-10-10
Im trying to set up leafnode at my system.Have done it before but to be honest I don't remember what I did to solve this problem.
Anyone who can help out?

```
Leafnode must have a fully-qualified and globally unique domain name,
not just "jon-desktop".
Edit your /etc/hosts file to add a unique, fully qualified domain name.
"localhost.localdomain" or thereabouts will not work;
it's qualified, but not unique.
```

---

### Post by helgman on 2007-10-10
Maybe this can help?

[Fully qualified domain name](http://en.wikipedia.org/wiki/FQDN) (Wikipedia)

The solution is knowing what a FQDN is and the error message you posted. jon-desktop.localdomain would be a FQDN (it really should have a dot after com but it's most often left out) and jon-desktop.home-ip.com, just to give you two examples. Hope this helps.

Good luck!

Regards,
Helgman

---

### Post by jon_gunnar on 2007-10-11
> **helgman said:**
> Maybe this can help?

[Fully qualified domain name](http://en.wikipedia.org/wiki/FQDN) (Wikipedia)

The solution is knowing what a FQDN is and the error message you posted. jon-desktop.localdomain would be a FQDN (it really should have a dot after com but it's most often left out) and jon-desktop.home-ip.com, just to give you two examples. Hope this helps.


I'l guess my question may have been a little unclear. I do know what a FQDN is.
But I have tried most variants in hosts file and still leafnode complains.

Maybe ubuntu uses another file to set the hostname.Have set the hostname file too without any changes.

But thank's a lot for the suggestion.

Jon Gunnar

---

### Post by helgman on 2007-10-11
From [Member leafnode-1.11.6/INSTALL of archive leafnode-1.11.6.tar.gz](http://fresh.t-systems-sfr.com/unix/src/misc/leafnode-1.11.6.tar.gz:a/leafnode-1.11.6/INSTALL).:

> 7.  (as root) If your system does not have a fully qualified domain name
    (Debian default installs belong to this group of systems), edit /etc/hosts
    to add one, for example, if your /etc/hosts has a line

    192.168.0.1 debian

    make that

    192.168.0.1 debian.example.com debian

    IMPORTANT: debian.example.com must be replaced by a real fully qualified
    domain name. Making up host names will cause trouble, like posts being
    discarded at the upstream server, posts being discarded when Message-IDs of
    different postings clash and other troubles. See one of the README-FQDN*
    files for details.

I don't know how leafnode works but maybe you have to match some interface/address set up in leafnode with a corresponding line in the hosts-file?

Regards,
Helgman

---

### Post by jon_gunnar on 2007-10-11
> **helgman said:**
>  

I don't know how leafnode works but maybe you have to match some interface/address set up in leafnode with a corresponding line in the hosts-file?

Regards,
Helgman

I got it working,but now gnus refuse to connect.Will have to look at this later.
But thanks for you're time and suggestions.

Jon Gunnar

---

### Post by andrew.46 on 2007-11-02
Hi,

 For ubuntu you need to modify the /etc/hosts file  and set IP Address, Hostname.Domain and then Alias in that order. Use ifconfig to find your IP address. An example is:

```
182.188.1.65  troy.invalid  troy
```

 I use .invalid myself as part of a legitimate fqdm.

               Andrew

---

