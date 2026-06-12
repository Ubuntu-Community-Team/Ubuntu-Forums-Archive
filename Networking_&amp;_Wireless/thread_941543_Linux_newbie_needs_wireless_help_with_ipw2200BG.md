---
title: "Linux newbie needs wireless help with ipw2200BG"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by mswfox on 2008-10-08
Hello Ubuntu Forums:

I am a complete newbie to Linux.  I installed Hardy Heron a few weeks ago, everything has been running great.  Wireless worked out of the box.  And then I had to get smart and try and install patched drivers for my Intel Pro Wireless 2200 BG that support packet injection.

Now, my wireless does not work at all.  When I used to "iwconfig" it would show my 2200BG as eth1.  Now when I run iwconfig it doesn't show anything as eth1 and it doesn't show my 2200BG at all, plus Ubuntu in the connections manager acts like I don't have a wireless card installed.  So I'm just trying to get back to a functional state at this point.  I have the official Intel ipw2200 driver package and I have the ieee80211 package.  I unpacked both of them but I don't know what to do to get them installed.  I already ran "sudo make" and "sudo make install" on both, but my wireless still does not work.  Also, if it helps any, in hindsight I realized that I did forget to "apt-get install build-essential" before I tried to install all of these drivers, but now I can't do it because I don't have a network connection.

Could anyone please explain to me how to get my wireless back to a functional state?  I'm posting in Windows XP right now (dual boot) so obviously the card itself still works just fine.

---

### Post by mswfox on 2008-10-08
Even a little bit of help pointing me in the right direction would be appreciated.

---

