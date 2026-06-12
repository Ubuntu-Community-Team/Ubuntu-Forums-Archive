---
title: "Linksys WUSB54GC v3 WPA Issue"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by SideSwipe on 2009-10-25
Hey guys,

I'm having an issue with a Linksys WUSB54GC v3 wireless adapter using WPA for wireless security on Ubuntu 9.04. It seems that the network manager is getting stuck in some sort of loop after entering the security key for the network. After a few minutes, an input box will appear asking for the security key again (yes, I've confirmed that it is correct).

Initally I had an issue getting the OS to see the adapter, however I was able to solve that with this guide: [http://ubuntuforums.org/showpost.php?p=7262158&postcount=2](http://ubuntuforums.org/showpost.php?p=7262158&postcount=2)

At the bottom of the guide, it mentions that if you suffer from WPA problems, you should follow this guide: [http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

Unfortunately whenever I reach the final step to run wpa_supplicant I receive one of these errors:

[LIST]
[*]ctrl_iface exists and seems to be in use
[*]Could not configure driver to use in managed mode
[*]invalid option 'w'
[/LIST]
I'm very close to getting this working, but I don't know how to proceed from here. Will I be able to use the native drivers I downloaded on the first guide, or will I have to use ndiswrapper  and the Windows drivers?

Many thanks for any help you can give! :)

---

### Post by SideSwipe on 2009-10-26
After a quick chat with the people I work with, they seem to believe that wpa_supplicant isn't working properly as the adapter is able to see networks in range, and join those using WEP.

Can anyone shed any light on this? If you need more information, please ask :)

---

