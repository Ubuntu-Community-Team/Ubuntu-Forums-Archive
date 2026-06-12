---
title: "iamfamous.dll mozilla - virus"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-01-01
my mozilla fox is acting differently..

i now worry that whether my firefox got infected with iamfamous.dll trojan virus...

i read in my school book that virus is the term unknown to linux :(

but now i fear..

can you tell me in which folder - firefox is installed so that i can open its compenents folder to see whether it has iamfamous.dll in it ?


if it is there , if i reintsall firefox will this problem be solved ????????



help A S A P !!!!!

---

### Post by Delever on 2009-01-01
Windows DLL files should not be able to work on Linux (normally). I suggest not to panic at first.

> my mozilla fox is acting differently..

Can you tell us WHAT is different, and what you expected instead of what it is now?

---

### Post by OutOfReach on 2009-01-01
Can you tell us what exactly is happening to Firefox?

---

### Post by handydan918 on 2009-01-01
Relax. Linux doesn't use .exe or .dll files. I have been running linux in various flavors on  my desktop for 8 years, and have deliberately opened .exe attachments from "nigerian businessmen". No problem.
In any case, if you want to find an executable like firefox, you can open a terminal and do```
which firefox
``` or whatever the name of the program is. 
If you DO have a .dll on your system, it isn't doing anything. It  can't. 


Just don't run  it in wine...


:P

---

### Post by k3lt01 on 2009-01-01
> **handydan918 said:**
> Just don't run  it in wine...This is the only way a dll can infect your Linux pc. Using a program like WINE or virtualising Windows within Linux may cause a problem but your fine if they aren't installed.

---

### Post by kimikrishna on 2009-01-01
oh ! thankyou..

my firefox automatically opened a site named indian.adultfriendfider...

i didnot choose that link in any way..... :O

thats the reason i feared...


btw can anyone tell me how to install WINE ?? and what is wine ??

---

### Post by bumanie on 2009-01-01
Agree with the above; .exe and .dll won't run on linux (except through wine). Also for a virus to wreak havoc on your system you would have to execute with root privileges. Strangely enough, I had to remove and reinstall firefox recently due to 'strange' behaviour - I had been playing around with some settings so it was probably that rather than any sinister spyware/virus. If you want to remove firefox and reinstall it, post back, it is very simple.

---

### Post by jrusso2 on 2009-01-01
> **handydan918 said:**
> Relax. Linux doesn't use .exe or .dll files. I have been running linux in various flavors on  my desktop for 8 years, and have deliberately opened .exe attachments from "nigerian businessmen". No problem.
In any case, if you want to find an executable like firefox, you can open a terminal and do```
which firefox
``` or whatever the name of the program is. 
If you DO have a .dll on your system, it isn't doing anything. It  can't. 


Just don't run  it in wine...


:P

There are .dll's in Linux in both WINE and for Win32codecs.  The OP. states this is a trojan not a virus.

Can you please explain what you did with what program.  Please post the link you downloaded from. Did you use the Windows firefox or the Linux one?

---

### Post by Delever on 2009-01-01
> **kimikrishna said:**
> oh ! thankyou..

my firefox automatically opened a site named indian.adultfriendfider...

i didnot choose that link in any way..... :O

thats the reason i feared...


btw can anyone tell me how to install WINE ?? and what is wine ??

You seem to be good with web resources, here is the link:

[http://www.winehq.org/](http://www.winehq.org/)

Wine is in repositories (Add/Remove)

---

### Post by kimikrishna on 2009-01-01
> **jrusso2 said:**
> There are .dll's in Linux in both WINE and for Win32codecs.  The OP. states this is a trojan not a virus.

Can you please explain what you did with what program.  Please post the link you downloaded from. Did you use the Windows firefox or the Linux one?
i used the firefox that is default installed in my ubuntu 810..

---

### Post by adult swim on 2009-01-01
> **delever said:**
> you seem to be good with web resources, here is the link:

[http://www.winehq.org/](http://www.winehq.org/)

wine is in repositories (add/remove)
:)

---

### Post by jrusso2 on 2009-01-01
Where is the link where you downloaded this item?

---

### Post by Delever on 2009-01-01
> **adult swim said:**
> :)

Please don't laugh, there is a proof: [http://ubuntuforums.org/showthread.php?t=1027170](http://ubuntuforums.org/showthread.php?t=1027170)

---

### Post by kimikrishna on 2009-01-01
> **Delever said:**
> Please don't laugh, there is a proof: [http://ubuntuforums.org/showthread.php?t=1027170](http://ubuntuforums.org/showthread.php?t=1027170)
@ delever..

why did you give the link of another topic created by me related to pritner problem ???

:O :-O :O

---

### Post by kimikrishna on 2009-01-01
> **jrusso2 said:**
> Where is the link where you downloaded this item?
what ??

do you mean "iamfamousdll" 

i didnt dwld it...

---

### Post by jrusso2 on 2009-01-01
I don't see how this has anything to do with what you posted its about a printer driver?

---

### Post by k3lt01 on 2009-01-01
If you read it all properly you will see he posted that link in response to a laughing smiley after he said you were good with web resources. He was giving proof to back up his statement. It should be taken as a complement.

---

### Post by handydan918 on 2009-01-01
> **jrusso2 said:**
> There are .dll's in Linux in both WINE and for Win32codecs. Yes, of course, you are correct. I meant to imply that a .dll/.exe coded for windows would not "prosper" on a unix system due to the vast difference in environment, and the permissions model.>  The OP. states this is a trojan not a virus.


> **kimikrishna said:**
> 
i now worry that whether my firefox got infected with iamfamous.dll trojan virus...

Two! Two! Two threats in one! It's a trojan, AND a virus! 
Big deal. it still won't work.

I kinda miss being able to b0rk my system by visiting the wrong site or clicking the wrong link....


not.

---

### Post by handydan918 on 2009-01-01
> **kimikrishna said:**
> what ??

do you mean "iamfamousdll" 

i didnt dwld it...

Then relax. If you didn't down load it, it isn't on your system. If it IS on your system, it is EXTREMELY unlikely to be capable of damaging your system or compromising your security.
I understand how you feel.  M first couple of years with linux were less enjoyable than they could have been, just because of the paranoia. once I got around to building a test box to try to infect, I relaxed a little. After months of exposing that old POS box to the worst the web has to offer, I suffered absolutely no compromises.
Now, if you can describe in detail what FF is doing that seems different, maybe someone can help you out.

---

### Post by ubudog on 2009-01-01
If you want to install WINE open a terminal and type: "sudo apt-get install wine".

---

### Post by kimikrishna on 2009-01-01
> "There is not enough room on the disk to save /tmp/b2EWA2PY.bin.part.

Remove unnecessary files from the disk and try again, or try saving in a different location. "

I get this whenever i click a download link.


and firefox crashes/////

now all my bookmarks are erased  ????????????


why is this happening ????

---

### Post by handydan918 on 2009-01-01
> **ubudog said:**
> If you want to install WINE open a terminal and type: "sudo apt-get install wine".

Yeah! Then you CAN worry about windows viruses! Yay!


:P

---

### Post by kimikrishna on 2009-01-01
i also get the same type of error mesasge when i open a office app.

---

### Post by HotShotDJ on 2009-01-01
> **bumanie said:**
> Strangely enough, I had to remove and reinstall firefox recently due to 'strange' behaviour - I had been playing around with some settings so it was probably that rather than any sinister spyware/virus. If you want to remove firefox and reinstall it, post back, it is very simple.Whether virus, malicious java script, or messing up your settings, removing firefox and then reinstalling it should not be necessary.  These things almost never (actually, pretty much NEVER) effect the entire system, just the user's account.  Backup your bookmarks (Bookmarks --> Organize Bookmarks --> Import and Backup), close all instances of Firefox, then delete your ~/.mozilla directory.  Start firefox, and you will be restored to its default settings.  Then just restore the bookmarks and reinstall any add-ons, extensions, plugins, etc.

---

### Post by handydan918 on 2009-01-01
> **kimikrishna said:**
> I get this whenever i click a download link.


and firefox crashes/////

now all my bookmarks are erased  ????????????


why is this happening ????

Sounds like your partition is full. Post the output of ```
df -h
```

---

### Post by stderr on 2009-01-01
Might be worth checking how much free space is on your /tmp folder/partition. If you created a partition for /tmp, you can see by doing:

```
df -h | grep /tmp
```

If not, just use

```
df -h
```

and look for / 


With regard to viruses, yep as everyone else has said, they're not to be concerned about on Linux. Even Windows viruses under Wine really struggle. I read an article once which tried to get a whole host of Windows viruses working under Wine. I recall the article's author having very little success at all ;) So even under Wine I don't tend to concern myself too much.

---

### Post by kimikrishna on 2009-01-01
> **handydan918 said:**
> Yeah! Then you CAN worry about windows viruses! Yay!


:P
ok.....

but all my bookmarks are gone

---

### Post by kimikrishna on 2009-01-01
> **handydan918 said:**
> Sounds like your partition is full. Post the output of ```
df -h
```
> Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      3.5G  3.4G     0 100% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  212K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  497M   1% /dev
tmpfs                 500M  264K  500M   1% /dev/shm
/dev/sda1              20G   19G  1.4G  93% /host
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-7-generic/volatile
overflow              1.0M   80K  944K   8% /tmp
/dev/sda6              20G   13G  6.9G  66% /media/Krishna
/dev/sda5              20G   19G  1.4G  93% /media/Archana
/dev/sda7              16G   15G  1.7G  90% /media/New Volume



I got this.....

---

### Post by jerome1232 on 2009-01-01
So it looks like you installed using wubi and only gave the root partition 3.4 GB's which is barely enough room for the system, the drive filled up and caused firefox to start acting strangely.

You need to expand your wubi disk.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by kimikrishna on 2009-01-01
> **jerome1232 said:**
> So it looks like you installed using wubi and only gave the root partition 3.4 GB's which is barely enough room for the system, the drive filled up and caused firefox to start acting strangely.

You need to expand your wubi disk.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)
yes .. i am in WUBI..

but i cannot download any file.........

when i click a dwld link.. FF crashes

---

### Post by jerome1232 on 2009-01-01
That's because your virtual wubi disk is full, you will need to delete some files and clear up some space. 


These commands may get you a few hundred megabytes

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by emshains on 2009-01-01
> **k3lt01 said:**
> This is the only way a dll can infect your Linux pc. Using a program like WINE or virtualising Windows within Linux may cause a problem but your fine if they aren't installed.

BS! A dll is much like a .so, a library. And check linux.com and search for ```
wine virus
```

---

### Post by stderr on 2009-01-01
> **kimikrishna said:**
> /host/ubuntu/disks/root.disk 3.5G 3.4G 0 100% /

100% utilised root partition. I just posted this for someone else; it may help if you're confused over what the root partition is, or how it can be full if you've got other entries which don't show as being full.

[http://ubuntuforums.org/showpost.php?p=6477408&postcount=5]("http://ubuntuforums.org/showpost.php?p=6477408&postcount=5")

You need to expand the disk, as jerome says. You may be able to get around it for a little while by doing things like

```
sudo apt-get autoclean
```

but 3.4Gs just won't be sufficient anyway - you need to expand it.

---

### Post by kimikrishna on 2009-01-01
> 
gokulakrishna@ubuntu:~$ sudo apt-get clean
[sudo] password for gokulakrishna: 
Gokulakrishna@ubuntu:~$ sudo apt-get autoremove
reading package lists... Done
building dependency tree       
reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 201 not upgraded.
Gokulakrishna@ubuntu:~$ 


i got this ...

---

### Post by mangcool on 2009-01-01
> **kimikrishna said:**
> oh ! thankyou..

my firefox automatically opened a site named indian.adultfriendfider...

i didnot choose that link in any way..... :O

thats the reason i feared...


btw can anyone tell me how to install WINE ?? and what is wine ??
WINE is a software or application on Ubuntu, you can use it to run Windows' .exe or .dll files. It can be useful if you want to play Windows' games on Ubuntu.

As long as you don't use WINE to run Firefox, you're good. Because if you use WINE to run Firefox, it'll run the .dll files too which can harm your Linux PC, if the .dll file is infected with virus.

---

### Post by handydan918 on 2009-01-01
> **kimikrishna said:**
> yes .. i am in WUBI..

but i cannot download any file.........

when i click a dwld link.. FF crashes

you don't seem to be paying attention. Let me spell it out for you. Your root directory is full. There is nowhere for the  system to write information to. No application can be counted on to work correctly with a full root partition. You MUST free some space up in order to solve your issue.

---

### Post by kimikrishna on 2009-01-01
> **handydan918 said:**
> you don't seem to be paying attention. Let me spell it out for you. Your root directory is full. There is nowhere for the  system to write information to. No application can be counted on to work correctly with a full root partition. You MUST free some space up in order to solve your issue.
how do i free space ??

tell me that.. 

I do not know.. + i am just a little user..

---

### Post by jerome1232 on 2009-01-01
Once you get enough space free you will need to install lvpm and resize root (In case  you missed my first links)

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

> Resizing virtual disks using LVPM (not necessary if you're transferring the install to a dedicated partition)

Run LVPM, and once the menu appears, select either "resizehome" (to resize the /home virtual disk) or "resizeroot" (to resize the / virtual disk).

Input the new size, in MB, of the virtual disk.

Wait until the program finishes creating a new disks file and copying files from original home disk file; it will pop up a final instruction window instructing to backup the original home disk file and renaming the newly created disk file

Boot into windows and navigate to c:\wubi\disks, move the old virtual disk to a different folder as backup, and rename new.virtual.disk to home.virtual.disk (if you used resizehome) or system.virtual.disk (if you used resizeroot)

Reboot into ubuntu

---

### Post by k3lt01 on 2009-01-02
> **emshains said:**
> BS! A dll is much like a .so, a library. And check linux.com and search for ```
wine virus
```A .dll may be just like a .so library but it isn't a .so library is it? So instead of BSing only me how about you argue your mute point with everyone else who said a .dll virus cant hurt Ubuntu unless WINE is installed.

As for WINE and Windows Virus' [take a look at this]("http://www.winehq.org/pipermail/wine-devel/2008-March/063434.html")

---

### Post by kimikrishna on 2009-01-03
is it possible to clear space by uninstalling some less used app ??? 

if yes , how do i uninstall using termnal ???

---

### Post by Paqman on 2009-01-03
> **kimikrishna said:**
> is it possible to clear space by uninstalling some less used app ??? 

if yes , how do i uninstall using termnal ???

You can uninstall any app from the terminal by:
```
sudo apt-get remove *packagename*
```

You may also want to reboot. That will clear out any junk you've got in /tmp and might give you enough space to get LVPM installed and resize your root.

Some of the other obvious stuff you can do is dump your browser cache and look for any data files that you can get rid of.

---

### Post by jerome1232 on 2009-01-03
----edit---- beaten to it. 

The only difference between our commands is mine removes the config files out, you may actually want to not use my --purge option so you can reinstall any apps you remove and still retain their settings.

Yes you should be able to clear up some more space that way.

via terminal it's ```
sudo apt-get remove --purge packagename
```

Replace packagename with the name of the actual package.

---

### Post by kimikrishna on 2009-01-03
@ jerome..

The lvpm that you gave did not move a bit..

I left it to resize for two hours .. and the bar did not move a pixel :x 

x-(

:confused::confused::confused:

---

