---
title: "UBUNTU NOOBIE NOOB needs help"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by ZekeWild on 2009-11-26
Gday; ):P

I'm new to Ubuntu and I'm trying to install some software without much luck.
I go to Applications-ubuntu reasorce centre- and then click on flashplayer, next and when i go to install it installs 3% then comes up with a error message:

The installation or removal of a software package failed.
E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.: ;)



"this happends for every program I try to install. even when I try to install Amarok to play Mp3's it still says the same message about the flashplug in.

Also dose anyone know where i can get Some software so i can run EXE's on Ubuntu, i know there are some around but i would like some Direct download links.


thanks.;)

Zeke.

---

### Post by JoshStrobl on 2009-11-26
When trying to install flashplugin go to:
System > Administration > Synaptic Package Manager.
go to the search and type in flashplugin and install flashplugin-installer.

to play mp3 and multiple other codecs search for gstreamer and then install:
gstreamer-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-nice
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

any other problem just let us know! ;)

---

### Post by akakingess on 2009-11-26
Try going to the System (menu) ----->Administration----->Synaptic Package Manager.  That will open the package manager and require you to enter your password. Once in there, type in the quick search bar flashplugin-nonfree , and that should show you the nonfree version of the flash plugin and you should be able to install from there. If you need more assistance, just let us know.

Sorry, to install you right-click on the check box next to it and choose Mark for Installation, when it is checked you hit the Apply button, and that should install it. If you choose to install the flashplugin-nonfree, it will automatically also choose the flashplugin-installer.

---

### Post by williejones on 2009-11-26
Zeke

You already have answers to most of your questions.  To run .exe programs you will need to install Wine.

---

### Post by ZekeWild on 2009-11-26
i went to  Synaptic Package Manager. in administration and clicked on it to open it up:

Enter password; ok i enter my password.
and now this box appears with a Read sign-

An error occurred
 
The following details are provided:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

WTF?

---

### Post by ZekeWild on 2009-11-28
The following details are provided:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

for anything i try to install on ubuntu, 

can i get these installations from: ubuntu software center to install software!!!!!!!!!1

also can some one posty a good download link for Wine thankx.

ANGERY FACE.

---

### Post by Spiffjiggins on 2009-11-28
I'd like to know how you installed adobe in the first freakn place. I can not. I don't know which ones to download and when I do, they don't download to the desktop, they download to the download box. And then I have NO idea what to do after that.

---

### Post by jamesisin on 2009-11-28
You should be able to install WINE through Synaptic (System --> Administration --> Synaptic Package Manager).

You may want to have a look at this post for all audio/video issues:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jamesisin on 2009-11-28
> **Spiffjiggins said:**
> I'd like to know how you installed adobe in the first freakn place. I can not. I don't know which ones to download and when I do, they don't download to the desktop, they download to the download box. And then I have NO idea what to do after that.

The post I provided above will walk you through setting up the software you need.

---

### Post by raktarok on 2009-11-28
For the flash issue, try these three commands from a terminal, in this order.
```
sudo rm /var/lib/dpkg/info/adobe-flashplugin.*
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin
```

Now you should be able to install programs, but if this does not help, post again. 

If you are trying to install flash, just do this:
```
sudo apt-get install ubuntu-restricted-extras 
```
It will drag java, flash, codecs and other stuff

Regarding wine, you can install it like this:
```
sudo apt-get install wine
```

If you don't like installing things via terminal, you can search the above package names in synaptic packet manager or software center.

No need to be so angry, though. :) the flash issue arose maybe because you used a package from adobe's website? and I think the issue's been around here for some days now.

---

### Post by ZekeWild on 2009-11-28
> **jamesisin said:**
> You should be able to install WINE through Synaptic (System --> Administration --> Synaptic Package Manager).

You may want to have a look at this post for all audio/video issues:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

i have already tryd this like 50 billion tymes 
i have not downloaded adobe. or flash that i know of.
although i would like to to be able to go onto youtube.

I have also uninstalled windwos and Ubuntu is now my operating systemn.reasorce managment is still coming up with the error message.


Z

---

### Post by raktarok on 2009-11-28
This should solve the error then.
First, make a backup of the file /var/lib/dpkg/status
```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak
```
Now open that file.
```
gksudo gedit /var/lib/dpkg/status 
```
Serach for adobe-flashplugin and delete the entire block that comes with it.
Proceed carefully though, do not mess up other lines.
Save the file and close it.Now you should be able to install packages. 
Try installing ubuntu-restricted-extras for flash, like I said above. And wine should install now too. 
Hope this helped!

---

### Post by ZekeWild on 2009-11-28
where can i find the file to put in zee code i'll go delete adobe

---

### Post by ZekeWild on 2009-11-28
went to serch can not find  adobe-flashplugin :(

---

### Post by wilee-nilee on 2009-11-28
[http://ubuntuforums.org/showthread.php?t=1338829](http://ubuntuforums.org/showthread.php?t=1338829)
Double threads are not allowed.

---

### Post by raktarok on 2009-11-28
Really? This did not work? you typed the above commands from terminal right?
and what output does this give now?
```
sudo dpkg --purge --force-all adobe-flashplugin
```

and you should have continued the other thread, double threads are not allowed....

---

### Post by ZekeWild on 2009-11-28
sudo dpkg --purge --force-all adobe-flashplugin

where abouts on the computer is this were are somne stepoby step instructions i can't install any programs and have no other operating system

---

### Post by raktarok on 2009-11-28
Are you using a terminal? Go to the menu and then Accessories > Terminal. Enter these commands there, in the correct order.(copy one line at a time and then hit enter) At the end, try installing some programs. It should work now.

If you don't understand what the commands do, don't worry. The commands with the word 'dpkg' in them, you will have to use terminal. But if what I told in my first post fails and you have to edit the file /var/lib/dpkg/status, then you can open the nautilus as root (press alt+F2, do gksudo nautilus) and then navigate to the folder,open the file and edit it like I said above. But it will be much faster using the terminal, believe me.

I am sorry, but I thought I had already given the step by step instructions. Its unfortunate that you have to deal with such an ugly problem so early on, I hope this does not ruin your impressions of Ubuntu and linux in general. Though I admit that you have to go to the commandline once in a while to solve some problems in linux (yours could be counted as one such problem) and this can be a bit intimidating to the new user, please be patient. 

I hope you give these steps a sincere try. Post again if you face the problem again. Sorry if the steps I described were not clear enough...

---

### Post by bapoumba on 2009-11-28
Threads merged.

To the OP, please post your sources.list:

```
cat /etc/apt/sources.list
```

---

### Post by ZekeWild on 2009-11-28
OK i tryed it in the tenamal and got this messadge:

zeke@badsatan:~$ sudo dpkg --purge --force-all adobe-flashplugin
[sudo] password for zeke: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 138076 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
zeke@badsatan:~$ 
zeke@badsatan:~$ 


were can i redownload this to uninstall it?
and if i redownload it?

thankx.

---

### Post by jrrader on 2009-11-28
> Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.

I saw this once when my dad upgraded from 9.04 to 9.10.
Nothing would install. Nothing would uninstall.  I manually removed the bad file (the same adobe-flashplugin) but it did not help.  I was putting Windows 7 on his computer so it didn't matter much.  If he wanted to keep Ubuntu I would have just popped in the live disk and reinstalled.  I was pretty sure his problem was related to doing an upgrade rather than a clean install.  The software sources were directed at the jaunty repos and removing them only made things worse.

But like I said, I didn't spend much time on it (and wouldn't have).

---

### Post by raktarok on 2009-11-28
> **ZekeWild said:**
> OK i tryed it in the tenamal and got this messadge:

zeke@badsatan:~$ sudo dpkg --purge --force-all adobe-flashplugin
[sudo] password for zeke: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 138076 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--purge):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
zeke@badsatan:~$ 
zeke@badsatan:~$ 


were can i redownload this to uninstall it?
and if i redownload it?

thankx.

Please try what I said in post #12. You have not tried that, I think. Then do this:
```
sudo apt-get remove adobe-flashplugin
sudo apt-get install ubuntu-restricted-extras
```
The package ubuntu-restricted-extras has the flash plugin.
This should work and if it still does not, please post the output of the commands here. Don't give up,this is a nasty problem, but it can be solved!

---

### Post by ZekeWild on 2009-11-29
[FONT=monospace]zeke@badsatan:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
zeke@badsatan:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
zeke@badsatan:~$ 



Quote: "Serch for flush plug in and delete it" in the document that was created in it i serched for flush plug in and could not find it.  


Still can not open Synapic pacage manager or istall Sorftware from ubuntu software center.

[/FONT]

---

### Post by raktarok on 2009-11-29
Post the output of these:
```
sudo ls /var/lib/dpkg/info/adobe*
```
Also, 
```
cp /var/lib/dpkg/status ~/Desktop
```
Now, the status file should be in your desktop. Attach it here, I will have a look at it.

---

### Post by ZekeWild on 2009-11-29
zeke@badsatan:~$ sudo ls /var/lib/dpkg/info/adobe*
[sudo] password for zeke: 
/var/lib/dpkg/info/adobe-flashplugin.list
/var/lib/dpkg/info/adobe-flashplugin.md5sums
/var/lib/dpkg/info/adobe-flashplugin.postinst
/var/lib/dpkg/info/adobe-flashplugin.prerm


statas is now on my desctop what next.

---

### Post by raktarok on 2009-11-29
First try this,
```
sudo rm /var/lib/dpkg/info/adobe*
```
This deletes the files starting with adobe, the files in the output you posted.
Then try removing and installing packages.
```
sudo apt-get remove adobe-flashplugin
sudo apt-get install ubuntu-restricted-extras
```
The package ubuntu-restricted-extras has the flash plugin.
If this still fails, post the output here and also attach the status file you copied to the desktop. You know how to attach files, right? You should click on the "manage attachments" button..

---

### Post by ZekeWild on 2009-11-29
[sudo] password for zeke: 
rm: cannot remove `/var/lib/dpkg/info/adobe*': No such file or directory
zeke@badsatan:~$ 


zeke@badsatan:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
zeke@badsatan:~$ 


zeke@badsatan:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
zeke@badsatan:~$ 




Ubuntu Software centure still refuses to install any software:

Package operation failed
The installation or removal of a software package failed.
E:I wasn't able to locate file for the adobe-flashplugin package. This might mean you need to manually fix this package.:

---

### Post by SunnyRabbiera on 2009-11-29
This is actually very weird, it seems your package manager is borked for some odd reason.
Did you try to manually install flash from adobes website using the .deb installer?

---

### Post by raktarok on 2009-11-29
Hmmm...strange..'ls' shows the files exist, but you can't delete it?
Okay try this:
```
cd /var/lib/dpkg/info/
sudo ls adobe*
sudo rm -v adobe*
sudo apt-get remove adobe-flashplugin
sudo apt-get install ubuntu-restricted-extras
```

If this fails, please attach the file 'status' that I told you to copy to your desktop earlier.

---

### Post by Gazneth on 2009-11-29
I think the force command from earlier did not go far enough. Please try the command below, it should work to remove the offending package.
```
sudo dpkg --remove -force --force-remove-reinstreq adobe-flashplugin
```

This is my go to command for most apt cache problems.

---

### Post by ZekeWild on 2009-11-29
zeke@badsatan:~$ cd /var/lib/dpkg/info/
zeke@badsatan:/var/lib/dpkg/info$ sudo ls adobe*
[sudo] password for zeke: 
ls: cannot access adobe*: No such file or directory
zeke@badsatan:/var/lib/dpkg/info$ 




zeke@badsatan:~$ sudo dpkg --remove -force --force-remove-reinstreq adobe-flashplugin
dpkg: conflicting actions -f (--field) and -r (--remove)


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
zeke@badsatan:~$

---

### Post by raktarok on 2009-11-29
Please attach the /var/lib/dpkg/status file here, as I told you some posts earlier. This problem is taking long to solve...

---

### Post by raktarok on 2009-11-29
And regarding the second command you tried, it should probably be this one:
```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```
Give it a try. 
And don't forget to attach the status file, please let me have a look at it,and see if something is wrong.

---

### Post by Gazneth on 2009-11-29
Maybe I was typing too quick I put in too many forces, used too much force :p:p  . This one should work.
```
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
```

---

### Post by ZekeWild on 2009-11-30
well that did it i Aparantly can install stuff now; however is thier a safe way to get flashplayer onto my computer without this problem coming up again?
Also can someone post a download link to wine with software instalation instructions? thanks.

---

### Post by raktarok on 2009-11-30
Glad to hear its finally solved! :)
For wine, you can do this:
```
sudo apt-get install wine
```

For flash, this worked fine in my laptop. It installs codecs, java and other stuff besides the flash-plugin. Give this a try.
```
sudo apt-get install ubuntu-restricted-extras
```

If you don't want to use terminal, then you can search for these packages in System > Administration > Synaptic Packet Manager OR in ubuntu software center.

Good luck and have fun with ubuntu!

---

