---
title: "Permisions Problem"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by chet on 2009-09-12
Hi All, I have installed Ubuntu 9 with no issues but the issue I'm having is running a binary file for installation.

I have downloaded from Groundworks open source groundwork-5.3 in the following way
```
wget http://superb-east.dl.sourceforge.net/sourceforge/gwmos/groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

Then changed the permissions so I can execute it.
```
chmod +x groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

Then went for the install.
```
./groundwork-5.3.0-br46-gw333-linux-32-installer.bin --mode text
```

Which returned
```
bash: ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin: No such file or directory
```

I was was asked to check that the check sum was correct which it is, and then to run the install from command line which returned
```
/home/monitor/groundwork-5.3.0-br46-gw333-linux-32-installer.bin: /home/monitor/groundwork-5.3.0-br46-gw333-linux-32-installer.bin: cannot execute binary file
```

Here are the permissions on the file.
```
-rwxr-xr-x 1 root root 283783258 2009-02-10 23:26 /home/monitor/groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

The support guy now thinks that I have a problem with my file system that is preventing me from running this install, do you have any idea where I can go from here and also do you know of a binary I can download and test that works with Ubuntu 9

Thanks all

---

### Post by Joshua Lückers on 2009-09-12
Try:
```

sudo chown your_username groundwork-5.3.0-br46-gw333-linux-32-installer.bin
sudo chmod +x groundwork-5.3.0-br46-gw333-linux-32-installer.bin
sudo ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin

```

---

### Post by chet on 2009-09-12
Thanks for getting back to me so quick
```
sudo: unable to execute ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin: No such file or directory
```
I did what you asked but still the same
Permissions now
```
277412 -rwxrwxrwx 1 monitor root    283783258 2009-02-10 23:26 groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

Thanks

---

### Post by talsemgeest on 2009-09-12
Try: ```
chmod 770 groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

---

### Post by chet on 2009-09-12
> **talsemgeest said:**
> Try: ```
chmod 770 groundwork-5.3.0-br46-gw333-linux-32-installer.bin
```

Cheers
The same though mate
> sudo: unable to execute ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin: No such file or directory

---

### Post by chet on 2009-09-12
Forgot to mention, if I follow my #1 on Ubuntu 8.04 it works a treat.

---

### Post by Joshua Lückers on 2009-09-12
Did you download the file as normal user (so not as root or with sudo). Because it works fine for me.

---

### Post by chet on 2009-09-12
No with root, I will try sudo..give me 5 mins....

---

### Post by talsemgeest on 2009-09-12
> **chet said:**
> Forgot to mention, if I follow my #1 on Ubuntu 8.04 it works a treat.
Just a quick check: when you are running the command, does the tab-completion of the file name work?

---

### Post by chet on 2009-09-12
> **talsemgeest said:**
> Just a quick check: when you are running the command, does the tab-completion of the file name work?
 yes it did, I just used ./grou then hit tab and it completed the line

---

### Post by talsemgeest on 2009-09-12
> **chet said:**
> yes it did, I just used ./grou then hit tab and it completed the line
Well, you have me stumped!

Sorry I can't be of more help

---

### Post by chet on 2009-09-12
Same issue with sudo
> 
Sudo wget [http://superb-east.dl.sourceforge.net/sourceforge/gwmos/groundwork-5.3.0-br46-gw333-linux-32-installer.bin](http://superb-east.dl.sourceforge.net/sourceforge/gwmos/groundwork-5.3.0-br46-gw333-linux-32-installer.bin)

sudo chmod +x groundwork-5.3.0-br46-gw333-linux-32-installer.bin 
sudo ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin
 
sudo: unable to execute ./groundwork-5.3.0-br46-gw333-linux-32-installer.bin: No such file or directory

Do you know of another binary I can try that is a know worker with ubuntu 9?

talsemgeest thanks for you help anyway.

---

### Post by chet on 2009-09-12
need to nip out, will check back later

Thanks

---

### Post by chet on 2009-09-12
anybody

---

### Post by 3rdalbum on 2009-09-12
If you're on 64-bit, install the ia32-libs package.

---

### Post by chet on 2009-09-12
Fantastic, that did the trick, well chuffed now :)

Thanks a lot

---

