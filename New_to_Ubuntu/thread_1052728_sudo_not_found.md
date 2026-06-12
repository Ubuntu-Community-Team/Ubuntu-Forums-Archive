---
title: "sudo: not found"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Chapati on 2009-01-28
Hey everyone,

I installed the latest version of Ubuntu. When the computer boots up, the Ubuntu command prompt loads up. I can't bring up the desktop because everytime I type sudo it say sudo: not found.

Help? I'm a complete newbie to Linux; never used it before and have only used Windows.

---

### Post by Crafty Kisses on 2009-01-28
Remember in Linux things are case sensitive, so if you are typing the following:
```
Sudo
```You will be getting the "command not found" error, but if you type the following:```
sudo
```That should actually work, if that doesn't work please get back to me.

---

### Post by Chapati on 2009-01-28
I've been using lowercase.

I even tried reinstalling Ubuntu, still getting the error.

---

### Post by phrostbyte on 2009-01-28
please paste in the output of "whereis sudo"

---

### Post by Chapati on 2009-01-28
I get "whereis: not found" for whereis.

Could I have possibly downloaded a faulty iso?

Also when I try "find sudo" it says no such file or directory exists (if that helps).

---

### Post by phrostbyte on 2009-01-28
If you are missing the "whereis" utility you have some serious issues over there.

anyway the output should look exactly like this:

bash: whereis: command not found

if not try typing "bash" and see if anything happens

But most likely you have a bad disc. I think there is a way to check if your disc is bad.

---

### Post by kshtjsnghl on 2009-01-28
You can run the md5 check sum for the disc to know if the disc is correct...

---

### Post by mcduck on 2009-01-28
You have to telell "sudo" what you want to do. running "sudo" alone is not going to take you anywhere.

The "sudo: not found" error doesn't mean that it couldn't find "sudo". It means you are running sudo, but sudo can't find what you are trying to run. (If "sudo" itself was missing you'd get error like this: "bash: sudo: command not found")

---

### Post by SeanHodges on 2009-01-28
> **mcduck said:**
> You have to telell "sudo" what you want to do. running "sudo" alone is not going to take you anywhere.

The "sudo: not found" error doesn't mean that it couldn't find "sudo". It means you are running sudo, but sudo can't find what you are trying to run. (If "sudo" itself was missing you'd get error like this: "bash: sudo: command not found")

Actually, running "sudo" on it's own should display the usage screen...

Chapati, can you indicate which of the following below looks the most like the output you are getting? and perhaps copy and paste the actual output from your terminal as well?

1)
```
sean@SEAN-PC:~$  sudo 
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
```

2)
```
sean@SEAN-PC:~$ sudo lll
sudo: lll: command not found
```

3)
```
sean@SEAN-PC:~$ sudo
bash: sudo: command not found
```

---

### Post by Chapati on 2009-02-03
Here is what I get when I boot Ubuntu up:

```


```

---

### Post by Chapati on 2009-02-03
Here is what I get when I boot Ubuntu up:

```

     Booting 'Ubuntu 8.10, kernel 2.6.27-7-generic'

     Filesystem type is fat, partition type 0x0C
The current working directory(i.e., the relative path) is /ubuntu/disks
     [Linux-bzImage, setup=0x3000, size=0x220cb0]
     [Linux-initrd @ 0x1f7d4000, 0x80b9a2 bytes]

Loading, please wait...
ALERT! /host/ubuntu/disks/root.disk does not exit. Dropping to a shell!

BusyBox v1.10,2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

```

And then the commands:

```

(initramfs) sudo startx
/bin/sh: sudo: not found
(initramfs) bash sudo
/bin/sh: bash: not found
(initramfs) sudo
/bin/sh: sudo: not found
(initramfs) bash
/bin/sh: bash: not found

```

Thats all I can do, I boot up and I can't go any further.

I installed Ubuntu with wubi.exe, tried 8.10, 8.04, even tried Kubuntu, and I'm getting the exact same thing for each.

---

### Post by hRob on 2009-02-03
I have two questions which I would like you to answer :
1. Are you running a dual boot?
2. Where did u download your wubi installer from?

IF you do run a dual boot, thee is a possibility that u didnt shut down winodws properly.. that might cause this problem.. reboot into windows and shut it down properly and then boot into linux.. that might solve the issue

the problem might also be with your wubi installer.. you might need to download it again.. download it from [www.wubi-installer.org](www.wubi-installer.org).. your download could've also been corrupted.. so try downloading it again and reinstalling..

and just out of curiosity.. from where exactly are u posting this from if your machine is down?

cheers,
hRob

---

### Post by SeanHodges on 2009-02-03
> **Chapati said:**
> ```
ALERT! /host/ubuntu/disks/root.disk does not exit. Dropping to a shell!

BusyBox v1.10,2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

```

As hRob hinted, Ubuntu is not starting up properly because the Wubi launcher cannot find some files it needs.

The program "sudo" is not available when you are using the emergency BusyBox shell. Basically you need to fix your Ubuntu installation before you will be able to use it.

The most common reason of this particular problem is that the "root.disk" file is no longer available when booting. This can be caused by an unclean shutdown of Windows, as the disk can be marked as "unclean", although there is also a chance that the file has been moved by Windows chkdisk or a rogue anti-virus program.

The first thing to check is that the following file is present on your system (change the drive letter accordingly):

C:\ubuntu\disks\root.disk


> **Chapati said:**
> I installed Ubuntu with wubi.exe, tried 8.10, 8.04, even tried Kubuntu, and I'm getting the exact same thing for each.

Did you uninstall each one before installing the next one? Otherwise you may have blatted over the top of an existing install and corrupted it.

---

### Post by hRob on 2009-02-03
> **SeanHodges said:**
> 
Did you uninstall each one before installing the next one? Otherwise you may have blatted over the top of an existing install and corrupted it.

@Sean 
does that actually happen? every time you install a newer version or a different version, atleast wat i thought was, the drive is formatted and the MBR gets replaced with info from the newer distro.. so i personally dont think there should be a problem with it as installing different distros on top of existing systems will not corrupt the installer..

@chapati
i think the problem is with your installation media.. try ordering one from shipit.ubuntu.com.. tht should do the trick.. keep us posted on wat is happening ;]

---

### Post by Chapati on 2009-02-11
Hey everyone, got it working.

It turned out to be a partitioning problem.

I ended up putting ubuntu on a usb and booting it up from there.

Works like a charm. Thanks for all the help :)

---

### Post by hRob on 2009-02-19
good that u got yours working.. now i have a small problem thats related to connecting to the internet.. please take a look at this link : [http://ubuntuforums.org/showthread.php?t=1074258](http://ubuntuforums.org/showthread.php?t=1074258)

---

