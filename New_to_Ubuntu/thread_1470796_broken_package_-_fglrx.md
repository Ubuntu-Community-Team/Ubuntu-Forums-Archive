---
title: "broken package - fglrx"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by Sharft 6 on 2010-05-03
The update manager opened up today and showed me the available updates. All of them install properly except "fglrx (new install)". A message comes up and tells me that a package broken. I found out that means I am supposed to open up synaptic package manager and hit fix broken packages. So I did that and down in the status bar it says 'successfully fixed package dependencies' or something like that. So now I hit apply changes and it comes up with this error

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1

These are the details
Oh never mind i can't seem to copy them :(

I think it's the exact same error that came up in the update manager meaning "fix broken packages" did nothing.

---

### Post by GSF1200S on 2010-05-03
> **Sharft 6 said:**
> The update manager opened up today and showed me the available updates. All of them install properly except "fglrx (new install)". A message comes up and tells me that a package broken. I found out that means I am supposed to open up synaptic package manager and hit fix broken packages. So I did that and down in the status bar it says 'successfully fixed package dependencies' or something like that. So now I hit apply changes and it comes up with this error

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1

These are the details
Oh never mind i can't seem to copy them :(

I think it's the exact same error that came up in the update manager meaning "fix broken packages" did nothing.

Run the following commands and paste the output here:
```
sudo dpkg --configure -a
sudo dpkg-reconfigure apt
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get install ubuntu-desktop

```
Dont run the last command if you are using Kubuntu or Xubuntu as you will install a lot of stuff you dont want/need. Also, what version of Ubuntu are you running?

---

### Post by Sharft 6 on 2010-05-03
I've done a bit more investigation and decided that I don't want anything to do with fglrx. I want my display settings back to the way they were before I downloaded and installed the proprietary drivers from the ati website.

Since then I've had openGL flicker, slow maximize times and an overall glitchy interface.

I've followed [this](https://help.ubuntu.com/community/RadeonDriver#Removing%20the%20proprietary%20fglrx%20driver) guide to remove fglrx but I don't think it worked

Note: this isn't the first time I've put these commands in. I just redid them all so I could post the results here in case it says anything.
```

philip@philip-ubuntu:~$ sudo apt-get remove --purge xorg-driver-fglrx
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
philip@philip-ubuntu:~$ glxinfo |grep vendor
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
philip@philip-ubuntu:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3,278kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132023 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu2 (using .../libgl1-mesa-dri_7.7.1-1ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu2 (using .../libgl1-mesa-glx_7.7.1-1ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Setting up libgl1-mesa-dri (7.7.1-1ubuntu2) ...

Setting up libgl1-mesa-glx (7.7.1-1ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
philip@philip-ubuntu:~$ less /etc/modules | grep fglrx
philip@philip-ubuntu:~$ less /etc/X11/xorg.conf | grep fglrx
/etc/X11/xorg.conf: No such file or directory
philip@philip-ubuntu:~$ 

```

oh and i'm running ubuntu 10.04 desktop x64

---

### Post by GSF1200S on 2010-05-03
> **Sharft 6 said:**
> I've done a bit more investigation and decided that I don't want anything to do with fglrx. I want my display settings back to the way they were before I downloaded and installed the proprietary drivers from the ati website.

Since then I've had openGL flicker, slow maximize times and an overall glitchy interface.

I've followed [this](https://help.ubuntu.com/community/RadeonDriver#Removing%20the%20proprietary%20fglrx%20driver) guide to remove fglrx but I don't think it worked

Note: this isn't the first time I've put these commands in. I just redid them all so I could post the results here in case it says anything.
```

philip@philip-ubuntu:~$ sudo apt-get remove --purge xorg-driver-fglrx
[sudo] password for philip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
philip@philip-ubuntu:~$ glxinfo |grep vendor
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
philip@philip-ubuntu:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3,278kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132023 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu2 (using .../libgl1-mesa-dri_7.7.1-1ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu2 (using .../libgl1-mesa-glx_7.7.1-1ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Setting up libgl1-mesa-dri (7.7.1-1ubuntu2) ...

Setting up libgl1-mesa-glx (7.7.1-1ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
philip@philip-ubuntu:~$ less /etc/modules | grep fglrx
philip@philip-ubuntu:~$ less /etc/X11/xorg.conf | grep fglrx
/etc/X11/xorg.conf: No such file or directory
philip@philip-ubuntu:~$ 

```

oh and i'm running ubuntu 10.04 desktop x64

The name of the fglrx driver in 10.04 is simply 'fglrx' so:
```
sudo apt-get remove fglrx
```

Unfortunately, I have no experience with ATI cards in Linux, (been using nvidia for awhile), so I cant be much help beyond the above. Good luck :)

---

### Post by Sharft 6 on 2010-05-03
...package not installed

So i suppose thats a good thing. But I can't enable desktop effects so i don't feel like I'm back to square 1 yet :(.

I think my best option is to reinstall
   -i accidently deleted my win7 boot files and windows repair is next to useless.
   -my data isn't on any of my os partitions
   -wanna reset my display:(

as much as I don't like running away from problems like this I'll just reinstall ubuntu and win7 to end the pain.

---

### Post by ~sHyLoCk~ on 2010-05-03
I am using HD4330, no fglrx installed but compiz desktop effects/cubes/burn effect,etc all working fine for me.

---

### Post by SuperXDE on 2010-05-03
Why don't you remove them with Synaptics , then after that reinstall everything from the beginning? I am having the same problem as you and I was able to remove them with Synaptics , now installing the hardware drivers , but I can't get the ATI Catalyst to work after installing , no idea why.

---

### Post by SuperXDE on 2010-05-03
Here is what I have done , I installed ATI driver , run the .run file I got from ATI website , then Poof ... as if I did not install any driver at all , it didn't install any package ... so I had to remove the ATI Driver that I installed , I went to /usr/share/ati/ and opened the fglrx_uninstaller.sh , Run in Terminal , Nothing worked ... So I opened the terminal , wrote sudo nautilus , navigated to that file , and Run in Terminal , the ATI Driver was removed , now I opened Synaptics , and installed the fglrx without any problems or errors ( ofcourse after removing all the broken and installed packages related to fglrx then Applying , then installing again)... however the problem still is persistent and the Desktop effects "could not be enabled" and it is working like I am using an ancient processor on this High-end laptop...

---

### Post by SuperXDE on 2010-05-03
If you install ATI drivers , and can't uninstall them because of some FORCE ATI UNINSTALL re-run fglrx_uninstaller.sh , etc... you simply go to usr/share/ and delete the folder named ATI , restart , go to synaptic , install fglrx and all related stuff ( except jockey KDE ) then restart again .. and tadaa~! to make sure that it was alright just go to the appearance under system menu and set the desktop effects to extra ( SYSTEM > PREFERENCES > APPEARANCE > DESKTOP EFFECTS > EXTRA )

Summary :
1-Uninstall the fglrx drivers , by opening syanptics , quick search fglrx and mark for complete removal everything except the jockies
2-Try uninstalling ATI drivers using sudo sh ./usr/share/ati/fglrx_uninstaller.sh
  1a- if it failed due to FORCE ATI UNINSTALL message , go to /usr/share using nautilus ( explorer ) and delete the folder named ATI

3- Restart your computer , it will give you a few error messages , just force it to open this session
4- Open synaptics , write in the quick search fglrx and install everything except the jockies as well.
5-restart
6-Test using the SYSTEM > PREFERENCES > APPEARANCE > DESKTOP EFFECTS > EXTRA 
7- if it worked , then congratulations ... you have got a video driver working now.

---

### Post by Sharft 6 on 2010-05-03
thanks for your help but I reinstalled ubuntu and now the interface is clean and smooth

---

