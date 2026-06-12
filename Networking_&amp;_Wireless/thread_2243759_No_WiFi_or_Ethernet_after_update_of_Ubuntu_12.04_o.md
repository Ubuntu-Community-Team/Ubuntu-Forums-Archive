---
title: "No WiFi or Ethernet after update of Ubuntu 12.04 on Dell Inspiron 1501"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by ljmartz on 2014-09-10
I have a Dell Inspiron 1501 running dual boot Ubuntu 12.04 with Windows Vista.  I just completed updates in Ubuntu and have lost my WiFi connection.  Having experienced WiFi connectivity problems in the past, I connected the laptop to my ethernet connection so that I could redownload the drivers and the laptop shows I have an eithernet connection, but I cannot get any data to pass trough the connection.  All attempts to use a browser return a no network error.  Any command that uses an internet connection fails.  In my Network connection box under the wireless tab, it does show "firmware missing."

Any help to resolve this problem is greatly appreciated.

---

### Post by varunendra on 2014-09-11
A wild guess is that you are probably another victim of the recent change in the linux-firmware-nonfree package, but the usual fix won't work without a working internet connection which you don't seem to have due to ethernet also not working.

So.. instead of posting a full-length post based on guess, let's first confirm the status. Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by ljmartz on 2014-09-11
As instructed from the link, I ran ```
wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
```  It returned ```
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Name or service not known. wget: unable to resolve host address `dl.dropbox.com'
```

---

### Post by Hadaka on 2014-09-11
Hi, please open a terminal.ctrl/alt/t and do..
(you dont need internet access for this)
Please COPY  and paste
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```
post the output
thanks.

---

### Post by varunendra on 2014-09-11
..and the link also mentions in **bold** how to download and **run the script without internet**. Please try that method instead.

---

### Post by ljmartz on 2014-09-11
```
lspci -n | egrep '0200|0280' | awk '{print $3}'
```

Returns
```
14e4:4311 
14e4:170c 


```

---

### Post by ljmartz on 2014-09-11
> **varunendra said:**
> ..and the link also mentions in **bold** how to download and **run the script without internet**. Please try that method instead.

Sorry about missing the step 2 part.  Tired and stressed...bad combinations for reading instructions.  Output of script is attached.

---

### Post by Hadaka on 2014-09-11
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
BOOT
your wired connection should now be working, please connect
to the internet and do..
```
sudo apt-get update
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
disconnect the ethernet cable and test wireless.
** Ignore any offer to install a proprietary or additional driver
thanks.

---

### Post by varunendra on 2014-09-11
Hmm, not exactly what I thought, but still about 98% close.. You ARE a victim of the linux-firmware-nonfree change.

Not sure why your ethernet is not working, maybe try changing your DNS. Please try this in a terminal -
```
ping -c4 8.8.8.8
```
If it returns ping replies, changing your current DNS to 8.8.8.8 and 8.8.4.4 (or any other working DNS) should work.

If the ethernet starts working, install the firmware required by your wireless card with -
```
sudo apt-get install firmware-b43-installer
```

If it doesn't work, please follow this post to install it offline : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

We'll deal with Ethernet later if required.

**EDIT:**
Hadaka won the 'who-posts-first-race', but touching the wrong target :p
The "linux-firmware-nonfree" method died this morning. See this bug report : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882) ..and the comments #3, #4 on it.

**PS:**
ljmartz, next time try the newer script (linked to my signature below). It is now much better than the old one that you used. :)

---

### Post by ljmartz on 2014-09-11
It seems that sleeping on it, at least in this case was benificial.  When I plugged ethernet in this afternoon, the ethernet was recongized and allowed data to transmit.  So with ethernet operational, ran ```

sudo apt-get install firmware-b43-installer 
```

Answered yes to all prompts and installed new firmware.  Rebooted, unplugged ethernet and WiFi is back!  Posting this reply using WiFi connection.  For future reference, what files should I not update so that I do not encounter the linux-firmware-nonfree change problem again?

---

### Post by varunendra on 2014-09-11
> **ljmartz said:**
> For future reference, what files should I not update so that I do not encounter the linux-firmware-nonfree change problem again?

I'm sure it will be automatically resolved in future updates, but for now, I *believe* it is a very good idea to simply purge the "linux-firmware-nonfree" package from your system if you installed it only for b43 -
```
sudo apt-get purge linux-firmware-nonfree
```

Alternatively, you can simply copy your /lib/firmware/b43 directory as a backup, and just restore it IF the firmware files/directory goes missing again (due to linux-firmware-nonfree update).

---

