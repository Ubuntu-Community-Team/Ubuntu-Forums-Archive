---
title: "Dual-Boot Ubuntu Trusty Tahir and Windows 7 Wifi problems"
date: 2014-06-30
forum: Networking &amp; Wireless
---

### Post by mac-c on 2014-06-30
Ok, I'm a complete noob to Linux, but I am getting a Raspberry Pi on July 5th, so I want to learn more about Linux before then. The only thing stopping me, well, is wifi problems. At my fathers house, the internet works fine (He knows what he's doing), but at my mother's house, the internet simply won't work on Ubuntu. It says I'm connected to the wifi modem, or router. I don't know, but I am connected. My mom suggested we call the internet company, but I don't think they're going to know anything a bout Ubuntu. People say that it's a problem with Windows, which the internet works on, an that I should reboot from Ubuntu twice, but that didn't work. I can't find this problem on the forums at all. When I try to use Firefox on Ubuntu, I can't even load the homepage, and I really want to use Ubuntu, as I would use it any day over Windows. I'm willing to try anything at this point! Please help!

---

### Post by jeremy31 on 2014-06-30
Open a terminal window in Ubuntu CTRL+ALT+t and post the results of this ```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```

---

### Post by mac-c on 2014-06-30
Ok, I managed to take that code, put it in a text file in Windows, open it in Ubuntu, and get the results from that. Here they are:

--2014-06-30 18:12:05--  [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 50.19.116.199
Connecting to dl.dropbox.com (dl.dropbox.com)|50.19.116.199|:443... connected.
Unable to establish SSL connection.

---

### Post by mac-c on 2014-06-30
[COLOR=#000000]Ok, I managed to take that code, put it in a text file in Windows, open it in Ubuntu, and get the results from that. Here they are:[/COLOR]

[COLOR=#000000]--2014-06-30 18:12:05-- [/COLOR][https://dl.dropbox.com/s/qjc87hzk1z5...ireless_script]("https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script")
[COLOR=#000000]Resolving dl.dropbox.com (dl.dropbox.com)... 50.19.116.199[/COLOR]
[COLOR=#000000]Connecting to dl.dropbox.com (dl.dropbox.com)|50.19.116.199|:443... connected.[/COLOR]
[COLOR=#000000]Unable to establish SSL connection.[/COLOR]

---

### Post by jeremy31 on 2014-07-01
Try it this way, from windows use this ```
https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
``` and then copy the file to your /home on ubuntu.  And from ubuntu in terminal ```
chmod +x wireless_script && ./wireless_script
``` then copy the wireless-info.txt or .tar.gz back to windows to post here.  If you can connect ubuntu with a wired connection, you should be able to run the code from my first post

The explanation in varunendras post about how to use without internet connection might be better [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

---

### Post by mac-c on 2014-07-01
Ok, I'll get back to you on that. I can connect via wired connection, so that's good.

---

