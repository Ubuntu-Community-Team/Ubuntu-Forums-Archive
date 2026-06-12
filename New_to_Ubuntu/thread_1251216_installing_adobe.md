---
title: "installing adobe"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by dzon65 on 2009-08-27
Firefox is currently using schockwave.Perhaps this is causing jerky flashvideo and jerky scrolling.I'd like to install the latest adobe.I've followed the instructions given by adobe but in the terminal the file isn't recognized (file doesn't exist).I'm probably doing something wrong so could anyone explain me how to install it?

---

### Post by sandyd on 2009-08-27
I can.
assuming you downloaded adobe flash to the desktop.... and theirs no other files with the edtension .deb, type this into the terminal (just copy and apste)
```

cd ~/Desktop
sudo dpkg -i *.deb
sudo apt-get install -f

```

---

### Post by dzon65 on 2009-08-27
Hi.Tried it but it gives me a mistake john@ubuntu:~$ cd ~/Desktop
bash: cd: /home/john/Desktop: Bestand of map bestaat niet
john@ubuntu:~$ sudo dpkg -i *.deb
[sudo] password for john: 
dpkg: fout bij afhandelen van *.deb (--install):
 kan archief niet benaderen: Bestand of map bestaat niet
Fouten gevonden tijdens behandelen van:
 *.deb
john@ubuntu:~$ 


So:mistake for *.deb (--install)
can't find archive.File or map doesn't exist (yet,it's there allright)
found mistakes for:*deb

---

### Post by tuxxy on 2009-08-27
Whats wrong with the Flash in the repos?  It should also be included with ubuntu-restricted-extras package.

If you are on 32-bit Ubuntu then search for flashplugin-nonfree using Synaptic or open terminal and enter this;

```
sudo apt-get install flashplugin-nonfree
```

If you run 64-bit then download [this file]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz") and extract it to /usr/lib/share/mozilla/plugins

---

### Post by presence1960 on 2009-08-27
> **dzon65 said:**
> Firefox is currently using schockwave.Perhaps this is causing jerky flashvideo and jerky scrolling.I'd like to install the latest adobe.I've followed the instructions given by adobe but in the terminal the file isn't recognized (file doesn't exist).I'm probably doing something wrong so could anyone explain me how to install it?

if you are using 32 bit ubuntu open a terminal and run this command ```
sudo apt-get install flashplugin-nonfree
```

for 64 bit ubuntu flash see [here]("http://ubuntuforums.org/showthread.php?t=772490")

first uninstall any other instances of flash including shockwave, swfdec or gnash. Then install the new version.

You will be better off if you stick to the repositories for your software as when you upgrade there will be problems with the software installed manually.

---

### Post by tuxxy on 2009-08-27
I would still recommend ubuntu-restricted-extras if you have not installed that package, it contains Flash, Java, Codecs, fonts etc

```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by dzon65 on 2009-08-27
The reason why I might install adobe is because my flash video is very jerky and not synch wit the sound.I've heard sometimes it's better to install adobe.Anyway,tried your method,it's a little better but still very jerky.Whilst having f.e youtube on the background,the scrolling goes slower,even when "fast-scrolling", half the page disappears.or makes the flash video "break"into pieces of color.So,shockwave's perhaps taking too much.

---

### Post by st33med on 2009-08-27
Shockwave does not exist for Ubuntu in a workable form...

Do you have an Intel graphics card?  The drivers have a hard time rendering Flash video.  Try not to put it in full screen or move your mouse a lot while playing something.

---

### Post by dzon65 on 2009-08-28
No,no intel.I've heard about those problems with intel.Mine is nvidia.I've tried downgrading to a previous one,to no avail.Same cracking  and not synched video,partly disappearing pages when scrolling...I do have schockwave plugin installed.9.0 r999.

---

### Post by Perfect Storm on 2009-08-28
> **dzon65 said:**
> Hi.Tried it but it gives me a mistake john@ubuntu:~$ cd ~/Desktop
bash: cd: /home/john/Desktop: Bestand of map bestaat niet
john@ubuntu:~$ sudo dpkg -i *.deb
[sudo] password for john: 
dpkg: fout bij afhandelen van *.deb (--install):
 kan archief niet benaderen: Bestand of map bestaat niet
Fouten gevonden tijdens behandelen van:
 *.deb
john@ubuntu:~$ 


So:mistake for *.deb (--install)
can't find archive.File or map doesn't exist (yet,it's there allright)
found mistakes for:*deb

Note, if you use an other language on your Ubuntu, you have to switch the word "Desktop" to the word of your language.

---

### Post by dzon65 on 2009-08-28
Yes,of course.That would be Bureaublad then.Tak.I'll give it another try,hopefully this works cause it's a really,really annoying thing.

---

