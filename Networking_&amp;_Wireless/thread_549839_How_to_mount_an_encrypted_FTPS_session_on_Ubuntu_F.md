---
title: "How to mount an encrypted FTPS session on Ubuntu Feisty(+)? curlftpfs buggy in feisty"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Rene7705 on 2007-09-13
The only option that I found to mount an FTPS session as drive/folder/path under Ubuntu 7.04 is using curlftpfs (and a manual partial upgrade to some packages of Gutsy). See [here]("http://ubuntuforums.org/showthread.php?t=549262") for details.
However I can't get curlftpfs to work correctly on a clustered ftp server, and it doesnt seem to cache things either, but DOES dnload all images in a nautilus-browsed directory, resulting in very long waits when working with larger directories..

I'm wondering if there's any other package that can mount an FTPS session, and hopefully cache things reliably aswell.

I've googled till page 30 of various searchqueries, and no luck.

Or should I give up hope on mounting FTPS, and search for an FTPS client that has a treeview and can facilitate external editors? I need something that doesnt nag about permissions towards my gvim. Anything you can recommend?

---

