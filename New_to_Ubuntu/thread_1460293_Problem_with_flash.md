---
title: "Problem with flash"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by OneLine on 2010-04-22
Hi, I installed flash and noticed it seems not to be stable, I went to [http://london.speedtest.net](http://london.speedtest.net) to try test my broadband speed but when I click the button to start the test nothing happens, I went to youtube to try a video, a video will play but I can't pause it, have I done something wrong?, I'm using the x64 version of Ubuntu. Thank You.

---

### Post by -humanaut- on 2010-04-22
I think its problems with flash player with the 64bit environment I've had some trouble with it myself

---

### Post by tom.swartz07 on 2010-04-22
Hey you two. 

Lets get you set up with Flash for your x64 system. The version that's in the software center is for 32 bit computers. 

Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players.

There is a really dead simple script that you could use to remove the offending programs, highlighted here: [http://ubuntuforums.org/showpost.php?p=8666948&postcount=72](http://ubuntuforums.org/showpost.php?p=8666948&postcount=72)


Once everything is all removed, you could start fresh and get the official Flash plugin.

Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type

```
gksu nautilus /usr/lib/flashplugin-installer
```

This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type
```
gksu nautilus /usr/lib/mozilla/plugins
```
Paste the same file into this folder, again agreeing to overwrite the current version 

Theres a PPA if you want to use it to keep your flash updated
```
sudo add-apt-repository ppa:sevenmachines/flash
```

If you are still having problems, try running this code in the terminal to make sure everything is up to date.
```
sudo apt-get update && sudo apt-get install flashplugin64-installer
```


And.. Thats it!

---

### Post by OneLine on 2010-04-23
Hi, Thanks for your reply, when I Hit ALT+F2 and typed *gksu nautilus /usr/lib/flashplugin-installer *I got this error message, *Could not find "/usr/lib/flashplugin-installer".*

---

### Post by xumuk37 on 2010-04-23
you can do this just copying libflashplayer.so downloaded from Adobe Labs to /usr/lib/mozilla/plugins/ folder and restarting the browsers...

---

### Post by OneLine on 2010-04-23
> **xumuk37 said:**
> you can do this just copying libflashplayer.so downloaded from Adobe Labs to /usr/lib/mozilla/plugins/ folder and restarting the browsers...

Hi, thanks for your fast reply, brilliant it's working now, thank you again.

---

### Post by xumuk37 on 2010-04-23
Welcome)

---

