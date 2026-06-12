---
title: "Radeon 5850 driver install, some other stuff"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by theubersmurf on 2010-04-24
So I'm giving Ubuntu another try, it has been a couple of years, but I wanted to get back into it. I'm having a much easier time with it now than I was then, but there are still hurdles.

The first and foremost of which is my GPU driver. I have in my system a Radeon 5850, and the OS prompted me that I may want to use a proprietary driver. I installed this and have an "Unsupported Hardware" message in the lower right of my screen. I'd had trouble with a manual installation of the driver proffered when I went to AMD's site, and deferred it to the OS, and I'm unsure if I should leave it like this. It can render my widescreen at resolution (1680x1050) and there is no more delay with visual effects, it's running compiz well as well, so it's at least functioning somewhat as a driver.

The second thing, and pretty high on the list, Is I want to buy a book. An actual book (NOT something online, something that I can refer to and read when I'm not at the comp so I'm not reading a huge text at the computer) that will help my understand the syntax used for the terminal. At this point I'm just regurgitating what I read online for commands. And I want to have some grasp of what I'm inputting and hopefully some idea how the OS works via corollary.

The last thing is the Kernel version of 9.10. My Sound card seems to be working with whatever is installed, (xonar DX) but I want to make sure I have the best driver available for it, and that everything will function fairly well.

Also, should I worry about my chipset drivers and NIC drivers at all?

---

### Post by -humanaut- on 2010-04-24
I'm not entirely sure what your asking? If everything is working there's no reason to fix it? Can you clear up what you need help with a little bit?

---

### Post by theubersmurf on 2010-04-24
Ok. My video card is using the proprietary driver the OS installed from the hardware drivers system utility. It's giving me an unsupported hardware logo in the bottom right portion of the screen. It seems to be working, but the logo makes me wary. I'm not sure the driver is the most recent (10.3) or if it's an older proprietary driver. Since I have a new card, I want a driver version that supports it properly.

I want a book on using the terminal, it's terms and syntax so I can read about it in my off time.

Should I worry about my chipset and NIC drivers, they seem to be working well. There is a proprietary NIC driver I want to install, but I'm unsure how.

Which kernel version is Ubuntu 9.10?

---

### Post by -humanaut- on 2010-04-24
> **theubersmurf said:**
> Ok. My video card is using the proprietary driver the OS installed from the hardware drivers system utility. It's giving me an unsupported hardware logo in the bottom right portion of the screen. It seems to be working, but the logo makes me wary. I'm not sure the driver is the most recent (10.3) or if it's an older proprietary driver. Since I have a new card, I want a driver version that supports it properly.

I want a book on using the terminal, it's terms and syntax so I can read about it in my off time.

Should I worry about my chipset and NIC drivers, they seem to be working well. There is a proprietary NIC driver I want to install, but I'm unsure how.

Which kernel version is Ubuntu 9.10?

uname -r
that command will give you the kernel version

I wouldn't be worry about the NIC or chipset if everything is working for you. I'm not sure which version ATI is at I have a nVidia card a good book for the Bash shell "Learning the BASH shell" by o'reilly books would be good also check out [http://tldp.org](http://tldp.org) for more info and suggestions and free documentation on Linux

the Linux Bible is also a Great reference book for all things Linux

---

### Post by quadproc on 2010-04-24
> **theubersmurf said:**
> ...
The first and foremost of which is my GPU driver. I have in my system a Radeon 5850, and the OS prompted me that I may want to use a proprietary driver. I installed this and have an "Unsupported Hardware" message in the lower right of my screen. I'd had trouble with a manual installation of the driver proffered when I went to AMD's site, and deferred it to the OS, and I'm unsure if I should leave it like this. It can render my widescreen at resolution (1680x1050) and there is no more delay with visual effects, it's running compiz well as well, so it's at least functioning somewhat as a driver.

I have learned that the Ubuntu "Hardware Drivers" utility does not necessarily correctly report the status of the system.  I have HD4870x2 cards and I am running fglrx but the Hardware Drivers utility says that the driver is not enabled even though it is.

Since the Hardware Drivers utility does not give you any choice or control over the driver installation, nor does it report correctly, I recommend that you not use it.  Much better to download the ATI driver version that _you_ want and do the install yourself.  That way, you can keep the installation directory, look it over, and perhaps learn some interesting things about ATI's methods.  And you'll know which version you installed.

For sure, if you are going to install an ATI driver, remove the old one first.  Failing to do that can cause a lot of trouble, including a system that doesn't do any output!

There are a bunch of potential issues regarding the version of the driver, the version of Ubuntu, and the vintage of the card.  You will need to be sure that all 3 are compatible with each other.
> 
The second thing, and pretty high on the list, Is I want to buy a book. An actual book (NOT something online, something that I can refer to and read when I'm not at the comp so I'm not reading a huge text at the computer) that will help my understand the syntax used for the terminal. At this point I'm just regurgitating what I read online for commands. And I want to have some grasp of what I'm inputting and hopefully some idea how the OS works via corollary.There are a number of web sites that contain information on bash programming; you could print out one or more of these.  But you probably want a decent sized book and that usually isn't practical to print.  There are several bash books on the market and they have been reviewed by various people.  The O'Reilly book was panned but I haven't seen it myself so I can't tell if it deserved criticism.  Another book by Chris Johnson didn't seem to receive review criticism but I have seen it and I think that it would be a little difficult for a beginner to use because there are many things that need explanation but the book is silent on those aspects.  It is probably OK for someone who is already knowledgeable in the Bourne shell or bash.  Another consideration is the vintage of the book; bash has been evolving and some of the books do not cover all of the language's capabilities.

If you have more questions then fire away.

quadproc

---

### Post by theubersmurf on 2010-04-25
Thank you for your reply. I do have some follow up questions. It says I need to restore the original Xorg configuration files.

1 Locate backup configuration files: ls /etc/X11/xorg.conf.original-*
  Take the latest version with the highest number and copy it over the existing
2
  xorg.conf file: cp /etc/X11/xorg.conf.original-<number> /etc/X11/xorg.conf

I'm not sure where to look for this stuff at all.

-----------------------------------------------------

Then, to install, it says this:

1 Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux
  driver download.
2 Enter the command sh ./ati-driver-installer-10-3-x86.x86_64.run to launch the ATI
  Proprietary Linux driver installer.
  The ATI Proprietary Linux Driver Setup dialog box is displayed.

When it says "navigate to the ATI Proprietary driver download" Does that mean using the gui or using the Terminal.

By way of explanation, I'm used to using DOS/DOS-like commands in the windows environment. To run an executable from the command line in Windows, I'd input the location of the file I want to run. C:\Program Files\...\yadda yadda.exe. I don't really know how the file system works in Ubuntu...and so I'm how I'm navigating there, or if it's writ in the terminal somehow.

---

### Post by cryptotheslow on 2010-04-25
***Edit to say:** Uninstall the current proprietary driver you installed via the "Hardware Drivers" application before you start this or you can end up in a big mess!*

> **theubersmurf said:**
> Thank you for your reply. I do have some follow up questions. It says I need to restore the original Xorg configuration files.

1 Locate backup configuration files: ls /etc/X11/xorg.conf.original-*
  Take the latest version with the highest number and copy it over the existing
2
  xorg.conf file: cp /etc/X11/xorg.conf.original-<number> /etc/X11/xorg.conf

I'm not sure where to look for this stuff at all.

Do this from a Terminal (Applications > Accessories > Terminal):
1. Navigate to the correct directory:
```
cd /etc/X11
```2. Make a backup of your existing xorg.conf (in case you should need to revert it):
```
sudo cp xorg.conf xorg.mybackup
```3. List the contents of the directory to identify which xorg.conf backup file you need to copy:
```
ls -l
```The -l gives the more detailed format of the directory listing with the timestamps.

4. Now you have identified the name of the file you want to copy:
```
sudo cp /etc/X11/xorg.conf.original-<number> /etc/X11/xorg.conf
```
-----------------------------------------------------

> **theubersmurf said:**
> Then, to install, it says this:

1 Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux
  driver download.
2 Enter the command sh ./ati-driver-installer-10-3-x86.x86_64.run to launch the ATI
  Proprietary Linux driver installer.
  The ATI Proprietary Linux Driver Setup dialog box is displayed.

When it says "navigate to the ATI Proprietary driver download" Does that mean using the gui or using the Terminal.

By way of explanation, I'm used to using DOS/DOS-like commands in the windows environment. To run an executable from the command line in Windows, I'd input the location of the file I want to run. C:\Program Files\...\yadda yadda.exe. I don't really know how the file system works in Ubuntu...and so I'm how I'm navigating there, or if it's writ in the terminal somehow.

I would recommend creating a new folder in your home directory called "atidriver" or somesuch, so you know where the driver install file is should you need to reinstall/uninstall it in future. Put your downloaded file in there (just use the normal GUI way of doing it).

Then back to a Terminal.

Navigate to the folder with the driver file in it:
```
cd ~/atidriver
```The ~ always represents your Home directory btw.

You may need to make the downloaded file executable by amending the permissions on it:
```
chmod +x ati-driver-installer-10-3-x86.x86_64.run
```Then execute it:
```
sh ./ati-driver-installer-10-3-x86.x86_64.run
```The ./ before the filename effectively means "this directory".

Then follow the prompts in the installer :D

---

### Post by theubersmurf on 2010-04-25
Ok, I tried running the installer, and it says I have to run it as a super User

---

### Post by cryptotheslow on 2010-04-25
Ubuntu doesn't have an xorg.conf file by default as it sets up most things automagically by detecting them at startup. The proprietary drivers quite often create an xorg.conf file to hold their particular settings.

If there is no xorg.conf file there at all - do not worry about it. Just proceed to the driver install bit.

---

### Post by theubersmurf on 2010-04-25
Ok then, good to know, how do I run it as a super user? I have myself set up as the admin, but that's obviously not doing it.

did some hunting, and sudo bash gave me the priveleges I needed, thanks for all your help.

---

### Post by cryptotheslow on 2010-04-25
> **theubersmurf said:**
> Ok then, good to know, how do I run it as a super user? I have myself set up as the admin, but that's obviously not doing it.

```
sudo sh ./ati-driver-installer-10-3-x86.x86_64.run
```

It will prompt you for your password when you do this then run the installer with su privileges.

---

### Post by theubersmurf on 2010-04-25
Again, thanks for the help. The unsupported hardware logo/warning is gone, I have access to CCC and can run at my native resolution and compiz is wobbling around like an eight year old pretending to be a rubber band.

---

