---
title: "mounting network drives"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by heyneman on 2010-11-16
I've got a network drive at school that I need to get at from home occasionally.  It requires me to VPN first, so I've installed vpnc,  and after VPNing I can mount manually just fine.

I also have a second partition on my hard drive (Data).  When I log in it shows up in Nautilus, with the option to "mount and open" on first click. I would love it if I could do the same with my network drive, but I can't seem to figure out how.

Data doesn't show up in fstab anywhere (and I can't manually mount /media/Data via just that argument to mount).  So where does Nautilus get the info that I have another drive to mount so that it presents me the option?

Thanks,

-Barrett

---

### Post by Efros on 2010-11-16
You would need to run vpnc automatically before you try to mount the drives. I can remember putting together a script that incorporated a delay for starting compiz back in Ubuntu 8.04. You should be able to do something similar, connect the vpn initiate a delay to allow the vpn connection to be made and then initiate the drive mount. Someone with better scripting experience than me may be able to help you.

---

### Post by heyneman on 2010-11-17
Yeah, I figured as much.  However, when I'm in lab I don't need to VPN to access the drive, so I don't *need* to run vpnc every time I boot up (although I don't believe it's actually a problem if I do...)

I'm still curious about the other part of my question, if anyone knows: how does Nautilus know to put my other partitions in the left bar to "mount and open"?  Is it scanning /dev looking for sd** and hd** devices other than my main drive?

---

