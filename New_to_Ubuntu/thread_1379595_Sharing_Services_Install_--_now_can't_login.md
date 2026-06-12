---
title: "Sharing Services Install -- now can't login"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by omghahalol on 2010-01-12
I was attempting to share a folder, and Ubuntu said that sharing services needed to be installed. I proceeded to install and they said a reboot was necessary. It hung on the reboot so I manually pulled power and now when I attempt to login nothing will work. 

I get to the GUI and automatic login doesn't work, states 'cannot authenciate user' no matter what I choose (my user, auto, or other). I ctrl+alt+f1 and get to CLI and I can't login as my user or as root, no error message displayed, just jumps back to: 

> Ubunto 9.10 compname tty1
compname login:Any ideas on what to do?

Thank you.

---

### Post by quixote on 2010-01-13
Just guessing, I'd say there was some file corruption during the sudden shutdown, and that unfortunately that included important system files.  (If you can't avoid physically pulling the power, try to wait until the indicator says the hard drive isn't spinning.)  Unless you have a system backup, it looks like you may be facing a reinstall. :(  (File corruption on sudden shutdown isn't just an ubuntu problem.  Try not to do that on any system.  Win 7, Mac, Winxp, or DOS!)

To try to recover your data first (assuming you have data on there that you want to keep), try booting with an ubuntu livecd, and see whether you can read the hard drive or any part of it.  If you can, move your data to some other media right away.  If you can't see it, and you really want the data, then it's time to try testdisk for recovery or possibly photorec.  But first let us know where things stand.

(PS.  Is that "LA" as in Los Angeles?  That's where I am too. :) )

---

