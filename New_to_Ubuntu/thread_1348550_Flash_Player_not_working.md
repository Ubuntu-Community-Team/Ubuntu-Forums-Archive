---
title: "Flash Player not working"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by elaine81 on 2009-12-07
Hi all , 

 just today i posted a question on my wireless in Ubuntu  , it was solved earlier just now at ard 11pm+ , now i got another problem ,  since my wireless is up  , i went to youtube.com , wanted to  watch the video , but forgotten  to install flashplayer , so i went to [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")

[LEFT]_[to ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")[download the flash player. I found some info from other website to open the file with "GDebi Package Installer. But still it prompt me this error msg "]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")_Dependency is not satisfiable: libnspr4-dev." Pls help , thanks!!!:D:D:D
[/LEFT]

---

### Post by philinux on 2009-12-07
> **elaine81 said:**
> Hi all , 

 just today i posted a question on my wireless in Ubuntu  , it was solved earlier just now at ard 11pm+ , now i got another problem ,  since my wireless is up  , i went to youtube.com , wanted to  watch the video , but forgotten  to install flashplayer , so i went to [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")

[LEFT]_[to ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")[download the flash player. I found some info from other website to open the file with "GDebi Package Installer. But still it prompt me this error msg "]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")_Dependency is not satisfiable: libnspr4-dev." Pls help , thanks!!!:D:D:D
[/LEFT]

If this is a 32 bit install then install flash from synaptic. flashplugin-nonfree

Or in firefox's address bar type this.

apt:flashplugin-nonfree

This will download the plugin from adobe that matches your installed version of ubuntu.

---

### Post by elaine81 on 2009-12-07
> **philinux said:**
> If this is a 32 bit install then install flash from synaptic. flashplugin-nonfree

Or in firefox's address bar type this.

apt:flashplugin-nonfree

This will download the plugin from adobe that matches your installed version of ubuntu.


I hv tried to key as wat u said in firefox add box , but was prompt " package not found". Was thinking of  installing thru terminal command  , but it prompt me to key password , and no matter how , i can keep anything , after it prompt me for password , thanks .

---

### Post by podgag on 2009-12-07
I have the same trouble...
I not so many time ago install Ubuntu 9.10 64-bit.
Then I've install flash player.
:cry:
"Could not open install_flash_player_10_linux.deb
The package might be corrupted or you are not allowed to open the file. Check the permissions."

---

### Post by philinux on 2009-12-07
> **elaine81 said:**
> I hv tried to key as wat u said in firefox add box , but was prompt " package not found". Was thinking of  installing thru terminal command  , but it prompt me to key password , and no matter how , i can keep anything , after it prompt me for password , thanks .

Ok. open a terminal. Apps>accessories>Terminal.

Copy and paste the following and post back the results.

```
cat /etc/apt/sources.list
```

---

### Post by sandyd on 2009-12-07
> **elaine81 said:**
> Hi all , 

 just today i posted a question on my wireless in Ubuntu  , it was solved earlier just now at ard 11pm+ , now i got another problem ,  since my wireless is up  , i went to youtube.com , wanted to  watch the video , but forgotten  to install flashplayer , so i went to [http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")

[LEFT]_[to ]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")[download the flash player. I found some info from other website to open the file with "GDebi Package Installer. But still it prompt me this error msg "]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")_Dependency is not satisfiable: libnspr4-dev." Pls help , thanks!!!:D:D:D
[/LEFT]

see link in my signatire (below)

---

### Post by sandyd on 2009-12-07
p.s. only do the install part. if you dont want a beta version of flash, use the nspluginwrapper method.

---

### Post by philinux on 2009-12-07
> **carlee said:**
> p.s. only do the install part. if you dont want a beta version of flash, use the nspluginwrapper method.

We aint sure if it's 32 0r 64 bit yet. :p

---

### Post by elaine81 on 2009-12-08
> **philinux said:**
> Ok. open a terminal. Apps>accessories>Terminal.

Copy and paste the following and post back the results.

```
cat /etc/apt/sources.list
```


Result come back as:

 No such File or Directory 


 Pls assist thanks

---

### Post by philinux on 2009-12-08
Are you sure you copied and pasted that command into a terminal.

It works fine here and shows my software sources.

---

### Post by elaine81 on 2009-12-09
> **philinux said:**
> Are you sure you copied and pasted that command into a terminal.

It works fine here and shows my software sources.


**opps.. so sorry i made a mistake by typing out , here is the result:**


elaine@elaine-laptop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
elaine@elaine-laptop:~$ ping 69.63.181.15
elaine@elaine-laptop:~$ 
elaine@elaine-laptop:~$ 

**Thanks , pls assist..**:D:D

---

### Post by wojox on 2009-12-09
Install ubuntu-restricted extras:

```
sudo apt-get install ubuntu-restricted-extras
```

You will get Flash and a bunch of plugins for your programs.

---

### Post by elaine81 on 2009-12-09
[B]Hi , thanks for ur prompt reply , 
Here is the result i get back:
[/B]


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras

---

### Post by wojox on 2009-12-09
What about:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by elaine81 on 2009-12-09
> **wojox said:**
> What about:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```



Yes!!!! It works !!! thanks for the help.... so grateful to u!!! Thanks!!!:D:D:D:D

---

### Post by jwvraets on 2009-12-09
The above solution only works once. Restart Firefox and I am back to the same old problem: No controls. This is the case if you have Compiz desktop effects running ant any level.

However, if you turn off all desktop effects, the controls work reliably. Seems there is a problem/conflict between Compiz and the flash player controls. Apparently you can either have working controls or desktop effects, just not both at the same time, sadly!

As for other solutions, I have tried a raft and have had no success. Would love to find  one that works in all cases.

---

### Post by philinux on 2009-12-09
> **jwvraets said:**
> However, if you turn off all desktop effects, the controls work reliably. Seems there is a problem/conflict between Compiz and the flash player controls. Apparently you can either have working controls or desktop effects, just not both at the same time, sadly!


I have both working fine. But then again I'm using an nVidia graphics card. 8600gt.

It most likely to be the source of your problem, i.e. driver related. What is your graphics card?

---

### Post by Zimrie on 2009-12-09
for adobe flash player

system/administration/software sources
in other software check all boxes

then open any page with flash, and install with missing plugin

---

### Post by jwvraets on 2009-12-09
[philinux]("http://ubuntuforums.org/member.php?u=353083") The video is provided by the onboard ATI Radeon 4200 on a Gigabyte GA785GMT-UD2H mobo (with 8 gig RAM, 500 meg dedicated to video). Drivers are latest of AMD/ATI support site. So, if it is a driver issue I am not sure what my options would be. I do know turning off the effects gives me working Flash controls. Not my preferred solution, but one I can live with if I have to. Appreciate the suggestion though.

JW

---

### Post by sandyd on 2009-12-09
nbm.

---

### Post by BLXX on 2009-12-09
Phil, thanks a lot!  This worked for me.  I'm new to Linux and I was losing my mind over this.  Thanks again!:KS

---

### Post by chambersc on 2009-12-25
Hey, I'm running into a problem with Google Chrome where it's not displaying Flash movies correctly.

Attached is a snapshot of the error that I'm running into.

---

### Post by twitchy2u on 2009-12-26
if you have 64 amd and firefox all you need is vlc and go in to preferences in firefox find flash stuff change it to vlc instead by clicking it and going in to /user/bin/vlc and there you got flash

---

