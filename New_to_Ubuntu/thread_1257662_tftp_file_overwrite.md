---
title: "tftp file overwrite"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by malcolmpdw on 2009-09-04
Hello,

I have configured TFTPD according to the very clear instructions on

[http://www.davidsudjiman.info/2006/0...tpd-in-ubuntu/](http://www.davidsudjiman.info/2006/0...tpd-in-ubuntu/)

At present, the transfer fails if the file already exists. I would like it to overwrite the existing file.

The problem lies with the permissions of the existing file.

If I do this first:

sudo chmod 777 filename

then the transfer overwrites the existing file.

But how can I get xinetd to create the first file with the permissions I require?

Thanks in advance!

Malcolm

---

