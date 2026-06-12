---
title: "Accessing Windows Share"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-05-15
If I go through the "Connect to Server" wizard, and open up that "Network Place" in Nautilus, I'm able to write to the share.

However, if I try to mount the share (from the command line), I can read it, but can't write to it.

So, the "Connect to Server" wizard does something behind the scenes that my command does not. Can someone help me diagnose the problem?

Here's the command I'm using (which allows me to read from the share, but not write to it):
```

sudo smbmount //theWinHost/websites /media/myShares/theWinBox/websites -o username=myUsername/theDomain

```

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-07-06
Here's what I ended up with for mounting Windows shares at work:

```

sudo smbmount //<hostname>/<windowsShareName> /media/<myMountDirectory> -o username=<myWork'sNetworkUsername>,workgroup=<myWork'sNetworkName>,rw,fmask=775,uid=<myLocalUbuntuUsername>

```

---

