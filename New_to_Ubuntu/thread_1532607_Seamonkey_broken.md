---
title: "Seamonkey broken"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by graceful1 on 2010-07-16
Recently, I installed Lucid. The quick and dirty is I cannot get Seamonkey to work. Period.

I used the Synaptic Package Manager to install Seamonkey.
Unfortunately, this was Seamonkey 2.0.4, while the latest stable build is actually 2.0.5.

So I have tried to install Seamonkey 2.0.5 following the directions here:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

I ran 
```
sudo apt-get install seamonkey-mozilla-build
```
 
Then I did these commands:
```
sudo apt-get update
```
and 
```
sudo apt-get upgrade

```

This is what was returned after the upgrade command:
```
The following packages will be upgraded:
  libusb-0.1-4 libvte-common libvte9 python-vte seamonkey seamonkey-browser
  seamonkey-chatzilla seamonkey-mailnews
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.8MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

I entered 'y' and the upshot of it is that a replacement Seamonkey was installed that appears to be the right version. However in my Application -> Internet menu, I now have THREE Seamonkeys, one called "Mozilla Build of Seamonkey," and NONE of them work when selected.

Here is a dump of what was on my terminal as it was installing, in case it is any help.

```
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libusb-0.1-4 2:0.1.12-14ubuntu0.2 [20.5kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libvte-common 1:0.23.5-0ubuntu1.1 [41.2kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libvte9 1:0.23.5-0ubuntu1.1 [554kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main python-vte 1:0.23.5-0ubuntu1.1 [16.5kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe seamonkey-mailnews 2.0.5+build1+nobinonly-0ubuntu0.10.04.1 [1,832kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe seamonkey-chatzilla 2.0.5+build1+nobinonly-0ubuntu0.10.04.1 [355kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe seamonkey-browser 2.0.5+build1+nobinonly-0ubuntu0.10.04.1 [12.0MB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe seamonkey 2.0.5+build1+nobinonly-0ubuntu0.10.04.1 [25.8kB]
Fetched 14.8MB in 1min 25s (174kB/s)                                           
(Reading database ... 196856 files and directories currently installed.)
Preparing to replace libusb-0.1-4 2:0.1.12-14ubuntu0.1 (using .../libusb-0.1-4_2%3a0.1.12-14ubuntu0.2_i386.deb) ...
Unpacking replacement libusb-0.1-4 ...
Preparing to replace libvte-common 1:0.23.5-0ubuntu1 (using .../libvte-common_1%3a0.23.5-0ubuntu1.1_all.deb) ...
Unpacking replacement libvte-common ...
Preparing to replace libvte9 1:0.23.5-0ubuntu1 (using .../libvte9_1%3a0.23.5-0ubuntu1.1_i386.deb) ...
Unpacking replacement libvte9 ...
Preparing to replace python-vte 1:0.23.5-0ubuntu1 (using .../python-vte_1%3a0.23.5-0ubuntu1.1_i386.deb) ...
Unpacking replacement python-vte ...
Preparing to replace seamonkey-mailnews 2.0.4+nobinonly-0ubuntu1 (using .../seamonkey-mailnews_2.0.5+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement seamonkey-mailnews ...
Preparing to replace seamonkey-chatzilla 2.0.4+nobinonly-0ubuntu1 (using .../seamonkey-chatzilla_2.0.5+build1+nobinonly-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement seamonkey-chatzilla ...
Preparing to replace seamonkey-browser 2.0.4+nobinonly-0ubuntu1 (using .../seamonkey-browser_2.0.5+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Unpacking replacement seamonkey-browser ...
Preparing to replace seamonkey 2.0.4+nobinonly-0ubuntu1 (using .../seamonkey_2.0.5+build1+nobinonly-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement seamonkey ...
Processing triggers for python-support ...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up libusb-0.1-4 (2:0.1.12-14ubuntu0.2) ...

Setting up libvte-common (1:0.23.5-0ubuntu1.1) ...
Setting up libvte9 (1:0.23.5-0ubuntu1.1) ...

Setting up python-vte (1:0.23.5-0ubuntu1.1) ...

Setting up seamonkey-browser (2.0.5+build1+nobinonly-0ubuntu0.10.04.1) ...

Setting up seamonkey-mailnews (2.0.5+build1+nobinonly-0ubuntu0.10.04.1) ...

Setting up seamonkey-chatzilla (2.0.5+build1+nobinonly-0ubuntu0.10.04.1) ...

Setting up seamonkey (2.0.5+build1+nobinonly-0ubuntu0.10.04.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for menu ...
grace@hermione:~$ 
```



I am really quite clueless about this and would appreciate any help.
Thanks,
G.

---

### Post by yeats on 2010-07-16
What is the output from the command line when you type

```
seamonkey
```?

---

### Post by mkvnmtr on 2010-07-16
If it was my system I would open synaptic and search for seamonkey. Then I would uninstall and remove  every instance of seamonkey I found. Then I would go to my home folder and find the .mozilla folder and delete the semonkey folder inside it. Then I would install the seamonkey mozilla-build. This will not save any bookmarks you may have had but if you have never gotten it to work maybe you do not yet have bookmarks to save.

---

### Post by graceful1 on 2010-07-17
> **chrissharp123 said:**
> What is the output from the command line when you type

```
seamonkey
```?


The cursor blinks for a few seconds and then I get the prompt, so in a word, nothing.

---

### Post by graceful1 on 2010-07-17
> **mkvnmtr said:**
> If it was my system I would open synaptic and search for seamonkey. Then I would uninstall and remove  every instance of seamonkey I found. Then I would go to my home folder and find the .mozilla folder and delete the semonkey folder inside it. Then I would install the seamonkey mozilla-build. This will not save any bookmarks you may have had but if you have never gotten it to work maybe you do not yet have bookmarks to save.

I did exactly what you said, and unfortunately, it still doesn't work. :-( I have a "Seamonkey" and a "Mozilla build of Seamonkey" in the Applications -> Internet menu, and neither one works.

---

### Post by techunit on 2010-07-17
ok well lets try this shall we... first lets get rid of sea monkey from your system...

```
sudo aptitude purge seamonkey
```

Then lets try to find a ppa...

---

### Post by graceful1 on 2010-07-17
> **mkvnmtr said:**
> If it was my system I would open synaptic and search for seamonkey. Then I would uninstall and remove  every instance of seamonkey I found. Then I would go to my home folder and find the .mozilla folder and delete the semonkey folder inside it. Then I would install the seamonkey mozilla-build. This will not save any bookmarks you may have had but if you have never gotten it to work maybe you do not yet have bookmarks to save.

Oh ****. I just realized that I deleted the entire .mozilla folder. I think this is very bad. Now what do I do?

---

### Post by mkvnmtr on 2010-07-17
What you have deleted is settings for Firefox, Thunderbird if you have it installed and Seamonkey. The folder will come back but without any settings. You will have to do your bookmarks and add ons again. Not a problem unless you do not have your bookmarks backed up. If you have seamonkey listed in the menu it was not removed in synaptic. The above command to remove and purge should do it. Then you should be working.

---

### Post by techunit on 2010-07-18
Um do you understand what seamonkey is? It is firefox thunderbird sunbird an IRC client and a html editor in one... you just could install firefox thunderbird and sunbird and get the same functionality..

---

### Post by graceful1 on 2010-07-21
> **techunit said:**
> ok well lets try this shall we... first lets get rid of sea monkey from your system...

```
sudo aptitude purge seamonkey
```

Then lets try to find a ppa...


I would love to find a ppa, but so far I have not. :-( I have retried adding Ubuntuzilla's source to my sources list and then doing "sudo apt-get install seamonkey". It seems to install okay, but then when I select Applications --> Internet --> Mozilla Build of Seamonkey, it TRIES to start -- that is, you see the tab at the bottom of the screen saying "Starting Mozilla Build of Seamonkey", but then the tab disappears, and the browser is not running. :-(

Entering "seamonkey" at the command line does nothing as well.

---

### Post by graceful1 on 2010-07-21
> **techunit said:**
> Um do you understand what seamonkey is? It is firefox thunderbird sunbird an IRC client and a html editor in one... you just could install firefox thunderbird and sunbird and get the same functionality..

Yes, I understand what SeaMonkey is. I have my own personal reasons why I want both Firefox and SeaMonkey installed. It was working fine before, and I was able to do updates easily using the old instructions [here]("https://help.ubuntu.com/community/SeaMonkey"), but now they are no longer valid. Following the instructions [here]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page") doesn't seem to work either. I would be grateful for any help.

---

### Post by ubunterooster on 2010-07-21
> **graceful1 said:**
> Oh ****. I just realized that I deleted the entire .mozilla folder. I think this is very bad. Now what do I do?
go to the trash and "restore" the Mozilla folder

---

### Post by ubunterooster on 2010-07-21
> **graceful1 said:**
> I would love to find a ppa, but so far I have not. :-( I have retried adding Ubuntuzilla's source to my sources list and then doing "sudo apt-get install seamonkey". It seems to install okay, but then when I select Applications --> Internet --> Mozilla Build of Seamonkey, it TRIES to start -- that is, you see the tab at the bottom of the screen saying "Starting Mozilla Build of Seamonkey", but then the tab disappears, and the browser is not running. :-(

Entering "seamonkey" at the command line does nothing as well.
Remove that PPA, and install the version of seamonkey that is in the regular Ubuntu repositories

---

### Post by graceful1 on 2010-07-21
> **ubunterooster said:**
> go to the trash and "restore" the Mozilla folder

Thanks.
Still can't get SeaMonkey to work even after purging and reinstalling. No ppa can I find.

---

### Post by ubunterooster on 2010-07-21
repo for Ubuntuzilla is in link

[http://www.ubuntuupdates.org/ppas/40](http://www.ubuntuupdates.org/ppas/40)

---

