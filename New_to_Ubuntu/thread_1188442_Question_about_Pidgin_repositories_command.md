---
title: "Question about Pidgin repositories command"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by PrimaryMaster on 2009-06-15
Hi everyone,

I run Hardy on my laptop and i want to update my Pidgin to the latest version. At Pidgin's website there is the following command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

. /etc/lsb-release

echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu \     $DISTRIB_CODENAME main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

The question is... Do i enter all this text as a single command or are these to be entered as separate commands? It seems to get the key fine but it doesn't update my resource list. Please help. Thank you.

UPDATE: I just received a Pidgin update. So i guess i did it at last. Still would like to know if this is a single command though. If someone can break it apart it'd help me understand. Thank you.

---

### Post by SOULRiDER on 2009-06-15
I believe you should be able to just paste everything and not have any issues.

---

### Post by Cheesemill on 2009-06-15
It's 3 commands, the \ just lets you split a command over several lines to make it easier to read. So it's the same as typing:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
. /etc/lsb-release
echo deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu $DISTRIB_CODENAME main | sudo tee /etc/apt/sources.list.d/pidgin-ppa.list
```

You can split any command up in this way, for example you could do
```
sudo \
apt-get \
update
```
instead of
```
sudo apt-get update
```

The commands you entered only installed the Pidgin PPA and key to your repos, it didn't include the update or upgrade commands needed to actually update your system. This is why the Pidgin update didn't happen immediately.

---

### Post by Locke_99GS on 2009-06-15
```
tee /etc/apt/sources.list.d/pidgin-ppa.list
```
Creates a sublist, which is why you're not seeing the entry in your sources.list.

```
$DISTRIB_CODENAME
```
Should equal Jaunty/Intrepid/Hardy/whatever.

---

### Post by PrimaryMaster on 2009-06-23
Thank you all. Been really helpful. :)

---

