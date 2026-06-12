---
title: "Repository access confusion"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by Anne Sejer on 2009-09-21
I've been getting used to Ubuntu for a few months now, and althoug I know very little about computers i enjoy learning a new system (new for me). I have had a problem I don't quite understand though. I have been trying to install compiz fusion, and when I go under add/ remove an application I get the following message

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

In the box it says:
Listemappen /var/lib/apt/lists/partial mangler.

I can't see that  have internet connection problems as I am here and now writing on this forum. What am I not understanding, and what should I be doing to get repository access?

Thank you all in advance - these forums are always very positive and helpful for spreading positive vibes for the linux world to people like me who really don't know allot about computers

Best, Anne

---

### Post by drs305 on 2009-09-21
Which version of Ubuntu are you currently using? 

If you post your sources.list we can see if there are any problems. Open a terminal (Applications, Accessories, Terminal) and enter:
```

gksu gedit /etc/apt/sources.list

```
You will be asked for your password.

---

### Post by Anne Sejer on 2009-09-21
Hi am running Ubuntu9.04
I am being called to the table for eating, but I will try to find a terminal after eating and post the list. Thank you,
Ane

---

### Post by Anne Sejer on 2009-09-21
Hi  again! Here is my list:
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse


That makes absolutely no sense to me!

:)

---

### Post by drs305 on 2009-09-21
I ran your sources.list and there aren't any problems in the active listings. There are several commented lines (lines starting with a # symbol which aren't acted upon) which contain references to *intrepid*. Although they aren't used, it would probably be best to remove them from the file. 

Open sources.list as per the previous post, and remove the following lines in **bold**. Then save and update the sources again.
> 
[COLOR="DarkRed"][B]# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse[/B][/COLOR]

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
[COLOR="DarkRed"][B]# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner[/B][/COLOR]


Since there aren't any errors in your sources.list, you might want to try a different server. Open Synaptic (System, Administration, Synaptic Package Manager). 
Go to Settings, Repositories, Download from:
Select "Other" and try another server.
Hit Reload to refresh the list.

If you still get errors, go to the "Third Party" or "Other Software" tab. Note which ones are selected and then untick any repositories enabled, and Reload again.

Finally, it appears you may have an error in your /var/lib/apt/lists/partial folder. Only if you are still getting errors:

Remove the entire contents of this folder (but not the *partial* folder itself:
```

gksu nautilus /var/lib/apt/lists/partial

```
Highlight everything in this folder and use SHIFT-DEL to remove the contents.
Then run:
```

sudo apt-get update
sudo apt-get upgrade

```
If asked for your password, type it and press ENTER. You won't see it as you type.

---

### Post by pedro3005 on 2009-09-21
And compiz fusion already comes installed. All you need is the package ccsm to configure it. Once you get this sorted out:
```
sudo apt-get install ccsm
```

---

### Post by Anne Sejer on 2009-09-21
Hi DRS305 & Pedro3005, Thanks for the help - I still haven't quite gotten it sorted out, but my eyelids are getting heavy, and I'll give it a shot tomorrow - I greatly appreciate the input, and actually think it's a challenge learning my way around the system a bit more. Thanks,
Anne

---

### Post by Anne Sejer on 2009-09-22
Hell o Again, I still haven't quite beaten this problem but I am definetly learning while trying!

I have tried to choose a new server, and delete the code lines as shown by DRS305 above but still no fun. 

Now I am trying to get the var/.... directory to update and upgrade and update. I have tried to run the code in the terminal, but I get this bellow which sort of has scared me:

gksu nautilus /var/lib/apt/lists/partial
anne@anne-laptop:~$ gksu nautilus /var/lib/apt/lists/partial

** (nautilus:4576): WARNING **: Unable to add monitor: Operation not supported
Sense key: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0xb9 0x00 0x00 0x00 0x00 0x00 0x00 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///var/lib/apt/lists
--> file:///root/Desktop
--> file:///var/lib/apt
--> file:///
--> file:///var
--> file:///var/lib
--> file:///root

(nautilus:4576): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 7 elements at quit time (keys above)

(nautilus:4576): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 7 elements at quit time
anne@anne-laptop:~$ 

I guess I don't really know if I am actually opening the folder in the terminal, and if so how I should highlight which files. I do think I have got the update and upgrade part from the terminal (as a concept anyway).

Thanks again!

Anne

---

### Post by drs305 on 2009-09-22
Anne, 

All the messages in the terminal are standard; and "monitor" isn't referring to your screen but system monitoring. Anyway, if nautilus opened in a separate window you can perform the tasks I outlined in the previous post. 

Once nautilus opens to the partial folder, you should see a (long or short) list of files. You can hold down the shift button and use the down cursor to highlight them all, or you can use your mouse.

I know those messages can be a bit intimidating - I might have warned you but I was hoping you wouldn't have to get that far.  ;-)

---

### Post by philinux on 2009-09-22
ccsm does not exist anymore, since which version I cant remember.

Its now compizconfig-settings-manager

---

### Post by Anne Sejer on 2009-09-22
Hmmmm, I'm not doing to wel here..... :(


anne@anne-laptop:~$ sudo apt-get update
[sudo] password for anne: 
E: Listemappen /var/lib/apt/lists/partial mangler.
E: Kunne ikke opnå låsen /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
anne@anne-laptop:~$ sudo apt-get update
E: Listemappen /var/lib/apt/lists/partial mangler.
anne@anne-laptop:~$ sudo apt-get upgrade


I think I am getting in deeper???

---

### Post by philinux on 2009-09-22
You must only have one package manager open at a time. Close synaptic. If that does not work then log out and in again then try the terminal commands.

---

### Post by Anne Sejer on 2009-09-22
Ok, I'm not sure or why, but there appered to be missing the artials folder which the system said it couldn't find - I then created one manually and bingo life got easier - I' don't quite know why, but it seems to funktioning online and downloading packages and updates again???

Thanks for everyones help, but if anyone can clear up my pleasant state of confusion it ould be appreciated - learn and live I guess.

Anne

---

### Post by drs305 on 2009-09-22
/var/lib/apt/lists contains information about available packages. Sometimes the list files become corrupted and part of the solution is to remove the files in the "lists" folder and "partial" subfolder.

The /var/lib/apt/lists/partial folder must exist. If you run any of the APT apps (installation apps) and it tries to find the "partial" folder and can't it generates an error message. That is why I told you to delete any files in "partial" but not the "partial" folder itself.

It doesn't matter if the "partial" folder is empty or not, it simply must exist. Once you created it, APT was happy to proceed.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

