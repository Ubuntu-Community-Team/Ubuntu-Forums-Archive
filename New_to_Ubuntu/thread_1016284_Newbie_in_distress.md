---
title: "Newbie in distress"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by hrdlukrnch on 2008-12-19
I am totally new to the scene.  I am familiar with windows xp and Vista, but want to try ubuntu and tell Mr. Gates it's over.  I have downloaded some programs but not sure how to install them.  I know the ".exe" file is different with this OS but don't know how to install.  Also I have 2 sata drives a 250gb and a 500gb with media on both but cant get them to "mount"
HELP.... Pleeeeeaaaaasssseeee?????
Thanx  hrdlukrnch

---

### Post by taurus on 2008-12-19
1.  How to install stuff in Ubuntu, [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware).

2.  How to mount ntfs filesystem--windows.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jerome1232 on 2008-12-19
What programs are these exactly? Do you have a link to thier websites?

A good amount of software can be found in Ubuntu's repos, look through add/remove to get started. Applications->Add/Remove... 

For a much more complete list look in Synaptic, System->Administration->Synaptic Package Manager

For your drives are they external drives or internal drives? 

If they are internal:

If you assigned them a mount point during the installation then that's where they'll be mounted, to see where everything is mounted use the mount command by itself. 

Otherwise they should be listed in your places menu. If you still can't find them then post the output of these commands
```
sudo fdisk -l
mount
```

If they are External then they should once again show up in you Places menu, if not post the output of those commands in addition to this one (with them plugged in)
```
lsusb
```

btw post the output of those wraped in code tags like this [noparse]```

```[/noparse]

---

### Post by Michael.Godawski on 2008-12-19
hi,
relax, easy, have fun...

Linux is not Windows. Have a look at psychocats site.
Humbly I add also mine:

[http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)

---

### Post by hrdlukrnch on 2008-12-19
well the software was the firefox update and "wine" which i was told would run some of my windows programs


as for the drives i had them unplugged during installation and I also have an 80 gb ext but thats not a big deal


I am a complete moron with this software so I need an idiots guide to ubuntu
step by step

thanks

---

### Post by Michael.Godawski on 2008-12-19
For wine have a look here:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

feel free to ask for advice if you have questions concerning the installation process of Wine.

---

### Post by jerome1232 on 2008-12-19
Okay well firefox is installed by default and will update along with your system, wine is included in the repositories and can be installed from with-in synaptic. 

You will need to enable universe to install it

System-Administration-Software Sources, put a check next to the one with the word universe in it.

Now open synaptic and search for wine, mark it for installation.

Plug your drives in and they should automaticly mount themselves and show up on your desktop.

---

### Post by Temposs on 2008-12-19
hi hrdlukrnch,
   
In most cases, you should not have to download new programs from their websites. Instead, you should use Ubuntu's built-in program installer.

If you go to the "Applications" menu, and click on "Add/Remove...", then you can search for programs like wine and firefox and most other things you may want to use. It's very easy to check any program you want to install and click Apply. All the programs you check will then be downloaded and installed automatically.

It's also generally unnecessary to download updates for programs you get in this way. Ubuntu will release updates to all programs you have on your computer, as long as they came installed by default or you got them using "Add/Remove..."

This means you don't need to download the Firefox update yourself. Ubuntu takes care of keeping firefox up to date for you, or any other program you get in this normal way.  All you have to do is click to install the automatic updates that Ubuntu sends to you, and that will appear as a little icon on the top right of the screen.

You should always see if you can install your programs in this way, as opposed to going to the website of the program you want to download. I hope you find it very easy to use.

Please keep asking questions here :-) You're on the right track!

---

### Post by Temposs on 2008-12-19
Additionally, if you'd like to get some step-by-step video tutorials, there are many located here: [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

You can get tours of many aspects of Ubuntu and the applications you can use with Ubuntu. I hope you find this helpful :-)

---

### Post by hrdlukrnch on 2008-12-19
Ok I'm gonna go over everything tonight and hopefully I can get to where I want to be with this for a while.  

I plugged the drives in and they are showing up but i cant access anything on them it says it can't mount the drives. in the details it says something about having windows and forcing option.  I just want access to my media without chancing deleting it

BTW Thanks so much guys for the help, I have alot to read up on

Thanks again
Ryan

---

### Post by jerome1232 on 2008-12-19
Okay more than likely you didn't use the safely remove option when you last had them in a windows computer. Next time plug it into the windows computer and be sure to select "safely remove hardware" before removing the drives.

Basically Ubuntu can see that they weren't safely last time and is refusing to mount them in case it caused errors.

---

### Post by hrdlukrnch on 2008-12-19
yea what had happened was my system had a virus or something and needed a reformat and I used my ubuntu disk to do so that way I could use the software and give it a whirl.

---

### Post by jerome1232 on 2008-12-19
If you dont' have a windows computer then you can use nftsfix to remove the log files that are telling Ubuntu they weren't disconnected correctly last time.

You would change /dev/sdxx to the real device path for your drive, if your not sure then post the code I have at the end of this post and we can help you with that.
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdxx
```


(if your not sure of the device path)
```
sudo fdisk -l
```

---

### Post by albinootje on 2008-12-19
> **hrdlukrnch said:**
> 
I plugged the drives in and they are showing up but i cant access anything on them it says it can't mount the drives. in the details it says something about having windows and forcing option.  I just want access to my media without chancing deleting it

Don't lose faith about that. 
Read something about NTFS on the ubuntuforums.org.
The question "why NTFS partitions cannot be mounted, and the forced option is suggested" has been answered several times.
Different solutions do exist for that problem.
If you are really worried about your data, then use the option to attach them to a MS-Windows machine, and then use "safely remove" before detaching them again. After that the problem should be solved.

---

