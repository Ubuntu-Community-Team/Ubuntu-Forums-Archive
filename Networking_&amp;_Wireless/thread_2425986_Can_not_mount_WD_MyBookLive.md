---
title: "Can not mount WD MyBookLive"
date: 2019-09-03
forum: Networking &amp; Wireless
---

### Post by bmiklos43 on 2019-09-03
I have Ubuntu 18.04 on a LAN with a router.  
 I have connected myWD MyBookLive ethernet to my router  and can find it through the IP address.  
 The NAS is empty only the factory original setup program is on it. Its Firmware was updated today successfully. I have created a user and also two shares for the drive with the WD setup screen.  
 But I can not see or mount the drive in any way I tried. On Ubuntu File Manager &#8594; Other locations I can not see MyBookLive, however initially I had the drive visible but since disappeared. I can not bring it back. Additionally I can not mount or access it.  
 Reading through suggestions, I tried some, but so far I did not get any results . Honestly, I am pretty new in Linux/Ubuntu and I am not sure where I am.  
 Any advise is well received. Thanks.

---

### Post by TheFu on 2019-09-03
Please be very careful.  [https://nvd.nist.gov/vuln/detail/CVE-2018-18472](https://nvd.nist.gov/vuln/detail/CVE-2018-18472)

Most routers have similar issues for storage connected to them.

Which protocol does the MyBookLive support for file sharing? That will determine any mount options needed.
[https://ubuntuforums.org/showthread.php?t=2005593](https://ubuntuforums.org/showthread.php?t=2005593) post #7 has a reasonable example for mounting.

---

