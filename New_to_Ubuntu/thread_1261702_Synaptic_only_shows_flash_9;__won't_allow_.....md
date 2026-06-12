---
title: "Synaptic only shows flash 9;  won't allow ...."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by lexrexus on 2009-09-09
Hardy?: 8.04   
Synaptic only shows flash 9 (flash non-free) so I installed.  Wont allow upgrade to be checked - its grayed out.  Some site or other insisted on 10.
I see from other's posts that 10 is being installed by others from repositories.
[I un-installed swfdec-mozilla]
Why doesn't my synaptic show non-free 10.whatever?

Is 9 from installation cd and repositories won't load properly w/my 'peddle-up' connection?

How do I proceed?


Tnx!

---

### Post by nhasian on 2009-09-09
see if this page helps you:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by lexrexus on 2009-09-15
Thanks 4 reply nhasian!  I used your link and followed to get .deb for 8.04
[3100~ bits/sec..................]  Installation finished!
'Reinstall Package'???..'
I guess its installed ? and I ignore 'reinstall pkg?'
Did about:- whatever it was - and it didn't list it;  but listed other plugins.
closed Ff.  and in term. put/got:
jk@jk-desktop:~$ sudo dpkg -i install_flash_player_10_linux.deb
[sudo] password for jk: 
dpkg: error processing install_flash_player_10_linux.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 install_flash_player_10_linux.deb
HOW might I proceed??   :confused:

---

### Post by baltadt on 2009-09-15
Check out my thread on this exact thing....[http://ubuntuforums.org/showthread.php?t=1266540](http://ubuntuforums.org/showthread.php?t=1266540)

This should fix your problem. let me know if you still have problems.
If you are using mozilla instead of firefox.. subsitute mozilla where you see firefox.

---

### Post by lexrexus on 2009-09-16
Baltadt!

Thank you!  It worked!!  Made one adjustment b4 it would work:


sudo cp /home/USERNAME/Desktop/libflashplayer.so /usr/lib/firefox/plugins

HAD TO CHANGE TO what file was named on desktop by download; ABOVE did not work (username substituted properly):

sudo cp /home/USERNAME/Desktop/install_flash_player_10_linux.tar.gz /usr/lib/firefox/plugins
enter password   ...   .

\\:D/\\:D/\\:D/           Thank you!!!

---

### Post by baltadt on 2009-09-16
Glad I could help.

---

