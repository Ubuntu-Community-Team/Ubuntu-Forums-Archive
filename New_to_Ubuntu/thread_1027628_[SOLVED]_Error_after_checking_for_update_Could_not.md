---
title: "[SOLVED] Error after checking for update: Could not download all repository indexes"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Aaris on 2009-01-01
I keep getting a warning asking me to run updates. When I open the update manager and click "Check" it gives me the message above. In the box, it says:

Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-amd64/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/deb-src/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-amd64/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/http://ppa.launchpad.net/banshee-team/ubuntu/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-amd64/Packages.gz](http://ppa.launchpad.net/banshee-team/ubuntu/dists/intrepid/intrepid/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz](http://blognux.free.fr/debian/dists/unstable/main/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I can see that this has to do with Banshee, but I can't quite figure out what's wrong. Could someone please point me in the right direction? I admit I haven't done much to try to resolve this myself, but I'm really not sure where to start. Thanks.

---

### Post by Shazaam on 2009-01-01
The servers might be down for maintenance or have been moved/removed. For a temporary work around go to System>Administration>Software Sources>Third Party Software and uncheck the offending entries. Then either reload the lists there, through Synaptic, or open terminal and enter...
```
sudo apt-get update
```
Later on you can re-enable them and try again.

---

### Post by Aaris on 2009-01-01
Thank you! This seems to have taken care of the update problem for the short-term.

---

