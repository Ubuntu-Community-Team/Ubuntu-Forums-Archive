---
title: "Download through terminal"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Macub on 2011-03-02
Hi all,

I'm having a problem downloading "daq-0.5.tar.gz" from Snort's site through terminal (Ubuntu Server).

The "daq-0.5.tar.gz" file is located here under "Source": [http://www.snort.org/snort-downloads](http://www.snort.org/snort-downloads).

If I point at the "daq-0.5.tar.gz" link in a browser the underlying link points to [http://www.snort.org/downloads/801](http://www.snort.org/downloads/801). If I click on the link, that file will download from [http://s3.amazonaaws.com](http://s3.amazonaaws.com)

I've tried the following...

sudo wget [http://www.snort.org/snort-downloads/daq-0.5.tar.gz](http://www.snort.org/snort-downloads/daq-0.5.tar.gz)

That returns 404: Not Found.

Also tried...

sudo wget [http://www.snort.org/downloads/801/daq-0.5.tar.gz](http://www.snort.org/downloads/801/daq-0.5.tar.gz)

That also returns 404 Not Found.

Also tried...

sudo wget [http://www.snort.org/downloads/801](http://www.snort.org/downloads/801)

That downloads "801" but I can't tell what that is, though it doesn't appear to be, or to contain, daq-0.5.tar.gz

Also tried...

[http://s3.amazonaaws.com/daq-0.5.tar.gz](http://s3.amazonaaws.com/daq-0.5.tar.gz)

That also returns 404: Not Found.

I started to research downloading the file through the Desktop transferring it to the server via ssh but I really would like to know how to download that file through the terminal for future reference.

Can anyone shed some light?

Thanks in advance for any help.

---

### Post by philinux on 2011-03-02
> **Macub said:**
> Hi all,

I'm having a problem downloading "daq-0.5.tar.gz" from Snort's site through terminal (Ubuntu Server).
Can anyone shed some light?

Thanks in advance for any help.

You missed their linky on the downloads page. 
[http://www.snort.org/snort-downloads/cli](http://www.snort.org/snort-downloads/cli)

---

### Post by Macub on 2011-03-02
Darn! That did it!

Thanks a lot, Phil.

---

