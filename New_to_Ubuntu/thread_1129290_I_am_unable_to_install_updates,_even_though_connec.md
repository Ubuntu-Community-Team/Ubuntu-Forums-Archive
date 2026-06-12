---
title: "I am unable to install updates, even though connected to internet and able to browse"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by mohdniyas on 2009-04-18
I am unable to install updates. The update manager gives the error that

"W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.24.21.23_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.24.21.23_i386.deb)
  Could not connect to 10.37.197.1:3128 (10.37.197.1), connection timed out


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.24.21.23_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.24.21.23_i386.deb)
  Unable to connect to 10.37.197.1 3128:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.24.21.23_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.24.21.23_i386.deb)
  Unable to connect to 10.37.197.1 3128:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.24.21.23_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.24.21.23_i386.deb)
  Unable to connect to 10.37.197.1 3128:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.14-21.51_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/linux-restricted-modules-common_2.6.24.14-21.51_all.deb)
  Unable to connect to 10.37.197.1 3128:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.14-21.51_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.14-21.51_i386.deb)
  Unable to connect to 10.37.197.1 3128:
"

Here IP **10.37.197.1 3128 is the proxy server at my office LAN**. But i am trying to update from **home, broadband connection**. I am able to browse internet, but still unable to install updates. Pls help me....Thanks...Niyas

---

### Post by coldReactive on 2009-04-18
When putting in those addresses to the web browser, they all result in 404.

---

### Post by dje on 2009-04-18
Open System >> Administration >> Software Sources. On the 'Download from:' dropdown select 'Main server' then click Close and then Reload when prompted.

Also check the proxy settings are correct in System >> Preferences >> Network Proxy

dje

---

### Post by bzarnsy on 2009-04-18
yet another unable to update or upgrade.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release)  Unable to find expected entry  main'./binary-i386/Packages in Meta-index file (malformed Release file?)

dose the same for main server.  what's up?

---

### Post by eilios on 2009-04-18
What version of Ubuntu are you using?

---

### Post by bzarnsy on 2009-04-18
i'm running ibex and trying to upgrade to jaunty rc

---

### Post by llamabr on 2009-04-18
Something funny like this happened about 8 years ago, everyone complained that the debian repositories were offline.  The next day we read in the paper that the building had burned down.

I'm sure that's not the problem, tho.  Post your sources.list.  When I click those, I get a 404 error.

---

### Post by cariboo on 2009-04-18
I just checked the links in post #4, they work here.

Jim

---

### Post by mohdniyas on 2009-04-19
Thanks a lot my dear friends....Just removed the Network Proxy ( System>Preferences>network Proxy) from Manual proxy to Direct Internet, and i am able to install updates...Also System>Administration>Software sources > Download From is changed to Main Server .........Thank you

---

### Post by sadaruwan12 on 2009-04-19
Hi,

Your firefox was able to connect because it was not configured for your company proxy but your system had a proxy thats why you where unable to down load the updates from ubutnu repo's the system was trying to go through the proxy that have been configured to your system.

---

