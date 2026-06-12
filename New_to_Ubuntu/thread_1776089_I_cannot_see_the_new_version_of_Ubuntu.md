---
title: "I cannot see the new version of Ubuntu"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by aaricia on 2011-06-05
Hello guys,

As I have more free time now, I am trying to upgrade from Ubuntu 9.1 to 10.1, but I cannot see the new version either through the Semantic Manager or through the shell.

I explain it better, when I type:

sudo do-release-upgrade from the shell,

I get the following message:
Checking for a new ubuntu release
No new release found

If go to the "Synaptic Package Manager" and click on the "Reload" button, I get the following error message:

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"


In "Software sources" I have tried connecting from the server in the UK (where I live), from the server in my country (Espanya) or the best server chosen by the system but it is not making any difference. 

Could you please advice about where can I find the public keys missing?

Thank you very much for your advice.

---

### Post by wildmanne39 on 2011-06-05
> **aaricia said:**
> Hello guys,

As I have more free time now, I am trying to upgrade from Ubuntu 9.1 to 10.1, but I cannot see the new version either through the Semantic Manager or through the shell.

I explain it better, when I type:

sudo do-release-upgrade from the shell,

I get the following message:
Checking for a new ubuntu release
No new release found

If go to the "Synaptic Package Manager" and click on the "Reload" button, I get the following error message:

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"


In "Software sources" I have tried connecting from the server in the UK (where I live), from the server in my country (Espanya) or the best server chosen by the system but it is not making any difference. 

Could you please advice about where can I find the public keys missing?

Thank you very much for your advice.

Hi, run this command in a terminal.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
```

---

### Post by dFlyer on 2011-06-05
> **aaricia said:**
> Hello guys,

As I have more free time now, I am trying to upgrade from Ubuntu 9.1 to 10.1, but I cannot see the new version either through the Semantic Manager or through the shell.

I explain it better, when I type:

sudo do-release-upgrade from the shell,

I get the following message:
Checking for a new ubuntu release
No new release found

If go to the "Synaptic Package Manager" and click on the "Reload" button, I get the following error message:

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2A8E3034D018A4CE
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0"


In "Software sources" I have tried connecting from the server in the UK (where I live), from the server in my country (Espanya) or the best server chosen by the system but it is not making any difference. 

Could you please advice about where can I find the public keys missing?

Thank you very much for your advice.

Just a quick side note 10.10 is not the new version. 11.04 is the current version.

---

### Post by mikewhatever on 2011-06-05
Ubuntu 9.10 is no longer supported, please see the link on how to upgrade an End of Life release.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
Note: You can only upgrade 9.10->10.04, no other path is supported.

---

### Post by aaricia on 2011-06-08
Thanks for your advice, both. I tried the first suggestion, but didn't work.
I am going to try changing the content in sources.list

---

