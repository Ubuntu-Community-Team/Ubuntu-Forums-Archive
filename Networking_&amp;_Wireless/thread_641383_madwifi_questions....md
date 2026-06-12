---
title: "madwifi questions..."
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by Peter.J.McDonald on 2007-12-15
I had a question, now I am installing madwifi tonight, does this update the network manager to then display a wireless connection...? or is it a seperate program causing me to manually switch to wired when I am at my desk? (running ubuntu 7.10)

reason I ask is I have an atheros card in my copmputer and ran the windows wireless driver program, installed my driver and it shows as working thru that program, but wireless still does not work, nor does it show in the network manager area of the desktop.

now I assume madwifi is set to correct this? or I could be wrong... just trying to see what exactly this does since their website and online info is very cryptic.

Thanks to anyone willing to help.

---

### Post by spd106 on 2007-12-15
It's a very complex issue.

The Madwifi driver module is delivered with the kernel, however because madwifi requires some non-free binary code to work it has a separate module that comes with the restricted modules package. This is why it appears in the Restricted Drivers Manager.

Unfortunately because of the binary part the Madwifi developers can't add support for new cards very quickly. So many of the newest cards do not work without having to switch to Ndiswrapper (Windows Wireless Drivers) instead.

So the preferred driver is Madwifi, but if that doesn't work then you should be able to use Ndiswrapper.

Ubuntu 7.10 has the latest version of Madwifi, so there's no point in downloading it from the madwifi.org website unless you go for the very latest svn code. I wouldn't recommend doing that unless you know exactly what you're doing.

---

