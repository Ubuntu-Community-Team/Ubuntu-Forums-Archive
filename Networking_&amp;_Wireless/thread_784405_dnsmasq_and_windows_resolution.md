---
title: "dnsmasq and windows resolution"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by debianbryan on 2008-05-06
i've been banging my head on the wall over this for the past month and haven't found a solution through google or through the forums here and i'm wondering if anybody else has experienced the same issues and knows what's happening:

i have a netgear switch serving dhcp and assigning my debian box as the primary dns.  the debian box is running dnsmasq, and does a fantastic job of local hostname resolution for my small network.  i assign my isp dns servers as the secondary and third dns servers so i can resolve external names.

everything works fine and dandy, i can resolve local non-qualified hostnames because the local domain suffix is automatically appended, and all external addresses resolve flawlessly.  BUT after a while the Windows machines will eventually lose the ability to resolve local names (not all at the same time, and it does not coincide with dhcp lease expiration).  external names still work, reverse name resolution via "ping -a" occasionally works, and nslookup tells me that the dns server is still resolving correctly.  it appears that the windows machines try to use the secondary isp dns server to resolve my local names (which obviously won't work), and i don't understand why it won't fail back and use the primary dns server which is working fine!  my ubuntu boxes never exhibit this issue.

i'm hoping somebody can tell me what i've done wrong (i can provide all the relevant .conf files if needed)

---

