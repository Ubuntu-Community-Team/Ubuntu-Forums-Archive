---
title: "new user -----&gt; problems"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by pink_bullets.PL on 2009-08-30
hey everyone. im new to ubuntu and i got so much problems with it. 
all hardware works fine but i cant install any software. 
i also have problems with running videos on websites. i assume its codec's issue but still i have no idea how to install them. 
i would really appreciate help.

---

### Post by halitech on 2009-08-30
couple of ways to install software

1. Add/remove programs
2. Synaptic package manager
3. in the terminal: sudo apt-get install <packagename>

for codecs, you need the multiverse and universe enabled then install ubuntu-restricted-extras

---

### Post by NoaHall on 2009-08-30
Google "flash player" and download and install the flash player from the official website.

To install something from a website, if it's a .deb, all you have to do is double click. To install something from the built in list, use Add/Remove located in the top left hand corner menu.

---

### Post by pink_bullets.PL on 2009-08-30
ok. i have been playing with:
1. Add/remove programs
2. Synaptic package manager
3. in the terminal: sudo apt-get install <packagename>
  but nothing was working. so idk. when i was using terminal there were errors coming out.



same stuff with flash player. i downloaded it but i cant install it cuz errors are appearing. 
maybe i shoulda write some commands in order to properly install new programs. huh?

---

### Post by NoaHall on 2009-08-30
Use "sudo apt-get update" and post the output on here.

---

### Post by roger_1960 on 2009-08-30
> **pink_bullets.PL said:**
> hey everyone. im new to ubuntu and i got so much problems with it. 
all hardware works fine but i cant install any software. 
i also have problems with running videos on websites. i assume its codec's issue but still i have no idea how to install them. 
i would really appreciate help.

Hi

Normally the GUI way is to go to "add/remove" on the main menu, select what you want and install from there.

Alternatively, use system>administration>synaptic package manager and  chose the package you want to install from there.

Probably for videos you are missing a flash codec.  Install a flash plugin from the firefox tools>add-ons>plugins menu

---

### Post by pink_bullets.PL on 2009-08-30
> **NoaHall said:**
> Use "sudo apt-get update" and post the output on here.

this is what came out

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US     
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 198B in 0s (206B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

---

### Post by zerhacke on 2009-08-30
sudo apt-get install ubuntu-restricted-extras will give you a working flash install.

---

### Post by NoaHall on 2009-08-30
You need to download and install the medibuntu gpg key. It will tell you how on the website.

---

### Post by halitech on 2009-08-30
open a terminal and run this
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by pink_bullets.PL on 2009-08-30
> **zerhacke said:**
> sudo apt-get install ubuntu-restricted-extras will give you a working flash install.


videos still doesnt work. its like buffering but nothing will play.

---

### Post by pink_bullets.PL on 2009-08-30
im kinda getting how to install programs but i still need help with videos.
if someone will solve my problem i will really appreciate

nothing really works so far ;/

---

### Post by finito on 2009-08-30
Have your tried restarting your rig.

---

### Post by oldos2er on 2009-08-30
Which version of Ubuntu are you running? You shouldn't mix repos for different Ubuntu releases (Hardy and Intrepid), as it can cause no end of problems.

---

### Post by pink_bullets.PL on 2009-08-30
> **oldos2er said:**
> Which version of Ubuntu are you running? You shouldn't mix repos for different Ubuntu releases (Hardy and Intrepid), as it can cause no end of problems.


Ubuntu 8.10 i think hardy.


> **finito said:**
> Have your tried restarting your rig. 	
i did

---

### Post by oldos2er on 2009-08-30
> **pink_bullets.PL said:**
> Ubuntu 8.10 i think hardy.


 Then you need to go into System, Administration, Software Sources, and disable Intrepid, enable Hardy. To double-check which version of Ubuntu you're running, run **lsb_release -a** in a terminal.

 Edit: Since the OP is running Hardy, disregard the above advice.

 Update: You can manually edit your sources.list with the command **gksu gedit /etc/apt/sources.list**. Either remove the lines referring to Hardy, or comment them out by adding a # in front of the line. Close the file, and run **sudo apt-get update**.

---

### Post by pink_bullets.PL on 2009-08-30
all right. so i checked my version and it says interpid.

but when i clicked on "Third-Party Software" in software sorces, the only thing checked is Medibuntu - Ubuntu 8.04 LTS "hardy heron".

is it a problem???

---

### Post by pink_bullets.PL on 2009-08-30
help!

---

### Post by halitech on 2009-08-30
you need to follow the steps here for 8.10

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by pink_bullets.PL on 2009-08-30
nothing works. im trying everything but for me its really hard. i got w32codecs and nothing changed.

---

### Post by halitech on 2009-08-30
what exactly are you trying to play? downloaded avi and mpeg files or websites like youtube?

---

### Post by pink_bullets.PL on 2009-08-30
websites like youtube. all videos and audio on my HD play without problem. 
its only playing videos on websites. even mp3 files from websites won't play.

---

### Post by halitech on 2009-08-30
have you installed flash and java? what video card do you have and what type of internet connection?

---

### Post by pink_bullets.PL on 2009-08-30
i have java and flash. 
im getting my internet through wireless. 
and my video card is intel graphics media acceleration 950.
seriously everything works fine except videos and audio on the websites

---

### Post by pedro3005 on 2009-08-30
Have you installed ubuntu-restricted-extras?

---

### Post by halitech on 2009-08-30
do you use compiz? if you do, try turning it off

---

### Post by Merk42 on 2009-08-30
Also so it doesn't get lost, the user has 8.10 (why not the latest 9.04 or the LTS 8.04 who knows) but also has 8.04 repositories, so I suspect that alone may be causing problems.

---

### Post by halitech on 2009-08-30
dang, missed that all together.

Pink, can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by AxelFlames on 2009-08-30
ok i have a Apple wireless router at home but its not recognised by Ubuntu for some strange reason,

i can connect tto it fiine though Vista but i don like usin it for some obvious reasons....

it has wep personal
i got the pw and all the info to get in,
it just doesnt register to my acer notebook

i tried doing the hidden wireless network thingy and entering info but it still didnt work or pop up.

i am verry new to ubuntu, barely know how to do anything beyond click, drag, and type.
can i have some step by step 'understandable' help please?

---

### Post by halitech on 2009-08-30
> **AxelFlames said:**
> ok i have a Apple wireless router at home but its not recognised by Ubuntu for some strange reason,

i can connect tto it fiine though Vista but i don like usin it for some obvious reasons....

it has wep personal
i got the pw and all the info to get in,
it just doesnt register to my acer notebook

i tried doing the hidden wireless network thingy and entering info but it still didnt work or pop up.

i am verry new to ubuntu, barely know how to do anything beyond click, drag, and type.
can i have some step by step 'understandable' help please?

could you please start a new thread as your issue is totally unrelated to the OP's and it is not polite to hijack a thread

---

### Post by AxelFlames on 2009-08-30
> **halitech said:**
> could you please start a new thread as your issue is totally unrelated to the OP's and it is not polite to hijack a thread

sorry- i thought i clicked on new thread :(

i thought i did...:confused:
sorry for da trouble- makin thread nao

---

### Post by pink_bullets.PL on 2009-08-30
> **halitech said:**
> do you use compiz? if you do, try turning it off


its not it. i turned it off and nothing changed.




and the output of     
cat /etc/apt/sources.list

 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by halitech on 2009-08-30
I'm only seeing Interpis stuff in there now. still in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
``` and post the results

---

### Post by pink_bullets.PL on 2009-08-30
> **halitech said:**
> I'm only seeing Interpis stuff in there now. still in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
``` and post the results



Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages [3518B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 15.4kB in 0s (15.9kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by halitech on 2009-08-30
did you have synaptic open while trying the above command?

---

### Post by pink_bullets.PL on 2009-08-30
now i made sure its off and something different came out

> Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-calc: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
                       Depends: openoffice.org-base-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-draw: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
                         Depends: openoffice.org-base-core (= 1:3.1.0-5ubuntu1~intrepid1) but 1:2.4.1-11ubuntu2.1 is installed
E: Unmet dependencies. Try using -f.


---

### Post by cranecreek on 2009-08-31
I'm guessing your looking at installing 3rd party software, use wget:

go to the site you want to download from, get the link and then use the terminal to download it ie:

wget javascript:earth.downloadEarth();

you'll be looking for file extendtions like tar.gz, bz bz2 and rpm

You can also use apt to find what you need

Good luck

---

### Post by halitech on 2009-08-31
in the terminal run
```
sudo apt-get -f install
```
this should take care of any dependencies. It looks like you tried to install OpenOffice 3 over 2.4

---

### Post by pink_bullets.PL on 2009-08-31
hehe thx. now i have open office 3.0 :)

but still videos on websites wont play

---

### Post by pedro3005 on 2009-08-31
Run:
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by halitech on 2009-08-31
> **pedro3005 said:**
> Run:
```

sudo apt-get install ubuntu-restricted-extras

```

has already been installed

OP - try
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by pink_bullets.PL on 2009-08-31
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by pink_bullets.PL on 2009-08-31
up

---

### Post by pink_bullets.PL on 2009-09-01
is there anyone who can help???

---

### Post by NoaHall on 2009-09-01
Uninstall the flash you have, and install the one from the official website.

---

### Post by pink_bullets.PL on 2009-09-04
flash is installed from a good site


i even followed steps from this site and nothing.
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

---

### Post by pink_bullets.PL on 2009-09-05
okay problem solved. 


this code helped  and i found it here [http://ubuntuforums.org/showthread.php?t=1196599](http://ubuntuforums.org/showthread.php?t=1196599)
```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree
```

---

