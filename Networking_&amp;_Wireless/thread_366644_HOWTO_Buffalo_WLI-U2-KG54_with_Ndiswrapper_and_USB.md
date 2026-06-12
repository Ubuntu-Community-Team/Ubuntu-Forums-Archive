---
title: "HOWTO: Buffalo WLI-U2-KG54 with Ndiswrapper and USB 2.0 support"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by Nakkis on 2007-02-21
As every owner of this USB-wireless adapter knows, the default rt2570 drivers that come with the kernel disconnect regularly, especially if you have enabled USB 2.0 support. I've managed to make this adapter work without any issues with the latest ndiswrapper and latest XP drivers for WLI-U2-KG54-AI from Buffalo website. 

Please tell me if there are any problems with this guide!

First, we need to blacklist the existing rt2570 driver so ndiswrapper can be used. 

```
sudo gedit /etc/modprobe.d/blacklist
```

Then add this line to the bottom of the file and save it. 

```
blacklist rt2570
```

Then we need to download the latest ndiswrapper from the ndiswrapper project page. I think that you need atleast version 1.37. 

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=483506](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=483506)

Navigate to the folder you downloaded the file and type 

```
tar zxvf tar zxvf ndiswrapper-1.37.tar.gz
```

to extract the archive. Next to to the directory you extracted the files into with

```
cd ndiswrapper-1.37
``` 

Type these commands to install ndiswrapper

```
make uninstall
```

```
make
```

```
sudo make install
```

[http://www.buffalo-technology.com/support/downloads.php](http://www.buffalo-technology.com/support/downloads.php)

Next step is to download the Windows drivers from the buffalo website. Download the drivers for WLI-U2-KG54-AI and unzip the archive to your home directory. Install the drivers with this command. 

```
sudo ndiswrapper -i netu2g54.inf
```

```
sudo ndiswrapper -m
```

Now you should see something like this if you use the 'ndiswrapper -l' command

> netu2g54 : driver installed
        device (0411:0066) present (alternate driver: rt2570)


If so, then everything is working!

To complete the install, you'll have to make sure ndiswrapper loads on every boot. 

```
sudo gedit /etc/modules
```

Add this line to the bottom of the file. 

```
ndiswrapper
```

Save the file, reboot and configure your wireless. You finally have stable wireless connection on reboot! Plus, these drivers work with NetworkManager for easy wireless configuration! :)

---

### Post by allanlewis on 2007-05-09
Will this method work in both Edgy and Feisty?
Also, are there any disadvantages to using ndiswrapper rather than native drivers?

---

### Post by cman on 2007-08-31
when I tried to install the driver I got this ```
cman@cman-desktop:~$ sudo ndiswrapper -i netu2g54.inf
installing netu2g54 ...
couldn't open netu2g54.inf: No such file or directory at /usr/sbin/ndiswrapper line 174.

```

trying it again gives me a "driver netu2g54 is already installed" message and -l command gives me: ```
cman@cman-desktop:~$ ndiswrapper -l
netu2g54 : invalid driver!

```

any ideas where I went wrong?

---

### Post by SuperDodge on 2008-01-06
There was an error with your driver installation.  You most likely didn't copy ALL of the files in the driver package and instead just copied the .inf file.  You can install the errored driver by typing:

sudo ndiswapper -e netu2g54

---

