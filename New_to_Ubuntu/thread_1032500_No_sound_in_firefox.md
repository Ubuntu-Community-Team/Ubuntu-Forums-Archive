---
title: "No sound in firefox"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by numbness05 on 2009-01-06
Hi everyone

Have Ubuntu 8.10 installed through wubi.
I have every thing up and running other than the audio when streaming video on the net Youtube for example...

Any bright ideas please anybody??

Many thanks:D

---

### Post by spcwingo on 2009-01-06
Try:

```
sudo apt-get install libflashsupport
```

It says it won't work with flash 10, but it's working for me. ;)

---

### Post by numbness05 on 2009-01-06
many thanks but unfortunately it hasn't worked I'll keep cracking away at it though....:D

---

### Post by spcwingo on 2009-01-06
Have you tried flash 9 from adobe's web site?

---

### Post by numbness05 on 2009-01-06
I haven't no..I am fairly new to this and until you suggested flash 10  I had no idea what I was facing :D I shall try flash 9 now

Many thanks 
Support like this doesn't exist in Windows!

---

### Post by numbness05 on 2009-01-06
No no luck when it came to installing flash 9 can only do it using command line and I'm not to great with it...:(

---

### Post by spcwingo on 2009-01-06
To do that with minimal command line:

Download flash 9 from here:

[http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz]("http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz")

choose "save file" and save to your home directory.  Now open your home directory and double click the file named flash_player_9_linux_dev.tar.gz.  That will open the file with your archive manager.  Double click the file shown inside of the archive manager, then plugin, then debugger.  That will show another archive named libflashplayer.so.tar.gz.  Click on it once to highlight it.  Then choose extract at the top and extract to your home directory.  Now open your home directory again and double click the file named libflashplayer.so.tar.gz.  Click the only file listed in your archive manager once and again choose extract.  Once again extract to your home directory.  Now open a terminal and type:

```
gksu nautilus
```

Enter your password when prompted and nautilus will open as root.  Navigate to your home directory and right click the file named libflashplayer.so.  Choose cut and then navigate to /usr/lib/firefox-addons/plugins/  Then paste under that directory.  Right click after pasting and select the permissions tab.  Change the ownership to root with read/write access.  Now below that change the group to root with read only access.  Finally, below that change others access to read only.  You should now be all set as far as flash.  If just the sound doesn't work again, try reinstalling libflashsupport through synaptic.  Let me know if this get the job done.

---

### Post by markbuntu on 2009-01-06
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

