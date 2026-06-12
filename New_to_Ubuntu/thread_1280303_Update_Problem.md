---
title: "Update Problem"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-10-01
I think i screwdup my Software Source third party
i am pretty sure there was a Jaunty listing here but is gone. now when i try to update its giving me cant find server error

---

### Post by vlad1975 on 2009-10-01
sorry heres a better ss

---

### Post by millertime on 2009-10-01
Heres what I have for 9.04

```
http://archive.canonical.com/ubuntu : Binary : Jaunty Partner
http://archive.canonical.com/ubuntu : Source : Jaunty Partner
http://ppa.launchpad.net/kwwii/ppa/ubuntu : Binary : Jaunty Main
http://ppa.launchpad.net/kwwii/ppa/ubuntu : Source : Jaunty Main
```All are named named Jaunty Main.

Hope that helps. Just try adding them and than updating again.

---

### Post by vlad1975 on 2009-10-01
Hey thanx.. but i tried copy and paste your codes in but the add source seems not to comeup.. what am i doing wrong?

---

### Post by vlad1975 on 2009-10-01
just an update i try adding deb then the link and it allowed me to added it in now i get this error

---

### Post by millertime on 2009-10-01
See my post #7

---

### Post by millertime on 2009-10-01
Actually

```

deb [http://archive.canonical.com/ubuntu]("http://archive.canonical.com/ubuntu/") jaunty partner
deb [http://archive.canonical.com/ubuntu]("http://archive.canonical.com/ubuntu/") jaunty partner -> Edit this to Source after

deb [http://ppa.launchpad.net/kwwii/ppa/ubuntu]("http://ppa.launchpad.net/kwwii/ppa/ubuntu/") jaunty main
deb [http://ppa.launchpad.net/kwwii/ppa/ubuntu]("http://ppa.launchpad.net/kwwii/ppa/ubuntu/") jaunty main -> Edit this to Source after

```Hope that works, It let me add them and they looked like the other ones 100%, Just remember to switch the second partner and second main to source instead of binary after clicking the EDIT button.

---

### Post by vlad1975 on 2009-10-01
AHH!!!!

I learn new things everytime i break something hahahaha

Thanx dude

---

### Post by millertime on 2009-10-01
Glad that worked, Ive only been using Linux for about 3 weeks too. Guess all that Windows Tech Support did pay off.

Cheers.

---

### Post by vlad1975 on 2009-10-01
woops spoke to early

seems like theres another error see screenshot..

looks like i really did a good job on screwing this up

---

### Post by vlad1975 on 2009-10-02
I did some tweeking now i am getting this error.. so i might be close to solving.. Any idea what this error means? and how to fix it?

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B4C340A1EDCA87CAFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.45 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by millertime on 2009-10-02
What do you see on the authentication tab of software sources.

It looks like you may be missing something in that regards.

EDIT: a 404 just means that specific file was not found, we know we have connection but the server is unable to locate the files specified. This could be authentication reasons or because it is just no longer there.

---

