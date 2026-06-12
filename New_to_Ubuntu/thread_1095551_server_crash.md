---
title: "server crash"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by rockerphil on 2009-03-13
ok, here's the deal. a good friend just brought me his Ubuntu 8.10 desktop machine that he's been using for a server (primarily a data storage machine). well here's where it gets fun. when the machine boots it'll give me the Ubuntu splash screen, but then returns this error code:

```
init: unable to execute "/bin/sh" for rcS: Exec format error
init: rcS main process (2316) terminated with status 255
init: unable to execute "/bin/sh" for rc-default: Exec format error
init: rc-default main process (2325) terminated with status 255
```

i've personally never encountered this particular error code before, but from what my buddy says he didn't have the server hooked up to a UPS and the power went out](*,) i've tried booting in to recovery mode to no avail, so now i'm kickin this one over to you guys to see if i can get it figured out. oh, also, i'm trying not to reformat the HDD. much thanx in advance,

Phil

---

### Post by rockerphil on 2009-03-13
anyone?

---

### Post by HermanAB on 2009-03-13
Boot with a Live CD, copy the data off toa USB disk drive, re-install the server and put the data back.  In the mean time, tell him to go and buy a UPS.

Cheers,

Herman

---

### Post by rockerphil on 2009-03-13
thanx for the response, it's much appreciated, but i'm trying to aviod having to reinstall the OS because the server is normally on a network with some other users added to it. he did give me the external HDD with the backup data on it, but i'd like to save him the trouble of having to reconfigure everything he's already done. is there some way to restore the /bin/sh file? possibly from a Live CD? much thanx in advance,

Phil

---

### Post by rockerphil on 2009-03-14
ok, just a quick update. I've made a little bit of headway in the boot process by restoring /bin/sh and /bin/dash and relinking /bin/sh to /bin/dash, so i get a LITTLE further in the boot process and was able to successfully got through an fsck in recovery mode, but now when i attempt resume normal boot i get this error message:

```
/bin/sh can't open chown
```

thus stopping the boot process in it's tracks. any suggestions folks? much thanks in advance,

Phil

---

### Post by rockerphil on 2009-03-15
ok, still lookin for some help on this one guys, cus i'm baffled on this one. and please remember, i'm trying to avoid having to reinstall the OS. any suggestions are appreciated. much thanx

Phil

---

### Post by adult swim on 2009-03-15
have you compared the output from the live cd ls -l /bin to the one on the hard drive to make sure your stuff has the right permissions?  on some test installs, i have copied entire directories from the live cd to my install and had luck.  maybe you could try that with /bin?  if this is a terrible idea, anyone feel free to chime in.

---

### Post by rockerphil on 2009-03-16
ok, just an update folks. i finally succumbed to reinstalling the OS. i installed Xubuntu 7.10 (i figured i could get it updated to at least 8.04 after installing) well this is where it gets fun. the Ethernet card shows up when i run lspci, but for some reason i can't get online with it. lspci shows that the Ethernet card is a Realtek RTL111/8168B PCI express gigabit PCI Ethernet controller. i've personally got a Realtek Ethernet card in my personal machine which runs Ubuntu, so i'm baffled on why it doesn't connect to the net. DID find this thread

[http://ubuntuforums.org/showthread.php?t=723569](http://ubuntuforums.org/showthread.php?t=723569)

but i don't have any wireless connections to connect through, it's either the Ethernet card or nothing. so any type of help is greatly appreciated. much thanks in advance,

Phil

---

### Post by rockerphil on 2009-03-16
nevermind folks, just got the driver installed and it's now online. thanks for the help, 

Phil

---

