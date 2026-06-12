---
title: "Certain software updates won't work (can't connect)"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by fillmont on 2011-07-07
I am attempting to update software through the Update Manager. Most of the updates have gone through, but certain packages relating to CUPS and compiz seem to not want to work.   I get an error message that the interenet cannot connect.  Details reveal this:      >  Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.4+bzr20110606-0ubuntu1~natty1_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.9.4+bzr20110606-0ubuntu1~natty1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.9.4+bzr20110606-0ubuntu1~natty1_all.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.6-5ubuntu1.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.6-5ubuntu1.2_all.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-ppdc_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.6-5ubuntu1.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.6-5ubuntu1.2_i386.deb) 404  Not Found [IP: 91.189.88.31 80]     I know the internet is working, since I'm using this forum and have had success with other packages.  Any help?

---

### Post by terrykiwi83 on 2011-07-07
Hi, could you list your sources.list file here please :)

---

### Post by jtarin on 2011-07-07
[Change your server]("http://blog.mypapit.net/2007/08/how-to-get-fastest-ubuntu-apt-get-repository-server-with-synaptic.html") and maybe improve your download speed at the same time.

---

### Post by MG&amp;TL on 2011-07-07
I tend to have this problem when I have weak internet, so if you possibly can, boost your signal (i.e. sit in same room as hub if you have wireless.) And yes, I could surf the web when I had this problem. 

As suggested above, try a different server/mirror whatever. It's probably in 'properties' 'settings' or it might be in 'software sources' - I can't provide any more, sorry, hope someone else can. :D

---

### Post by wildmanne39 on 2011-07-07
Hi, I click on the links your provided and they are not on the server.

---

