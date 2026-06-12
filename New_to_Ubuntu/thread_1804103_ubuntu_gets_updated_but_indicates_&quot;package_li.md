---
title: "ubuntu gets updated but indicates &quot;package list not updated&quot;"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by sugavaneshb on 2011-07-14
Mine is Ubuntu 11.04 desktop edition...When i open the update manager to update the system and press check... it checks for and downloads or updates or whatever a list and shows a list of packages to download... I accept them and the system downloads,installs and restarts....... Now when I open the update manager again,it says,

"The package info. was updated 26 days ago... There might be software updates available for this system..." 

So i press the check button again... It shows up an error "check your internet connection" with details showing up.......

"W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595, W:Failed to fetch [http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."....


And there are no packages list showed up to be downloaded.... What am i supposed to do now? Is the system really updated? Are there any broken packages...??! Help me out.....

---

### Post by raja.genupula on 2011-07-14
hey 

just run this 

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

---

### Post by sugavaneshb on 2011-07-14
> **raja.genupula said:**
> hey 

just run this 

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update


I tried it... It downloaded some packages i suppose but still shows some error like this,.....
"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595
W: Failed to fetch [http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/sugavaneshb/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead."

---

### Post by plucky on 2011-07-14
> W: Failed to fetch [http://ppa.launchpad.net/sugavaneshb...source/Sources](http://ppa.launchpad.net/sugavaneshb...source/Sources) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/sugavaneshb...-i386/Packages](http://ppa.launchpad.net/sugavaneshb...-i386/Packages) 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead."

You have a non-valid PPA in your Software Sources list.

Open the Repositories Tab in Synaptic Package Manager and un-tick the PPA ```
http://ppa.launchpad.net/sugavaneshb...source/Sources
```

Then Reload and see if you still get the same error.

Good Luck

---

### Post by sugavaneshb on 2011-07-14
> **plucky said:**
> You have a non-valid PPA in your Software Sources list.

Open the Repositories Tab in Synaptic Package Manager and un-tick the PPA ```
http://ppa.launchpad.net/sugavaneshb...source/Sources
```

Then Reload and see if you still get the same error.

Good Luck


Thanx... I suppose it solved half of the problem i suppose... But now still i get this error when i try to reload...

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595"

....When the PPA is not included at all there is no  error... so should i remove ppa completely from souces...i mean untick...

---

### Post by plucky on 2011-07-14
> **sugavaneshb said:**
> Thanx... I suppose it solved half of the problem i suppose... But now still i get this error when i try to reload...

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2CC98497A1231595"

....When the PPA is not included at all there is no  error... so should i remove ppa completely from souces...i mean untick...

If it is a valid PPA,you can run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2CC98497A1231595
``` to add the key.

If it isn't a valid PPA ,you can delete it from Software Sources.

Good Luck

---

### Post by sugavaneshb on 2011-07-15
> **plucky said:**
> If it is a valid PPA,you can run ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2CC98497A1231595
``` to add the key.

If it isn't a valid PPA ,you can delete it from Software Sources.

Good Luck

Voila.... Thanx.. I think it worked.. no more bugs with the update manager as of now...

---

