---
title: "ubuntu 14.04 wireless not working BCM4313"
date: 2014-04-28
forum: Networking &amp; Wireless
---

### Post by maundr on 2014-04-28
Hello Ubuntu forum goers! you guys seems super helpful so maybe you have some insight to my problem. I cannot get ubuntu to connect with my wireless card broadcom BCM4313. I checked chilis super helpful sticky and it says that my card falls under special case #1 where i need to use the driver combination bcma and brcmsmac. How would i go about doing so? i know that brcmsmac is included in the kernel. What do i need to do to get them to work in a fresh install?

Thanks !

---

### Post by varunendra on 2014-04-28
Welcome to the forums maundr! :)

The brcmsmac driver should work out of box without requiring you to do anything extra. The only common case when it doesn't, is if you chose to "Install Updates" during installation of Ubuntu, or accepted the proprietary wireless driver by "Additional Drivers" option after installation. Both these actions install the proprietary driver "wl" which blacklists the brcmsmac, thus preventing it to load at startup.

If you have it (the proprietary one) installed, just purge (completely remove) it with the following command (to be run in a terminal which you can open with "Ctrl-Alt-T")-
```
sudo apt-get purge bcmwl-kernel-source
```
..and reboot.

If it still doesn't work, please post back the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by maundr on 2014-04-28
Thanks Varunendra ! I was able to get it working while playing around with it. 

I did this as you advised 
```
 sudo apt-get purge bcmwl-kernel-source 
```

and restarted I did a quick 
```
sudo lshw 
```

to check that the brmsmac driver was loaded and NOT the wl. This gave me limited wifi connectivity as that I could connect to my acces point but was not able to use the internet.

removing blacklist bcm43xx from blacklist.conf and restarting did the trick.

Thanks again!
~maundr

---

### Post by varunendra on 2014-04-28
> **maundr said:**
> removing blacklist **bcm43xx** from blacklist.conf and restarting did the trick.
Hmm.. that module is obsolete and no more exists in the kernel. So it must be just a coincidence or something else. But as long as it is working, who cares ! :)

If the connection is stable and satisfactory now, please mark the thread as [SOLVED] using "Thread Tools" link above the top post on this page. It helps others by indicating the thread contains a possible solution to the problem mentioned in its Title.

---

### Post by maundr on 2014-04-28
Marking as SOLVED
just a tip for others trying to get the driver working for some reason the driver is buggy when trying to connect to mixed b/g/n wireless as I was getting continous drops. It can be fixed with restarts or 

```
sudo modprobe -r brcmsmac
```
```
sudo modprobe brcmsmac
```

however a more permanent solution was to change my home wireless router to b/g wireless ONLY and I havent had a problem since. From what I can tell its a problem with the driver in the current kernel hopefully a better version or more compatible driver will be released eventually.

---

### Post by Garrett_Berg on 2014-08-21
Hello all,

I was having exactly the same problems and purging the driver fixed it! However, whenever I put the computer to sleep (by closing the lid) the wifi no longer works.

One solution is to type
> s[COLOR=#000000][FONT=Ubuntu Mono]udo modprobe -r brcmsmac
[/FONT][/COLOR]sudo modprobe brcmsmac

As maundr suggested.

Is there a way to do this every time I wake from sleep?

Thanks so much!

---

### Post by varunendra on 2014-08-21
Welcome to the forums Garrett!

> **Garrett_Berg said:**
> Is there a way to do this every time I wake from sleep?
Yes - just do that everytime you wake from sleep, nobody will stop you :p

Okay, bad joke, I know. The answer now..

Please try the simpler fix first -

Open a terminal (Ctrl-Alt-T) and run the following code in it -
```
echo 'SUSPEND_MODULES="$SUSPEND_MODULES brcmsmac"' | sudo tee /etc/pm/config.d/modules
```
Please note that there is the closing double-quote mark, followed by a closing single-quote mark after "brcmsmac" above. This will create a file with name "modules" in you /etc/pm/config.d directory, containing a single line -
```
SUSPEND_MODULES="$SUSPEND_MODULES brcmsmac"
```
..in it. It is supposed to automatically reload the module(s) mentioned in the line in double-quotes. If it works, nothing more is needed and you can stop here, letting us know that it worked.

However, if it doesn't work as expected, try what is suggested in this post : [http://ubuntuforums.org/showpost.php?p=13085936](http://ubuntuforums.org/showpost.php?p=13085936)

If that one works, let us know. If still not, it will probably best to start your own thread, posting a wireless_script report in it (mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) ), as well as clearly mentioning whatever you tried (including above) as a fix. Feel free to PM me to have a look at it, if you create one.

---

