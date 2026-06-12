---
title: "VPN help -- unsupported protocol 0x2145"
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by troy7777 on 2005-04-22
hi! i'm running hoary and trying to get vpn to work. i got pptp, pptp-linux and kernel-patch-mppe installed.

when i issue:

pon wifi-place

everything seem to work. i don't get any error messages. but then when i start pinging outside address, i get an error that says:

Unsupported protocol: 0x2145

could anybody tell me what's wrong and how to fix it? do i need to compile the kernel?

any help would be appreciated. Thanks a lot!

---

### Post by troy7777 on 2005-04-27
anybody?  :)

---

### Post by alastair on 2005-04-27
Check the web first e.g.

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppc](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppc)

---

### Post by troy7777 on 2005-04-27
yup, did that. except for turning mppe on pptp server. didn't work either.

i've read that the kernel has to be patched for mppe support and pfc bug. now, i see that the kernel 2.6.10 has mppe built-in, but i don't know if it's the pfc bug (don't know what that is). is that patch included in the 2.6.10 kernel from the ubuntu archive?

so i could compile the kernel with the 2.6.10 patch (i think linux-source-2.6.10 already include that), but what to do with the pfc thing?

thanks for the help!  O:)

---

