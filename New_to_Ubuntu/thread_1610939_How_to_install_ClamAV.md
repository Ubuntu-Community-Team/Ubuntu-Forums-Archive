---
title: "How to install ClamAV?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by grobar87 on 2010-11-01
Hi,
How to install ClamAV on Ubuntu 10.10?
Thanks.

---

### Post by lhb1142 on 2010-11-01
> **grobar87 said:**
> Hi,
How to install ClamAV on Ubuntu 10.10?
Thanks.

In my opinion the easiest way is still the old-fashioned way - go into the Synaptics Package Manager (System->Administration-Synaptics Package Manager).

Enter  clam  in the search box; click on clamav which will also select dependencies, click on clamav-daemon (both of these are Canonical-supported), and finally click on clamtk (community-supported, the graphical front end so you can easily use ClamAV). Note that clamtk appears on the list before ClamAV itself does.

You know of course that you do not need an antivirus program for yourself; scanning your files merely ensures that you do not send an infected file to some hapless person still running Windows.

While you're at it, why not enter into Synaptics' search box  ufw ? This will bring up ufw (the Ubuntu firewall) which is already installed but will also show  gufw  the graphical front end. If you install gufw you will easily be able to view and possibly adjust your firewall (though unless you are a very advanced user, I suggest that you leave it alone).

I hope this helps you.

---

### Post by grobar87 on 2010-11-01
> **lhb1142 said:**
> In my opinion the easiest way is still the old-fashioned way - go into the Synaptics Package Manager (System->Administration-Synaptics Package Manager).

Enter  clam  in the search box; click on clamav which will also select dependencies, click on clamav-daemon (both of these are Canonical-supported), and finally click on clamtk (community-supported, the graphical front end so you can easily use ClamAV). Note that clamtk appears on the list before ClamAV itself does.

You know of course that you do not need an antivirus program for yourself; scanning your files merely ensures that you do not send an infected file to some hapless person still running Windows.

While you're at it, why not enter into Synaptics' search box  ufw ? This will bring up ufw (the Ubuntu firewall) which is already installed but will also show  gufw  the graphical front end. If you install gufw you will easily be able to view and possibly adjust your firewall (though unless you are a very advanced user, I suggest that you leave it alone).

I hope this helps you.

Thanks for this.Very nice post.I install ClamAV and everything works fine.:)

---

