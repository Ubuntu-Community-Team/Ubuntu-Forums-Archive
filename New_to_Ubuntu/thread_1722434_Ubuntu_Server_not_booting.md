---
title: "Ubuntu Server not booting?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Skybucks100 on 2011-04-05
Hi,
I installed Ubuntu Server 10.10 on my Dell Poweredge 600SC. I was promoted to restart my server. I restarted my server and it gave m the no OS installed :confused:. Any help would be awesome. Also I am a brand new to Linux server stuff...

---

### Post by fela on 2011-04-05
Try taking the disk out and booting another PC with it.

Then you'll know if it's a hardware or if it's a software problem.

Or, you could try the ubuntu live CD and see if you can access your partitions. Also, while your at it, run (again from the live CD of course):

```
sudo file -s /dev/sda
```

Where sda is your disk that you installed Ubuntu to. This command outputs the boot sector of your disk, and it *should* say something about GRUB (GRand Unified Bootloader).

---

### Post by Skybucks100 on 2011-04-05
[QUOTE=fela;10642676]Try taking the disk out and booting another PC with it.

Then you'll know if it's a hardware or if it's a software problem.

Or, you could try the ubuntu live CD and see if you can access your partitions. Also, while your at it, run (again from the live CD of course):

```
sudo file -s /dev/sda
```
Hi, I took the disk out right before I rebooted. Also is the Live CD the same as a Disk with the ISO burned to it? A bit confussed on that part.

---

### Post by fela on 2011-04-05
> **Skybucks100 said:**
> Hi, I took the disk out right before I rebooted. Also is the Live CD the same as a Disk with the ISO burned to it? A bit confussed on that part.

Hi, I meant the hard disk, not the CD. Or at least check that it's all seated properly etc.

The live CD is the ISO 'extracted' onto a CD.

---

### Post by Skybucks100 on 2011-04-05
> **fela said:**
> Hi, I meant the hard disk, not the CD. Or at least check that it's all seated properly etc.

The live CD is the ISO 'extracted' onto a CD.
Hi I got it to boot up! Thanks! Now I have one last question... I'm trying to install Smartfoxserver how do you know install a program on Ubuntu Server? Or could point me in the direction of the Docs?

---

### Post by fela on 2011-04-06
> **Skybucks100 said:**
> Hi I got it to boot up! Thanks! Now I have one last question... I'm trying to install Smartfoxserver how do you know install a program on Ubuntu Server? Or could point me in the direction of the Docs?

Hi, maybe you should post what you did to get it working so other people can use this for future reference.

To install a package, type ```
sudo apt-get install packagename
```

You might have to update your packagelists if this is a new install: ```
sudo apt-get update
```

To search for a package by name, type ```
sudo apt-cache search keyword
```

---

### Post by Skybucks100 on 2011-04-06
> **fela said:**
> Hi, maybe you should post what you did to get it working so other people can use this for future reference.

To install a package, type ```
sudo apt-get install packagename
```

You might have to update your packagelists if this is a new install: ```
sudo apt-get update
```

To search for a package by name, type ```
sudo apt-cache search keyword
```

Ya what happened was is my server (A dell Poweredge 600SC) was set to OS install in the BIOS option panel and i turned it off and it worked :)Also would i have to burn the Linux install download on to a disk and put it on my server and then do the install code?

---

### Post by fela on 2011-04-06
> **Skybucks100 said:**
> Ya what happened was is my server (A dell Poweredge 600SC) was set to OS install in the BIOS option panel and i turned it off and it worked :)Also would i have to burn the Linux install download on to a disk and put it on my server and then do the install code?

No, just make sure you're connected to the internet, and run that command. No disks involved.

---

### Post by Skybucks100 on 2011-04-06
> **fela said:**
> No, just make sure you're connected to the internet, and run that command. No disks involved.

Hi,
I did the code and I get this:
sudo apt-get install smartfoxserver
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package smartfoxserver


Is this normal or is something wrong?

---

### Post by fela on 2011-04-07
> **Skybucks100 said:**
> Hi,
I did the code and I get this:
sudo apt-get install smartfoxserver
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package smartfoxserver


Is this normal or is something wrong?

The package must have a different name.

Try doing this:

```
sudo apt-cache search smart | grep fox
```

Or even more specific:

```
sudo apt-cache search smart | grep fox | grep server
```

Although 'server' might not be part of the package name.

That will output the correct package name, with which you apt-get install.

---

### Post by jerome1232 on 2011-04-07
It's not in the repositories.

You have to download it. Assuming I found the version you want:

```
wget http://www.smartfoxserver.com/download/SFSBASIC_linux_1.5.5.tar.gz
```

Extract it and then follow their documentation on how to install it.

[http://www.smartfoxserver.com/docs/](http://www.smartfoxserver.com/docs/)

---

### Post by Skybucks100 on 2011-04-07
> **jerome1232 said:**
> It's not in the repositories.

You have to download it. Assuming I found the version you want:

```
wget http://www.smartfoxserver.com/download/SFSBASIC_linux_1.5.5.tar.gz
```

Extract it and then follow their documentation on how to install it.

[http://www.smartfoxserver.com/docs/](http://www.smartfoxserver.com/docs/)
Hi,
Thanks! But I have about 2 main problems... It says:
> 
1. open a terminal window and move to the folder where you have downloaded the file.
2. type "gzip -d filename.tar.gz" to extract the .tar file (where "filename" is the name of the downloaded file) 
3. type "tar xf filename.tar" to extract the files.
4. move inside the uncompressed folder and type ./install 

I can't download it, a terminal? I'm assuming it means that screen that the ubuntu server has...

If you could help out with those that would be awesome!

---

### Post by jerome1232 on 2011-04-07
that wget command i gave you will download the basic version of smartfox server 1.5.5 to your current working directory (your home directory probably)

Since your using Ubuntu Server you are probably using a command line only interface, so no need to open a terminal emulator, your in one :)  My Ubuntu server is command line only, but I log into it via ssh from a computer with a gui. That way I can copy things like links into it.



Really you can

```
wget http://www.smartfoxserver.com/download/SFSBASIC_linux_1.5.5.tar.gz
tar xzfv SFSBASIC_Linux_1.5.5.tar.gz
cd *whaterver_dirictory_gets_created*
./install
```

If it complains about admin rights or about it needing root privliges type sudo before the ./install.

---

### Post by Skybucks100 on 2011-04-07
> **jerome1232 said:**
> that wget command i gave you will download the basic version of smartfox server 1.5.5 to your current working directory (your home directory probably)

Since your using Ubuntu Server you are probably using a command line only interface, so no need to open a terminal emulator, your in one :)  My Ubuntu server is command line only, but I log into it via ssh from a computer with a gui. That way I can copy things like links into it.



Really you can

```
wget http://www.smartfoxserver.com/download/SFSBASIC_linux_1.5.5.tar.gz
tar xzfv SFSBASIC_Linux_1.5.5.tar.gz
cd *whaterver_dirictory_gets_created*
./install
```

If it complains about admin rights or about it needing root privliges type sudo before the ./install.
HI, 
I type in:
wget [http://www.smartfoxserver.com/download/SFSPRO_linux_1.6.6.tar.gz](http://www.smartfoxserver.com/download/SFSPRO_linux_1.6.6.tar.gz) (which is the pro one) 
and I get something saying 
--2011-04-10:31:55-- [http://www.smartfoxserver.com/download/SFSPRO_linux_1.6.6.tar.gz](http://www.smartfoxserver.com/download/SFSPRO_linux_1.6.6.tar.gz)
Resolving [www.smartfoxserver.com](www.smartfoxserver.com)... failed: Temporary failure in name resolution/

---

### Post by fela on 2011-04-07
Hi, are you sure you are connected to the internet? Try ```
ping google.com
```

---

### Post by Skybucks100 on 2011-04-07
> **fela said:**
> Hi, are you sure you are connected to the internet? Try ```
ping google.com
```
I get:
ping: unknown host google.com

---

### Post by jerome1232 on 2011-04-08
Okay so what is the output of the following two commands, make sure to post the output wrapped in code tags. Make sure your in advanced mode, highlight the output and click the # button.

```
ifconfig
sudo lshw -C network
```

---

