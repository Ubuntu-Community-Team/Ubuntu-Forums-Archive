---
title: "XRDP Issues"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by compgeek83 on 2008-05-17
I have installed XRDP from synaptic but when I go to check it's status or restart it i get 

```
Starting xrdp: start-stop-daemon: Unable to set gid to 125 (Operation not permitted
```


any ideas?

---

### Post by compgeek83 on 2008-05-20
bump...

any ideas?? anyone?

---

### Post by NoThanksM$ on 2008-07-12
I'd like to know about this too - no one has any experience getting xrdp to work after installing from synaptic?

---

### Post by tjandracom on 2008-08-07
what ubuntu version you had?
i had successfully install xrdp on fresh installed Hardy Heron 8.04. i've heard that xrdp doesn't work with ubuntu version prior to Gutsy Gibon. maybe the library, but i don't know for sure. i myself failed with Dapper 6.06.

and i connect via xrdp using X11rdp instead of xvnc, so each user can have their own session running independently, just like Windows Terminal Server does. it's very cool once you managed to set it up correctly, and in my case, i succesfully eliminate the Windows Server altogether.

---

### Post by NoThanksM$ on 2008-08-07
I'm using 8.04 as well.  I found this post [http://www.bramkortleven.be/?p=34](http://www.bramkortleven.be/?p=34) that links to here:  [http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/](http://www.linuxquestions.org/questions/linux-server-73/xrdp-authenticates-but-does-not-load-x-server-rdp-592138/) but I haven't given it a try yet.

---

### Post by tjandracom on 2008-08-09
yes, the link you mentioned above is just the right link.
the hardest part is to compile X11rdp binary from the source, because this file is not included in the xrdp package, and building from source is the only way to get the binary.
you should give it a try.

---

