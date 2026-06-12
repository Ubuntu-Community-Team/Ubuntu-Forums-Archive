---
title: "tar.gz"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by koglaa on 2010-01-17
Yes, I know this has been asked before, but all the previous guides didn't work (I must have done something wrong), so here I ask you for your help on how to install a tar.gz file.

Screenshot
[IMG]http://i45.tinypic.com/vo7x92.jpg[/IMG]

As you see, I've extracted the file.  I got lost what to do from there.  Thanks for your help.

---

### Post by SuperSonic4 on 2010-01-17
Open a terminal and paste the output of the second command

```
cd ~/Desktop/antivir-workstation-pers3.0.5-13/
```

```
ls
```

Look for either an INSTALL or README file.

Usually it's

```
./configure --prefix=/usr
make
sudo make install
```

but ./configure has many options which you can use to turn features on/off or where to install it to (/usr/local for example will allow you to run repo versions of programs with compiled ones which is what I do with x264)

```
./configure -h
``` has all the options available

edit: Could you reduce the size of that screenshot please? It even stretches my widescreen monitor (1440 wide)

---

### Post by ikt on 2010-01-17
Any reason why you're trying to install on a live cd?

---

### Post by koglaa on 2010-01-17
ubuntu@ubuntu:~/Desktop/antivir-workstation-pers-3.0.5-13$ ls
AV_WKS_PERS       --     etc             --     LICENSE                --     script                       --     vdf
bin               --     hbedv_key       --     LICENSE.DE             --     smcpkg
contrib           --     install         --     README                 --     uninstall
doc               --     legal           --     README.uninstall       --     uninstall_smcplugin.sh

And I got lost to what you said after that.
./configure just brings up 
```

ubuntu@ubuntu:~/Desktop/antivir-workstation-pers-3.0.5-13$ ./configure --prefix =/usr
bash: ./configure: No such file or directory

```

---

### Post by ikt on 2010-01-17
> **koglaa said:**
> ubuntu@ubuntu:~/Desktop/antivir-workstation-pers-3.0.5-13$ ls
AV_WKS_PERS       --     etc             --     LICENSE                --     script                       --     vdf
bin               --     hbedv_key       --     LICENSE.DE             --     smcpkg
contrib           --     install         --     README                 --     uninstall
doc               --     legal           --     README.uninstall       --     uninstall_smcplugin.sh

And I got lost to what you said after that.
./configure just brings up 
```

ubuntu@ubuntu:~/Desktop/antivir-workstation-pers-3.0.5-13$ ./configure --prefix =/usr
bash: ./configure: No such file or directory

```

use the command: vi README

to read what the readme file has to say.

---

### Post by koglaa on 2010-01-17
Don't know what you meant by vi, but heres the readme
```


 AntiVir Workstation Install-Package Directory


 install           <- install script
 LICENSE           <- Avira GmbH Software License Agreement

 doc/     <- documentation (handbook, manual, changelog)
 bin/     <- executable files
 vdf/     <- virus definition files
 legal/   <- 3rd-party licenses
 contrib/ <- 3rd-party software (dazuko, gnome-applet)

 etc/    <- configuration files
 script/ <- shell scripts
 smcpkg/ <- SMC-specific files

```

And yes, this computer has got some malware on the HDD which I need to clean.  Formatting is NOT an option

---

### Post by ibuclaw on 2010-01-17
Look like you need to run:
```
sudo ./install
```
To run the installer.

Also, FYI -
tar = Tape ARchive
gz = GZip

A tar.gz file is just the Unix equivalent of the zip format. It is by no means an installer, and by no means is there a universal way to install programs that may be 'zipped up' inside them.

Regards
Iain

---

### Post by koglaa on 2010-01-17
> **tinivole said:**
> Look like you need to run:
```
sudo ./install
```
To run the installer.

Also, FYI -
tar = Tape ARchive
gz = GZip

A tar.gz file is just the Unix equivalent of the zip format. It is by no means an installer, and by no means is there a universal way to install programs that may be 'zipped up' inside them.

Regards
Iain

Seemed to work.  Thanks.  What's up with the make command for compiling then?

---

### Post by ibuclaw on 2010-01-17
> **koglaa said:**
> Don't know what you meant by vi, but heres the readme
vi is a text editor. But users who are not aware of it's keybindings will not be very good at navigating through it.
For example, if I were to say you type in dd to move a line to the buffer, p to move the buffer to the text file, :w to save and :q to quit, you won't know what on earth I'm talking about. ;)

Back on the subject of infected system though ...

For a proprietary scanner, I recommend Avast! Linux: [http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

For an open source scanner:
```
sudo apt-get install clamtk
```

Regards
Iain

---

### Post by ibuclaw on 2010-01-17
> **koglaa said:**
> Seemed to work.  Thanks.  What's up with the make command for compiling then?

Autotools and Automake are a popular type of build system. A good 60%+ of open source applications use it to configure and compile the source code on systems. Variants include cmake, qmake, scons and waf. But which one you use tends to vary on what language you are using.

If it all seems a bit confusing - that's because it is. If you are new to this, there is alot to take in, so it's best to stick to the KISS approach, and keep things simple.

Regards
Iain

---

### Post by Troxer on 2010-01-29
I have a similar problem:

I installed Ubuntu Karmic Koala on VMWare. The PC I installed it on doesn't have an internet connection. I copied the GNU C++ compiler and Code::Block packages on the desktop of Ubuntu. Now I am lost.
When I unpack and try to "make" inside the folder it doesn't make.

Can you please let me know the exact sequence of commands?

I have experience in C++ programming but not Linux.

---

