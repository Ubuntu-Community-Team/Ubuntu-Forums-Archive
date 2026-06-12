---
title: "Update manager failing"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Metaxa on 2009-09-08
Hello folks,

I am trying to run update manager. I am getting and error which states, not all updates can be installed, and give me the option for a partial upgrade. when I choose to upgrade I get a repository index error with the following internal message, in the prompt that is.


GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFFFailed to fetch cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)/dists/hardy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)/dists/hardy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Any help would be appreciated.

Hugo

---

### Post by rajeev1204 on 2009-09-08
Go to system>administration>software sources and uncheck cdrom .
then try update.

Also,partial updates can be tricky as some packages are held back due to many reasons so try updating after a few hours.

---

### Post by Metaxa on 2009-09-08
Unchecked that.

I am still getting another error when I partially upgrade. It relates to openoffice.org and all associated packages.

Error authenticating some packages.

Hugo

---

### Post by RedSingularity on 2009-09-09
Try unchecking the openoffice scribblers box in your sources list.

---

### Post by ramjet_1953 on 2009-09-09
Try this:

1. Open Synaptic Package Manager

2. Navigate to: Settings>Preferences>Distribution

3. Click on "Always prefer highest version".

4. Click on "Apply" and close the window.

5. Click on the "Releoad" button in the top left of the Synaptic window.

6. Now try updating again.

Hopefully, this will work.

Regards,
Roger :)

---

