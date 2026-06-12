---
title: "Skype upgraded to the next Beta version and I didn't want it to.  How do I revert?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by diablo75 on 2009-12-05
A few weeks ago I downloaded the Beta version of Skype from Skypes website to try it out, and it didn't work at all (sound wise).  There were still some bugs in when it came to Pulse Audio.  So I removed it, and then reverted to the previous version by doing a sudo apt-get install skype which worked because I have the medibuntu repositories enabled.  But today some updates came down and I didn't look them over and apparently the people that run the medibuntu repositories thought it'd be a wonderful idea to upgrade skype to that same beta version.  So I'm stuck with the same audio problems I was trying to avoid.

What's the best way for me to revert back to the previous version so I can continue with a copy that's not broken.  I'm using Ubuntu 9.04 by the way...

---

### Post by RJ12 on 2009-12-05
first you need to uninstall it by running sudo apt-get remove skype
The stable one should be on skype's website as a .deb package... double click it when downloaded and click install package


These might not be correct instructions so wait for someone to confirm this is right:D

---

### Post by nwadams on 2009-12-05
if you go to the synaptic package manager and look up skype. In the properties or advanced options (i can't remember what it is exactly) you can go to the version tab and force a version that works for you.

---

### Post by stlsaint on 2009-12-05
i suggest removing skype all together and re-install from skype website with version you want.

---

### Post by mikewhatever on 2009-12-05
> **stlsaint said:**
> i suggest removing skype all together and re-install from skype website with version you want.

But the only version available on skype.com is the current beta. You can still get the older version (2.0.0.72) from Medibuntu - Intrepid.
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

---

### Post by darkstaar on 2009-12-05
Try [http://packages.medibuntu.org/jaunty/skype-common.html](http://packages.medibuntu.org/jaunty/skype-common.html) & [http://packages.medibuntu.org/jaunty/skype.html](http://packages.medibuntu.org/jaunty/skype.html)

---

### Post by diablo75 on 2009-12-05
> **darkstaar said:**
> Try [http://packages.medibuntu.org/jaunty/skype-common.html](http://packages.medibuntu.org/jaunty/skype-common.html) & [http://packages.medibuntu.org/jaunty/skype.html](http://packages.medibuntu.org/jaunty/skype.html)

These appear to link to the latest version (2.1.0.47) which is the beta version that doesn't work for me...

---

### Post by diablo75 on 2009-12-05
> **mikewhatever said:**
> But the only version available on skype.com is the current beta. You can still get the older version (2.0.0.72) from Medibuntu - Intrepid.
[http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype_2.0.0.72-0medibuntu4_i386.deb)

I'll try this (I think it'll work) and let you know what happens later today.  Thanks!

---

### Post by diablo75 on 2009-12-06
I tried to install the above deb file, but I need to install the skype-common deb file before hand to meet a dependency requirement.  When I tried to install, I got the following error:

> Error: Dependency is not satisfiable: skype-common (= 2.0.0.72-0medibuntu4)

Where might I download this from?

---

### Post by diablo75 on 2009-12-06
SOLVED.

I used the above link for downloading and trimmed the file name off the end of it to get to the folder index:

[http://packages.medibuntu.org/pool/non-free/s/skype](http://packages.medibuntu.org/pool/non-free/s/skype)

And found the file I needed:

[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

I then installed the skype-common package, then the main skype package.  There was an error on the package installer saying there was a "Break", but I ignored it, tested Skype, and made a test phone call.  It works again.

Finally, I went into Synaptic and locked the package version so it won't attempt to upgrade itself again.

---

### Post by mikewhatever on 2009-12-06
Well, it's on the same page:
[http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb](http://packages.medibuntu.org/pool/non-free/s/skype/skype-common_2.0.0.72-0medibuntu4_all.deb)

---

