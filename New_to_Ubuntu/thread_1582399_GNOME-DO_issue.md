---
title: "GNOME-DO issue"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by juil on 2010-09-26
I just added the Gnome-Do's ppa but synpatic doesn't seem to find it. I tried searching for this topic in the forums with no results....


```
skynet@skynet-desktop~ $ [COLOR="Blue"]sudo add-apt-repository ppa:do-core/ppa[/COLOR]
[sudo] password for skynet: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv A5D19FDCAA6ABB440CD3464628A8205077558DD0
gpg: requesting key 77558DD0 from hkp server keyserver.ubuntu.com
gpg: key 77558DD0: public key "Launchpad PPA for GNOME Do Core Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
```


Then i ran:

```
[COLOR="blue"]sudo apt-get update[/COLOR]
```

but it gave me the following error when i reloaded synaptic, as shown in the screenshot. Isn't 'sudo add-apt-repository ppa:do-core/ppa' supposed to also add it to the sources.list? I don't see it there although i do see the key and in the other software tab in software sources.

---

### Post by oldos2er on 2010-09-26
There's no Lucid version of that particular gnome-do ppa, it only goes up to Karmic.

---

### Post by juil on 2010-09-26
I see. I was at the launchpad for Gnome-Do and they said:

> Adding the PPA to Ubuntu 9.10 (Karmic) and later

If you're using the most recent version of Ubuntu (or any version from Ubuntu 9.10 onwards), you can add a PPA to your system with a single line in your terminal.

and so on... well thanks for your reply. Topic solved.

---

