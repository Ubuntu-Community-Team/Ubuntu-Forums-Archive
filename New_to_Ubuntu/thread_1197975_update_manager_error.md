---
title: "update manager error"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by Def_101 on 2009-06-26
recently when trying to update i got the folowing error

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7


not sure what this means

---

### Post by Steelmourne on 2009-06-26
I get the same errors half the time when I wirelessly connect to a network.. To fix it open up terminal from the Accessories menu then type: sudo apt-get update -o Acquire::http::No-Cache=true

Then type exit to close terminal, open up update manager and check for updates again. You might also try setting the update server closer to where you live in software sources under the administration menu.

---

### Post by drs305 on 2009-06-26
> **Def_101 said:**
> recently when trying to update i got the folowing error

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4874D3686E80C6B7


not sure what this means

You can import the key. It's a verification procedure:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4874D3686E80C6B7

```

---

### Post by Def_101 on 2009-06-26
tried to use your idea steelmourne but it came back with the same error.

so i tried drs305 s idea worked flawessly thank you and i will know for the next time

---

### Post by lewys93 on 2009-07-16
I've been having problems similar to this, I also get many sources saying 'Hit' when I try to update 'sources.lst'. Is this a problem?

---

### Post by Elep.Repu on 2009-07-16
> **lewys93 said:**
> I've been having problems similar to this, I also get many sources saying 'Hit' when I try to update 'sources.lst'. Is this a problem?

No, if it says hit, it's a good thing.

If you can do:
```
sudo apt-get update
``` (with no errors)
then the normal command that follows is 
```
sudo apt-get upgrade
```

---

### Post by lewys93 on 2009-07-19
> **Elep.Repu said:**
> No, if it says hit, it's a good thing.

If you can do:
```
sudo apt-get update
``` (with no errors)
then the normal command that follows is 
```
sudo apt-get upgrade
```


Thanks.
What about 'ign'. I'm guessing that means 'ignored'.
I get it on the following packages:
```

Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB  
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Translation-en_GB
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages

```

---

