---
title: "installing software in terminal"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Orions on 2010-05-25
Can anyone post some tutorial how to install progs in terminal? I hawe some files like tar.gz or something.

---

### Post by nmaster on 2010-05-25
> **Orions said:**
> Can anyone post some tutorial how to install progs in terminal? I hawe some files like tar.gz or something.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

in the future, you should try this link before starting a thread: [http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=)

---

### Post by isaacj87 on 2010-05-25
> **Orions said:**
> Can anyone post some tutorial how to install progs in terminal? I hawe some files like tar.gz or something.

Given the file type, it seems you've downloaded something you need to compile. What is the program that you've downloaded?

---

### Post by Orions on 2010-05-25
it's kind a difficilt. Now I'm running on win vista, becouse the only internet connection avaiable is usb wireless modem, that runs only with software. The problem is to gen i-net for ubuntu, wich is secondary os on my laptop. MobilePartner.tar is the one.
 
And manual.. but I don't understand it. Anytime i need some help with ubuntu I must restart system, it's quite annoyng. I only need to get internet working, and than I could google ewerything from ubuntu myself.
 
--How to Install----------------------
*You need login as root*
1. Run "install" in TERMINAL to install MobilePartner
   eg: # bash /<path>/install
   
2. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit.
3. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct
4. Finish installing
--How to run--------------------------
* From shortcut in desktop
* Run MobilePartner in your install path
   eg: # /<install path>/MobilePartner
* Plug in your device, it will run automatically(Not supported in Xandros)

---

### Post by bodhi.zazen on 2010-05-25
A tar.gz is an archive, like a Zip file.

The contents can vary, what are you trying to install ?

Where did you get it ?

What is in the README file ?

If the package is in the Ubuntu repositories, use apt-get to install it.

If it is source code you first need to install any dependencies. You then extract the file and cd into the directory.

You then run

./configure
make
sudo make install

---

### Post by Nythain on 2010-05-25
actually the installation looks pretty simple, it has an install script...
just un tar that bad boy then it looks like a good
```

sudo install

```
will do the trick, after following the directions/questions

---

### Post by Orions on 2010-05-25
I can't use use apt-get to install it, because I hawen't internet connection when running on ubuntu. I am trying to install wireless usb modem and I get it from my local providers web page. Because theare isn't any info for total newbies in linux, I am not able to run it. 
And this is readme:
--How to Install----------------------
*You need login as root*
1. Run "install" in TERMINAL to install MobilePartner
eg: # bash /<path>/install

2. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit.
3. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct
4. Finish installing
--How to run--------------------------
* From shortcut in desktop
* Run MobilePartner in your install path
eg: # /<install path>/MobilePartner
* Plug in your device, it will run automatically(Not supported in Xandros)

---

### Post by Orions on 2010-05-25
Ok, than what are the commands for un-taring it? And how I can change path in terminal?

---

### Post by Nythain on 2010-05-25
```

cd /path/to/where/you/want/to/go

```
that will get you around, as for untar'ing, tar --help or google "untar gz", i dont know the command off the top of my head because i have my shell set to do it for me when i type in the name of a tar'd file :)

---

### Post by Ozymandias_117 on 2010-05-25
```
cd *directory*
``` to change directories (Folders) eg. ```
 cd Downloads
``` remember that *nix is case sensitive, so Downloads, downloads and DOWNLOADS are three different files/folders.

then to untar is ```
 tar -xvzf *filename*
``` Though note if the tarball is .tar.bz2 then it would be tar -xvjf filename

---

### Post by da burger on 2010-05-25
> **Ozymandias_117 said:**
> Though note if the tarball is .tar.bz2 then it would be tar -xvjf filename

If you don't want to learn 2 commands:
```
tar -xvaf filename
```
will work for either as long as the extension is accurate.

---

### Post by gandaran on 2010-05-25
Orions
you don't need to run all those commands, just follow these simple instructions, move the package to your home user folder/directory, right click the package and choose extract, all extracted files must be on your user folder so you don't need the cd thing.
now open terminal and type *sudo bash /install * hit enter and your password, this  is according to your instructions, should work, if any error messages post them.

---

### Post by Orions on 2010-05-25
I hawe installed files, but now I can't launch it. 
It's said in manual - --How to run--------------------------
* From shortcut in desktop
* Run MobilePartner in your install path
eg: # /<install path>/MobilePartner
But no desktop icons has appeared, and when I write in termial something like that - home/user/Desktop/Linux/MobilePartner Nothing happens.
 
  And, yes, I had some errors about cannot create patch, but I restarted to Win vista, so I'm will not be able to post them. Strange is that, when I tryed to install prog one more time, terminal asked me if owerwrite files or not, so I think it's installed correctly. Maybee I can uninstall all Mobile partner files and reinstall?

---

### Post by Ozymandias_117 on 2010-05-25
> **da burger said:**
> If you don't want to learn 2 commands:
```
tar -xvaf filename
```
will work for either as long as the extension is accurate.

Awesome trick, good to know :)

---

### Post by SRST Technologies on 2010-05-25
> **gandaran said:**
> Orions
you don't need to run all those commands, just follow these simple instructions, move the package to your home user folder/directory, right click the package and choose extract, all extracted files must be on your user folder so you don't need the cd thing.
now open terminal and type *sudo bash /install * hit enter and your password, this  is according to your instructions, should work, if any error messages post them.

Holy ****, what kind of terminal are you using that has a right click function to extract files?

---

### Post by Ozymandias_117 on 2010-05-25
> **SRST Technologies said:**
> Holy ****, what kind of terminal are you using that has a right click function to extract files?

+1 Also, why would he have to type sudo bash ./install? If you're in a bash shell... Not to mention I wouldn't sudo it unless it expressly states it has to be :P

---

### Post by bodhi.zazen on 2010-05-25
> **SRST Technologies said:**
> Holy ****, what kind of terminal are you using that has a right click function to extract files?

Not the terminal, the gui / archive manager.

Add this to ~/.bashrc (taken from my ~/.zshrc :twisted: )

```
# Extract files from any archive[FONT=monospace]
[/FONT]# Usage: ex <archive_name>[FONT=monospace]
[/FONT]function ex ()[FONT=monospace]
[/FONT]{[FONT=monospace]
[/FONT] if [ -f "$1" ] ; then[FONT=monospace]
[/FONT]case "$1" in[FONT=monospace]
[/FONT][INDENT]*.tar)                tar xvf $1        ;;[/INDENT][INDENT]*.tar.bz2 | *.tbz2 )  tar xjvf $1        ;;[/INDENT][INDENT]*.tar.gz | *.tgz )    tar xzvf $1     ;;[/INDENT][INDENT]*.bz2)                bunzip2 $1       ;;[/INDENT][INDENT]*.rar)                unrar x $1     ;;[/INDENT][INDENT]*.gz)                 gunzip $1     ;;[/INDENT][INDENT]*.zip)                unzip $1     ;;[/INDENT][INDENT]*.Z)                  uncompress $1  ;;[/INDENT][INDENT]*.7z)                 7z x $1    ;;[/INDENT][INDENT]*.xz)                 tar xJvf $1     ;;[/INDENT][INDENT]*)   echo ""${1}" cannot be extracted via extract()" ;;[/INDENT]esac[FONT=monospace]
[/FONT] else[FONT=monospace]
[/FONT][INDENT]echo ""${1}" is not a valid file"[/INDENT] fi[FONT=monospace]
[/FONT]}[FONT=monospace]
[/FONT]# Modified by bodhi.zazen[FONT=monospace]
[/FONT]# Thanks to rezza at Arch Linux
```

---

### Post by coolman98 on 2010-05-25
First read the install page witch will give you instructions to install.
If you can't find it google it'if you STILL can't find anything then
cd to the directory  (eg. cd /home/christopher/john
make
make install.:P

---

### Post by gandaran on 2010-05-26
> **Orions said:**
> I hawe installed files, but now I can't launch it. 
It's said in manual - --How to run--------------------------
* From shortcut in desktop
* Run MobilePartner in your install path
eg: # /<install path>/MobilePartner
But no desktop icons has appeared, and when I write in termial something like that - home/user/Desktop/Linux/MobilePartner Nothing happens.
 
  And, yes, I had some errors about cannot create patch, but I restarted to Win vista, so I'm will not be able to post them. Strange is that, when I tryed to install prog one more time, terminal asked me if owerwrite files or not, so I think it's installed correctly. Maybee I can uninstall all Mobile partner files and reinstall?
 
Orions
where did you install the files? in home/user/Desktop/Linux/MobilePartner?
according to instructions you have to specify the install path and install them in the root file system (*Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct*) or the software won't work.
did you use sudo in the install command? you have to if you want the root install.

---

### Post by SRST Technologies on 2010-05-26
> **bodhi.zazen said:**
> Not the terminal, the gui / archive manager.


I was working under the assumption that since the user asked for terminal commands, they did not want to or could not use the GUI.

---

### Post by michaelA1330 on 2010-05-26
sudo-apt-get-install-"program"

---

### Post by SRST Technologies on 2010-05-26
There is no dash after install.

sudo apt-get install foo

---

### Post by 3rdalbum on 2010-05-26
First, I'll ask whether you have actually tried seeing if you can use the modem from Network Manager without having to install the driver? You'll need to right-click the network manager applet on your panel and choose Edit Connections, then go to Mobile Broadband and click the Add button.

Now, if this doesn't work to set up the connection, THEN install the software.


> **Orions said:**
> 
--How to Install----------------------
*You need login as root*
1. Run "install" in TERMINAL to install MobilePartner
   eg: # bash /<path>/install

In the terminal, type the following, make sure there's a space at the end, and then drag the "install" file to the terminal:

```
sudo bash 
```

When you've dragged the file to the terminal, click in the terminal again to bring it to the front, and then press Enter.

> Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct

Yep, so just press Enter and it will install to /usr/local/Mobile_Partner.

> 
* Run MobilePartner in your install path
   eg: # /<install path>/MobilePartner
* Plug in your device, it will run automatically(Not supported in Xandros)

The file is in /usr/local/Mobile_Partner. This is a location on your hard disk. You can right-click your desktop and choose "Create Launcher", and then click the "Browse" button and choose the /usr/local/Mobile_Partner location. Give the launcher a name, and there you go.

---

### Post by Orions on 2010-05-26
Yes, I used sudo, but did not changed install path. But somethin hapened in terminal, vith errors folowing:
 
Please input the absolute path for install[/usr/local/Mobile_Partner]: /aspire6 
Local path is: /usr/local/Mobile_Partner
Installing Mobile Partner...chmod: cannot access `/usr/local/Mobile_Partner/config': No such file or directory
cp: cannot stat `./config/fontconfig/fontconfig.properties': No such file or directory
cp: cannot stat `./config/fontconfig/fontconfig.SuSE.properties': No such file or directory
[ done ] 
Installing Driver...
/usr/local/Mobile_Partner/driver/ndis_driver
The current system can not support ndis feature
ADDRUNLEVEL=/etc/rc3.d
`/etc/rc3.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc3.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc2.d
`/etc/rc2.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc2.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc4.d
`/etc/rc4.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc4.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
ADDRUNLEVEL=/etc/rc5.d
`/etc/rc5.d/S99runhwactivator' -> `/etc/init.d/runhwactivator'
`/etc/rc5.d/K10runhwactivator' -> `/etc/init.d/runhwactivator'
./driver/install: line 114: chkconfig: command not found
cp: cannot create regular file `/etc/acpi/suspend.d/': Is a directory
chmod: cannot access `/etc/acpi/suspend.d/010-huawei-suspend.sh': No such file or directory
Finished, press any key to exit
 
 
 
How to change install path to root directory?

---

### Post by jagmeet on 2010-05-26
fg

---

### Post by krizanand on 2010-08-08
Sorry guys to poke into this thread, I am having a problem installing tar.bz2, application I am trying to install is Firefox 4.1 beta, I unpacked it got into the terminal cd to that path and typed ./configure it says no such file or directory could be found, then I typed make ***same thing*** then make install ***same thing***
 
Am I doing anything wrong here? please guide me to install.

Yes I did some searching and found nothing clear cut on this. If you can pull up some threads on this which I couldn't please post it here I will get on with it.. 

Many Thanks..:p

---

### Post by mikewhatever on 2010-08-08
> **krizanand said:**
> Sorry guys to poke into this thread, I am having a problem installing tar.bz2, application I am trying to install is Firefox 4.1 beta, I unpacked it got into the terminal cd to that path and typed ./configure it says no such file or directory could be found, then I typed make ***same thing*** then make install ***same thing***
 
Am I doing anything wrong here? please guide me to install.

Yes I did some searching and found nothing clear cut on this. If you can pull up some threads on this which I couldn't please post it here I will get on with it.. 

Many Thanks..:p

Not all tar.gz files contain source code. Many are compressed binaries, which is usually the case with Firefox. All you need to do is unpack it, cd into the unpacked directory, and run the 'firefox' executable.

---

### Post by bodhi.zazen on 2010-08-08
> **krizanand said:**
> Sorry guys to poke into this thread, I am having a problem installing tar.bz2, application I am trying to install is Firefox 4.1 beta, I unpacked it got into the terminal cd to that path and typed ./configure it says no such file or directory could be found, then I typed make ***same thing*** then make install ***same thing***
 
Am I doing anything wrong here? please guide me to install.

Yes I did some searching and found nothing clear cut on this. If you can pull up some threads on this which I couldn't please post it here I will get on with it.. 

Many Thanks..:p

As mikewhatever indicated, it depends on the contents of the archive. tar file (.tar.bz) are archives, like zip files. You need to look at the contents, read the README, or look of the web page where you obtained the archive for instructions. Of course instructions vary in quality, but I tend to avoid installing poorly documented applications.

FYI: Firefox comes as a binary, although you can also download and compile the source code. Detailed instructions for doing so are on the mozilla web pages:

[http://www.mozilla.org/developer/](http://www.mozilla.org/developer/)

[https://developer.mozilla.org/en/Build_Documentation](https://developer.mozilla.org/en/Build_Documentation)

[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

Firefox is a bit complicated as you can see. I posted a how to compile icecat, which is basically firefox without the branding. 

[http://blog.bodhizazen.net/linux/icecat-64-bit-how-to-compile/](http://blog.bodhizazen.net/linux/icecat-64-bit-how-to-compile/)

The how-to is written for 64 bit icecat on Fedora,  but you should be able to adapt easily for Ubuntu.

If you prefer there is a ppa for nightly builds of firefox

[http://ubuntuforums.org/showthread.php?t=730868](http://ubuntuforums.org/showthread.php?t=730868)

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Personally , I prefer to compile icecat, but there is a ppa for icecat as well =)

[https://launchpad.net/~gnuzilla-team/+archive/ppa/+packages](https://launchpad.net/~gnuzilla-team/+archive/ppa/+packages)

---

### Post by krizanand on 2010-08-13
@mikewhatever Thanks! a lot, was scratching my head on this, I didn't know it would be this simple. Directly opened the firefox executable file, voila! it prompted me to "open in terminal" and everything was fine.

@bodhi.zazen Thanks! for taking your time in putting those links much appreciated, I am very new to Ubuntu and learning things slowly, surely will go through those links and try.

Thanks a lot guys, have a good day.:D

---

