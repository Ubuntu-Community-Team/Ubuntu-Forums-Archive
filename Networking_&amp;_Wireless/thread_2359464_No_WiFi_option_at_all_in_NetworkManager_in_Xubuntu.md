---
title: "No WiFi option at all in NetworkManager in Xubuntu 16.04"
date: 2017-04-24
forum: Networking &amp; Wireless
---

### Post by themusicman on 2017-04-24
Hi All

Have successfully installed Xubunto 16.04 on an old Macbook into dual boot mode, and it boots up fine, except there are no WiFi options available at all.  I can't see any hotspots or WiFi access points and am not sure where to start as Linux is all new to me!

Happy to use Terminal - with help - and am wondering if there's anyone out there who knows what I do next, please?

Thanks.

---

### Post by slickymaster on 2017-04-24
Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself.

---

### Post by themusicman on 2017-04-24
> **slickymaster said:**
> Please download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself.

Thanks for this!

Please excuse the noobiness!!I must ask... how do I run this script? And I assume you mean run it from within Xubuntu?  If so, I need to download it on another machine and copy it across via a USB stick or similar as I can't get on the net to download it when I am in Xubuntu!

The joys, eh! :)

---

### Post by slickymaster on 2017-04-24
> **themusicman said:**
> Thanks for this!

Please excuse the noobiness!!I must ask... how do I run this script? And I assume you mean run it from within Xubuntu?  If so, I need to download it on another machine and copy it across via a USB stick or similar as I can't get on the net to download it when I am in Xubuntu!

The joys, eh! :)

Yes, you have to run it from within the Xubuntu box. If you're able to download it on another computer, just do it and copy it to the Xubuntu install, the open a terminal window in the folder where you copied it and run the following```
chmod +x wireless-info
./wireless-info
```

---

### Post by themusicman on 2017-04-24
> **slickymaster said:**
> Yes, you have to run it from within the Xubuntu box. If you're able to download it on another computer, just do it and copy it to the Xubuntu install, the open a terminal window in the folder where you copied it and run the following```
chmod +x wireless-info
./wireless-info
```

Right, what seems to be happening is that when I copy that file to the USB stick to port across to my other Mac, the file that it creates when I download it is called

wireless-info.txt

I then copy that to my USB, and insert it into the other machine.  When I open a terminal from the folder in Xubuntu where I have copied that file, I get '**No such file or directory**'

Sorry for beeing a noob! :)

---

### Post by slickymaster on 2017-04-24
Can you please post here in the thread the output you get from```
ls -la /path_to_folder_where_script_is
```

---

### Post by themusicman on 2017-04-24
> **slickymaster said:**
> Can you please post here in the thread the output you get from```
ls -la /path_to_folder_where_script_is
```

Sure, sir, here you go.

Also... I did a google search for the script, and found it on Github, so downloaded it from there and was able to copy the extracted Zip contents to Xubuntu.  The image shows the output of the command you requested after opening a terminal window within the USB drive containing that script.

[ATTACH=CONFIG]274745[/ATTACH]

---

### Post by Hadaka on 2017-04-24
Hi, please post the output of..
```
lspci -n | awk '/0200|0280/{print$3}'
```
Thanks

---

### Post by themusicman on 2017-04-24
> **Hadaka said:**
> Hi, please post the output of..
```
lspci -n | awk '/0200|0280/{print$3}'
```
Thanks

Sure, no pic needed this time as it was easy to type it!

14e4:4328
11ab:436a

:)

---

### Post by Hadaka on 2017-04-24
Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```


**IF you have NO internet connection ...go here
[https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347](https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347)

keep us informed.
thanks

---

### Post by themusicman on 2017-04-24
Hi Hadaka - thanks for this.  I do this a line at a time, yes?

Sorry for the noobiness, not used these scripts before so want to make sure I do it right.

---

### Post by LastDino on 2017-04-24
Yes, line at a time

---

### Post by themusicman on 2017-04-24
> **LastDino said:**
> Yes, line at a time

Ok, doing so now, but line 3 didn't run, said no such file!  I continued :)

Am Excited :)

---

### Post by themusicman on 2017-04-24
> **Hadaka said:**
> Hi, from a working wired connection please do..
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```


**IF you have NO internet connection ...go here
[https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347](https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347)

keep us informed.
thanks

Well Hadaka... just so you can sleep easier tonight, I thought I'd let you know that I am posting this from my Macbook, running Xubuntu 16.04, connected to the internet via WiFi on my iPhone hotspot.

Wohooooooo... how awesome is this.

Thanks so much for your help. Really appreciated.

Will mark this as solved.

---

### Post by Hadaka on 2017-04-24
Hi, themusicman, Glad that worked for you.
I usually post a note saying "Ignore any file not found
or error message" on those commands. My apologies
for not doing so. Thank you for marking your thread solved.

---

