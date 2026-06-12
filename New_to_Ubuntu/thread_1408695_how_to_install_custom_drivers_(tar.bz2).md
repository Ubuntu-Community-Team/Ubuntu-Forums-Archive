---
title: "how to install custom drivers (tar.bz2)"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by rid3 r3d on 2010-02-16
Hey everyone, 
I'm relatively new to Linux. Recently I bought a D-Link DWL-G122 to work alongside my built in wireless card. I found the driver that I need from here: [http://homepages.tu-darmstadt.de/~p_larbig/wlan/#rt2570]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/#rt2570")
I realize that I cannot install a compressed file like these, so I was wondering if someone could explain to me how to install this driver once I have extracted the files to another location.
Thanks!

---

### Post by HarrisonNapper on 2010-02-16
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hopefully, there's a solution that's less tl;dr and/or risky to your current drivers. In that guide, make sure not to uninstall all free drivers, just the one you are replacing. As I said, though, might be best to wait for someone who uses Gnome (not me) to say something like "right-click==solved" or something like that :)

---

### Post by rid3 r3d on 2010-02-16
Thanks for the input. I know how to blacklist the normal drivers, I am just unsure how to unpack and install that specific driver.

---

### Post by HarrisonNapper on 2010-02-18
In the case of that link, you would install it using Ndiswrapper if it's not supported in Ubuntu. Wish I could be of more help here, but that's about the extent of my knowledge. Hopefully, someone else will chime in who knows more about it.

---

### Post by wojox on 2010-02-18
Make sure you have build-essential installed:

```
sudo apt-get update && sudo apt-get install build-essential
```

Then you should be able to cd/to/downloaded.tar.bz2

```
tar xvjf filename.tar.bz2
```

Then 

```
ls
```

Look for directions. Usually it's ./configure, make, sudo make install

---

