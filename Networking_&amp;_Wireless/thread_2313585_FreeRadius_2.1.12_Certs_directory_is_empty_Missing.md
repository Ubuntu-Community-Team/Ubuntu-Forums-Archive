---
title: "FreeRadius 2.1.12 Certs directory is empty??? Missing makefile, readme, cfg's."
date: 2016-02-13
forum: Networking &amp; Wireless
---

### Post by mike_johnson2 on 2016-02-13
Hi, I was trying to create certificates for my installation of FreeRadius.

I installed it using the apt-get install freeradius on ubutu 14.04.03, so all my files came from there.

I went to the /etc/freeradius/certs to create some certificates, and the onliest things I found were **ca.pem,** dh, **server.key,** and [B]server.pem

[/B]There was no readme file, no configuration files, no makefile, nothing.

I was about to post this to ask for help getting these files, but I found some files that seem to be correct.
So, instead I'll just post where I found them incase anyone else runs into this.

[http://www.filewatcher.com/b/ftp/ftp.man.pulawy.pl/pub/windows/freeradius/freeradius-server-2.1.12/raddb/certs-0.html](http://www.filewatcher.com/b/ftp/ftp.man.pulawy.pl/pub/windows/freeradius/freeradius-server-2.1.12/raddb/certs-0.html)

I haven't used the new certs yet but this set of files seemed to properly create certificates for me.
Maybe these are already in another directory in the FreeRadius package, not sure.

(by the way - why does the server only allows tagging posts with tags that are 18 characters or less, and then only allow tags that come from a list of which many are over 18 characters, and then tells you the tags you can choose from are invalid?)

---

