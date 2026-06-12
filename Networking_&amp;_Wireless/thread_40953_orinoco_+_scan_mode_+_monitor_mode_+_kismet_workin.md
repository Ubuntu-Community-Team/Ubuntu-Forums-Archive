---
title: "orinoco + scan mode + monitor mode + kismet working"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by sebw on 2005-06-11
Hi,

I was running drivers that came with ubuntu for my orinoco silver pc card.
After succesfully patching these drivers which added the monitor function, I was able to use Kismet which was working great.

Now, I'd like to get scan mode along with monitor mode.

> iwlist eth1 scan
reports : eth1      Interface doesn't support scanning : Operation not supported

I have followed that guide here to compile the latest drivers (0.15rc2) that natively support scan mode : [http://ubuntuforums.org/archive/index.php/t-12340.html](http://ubuntuforums.org/archive/index.php/t-12340.html) 

Scan mode was working but monitor mode was working so-so. Kismet would only listen to a specific channel and not all..

From what is being said here [http://lists.samba.org/archive/wireless/2005-March/002854.html](http://lists.samba.org/archive/wireless/2005-March/002854.html) , the drivers needs to be patched to work fine with Kismet.

If someone can help me finding that patch or a tweaked drivers that natively support both scan mode (for wifi-radar) and fully working monitor mode (for Kismet)... 

Thanks
Seb

---

