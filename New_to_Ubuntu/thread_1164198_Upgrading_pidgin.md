---
title: "Upgrading pidgin"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by M0GEJ on 2009-05-19
I am currently running pidgin 1:2.5.5 and have never been able to get it to work properly (it keeps disconnecting from msn). Anyway, I thought that in the process of trying to fix it I would download the latest version. I have been onto the pidgin website and tried to set up the PPA but could not get this to work. I am not really sure how to install it from source, but think it would be better if I could add it to the repositories list. Anyone able to help?

---

### Post by Tibuda on 2009-05-19
Pidgin last stable version is 2.5.5, so if you want a newer version you have to install from the last unstable development source code. MSN is known to block third-party clients, but if you install the [msn-pecan]("apt:msn-pecan") package you'll get better support.

---

### Post by M0GEJ on 2009-05-19
Ok-probably don't want to do that. Will try and fix it another way then :$

---

### Post by Mornedhel on 2009-05-19
[FONT=Verdana]Add this line to the bottom of /etc/apt/sources.list :

[/FONT]```
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
```

Get the key from here : [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7FB8BEE0A1F196A8](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7FB8BEE0A1F196A8) (copy paste the contents, starting with ------BEGIN PGP PUBLIC KEY BLOCK, into a file that you create, called something.gpg).

Import the key : ```
sudo apt-key add something.gpg
```

Update your cache : ```
sudo apt-get update
```

Upgrade from Pidgin (current Jaunty) to Pidgin (bleeding edge PPA) : ```
sudo apt-get upgrade
```

---

### Post by spcwingo on 2009-05-19
2.5.5 is the latest.  If you would still like to add the ppa just save this as a text file:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXXu9wEEAM2fOLi65x7hpnmDhTelWDSz+2ktpBuaBizVnVrS5clEVW5BfvQQbqzF1rur
gxTf+0y54s+ZIDOX1OIpiaZK9RYIxWq9KuF2urwv4qK3e0AeWYU6b44YPjgFhQ/LEq0QCTuN
/fKpIenTov9P2O66t9d5cQfiAtTB0NogMLiAjXOBABEBAAG0I0xhdW5jaHBhZCBQUEEgZm9y
IFBpZGdpbiBEZXZlbG9wZXJziEYEEhECAAYFAknOAzkACgkQbfU6uV4fG84AJgCgudiLwQbD
+Kur+VdVc8GVMKu15XYAoKzf06cdX4l+RnfTHJ6hj5TQlY9MiLYEEwECACAFAkl17vcCGwMG
CwkIBwMCBBUCCAMEFgIDAQIeAQIXgAAKCRB/uL7gofGWqIi6A/9jDrYXq2wgFjQkCFGH+Nxd
IbGs1O4OKs+AMe2UiN5YVkQu9XOYoaYaxwNe0WnFJhf4cxPChkWYk16GVMchnDWppVUaUGh4
ojmbY4Gi7VnwC0AiMbtZgnJN9NTZ5W2IhmHJKKkFSZcdbcjNr0YL/8XusbTw4Zeb7214G77z
8qj9/Q==
=CKTU
-----END PGP PUBLIC KEY BLOCK-----

```

Then open up software sources and import the above key.  Lastly, with software sources still open go here:

[https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/~pidgin-developers/+archive/ppa")

choose your release, and enter those into software sources then close.  When closing it will ask if you would like to refresh your sources.  Select yes and you should be all set once pidgin is updated.

---

### Post by Tibuda on 2009-05-19
> **M0GEJ said:**
> Ok-probably don't want to do that. Will try and fix it another way then :$

I think you didn't understood me. msn-pecan is not a different application, it is a plugin that allows Pidgin to connect to MSN in a different protocol (WLM or Windows Live Messenger).

---

### Post by M0GEJ on 2009-05-19
oops was thrown by the 1 in there. Am trying to add it to the sources list at the moment. Am not sure how I can get pidgin to stop disconnecting though....

---

### Post by M0GEJ on 2009-05-19
sorry danielrmt- I did misunderstand you there. I have just tried to install those files from synaptic and an error message flashed up to quickly for me to be able to read. Pidgin has been trying to reconnect for over a minute now...

---

### Post by Arup on 2009-05-19
> **Mornedhel said:**
> [FONT=Verdana]Add this line to the bottom of /etc/apt/sources.list :

[/FONT]```
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) jaunty main
```

Get the key from here : [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7FB8BEE0A1F196A8](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x7FB8BEE0A1F196A8) (copy paste the contents, starting with ------BEGIN PGP PUBLIC KEY BLOCK, into a file that you create, called something.gpg).

Import the key : ```
sudo apt-key add something.gpg
```

Update your cache : ```
sudo apt-get update
```

Upgrade from Pidgin (current Jaunty) to Pidgin (bleeding edge PPA) : ```
sudo apt-get upgrade
```

Thanks, was looking for this repo, I use pidgin on regular basis and need to keep it updated automatically.

---

