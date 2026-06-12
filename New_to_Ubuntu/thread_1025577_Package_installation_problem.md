---
title: "Package installation problem"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Red Rebel on 2008-12-30
I downloaded Bit-Torrent 5.22_pyton_2.4.deb. When I clicked on the package, it gave me the option to install the package automatically, however, after install successfully completed, I can't find it anywhere to run it. I figured it would have showed up where transmission is, which is under applications--> Internet. I looked elsewhere, and still can't find it. Is there another step I must perform to get it to show in the menu? Any help with this would be greatly appreciated....

---

### Post by linux_tech on 2008-12-30
what is output of

```

apt-cache show Bit-Torrent

and 

dpkg --get-selections | grep Bit-Torrent 
```

---

### Post by Red Rebel on 2008-12-30
ah, no wonder it is not showing up. The install consisted of the terminal version only. Now I need to find where the gui install package is.. thanks a million...

---

### Post by Red Rebel on 2008-12-30
Do you know how I can go about finding the bit-torrnet gui deb package?

I cant seem to find it. Is there a way to do it with sudo apt get?

thanks.

---

### Post by Bucky Ball on 2008-12-30
Synaptics and search for bit torrent and see what the turns up ...

The gui could possibly be there. Sorry, on the wrong computer to check.

---

### Post by linux_tech on 2008-12-30
The command to install it should be something like
sudo dpkg -i dist/bittorrent_5.x.y_python2.z.deb

After installing close and reopen browser, then test by trying a download

---

### Post by Red Rebel on 2008-12-30
I was able to install the package properly. The package  I installed is a terminal version only. I am using for a bit torrent gui, which I can't seem to find.

---

### Post by linux_tech on 2008-12-30
bittorrent  requires the python 2.2 package. You should also install the packages libwxgtk2.4-python and mime-support, if you plan to use the GUI version of the client.

You can run ```
python -V
```
to see what version python you have installed

---

### Post by Red Rebel on 2008-12-30
I ran the command you said to run, and it cam up with python 2.5.2

---

### Post by linux_tech on 2008-12-30
this has some useful info -
[http://dessent.net/btfaq/](http://dessent.net/btfaq/)

---

