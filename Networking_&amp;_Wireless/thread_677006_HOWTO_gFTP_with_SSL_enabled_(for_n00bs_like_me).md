---
title: "HOWTO: gFTP with SSL enabled (for n00bs like me)"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by sceo on 2008-01-24
It seems that there is quite a lack of clients that support FTPS (excepting FileZilla beta3, which I found buggy on Gutsy from repos), so many turn to gFTP.  This is FTP over SSL (FTPS) NOT FTP over SSH (SFTP).  However, the packages in the repo's for gFTP do not include ssl support, as it is non-free.  The answer is to roll your own.  Here's how I did it.  It strikes me as quite possible that most people will be like "yeah, duh" but for n00bs like me, this may be a big step.

One option is to use Seveas repo's for this.  ATM, though, there is no package for Gutsy ([http://seveas.theplayboymansion.net/seveas/dists/feisty-seveas](http://seveas.theplayboymansion.net/seveas/dists/feisty-seveas)).  Installing the Feisty packages causes update-manager to nag you about installing the newer version, though.

First off, I can't say how I managed to satisfy my dependencies.  At one point I had the seveas packages installed, and similarly I had gftp-gtk and gftp-common installed from repo's.

All I needed to do then, was:
[LIST]
[*]sudo apt-get install libssl-dev
[*]sudo apt-get install openssl
[*]download the source for gftp from its web site ([http://gftp.seul.org/](http://gftp.seul.org/))
[*]untar the source, and CD to the source directory
[*]./configure --enable-ssl
[*]make
[*]sudo make install
[/LIST]

Now, starting gFTP shows me the SSL options, and no nag from update-manager.  I really hope this helps somebody!

---

