---
title: "Shutdown mystery...."
date: 2009-10-11
forum: New to Ubuntu
---

### Post by cj13579 on 2009-10-11
Hi all,

I have some strange happenings going on when I shut down my Jaunty laptop down. I don't remember doing anything that may have caused this to happen and it's not a critical error (I don't think), it just means that it takes an age to shut my laptop down!

If someone could shed some light on the code below it would be much appreciated...

```
acpid exiting

nm-system-settings SCPlugin -Ifupdown devices removed (udi org/freedesktop/hal/devices/net_00_16_d3_65_d3_37
nm-system-settings SCPlugin -Ifupdown devices removed (udi org/freedesktop/hal/devices/net_00_c0_a8_f0_69_7e

[123.2728777] CIFS VFS: server not responding
[123.2722937] CIFS VFS: no response for CMD 50 mid 35
```

---

### Post by yeats on 2009-10-11
This is an old thread, but it may shed some light:

[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

### Post by mprince on 2009-10-11
Are you using Samba shares? If so, you should have a look at these:

[http://www.linuxquestions.org/questions/linux-general-1/samba-issue-when-doing-shutdown-cifs-vfs...-629390/](http://www.linuxquestions.org/questions/linux-general-1/samba-issue-when-doing-shutdown-cifs-vfs...-629390/)

[http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/](http://whereofwecannotspeak.wordpress.com/2007/12/25/unmount-samba-filesystems-before-shutdown-or-reboot/)

---

### Post by cj13579 on 2009-10-11
> This is an old thread, but it may shed some light:

[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

Thanks chrissharp123. The script on that link seemed to work a treat.

> Are you using Samba shares? If so, you should have a look at these:

[http://www.linuxquestions.org/questi...vfs...-629390/](http://www.linuxquestions.org/questi...vfs...-629390/)

[http://whereofwecannotspeak.wordpres...own-or-reboot/](http://whereofwecannotspeak.wordpres...own-or-reboot/)

mprince, thanks for this. If the scrip in chrisshap123's post doesn't work in the future I shall use your links which I have had a quick look at. I was using samba shares so these should be helpful! 

Many thanks again both!

---

