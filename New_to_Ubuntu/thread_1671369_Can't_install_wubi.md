---
title: "Can't install wubi"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by ahdb on 2011-01-19
Hello all
 
I have tried several times to install wubi but keep getting the same error message.  Can someone please explain what I can do to install wubi?  Here are the details:
 
I am using Windows 7.  I went to the web page [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) and followed the instructions. First I downloaded wubi.exe onto my desktop, and then I double-clicked it.  A message appeared saying "You are about to install Ubuntu-10.4.1" and then "Installing Ubuntu-10.4.1".  Then I got a message saying "an error occurred: Permision denied. For more information, please see the log file C:\users\abvi\appdata\local\temp\wubi-10.4.1-rev190.log".  I have attached this log file.
 
I'd be grateful for any suggestions!
 
ahdb

---

### Post by bcbc on 2011-01-19
> DownloadError: Problem connecting to tracker - (10054, 'Connection reset by peer')

You are having a problem downloading the Ubuntu .iso. Wubi uses a bittorrent client - it requires you to allow pyrun.exe access to your firewall. 

Generally it should work (although it is much slower than current bittorrent clients). So I'm not sure why it's not working for you. What you can do is to download the Ubuntu .iso yourself, and place it in the same folder as wubi.exe and then run wubi. (Just make sure you have the same release - the wubi.exe you are running is 10.04.1).

After installing, please avoid updates to packages grub-pc and grub-common - they are known to cause problems with wubi installs.

---

### Post by LinuxFox on 2011-01-20
In addition to what bcbc said, when I tried Wubi with the iso in the same folder with Wubi, it still tried to download an Ubuntu iso.  If this happens, try disconnecting from the Internet while installing.

Once Wubi is done, then re-connect the Internet before restarting.  Just wanted to point this out since it happened to me with Wubi a few times.

---

### Post by ahdb on 2011-01-20
Hello 

Thank you, to both bcbc and LinuxFox, for your answers.  However, I still can't install wubi.  I placed the iso file (which does download when I try intalling) in the same directory as the exe file.  I also deleted the iso file from the location that the installer had put it.  I tried while connected to the internet and also while not connected.

The iso file is called ubuntu010.4.1-desktop-amd64.iso .

When I double click wubi.exe the following happens:

1.  I get a message announcing that the previous attempt at installation will be uninstalled.
2. I get asked to set a password.
3.  It appears to start installing.  
4.  If I'm connected to the internet I get the same error message as before (permission denied to iso file).
5.  If I'm not connected to the internet, I get the following error message "An error occurred: Cannot download the metalink and therefore the ISO.  For more information, please see the log file ...".  I've attached the log file.

What else am I doing wrong? Is it possible to download all the files required for installation so that I don't have to be connected to the internet during installation?

ahdb

---

### Post by bcbc on 2011-01-20
> 01-21 09:54 DEBUG  Distro:   checking Ubuntu ISO D:\ABVI's Documents\Agnes\ubuntu\ubuntu-10.04.1-desktop-amd64.iso
01-21 09:54 DEBUG  Distro:     wrong size: 0 < 600000000


Download wubi.exe and the ubuntu-10.04.1-desktop-amd64.iso into the same folder. The .iso will be about 700MB (probably 699).

Then run it. Do not disconnect from the internet. It uses the net to run an md5sum check on your .iso to make sure it's OK. 

If you aren't connected to the net you have to tell wubi to bypass this check or burn the .iso to CD and run it from there (that's the only way).

---

### Post by bou3lam on 2011-02-18
bcbc , ive just arrived fro another post yours about the migrators :) im trying to do a new install of ubuntu with wubi and then migrate it with your script , but im getting the same error as ahdb, i dont understand what happened i've installed uninstalled with wubi many times , i have ubuntu-10.04.1-desktop-i386.iso and i put wubi with in the same disk, its run untill 0seconds and the error appear, here the log file [http://rapidshare.com/files/448694830/wubi-10.04.1-rev190.txt](http://rapidshare.com/files/448694830/wubi-10.04.1-rev190.txt)  
please help

---

### Post by bcbc on 2011-02-18
> **bou3lam said:**
> bcbc , ive just arrived fro another post yours about the migrators :) im trying to do a new install of ubuntu with wubi and then migrate it with your script , but im getting the same error as ahdb, i dont understand what happened i've installed uninstalled with wubi many times , i have ubuntu-10.04.1-desktop-i386.iso and i put wubi with in the same disk, its run untill 0seconds and the error appear, here the log file [http://rapidshare.com/files/448694830/wubi-10.04.1-rev190.txt](http://rapidshare.com/files/448694830/wubi-10.04.1-rev190.txt)  
please help
The problem is the 10.04.2 has been released. So when wubi tries to check the md5sum it can't find it for 10.04.1
> [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink) > E:\ubuntu\install
02-19 02:11 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found

Instead it gets the one for [10.04.2]("http://releases.ubuntu.com/lucid/MD5SUMS")
> 477350cbea8936c63d587cf2be69181b *ubuntu-10.04.2-desktop-i386.iso
and this fails:
> 02-19 02:12 ERROR  CommonBackend: Invalid md5 for ISO E:\ubuntu-10.04.1-desktop-i386.iso (477350cbea8936c63d587cf2be69181b != 9a95ed6f6ec38fb58c446dba1add6a08 )


Why don't you try using the --skipmd5check option. It should go ahead an use what you've got with checking the net. (Or just disconnect from the net first).

To use --skipmd5check:
Right-click Wubi.exe and select "Create Shortcut". Then right-click the shortcut, select Properties, and modify the Target line, for example: "E:\wubi.exe" --skipmd5check

---

### Post by bou3lam on 2011-02-18
thanks alot i will do this now, another thing, i have 3 partitions c=windows D:empty for ubuntu , and E: for storing files, may i install wubi in E and later migrate it to D ? will this cause loss of disk space :)? sorry im a total newb in ubuntu and linux

( i wont install untill you answer me so i wont do any mistakes :)   )

---

### Post by 3rdalbum on 2011-02-18
If you already have a free partition, why not do a real install of Ubuntu by booting up your computer from the CD and then double-clicking the installer from the live session?

---

### Post by bou3lam on 2011-02-18
cd broken, no usb , for this im using wubi

---

### Post by bcbc on 2011-02-18
> **bou3lam said:**
> thanks alot i will do this now, another thing, i have 3 partitions c=windows D:empty for ubuntu , and E: for storing files, may i install wubi in E and later migrate it to D ? will this cause loss of disk space :)? sorry im a total newb in ubuntu and linux

Yes. That will work.
Be careful though - e.g. don't update grub while running wubi. If you have a problem you can't boot a cd to fix it.

---

### Post by bou3lam on 2011-02-18
i always uninstalled grub , i hate it :) another time please : i will install ubuntu in E with 14GB as space allocated for ubuntu , in E there is some 30 GB free, in D 15 GB  , when i will move ubuntu with your script to D , the 14GB from E will move with ubuntu too to D :)? excuse me for being a dumby :)))

---

### Post by bcbc on 2011-02-19
The script formats the empty partition (in your case D: ) and then copies the files. So it doesn't matter how big the Wubi install is: the migrated install will always be as big as the target partition. 

So e.g. if all you are going to do is migrate after installing, you could create a 3 or 4 GB wubi install if you like, and the end result is the same. (It doesn't make the migration faster - still the same number of files to be copie - but it makes installing wubi a little faster.)

---

### Post by bou3lam on 2011-02-19
you didnt understand me , i want to know about the space which wubi will be using in E, will this space stay in E after migration or it will be moved with ubuntu to D ? if i understand wubi is like an image , an iso

---

### Post by bcbc on 2011-02-19
> **bou3lam said:**
> you didnt understand me , i want to know about the space which wubi will be using in E, will this space stay in E after migration or it will be moved with ubuntu to D ? if i understand wubi is like an image , an iso

Wubi will remain as it is until you uninstall it. To do this boot windows, go to control panel, add/remove, select Ubuntu. So no - the space will stay in E, but when you uninstall it will be freed up completely.

---

### Post by bou3lam on 2011-02-19
and in case if i use your script to migrate ubuntu to a partition, will this space stay in E after migration or it will be moved with ubuntu to D ?

---

### Post by bcbc on 2011-02-19
I am not sure I understand...

When you install wubi it creates a virtual disk (the root.disk file) for the size you choose - the file results on the ntfs partition. 

If you selected a 5GB wubi install then the root.disk is 5GB but the files on it will take up about 2.5GB.

When you migrate to D: the partition is 15GB, and the 2.5GB of files are copied onto it. The space on D: will be 12.5GB. It doesn't change anything on the E: partition.

---

### Post by bou3lam on 2011-02-19
thats what i wanted to know :) thanks a lot :)

---

### Post by chikaaHm on 2011-02-19
I do not near it. I shall  give you solve shortly. 

  [   photo retouching](http://www.retouchassistant.com/index.php)

---

