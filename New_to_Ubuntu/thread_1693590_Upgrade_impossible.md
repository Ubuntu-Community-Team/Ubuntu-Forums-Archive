---
title: "Upgrade impossible"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by MibunoOokami on 2011-02-23
Hey all. I'm not exactly new to using Ubuntu but just cant for the life of me upgrade to 10.04 or higher from 9.10. There used to be a prompt in update manager but at that time I was unable to upgrade due to internet usage restrictions. I have tried adjusting the settings in the update manager and even tried using the commands ```
sudo apt-get upgrade
``` and ```
sudo aptitude upgrade
``` but to no avail.
Can anyone help me out here is there something else I should be doing. I have tried googling for help before signing up but the few posts I found on the subject said to adjust the settings in the update manager which as I said I already had tried.

---

### Post by tajiknomi on 2011-02-23
I think you are using 9.10, Follow the **Screenshot**, If you select the LTS Option , you will be prompt that "[SIZE=2]their is an another Version Available(10.04), you want to upgrade..??[/SIZE]. In the **2nd Screenshot** you will see at the top of your update manager an Upgrade option.

But my personal Opinion is to Install Fresh 10.04(LTS) OR 10.10(Normal release), Because Sometimes Upgrade Cause Issue, so better idea will be to download Either 10.04 OR 10.10 & Replace 9.10....

Edit:-```
apt-get upgrade
```

This Command doesn't upgrade your Distro, it just Upgrade your Repositories.

---

### Post by MibunoOokami on 2011-02-23
> **tajiknomi said:**
> I think you are using 9.10, Follow the **Screenshot**, If you select the LTS Option , you will be prompt that "[SIZE=2]their is an another Version Available(10.04), you want to upgrade..??[/SIZE]. In the **2nd Screenshot** you will see at the top of your update manager an Upgrade option.

But my personal Opinion is to Install Fresh 10.04(LTS) OR 10.10(Normal release), Because Sometimes Upgrade Cause Issue, so better idea will be to download Either 10.04 OR 10.10 & Replace 9.10....

Edit:-```
apt-get upgrade
```This Command doesn't upgrade your Distro, it just Upgrade your Repositories.

Thanks for the reply I am using 9.10 and have done exactly what you said previously but the upgrade button just wont reappear. I've read somewhere that doing a fresh install could erase all my files and I have no available space to backup the hdd. I guess if this is my only choice though I will need to buy another hd so I can back stuff up.

edit> Perhaps my settings in my screenshot have something to do with it. I noticed in yours that the pre-released updates box is unchecked and the unsupported one is checked whereas its the opposite in mine.

---

### Post by tajiknomi on 2011-02-23
Press ALT+F2 it will show you a manager,

paste this command their and Select **RUN** button, and see if it shows you then...

```
update-manager -d
```

---

### Post by MibunoOokami on 2011-02-23
OK it installed 15 backports. But still didn't popup with upgrade button

---

### Post by MibunoOokami on 2011-02-23
> **tajiknomi said:**
> Press ALT+F2 it will show you a manager,

paste this command their and Select **RUN** button, and see if it shows you then...

```
update-manager -d
```

No go seems a bit odd I think, even after matching my settings to yours.

---

### Post by tajiknomi on 2011-02-23
> **MibunoOokami said:**
> No go seems a bit odd I think, even after matching my settings to yours.

See these Solutions in the similar thread > [http://ubuntuforums.org/showthread.php?t=1144658&page=2](http://ubuntuforums.org/showthread.php?t=1144658&page=2)

---

### Post by MibunoOokami on 2011-02-23
> **tajiknomi said:**
> See these Solutions in the similar thread > [http://ubuntuforums.org/showthread.php?t=1144658&page=2](http://ubuntuforums.org/showthread.php?t=1144658&page=2)

I did the sudo dist-upgrade thing and got a message "E: couldn't find package dist-upgrade" went to do the server upgrade as mentioned in post #5 of that thread tried to install the manager core and got a message "update-manager-core is already the newest version" Does any of that help? I have refreshed dozens of times as others said they did but the button still won't appear. Seems I may have no choice but to do a fresh install. Thanks for your assistance so far.

---

### Post by alphacrucis2 on 2011-02-23
Just edit your /etc/apt/sources.list file (using gksudo gedit) changing all occurences of karmic to lucid. Comment out any PPA's in the file and save. Then:

sudo apt-get update
sudo apt-get upgrade

Don't try going direct from karmic (9.10) to maverick (10.10) as that will very likely fail. You would have to complete the upgrade to lucid (10.04) first.

---

### Post by tajiknomi on 2011-02-23
> **MibunoOokami said:**
> I did the sudo dist-upgrade thing and got a message "E: couldn't find package dist-upgrade" went to do the server upgrade as mentioned in post #5 of that thread tried to install the manager core and got a message "update-manager-core is already the newest version" Does any of that help? I have refreshed dozens of times as others said they did but the button still won't appear. Seems I may have no choice but to do a fresh install. Thanks for your assistance so far.

+1 for Alphacrusis2. Try that what he has mentioned.

Fresh install is quite better as Compared to Upgrade, Because many issues Arise when one Upgrade his OS(as far as i have seen).


Good Luck

---

### Post by MibunoOokami on 2011-02-23
> **alphacrucis2 said:**
> Just edit your /etc/apt/sources.list file (using gksudo gedit) changing all occurences of karmic to lucid. Comment out any PPA's in the file and save. Then:

sudo apt-get update
sudo apt-get upgrade

Don't try going direct from karmic (9.10) to maverick (10.10) as that will very likely fail. You would have to complete the upgrade to lucid (10.04) first.

I've never had to do anything like this before and am unsure how to proceed. I can't seem to find  /etc/apt/sources.list I am feeling a little new now lol

---

### Post by tajiknomi on 2011-02-23
> **MibunoOokami said:**
> I've never had to do anything like this before and am unsure how to proceed. I can't seem to find  /etc/apt/sources.list I am feeling a little new now lol

Try  this Command and that will let you edit the file:-

```
gksu gedit /etc/apt/sources.list
```

---

### Post by MibunoOokami on 2011-02-23
> **tajiknomi said:**
> Try  this Command and that will let you edit the file:-

```
gksu gedit /etc/apt/sources.list
```

Excellent I have managed to open that file and have changed ll karmic to lucid but before saving I thought I should mention that jaunty appears a few times in that file so want to double check that is OK. Another thing maybe I should have mentioned earlier is that my processor is 64-bit does that make any difference?

Thanks

---

### Post by alphacrucis2 on 2011-02-23
> **MibunoOokami said:**
> Excellent I have managed to open that file and have changed ll karmic to lucid but before saving I thought I should mention that jaunty appears a few times in that file so want to double check that is OK. Another thing maybe I should have mentioned earlier is that my processor is 64-bit does that make any difference?

Thanks

You shouldn't normally have mixed sources (jaunty and karmic) although are you sure the lines that say jaunty aren't commented out - ie the line starts with a # symbol. Don't worry about 32 versus 64 bit. Apt will bring in the correct packages for your install.

Just a thought. Paste your sources.list file here for us to have a look first if you are unsure.

---

### Post by MibunoOokami on 2011-02-23
> **alphacrucis2 said:**
> You shouldn't normally have mixed sources (jaunty and karmic) although are you sure the lines that say jaunty aren't commented out - ie the line starts with a # symbol.

They are commented out except for one that says "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse" can paste the entire thing if need be

---

### Post by alphacrucis2 on 2011-02-23
> **MibunoOokami said:**
> They are commented out except for one that says "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse" can paste the entire thing if need be

is there also a line that says "....karmic multiverse"? (or "....lucid multiverse"after you have edited it). If so then comment out the jaunty line (ie type a # at the beginning of the line). If there was no karmic multiverse line then I would just change the jaunty line to read "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse"

Hope that makes sense. Multiverse contains packages that aren't officially supported by Ubuntu. I have no idea why your sources are specifying jaunty rather than karmic for the multiverse repo. That could end up causing dependency problems.

---

### Post by MibunoOokami on 2011-02-23
> **alphacrucis2 said:**
> is there also a line that says "....karmic multiverse"? (or "....lucid multiverse"after you have edited it). If so then comment out the jaunty line (ie type a # at the beginning of the line). If there was no karmic multiverse line then I would just change the jaunty line to read "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse"

Yes there is so just commented jaunty out and doing sudo apt-get update now. Seems to be working, will post again after apt-get upgrade.

---

### Post by MibunoOokami on 2011-02-23
That took an extremely long time. I got a notice saying a restart is required and as it started restarting I noticed an error message which said something about dependencies may not work properly. After the restart it's like my keyboard won't work, I cannot login to Ubuntu so I am now assuming I will need to do a fresh install luckily I have another machine with windows that I can use to download an install ISO. I assume with a fresh install I can go straight to the latest 10.10 version skipping 10.04

---

### Post by alphacrucis2 on 2011-02-23
> **MibunoOokami said:**
> That took an extremely long time. I got a notice saying a restart is required and as it started restarting I noticed an error message which said something about dependencies may not work properly. After the restart it's like my keyboard won't work, I cannot login to Ubuntu so I am now assuming I will need to do a fresh install luckily I have another machine with windows that I can use to download an install ISO. I assume with a fresh install I can go straight to the latest 10.10 version skipping 10.04

Sorry it didn't work out. I have upgraded that way successfully a number of times. Yes you can go straight to 10.10 for a fresh install. If you had set up /home as a separate partition then that makes the process non destructive for your data. Otherwise I recommend booting off a live CD and backing up any data you need before proceeding. Before that it might still be possible to recover. Can you boot into recovery mode?

---

### Post by MibunoOokami on 2011-02-23
> **alphacrucis2 said:**
> Sorry it didn't work out. I have upgraded that way successfully a number of times. Yes you can go straight to 10.10 for a fresh install. If you had set up /home as a separate partition then that makes the process non destructive for your data. Otherwise I recommend booting off a live CD and backing up any data you need before proceeding. Before that it might still be possible to recover. Can you boot into recovery mode?

That's alright mate, I appreciate yours and everyone else' help. I may have done something wrong when changing that file I haven't tried getting into recovery mode will try now

---

### Post by MibunoOokami on 2011-02-23
Just tried recovery mode came up with a message of sorts saying "apparmor profile failed" a few minutes later a colored screen appeared with options to choose from but before I could do anything the screen started scrolling and when it stopped there were lots of messages saying "illegal request" and "media region mismatched" really doesn't sound good especially if recovery mode won't work

---

### Post by alphacrucis2 on 2011-02-23
> **MibunoOokami said:**
> Just tried recovery mode came up with a message of sorts saying "apparmor profile failed" a few minutes later a colored screen appeared with options to choose from but before I could do anything the screen started scrolling and when it stopped there were lots of messages saying "illegal request" and "media region mismatched" really doesn't sound good especially if recovery mode won't work


Yeah. Looks like it will be too difficult to sort out. Before installing Maverick you will want to do the "TRY" option from the CD before installing to check that it is happy with your hardware.

---

### Post by MibunoOokami on 2011-02-24
I have burnt the ISO and it seems to be working fine however I can't save some files due to permission restrictions is there anyway to remove the permissions and save the files from 9.10?

---

### Post by tqk on 2011-04-20
> **tajiknomi said:**
> I think you are using 9.10, Follow the **Screenshot**, If you select the LTS Option , you will be prompt that "[SIZE=2]their is an another Version Available(10.04), you want to upgrade..??[/SIZE]. In the **2nd Screenshot** you will see at the top of your update manager an Upgrade option.

But my personal Opinion is to Install Fresh 10.04(LTS) OR 10.10(Normal release), Because Sometimes Upgrade Cause Issue, so better idea will be to download Either 10.04 OR 10.10 & Replace 9.10....

Edit:-```
apt-get upgrade
```

This Command doesn't upgrade your Distro, it just Upgrade your Repositories.
Nope, you're wrong. "apt-get update && apt-get upgrade && apt-get dist-upgrade" just took my Karmic 9.10 to Lucid 10.4, and it did it pretty well.  I see tiny, cosmetic things for me to adjust, but most everything just works.

Edit /etc/apt/sources.list in vi then:

:%s/karmic/lucid/g

and exit ("ZZ"), then run that apt-get line above.  You'll have to fit sudo in there; I don't use it.

---

### Post by Bladeforger on 2011-09-24
> **alphacrucis2 said:**
> Just edit your /etc/apt/sources.list file (using gksudo gedit) changing all occurences of karmic to lucid. Comment out any PPA's in the file and save. Then:

sudo apt-get update
sudo apt-get upgrade

Don't try going direct from karmic (9.10) to maverick (10.10) as that will very likely fail. You would have to complete the upgrade to lucid (10.04) first.

This works!  At least it appears to have done so thus far... 

Thanks!!!!

---

### Post by oldos2er on 2011-09-24
Not sure if upgrading the OS in the manner you described is supported. Next time just run ```
update-manager -d
```

---

### Post by MibunoOokami on 2012-08-21
It seems I never updated this thread with an outcome. If I recall correctly, I ended up doing a fresh install. I'm just going through my old threads and marking relevant ones as solved since I've only recently learned how to do that.

---

