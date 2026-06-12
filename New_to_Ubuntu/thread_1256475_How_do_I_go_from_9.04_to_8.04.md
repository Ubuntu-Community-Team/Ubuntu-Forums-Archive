---
title: "How do I go from 9.04 to 8.04?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by brando337 on 2009-09-02
Hello everyone. I just downloaded and installed ubuntu  9.04,  but now i wish to install 8.04 cause i am having trouble getting sound and flash video to work properly and I hear 8.04 is more stable.  My question; Is there some special process to revert to an older version or can i just boot with 8.04 and it will just overwrite 9.04 ? thanks for your help.

---

### Post by Tclarkie on 2009-09-02
how did you install flash, it would be easier just to fix the problem

---

### Post by brando337 on 2009-09-02
I installed from a cd.  When I go to install flash It gives me an error message that says :Wrong architecture 'i386'

---

### Post by zkriesse on 2009-09-02
Hmm....that doesn't sound right. How are you trying to install flash? What I do is go to a website like Hulu and download it from there. Do the Adobe one if you do it the way I do.

---

### Post by k3lt01 on 2009-09-02
You are always better off to install programs through "Synaptic" or "Add/Remove". That way the correct architecture for your system is downloaded and installed.

To answer your original question the only way I know of that you can go backwards is to download the older version and do a fresh install.

---

### Post by nhasian on 2009-09-02
there is no way to downgrade to an older version of ubuntu.  Yes you can just boot off the 8.04 LiveCD and overwite the old ubuntu if you want to, but lets try to fix your flash problem first.  Lets find out what CPU architecture your using with the terminal command:

```
uname -a
```

please post the output here

---

### Post by brando337 on 2009-09-02
the way i tired is through their site.  I went to youtube and the "install missing plugin" box appeared and I followed directions there. I even used some commands i found from another form to  try it from the terminal.ill try hulu.

---

### Post by brando337 on 2009-09-02
Linux brandon-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_

---

### Post by running_rabbit07 on 2009-09-02
Kernel looks out of date.

---

### Post by st33med on 2009-09-02
Linux brandon-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_  << It cut off right here.  It looks like you have a 64 bit processor. Did you install 64-bit Ubuntu?

---

### Post by nhasian on 2009-09-02
okay your using the 64 bit version of ubuntu.  lets install the 64 bit version of adobe flash as well.  follow the instructions on this page:

[http://ubuntuforums.org/showthread.php?t=1241313](http://ubuntuforums.org/showthread.php?t=1241313)

---

### Post by brando337 on 2009-09-02
yea i installed the 64bit version cause i have a 64 bit laptop.

---

### Post by jerrrys on 2009-09-02
> **brando337 said:**
> the way i tired is through their site.  I went to youtube and the "install missing plugin" box appeared and I followed directions there. I even used some commands i found from another form to  try it from the terminal.ill try hulu.

three things

#1  just install **ubuntu restricted extras **from synaptic package manager and you will get the whole package for your system

#2  while on ubuntu, you will get these popups telling you you need to install this or that.  do not. if necessary first use synaptic.

#3  you can install on top of ubuntu

---

### Post by brando337 on 2009-09-02
yes cause im almost positive i have a 64 bit processors

---

### Post by jerrrys on 2009-09-02
Accessories>terminal  and enter
[B]sudo lshw
[/B]how wide is it?

---

### Post by brando337 on 2009-09-02
yea its 64bits

---

### Post by jerrrys on 2009-09-02
i386 is 32 bit version

---

### Post by brando337 on 2009-09-02
i dont see a 64 bit version of flash player on their site. do they even make one?

---

### Post by jerrrys on 2009-09-02
its out there, but im a 32 bit user and don't know about that, other then restricted extras.  and i must say at the risk of sounding bias; ubuntu 8.04 32 bit may be the way to go until you get some experience.  it just works...

---

### Post by Sub101 on 2009-09-02
I used the script linked here: [http://ubuntuforums.org/showpost.php?p=7717588&postcount=775](http://ubuntuforums.org/showpost.php?p=7717588&postcount=775)

and copied below due to being posted outside of code tags. 

```
#!/bin/bash
# Script created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

