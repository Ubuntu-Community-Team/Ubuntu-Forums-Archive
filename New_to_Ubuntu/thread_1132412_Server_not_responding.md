---
title: "Server not responding"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by theozzlives on 2009-04-21
I thought I had this fixed in 8.10 with a mountcifs script, but anyhow when I shutdown or restart I get the errors in the screenshot. any help would be appreciated. I'm using Jaunty 32 bit BTW.

---

### Post by hyperyoda on 2009-04-21
> **theozzlives said:**
> I thought I had this fixed in 8.10 with a mountcifs script, but anyhow when I shutdown or restart I get the errors in the screenshot. any help would be appreciated. I'm using Jaunty 32 bit BTW.

Hi!

There is a bug on this filed for jaunty:

[https://bugs.launchpad.net/ubuntu/+bug/357578](https://bugs.launchpad.net/ubuntu/+bug/357578)

Try this solution:
[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

---

### Post by theozzlives on 2009-04-22
> **hyperyoda said:**
> Hi!

There is a bug on this filed for jaunty:

[https://bugs.launchpad.net/ubuntu/+bug/357578](https://bugs.launchpad.net/ubuntu/+bug/357578)

Try this solution:
[http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/](http://www.jejik.com/articles/2007/07/automatically_mounting_and_unmounting_samba_windows_shares_with_cifs/)

Thanks for your help, but it's like my mountcifs script it works in Intrepid but not Jaunty.

---

### Post by HermanAB on 2009-04-22
Howdy,

You can debug the connection using smbclient as described here:
[http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

