---
title: "ldconfig"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by kalhua on 2011-06-25
Hello, I have been trying to get Ubuntu 10.04 LTS up and running with my main purpose being the use of XBMC.  I have just about gotten everything working the way I want but am having an issue that I have not been able to resolve.  I think it is very basic but unfortunately my searching a yielded me no usable results.  The issue is that during the final stages of installing XBMC from command line the following error is produced:

/sbin/ldconfig.real: Can't link //usr/lib/xbmc/system/players/dvdplayer//build/buildd/xbmc-11.00~git20110625.e1a0b08/system/players/dvdplayer/libdvdcss-i486-linux.so to libdvdcss-i486-linux.so
/sbin/ldconfig.real: Can't link //usr/lib/xbmc/system/players/dvdplayer//build/buildd/xbmc-11.00~git20110625.e1a0b08/system/players/dvdplayer/libdvdnav-i486-linux.so to libdvdnav-i486-linux.so

I do not have a clue of how to fix it.  I did do some looking around and found both libdvdcss-i486-linux.so & libdvdnav-i486-linux.so located in the following path: /usr/lib/xbmc/system/players/dvdplayer

I can get xbmc to run but it immeadiately crashes when I attempt to play an audio file.  I am not sure if the above error is even the cause but figured I may as well try to get it resolved hopefully fixing the issue and learning something in the process.

Thanks

---

