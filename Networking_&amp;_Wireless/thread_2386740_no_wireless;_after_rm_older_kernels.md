---
title: "no wireless; after rm older kernels"
date: 2018-03-09
forum: Networking &amp; Wireless
---

### Post by linuxcss22 on 2018-03-09
I was removing older kernels in xubuntu 16.04 ...
on reboot said missing kernel file so I copied from another machine to /boot
via live boot
then it would boot but now NO wireless (thinkpad T560) ...
I have network wired access ... how do I reinstall the wireless stuff ?

thanks

---

### Post by wildmanne39 on 2018-03-09
Hello and welcome to the forum!

Please post the output of:
```
dpkg --list | grep linux-image
```
between code tags.

Thanks

---

### Post by linuxcss22 on 2018-03-09
```

rc  linux-image-4.4.0-101-generic                 4.4.0-101.124                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-103-generic                 4.4.0-103.126                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic                 4.4.0-104.127                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-109-generic                 4.4.0-109.132                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-112-generic                 4.4.0-112.135                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-116-generic                 4.4.0-116.140                                            amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                  4.4.0-31.50                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                  4.4.0-57.78                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic                  4.4.0-63.84                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                  4.4.0-66.87                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic                  4.4.0-72.93                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic                  4.4.0-75.96                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-78-generic                  4.4.0-78.99                                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic                  4.4.0-79.100                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generic                  4.4.0-81.104                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-83-generic                  4.4.0-83.106                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic                  4.4.0-87.110                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic                  4.4.0-89.112                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic                  4.4.0-91.114                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic                  4.4.0-92.115                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-93-generic                  4.4.0-93.116                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-96-generic                  4.4.0-96.119                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-97-generic                  4.4.0-97.120                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-98-generic                  4.4.0-98.121                                             amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-101-generic           4.4.0-101.124                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-103-generic           4.4.0-103.126                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-generic           4.4.0-104.127                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic           4.4.0-109.132                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic           4.4.0-112.135                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-116-generic           4.4.0-116.140                                            amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic            4.4.0-31.50                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic            4.4.0-57.78                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic            4.4.0-66.87                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic            4.4.0-72.93                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic            4.4.0-75.96                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-78-generic            4.4.0-78.99                                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic            4.4.0-79.100                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-generic            4.4.0-81.104                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-83-generic            4.4.0-83.106                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic            4.4.0-87.110                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic            4.4.0-89.112                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic            4.4.0-91.114                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic            4.4.0-92.115                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-93-generic            4.4.0-93.116                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-96-generic            4.4.0-96.119                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-97-generic            4.4.0-97.120                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-98-generic            4.4.0-98.121                                             amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.116.122                                            amd64        Generic Linux kernel image

```

---

### Post by wildmanne39 on 2018-03-09
I do not think removing the old kernels caused your issue, I see:
```
linux-image-4.4.0-116-generic
```
That has been causing issues because of a different version of gcc is getting installed.

Please post the output of:
```
dmesg
```

Thanks

---

### Post by linuxcss22 on 2018-03-09
when I paste dmesg output here (how do I fix this ...???)
I get this 
 				Your submission could not be processed because a security token was missing.

 If this occurred unexpectedly, please [inform the administrator]("https://ubuntuforums.org/sendmessage.php")  and describe the action you performed before you received this error.  If possible, please include the error page URL plus the date and time  the error occured. 

 Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
 			
 			Ubuntu Forums

---

### Post by wildmanne39 on 2018-03-09
Wow I did not expect it to be that long, just post it to pastebin then post the link here.

---

### Post by linuxcss22 on 2018-03-09
I wrestled with apparent missing file 'extra' part for this:
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85 
I see wireless on my panel now but not sure of stability,
what is last know working version of kernel that wireless worked?
And how do I get my system synced to that (already tried software update)
but says system is up to date?  (do I need to remove 116 via synaptic?)
and  Do I need to post another
dpkg --list | grep linux-image

also how do I get all the other kernels to not be listed in grub ...
I forgot to do a complete removal with synaptic? I'd like to free up that space.

---

