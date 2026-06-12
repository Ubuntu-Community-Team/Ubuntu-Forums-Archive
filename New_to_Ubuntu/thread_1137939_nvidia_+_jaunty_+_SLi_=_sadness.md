---
title: "nvidia + jaunty + SLi = sadness"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by hoodaman on 2009-04-26
I'm new to linux and am having an issue. My system is as follows:

4GB RAM
ASUS A8N-SLi Premium
AMD 64 Dual Core Opteron 185
2x BFG nvidia Geforce 9600GT

I freshly install jaunty on it's own partition--cool
Gnome fires up after the reboot--cool
I see that I need to update my graphics drivers. I try to use jockey to pull down the nvidia drivers per it's recommendation. Jockey hangs. I reboot and all I get is a command prompt. Not knowing how to fix this I clean house and start over.

Back to a desktop after another install. This time I make a backup of xorg.conf as I gather all sorts of important stuff about the way the gui works is stored in there.
I read up on envy. sounded foolproof. I downloaded the latest version and tried it. Same thing. I reboot to a command prompt. tried restoring my backed up xorg.conf. Didn't work. Clean house and start again (startx doesn't work, sudo /etc/init.d gdm start works but doesn't ever pull up the x server when I throw startx at it)

I then found a thread [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I followed the instructions in the first post to the T. Reboot. Same problem. GUI never loads. So here I am. Is it the dual graphics cards that's giving me so much grief? And if so, how do I get past this barrier?

Thanks in advance

---

### Post by inobe on 2009-04-26
i have some steps you can try.

i have a 9400gt and it's working great with the 180.51 driver.

did not use "hardware drivers" and certainly didn't install manually !

added this to repository, i used the stable repo

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

add the key, applications> accessories> terminal

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

to add the source go to system> administrator> synaptic> settings> repositories> third party software....

click add and paste

```
deb http://www.avenard.org/files/ubuntu-repos intrepid release
```

close software sources when done and click reload button on synaptic.

close synaptic.

you should then be notified, when this happens' install the upgraded driver and reboot.


every time a new driver is released you will get notified.

a big thanks to the fella that owns and maintains this site.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

if you have any questions feel free to ask.

---

### Post by hoodaman on 2009-04-26
thanks for the quick reply! I'll definitely try this and post back with my results :)

---

### Post by TigerCR1200 on 2009-04-26
Are you getting back to the command prompt or simply to a black screen? I have read and ran into with my 9800GTX+ the need for a bios update to the video card to get 180 to work. It was giving a black screen not the command prompt, I was not able to change to a command prompt either I had to go through the recovery mode to make changes.

---

### Post by inobe on 2009-04-26
noticed you have sli, after you run threw the setup we can troubleshoot from there.

---

### Post by hoodaman on 2009-04-26
I added the keys and the sources but I'm not sure which files I'm supposed to download...

sorry I'm not better versed in this sort of thing. I'm learning though :)

---

### Post by inobe on 2009-04-26
did update manager notify you of updates ?

if not make sure nothing is open besides firefox and go to application> accessories> terminal

type

```
sudo apt-get update
```

then hit enter.

you should then see the update notification, simply install all updates then restart.

---

### Post by hoodaman on 2009-04-26
tis not giving me update notifications...

the command gave me a list of sources which either  say hit or ign next to them.

there are 2 sources listed under avenard. one has hit next to it, one says ign.

---

### Post by inobe on 2009-04-26
okay open synaptic and search **nvidia** then list what is installed for 180.

here's what i have for reference

[B]nvidia-180-libvdpau
nvidia-settings
nvidia-180-kernel-source
nvidia-common
nvidia-180-modealiases
nvidia-glx-180
jockey-common
jockey-gtk[/B]

---

### Post by hoodaman on 2009-04-26
okay when I chose the nvidia glx-180 package it wanted to remove the following things and that doesn't seem right:

ubuntu-desktop
xorg
xserver-xorg-*

*-a crapton of stuff

is that what it's supposed to do?

---

### Post by inobe on 2009-04-26
no it's not suppose to remove ubuntu desktop.

give me a minute

---

### Post by inobe on 2009-04-26
reboot your machine and list what is installed for 180 !

[IMG]http://www.itsyourpc.org/duane/files/nvidia1.jpg[/IMG]

when you reboot confirm it's 180.51, go back into synaptic and check. 180.51.

---

### Post by hoodaman on 2009-04-26
the only thing listed as installed on my system that's 180 is modaliases and it's 180.44

I didn't install the drivers because you said that it's not supposed to remove ubuntu desktop.

---

### Post by inobe on 2009-04-26
the ubuntu desktop deal isn't suppose to happen.

i am uncertain where to go from here.

you should have been notified of an update then allow update manager to install them.

are you sure you followed the initial guide, also when adding the source did you click reload ?

---

### Post by hoodaman on 2009-04-26
I added the key per the first post. double checking everything to make sure it wasn't mistyped. it shows up in "software sources" as an entered key.

I added the repos in synaptic per the first post. They show up properly and I did click the reload button. It does not prompt me for updates.

I am not sure why. If you're sure it's supposed to, I believe that it is. It doesn't though and I don't wanna install the drivers manually from synaptic as it says it wants to remove pretty much everything that looks like it makes the gui work.

I'm not sure what exactly to do.:(

---

### Post by inobe on 2009-04-26
lets assume the changes you made in the past with envy or whatever was done may have contributed to this, possibly trying to reverse what was done may help.

notice this thread, not similar to yours situation' however this is what the person had to do but it was a success.

[http://ubuntuforums.org/showthread.php?p=7139925#post7139925](http://ubuntuforums.org/showthread.php?p=7139925#post7139925)

maybe something in there will help you

---

### Post by shload on 2009-04-26
what about drilling into...system > administration > hardware drivers, then choosing the 180 driver and clicking the activate button. 

This is the route i usually go for installing nvidia drivers and it's worked for me.

---

### Post by hoodaman on 2009-04-26
> **shload said:**
> what about drilling into...system > administration > hardware drivers, then choosing the 180 driver and clicking the activate button. 

This is the route i usually go for installing nvidia drivers and it's worked for me.

That was the first thing I tried. The system hangs when I try to download that and when I reboot it goes to a command prompt.

> **inobe said:**
> lets assume the changes you made in the past with envy or whatever was done may have contributed to this, possibly trying to reverse what was done may help.

notice this thread, not similar to yours situation' however this is what the person had to do but it was a success.

[http://ubuntuforums.org/showthread.php?p=7139925#post7139925](http://ubuntuforums.org/showthread.php?p=7139925#post7139925)

maybe something in there will help you

this is actually on a fresh install so envy and all the previous steps I've tried are moot at this point.

---

### Post by inobe on 2009-04-26
i was hoping we could get you a newer driver, newer than 180.44.


if you are willing to go ahead and have nothing to lose remember the list of components, they would apply to you as well.


goodluck :)

---

### Post by hoodaman on 2009-04-26
I installed the drivers.

It booted to a command prompt.

whatever is in those drivers completely guts my gui every time I try to fix it.

I don't know how to fix it, probably not possible since it says it removes all traces of xorg, xserver, ubuntu-desktop, the kitchen sink, the family dog and whatever else it can take.

I've got 2 graphics cards. I have a feeling that something with that is causing the issue. What I'm wondering is, is it even possible to do what I'm trying to do?

---

### Post by inobe on 2009-04-26
notice post #8
 

[http://ubuntuforums.org/showthread.php?t=1007061](http://ubuntuforums.org/showthread.php?t=1007061)

also if i find anymore information it will get sent to you.

---

### Post by 4Orbs on 2009-04-26
```
That was the first thing I tried. The system hangs when I try to download that and when I reboot it goes to a command prompt.
```

I suggest trying this again from the Hardware Drivers Mgr. For some reason the progress bar fails to give any indication of activity while it's downloading and installing the driver. In my case, after waiting a few minutes the progress bar suddenly jumped to 80% and finished installing the driver. Even if Jockey crashes during the driver activation (from Hardware Drivers Mgr), you should try waiting five minutes or so, and then reboot. In this case (Jockey crashing) you will just have to guess when the installation finishes, you won't even get a notification to reboot.

---

### Post by hoodaman on 2009-04-26
> **4Orbs said:**
> ```
That was the first thing I tried. The system hangs when I try to download that and when I reboot it goes to a command prompt.
```I suggest trying this again from the Hardware Drivers Mgr. For some reason the progress bar fails to give any indication of activity while it's downloading and installing the driver. In my case, after waiting a few minutes the progress bar suddenly jumped to 80% and finished installing the driver. Even if Jockey crashes during the driver activation (from Hardware Drivers Mgr), you should try waiting five minutes or so, and then reboot. In this case (Jockey crashing) you will just have to guess when the installation finishes, you won't even get a notification to reboot.

To be fair. I did retry this again per your advice. It did give me a progress bar and Jockey didn't crash on me and it did install the driver and it did prompt me to reboot and it still went to a command prompt upon reboot.

> **inobe said:**
> notice post #8
 

[http://ubuntuforums.org/showthread.php?t=1007061](http://ubuntuforums.org/showthread.php?t=1007061)

also if i find anymore information it will get sent to you.

that looks like the key right there. I'm definitely gonna get this working. I refuse to admit defeat but I'm not above asking for the guidance of others either. I appreciate the help everyone's suggested thus far and I'll post back here with my results after I try this.

---

### Post by inobe on 2009-04-26
i hope you get it working, i also admire your determination :)

i seen some threads regarding disabling sli ?

i never had' i don't know.

---

### Post by inobe on 2009-04-26
hey hood, look what i just found

[http://ubuntuforums.org/showthread.php?t=1139101](http://ubuntuforums.org/showthread.php?t=1139101)

that fella has two video cards.

---

### Post by hoodaman on 2009-04-26
wow. on point for sure. I've got some work to do. Hope this works. Here we go...

EDIT: I followed the advice in the sli thread linked to above and it worked!

I'm a happy guy right now. Thanks for all your help!

---

### Post by hman1169 on 2009-04-26
I just got my graphics back up in the 9.04 - the Jaunty Jackalope, I couldn't start x server after trying some alternate drivers.
I completely killed X server...

This worked for me. I found the Nvidia installer to work better than the synaptic package management

Anyway, as you can see by me being able to type here, I was able to get it going... I am a newbie to this forum, and still learning Linux, (although Ubuntu is easy)I think anyone should be able to follow this - New to Linux or not...

I found I had to do the command line install for my GeForce 8400 GS and one driver covers all the GeForce Models.
You need to download [**NVIDIA-Linux-x86-180.51-pkg1.run**]("http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run") to your desk top. once you get it there, launch your synaptic package management.  do a "Quick Search" for "NVIDIA" mark anything that is green, having to do with Nvidia for "Removal" if it isn't marked, don't worry about it. 

For the Nvidia installer to work, all other versions of Nvidia graphics need to be removed from teh Synaptic Package Manager.

After you get all the package managed Nvida drivers and software removed you should be able to run the configuration file.

I found, to run it, this seemed to work best.

First you'll have to stop X...  Ctrl + Alt+ F1 (sometimes twice)

then, **sudo /etc/init.d/gdm stop** This actually stops X server.
enter your password (provided your on an administrator account) 
it will stop your x server.

now cd (Change Directory) to your Desktop (capital D in Desktop)
I say Desktop because that's where we left the NVIDIA-Linux-x86-180.51-pkg1.run

Now that your in the directory, and you have already killed the x server, you can simply type

**sh NVIDIA-Linux-x86-180.51-pkg1.run** 

follow the on screen selections. Don't worry if it finds an error, let it fix it and move on... it should install... When it's finished it will tell you and you can do the following:

either restart your computer or start your x server 
/etc/init.d/gdm start

I restarted the computer and then set the visual effects to "Extra" and it seems to be working fine.

Hope this helps...

Chris

Links
[http://www.nvidia.com/object/linux_display_ia32_180.51.html](http://www.nvidia.com/object/linux_display_ia32_180.51.html)

I think this is right, if anyone sees an error in my plan, My feelings will not be hurt!

---

### Post by inobe on 2009-04-26
> **hoodaman said:**
> wow. on point for sure. I've got some work to do. Hope this works. Here we go...

EDIT: I followed the advice in the sli thread linked to above and it worked!

I'm a happy guy right now. Thanks for all your help!

hey hood, that's great news :)

enjoy

---

### Post by rmjohnson144 on 2009-04-29
> **inobe said:**
> i have some steps you can try.

i have a 9400gt and it's working great with the 180.51 driver.

did not use "hardware drivers" and certainly didn't install manually !

added this to repository, i used the stable repo

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

add the key, applications> accessories> terminal

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

to add the source go to system> administrator> synaptic> settings> repositories> third party software....

click add and paste

```
deb http://www.avenard.org/files/ubuntu-repos intrepid release
```

close software sources when done and click reload button on synaptic.

close synaptic.

you should then be notified, when this happens' install the upgraded driver and reboot.


every time a new driver is released you will get notified.

a big thanks to the fella that owns and maintains this site.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

if you have any questions feel free to ask.

You may want to remove all reference to this website.  Either they botched it or it is malware.  This setup is removing x-server completely on install.  I tried it 3 times and everytime it removes x-windows and leaves you at the command prompt.  I found this link that is good and is just a configuration issues.

[http://ubuntuforums.org/showthread.php?t=1139101&highlight=enabling+nvidia+drivers+jaunty](http://ubuntuforums.org/showthread.php?t=1139101&highlight=enabling+nvidia+drivers+jaunty)

Hope this helps
-=Mark=-

---

### Post by MockY on 2009-04-29
You are probably better off installing the latest drivers (185), and not the ones suggested in Hardware Drivers (180)
Download them [HERE]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.04/NVIDIA-Linux-x86-185.18.04-pkg1.run") and the follow instructions listed [HERE]("http://ubuntuforums.org/showpost.php?p=7169153&postcount=6")

---

### Post by rmjohnson144 on 2009-04-29
yeah, I did both of those as well with same issues.  I think this 9.04 has a messed up xorg.conf file as that seemed to be a different step from the previous dozen or more reinstalls I've tried.  (The PCI:2:0:0 or whatever lspci reports.)

-=Mark=-
ps, I think mine was a case of multi-card setup.  I think it may be fine on single card setups.

---

### Post by inobe on 2009-05-01
> **rmjohnson144 said:**
> You may want to remove all reference to this website.  **Either they botched it or it is malware.**  This setup is removing x-server completely on install.  I tried it 3 times and everytime it removes x-windows and leaves you at the command prompt.  I found this link that is good and is just a configuration issues.

[http://ubuntuforums.org/showthread.php?t=1139101&highlight=enabling+nvidia+drivers+jaunty](http://ubuntuforums.org/showthread.php?t=1139101&highlight=enabling+nvidia+drivers+jaunty)

Hope this helps
-=Mark=-

that's absurd, i would like to see proof of your claims.

it's simply an incompatible source for 9.04, but only seems to work with upgrading to 9.04...

if you are running 9.04 don't touch the source' instead compile the new kernel modules or use those in hardware drivers.

as me and hoodman went threw the setup it was apparent to be the case.

---

### Post by rmjohnson144 on 2009-05-02
> **inobe said:**
> hey hood, look what i just found

[http://ubuntuforums.org/showthread.php?t=1139101](http://ubuntuforums.org/showthread.php?t=1139101)

that fella has two video cards.

Actually that link to Ed-Koala's method is what HoodMan used to get it working, as well as myself, not this repository you posted.


I reinstalled your repository links and found the offending program was nvidia-glx-180.

Here's a screenshot of the avenard.org repository you posted:

[[IMG]http://img18.imageshack.us/img18/1641/ubunti904.th.jpg[/IMG]](http://img18.imageshack.us/my.php?image=ubunti904.jpg)

as you can see it is completely uninstalling all of x-server.



Here's a screenshot of the original Ubuntu repository:
[[IMG]http://img14.imageshack.us/img14/6118/glx180org.th.png[/IMG]](http://img14.imageshack.us/my.php?image=glx180org.png)

So, if you can, please delete all links to Avanard's Repositories in your posts until you can verify they have been fixed.

Thanks
-=Mark=-

---

### Post by rmjohnson144 on 2009-05-02
OK, I looked over their website a little more and found documentation on installing.  It seems you had a typo on your repository link.

```
deb http://www.avenard.org/files/ubuntu-repos intrepid release
```

It should read read:
```
deb http://www.avenard.org/files/ubuntu-repos jaunty release
```

You have intrepid listed instead if jaunty.  I haven't fully tested it yet, but when I open the repository and reload it no longer tries to remove x-server.  I think if you just update that one line that all should be ok.

-=Mark=-
ps. here's a link to the avenard.org repository installation guide.
[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by inobe on 2009-05-02
i haven't tested either, i think hoodman did and was successful.


i do plan on testing myself and seeing if that is a workaround, a lot of folks could really use that repo for jaunty.




apparently the repo only works threw upgrades to 9.04.


example : someone using the repo in 8.10 upgraded to 9.04, it wasn't complicated except the fact jaunty tried loading the default 180.44 when he already had a newer version, that may have been the hiccup but must consider the 180.11 and 180.44 drivers didn't like his onboard nvidia chip.

[http://ubuntuforums.org/showthread.php?t=1143504](http://ubuntuforums.org/showthread.php?t=1143504)

> Actually that link to Ed-Koala's method is what HoodMan used to get it working, as well as myself, not this repository you posted.


me and hood were discussing the problem with the repo via pm and he did mention it working by changing from intrepid to jaunty, i didn't confirm it !


i have went back and edited some posts to let folks know about the desktop removal issue and stated that it was a non compatible repo for jaunty.

since i haven't confirmed editing the repo name' and if it actually works i didn't include any information to that.

---

### Post by rmjohnson144 on 2009-05-02
I cleared out my backup drive and I'm installing 9.04 from scratch and testing it out now.

I'll let you know how it works out.
-=Mark=-

---

### Post by inobe on 2009-05-02
sounds good, i won't be able to test this for at least a few days.


this will help a lot of folks, thanks

---

### Post by rmjohnson144 on 2009-05-02
OK, it still turns out the jaunty version is not configure multi video cards still, but it doesn't remove x-server like before.

Luckily I was able to get it working by only editing the xorg.conf file and adding the BusID line and nothing else.

Maybe you can add that step after the driver install, before rebooting.  I didn't do it and got the command prompt, but I was able to type it in there using nano instead of gedit to edit the xorg.conf file.  when I rebooted all is fine now.

-=Mark=-

---

### Post by inobe on 2009-05-02
great stuff, thanks again.


for those that didn't review what gets removed and went ahead......... anyway !

if you ended up in a server ui due to the repo' simply run

```
sudo dpkg-reconfigure xserver-xorg
```

if you get an error saying xserver isn't installed' do

```
sudo apt-get install ubuntu-desktop
```

if you get an nvidia error' do

```
sudo apt-get remove nvidia-glx
```

then run the ubuntu-desktop command....

after that you will need to manually remove the driver from the repo in synaptic, this will intern replace the 180.51 with 180.44.

---

### Post by rmjohnson144 on 2009-05-03
> **inobe said:**
> great stuff, thanks again.


for those that didn't review what gets removed and went ahead......... anyway !

if you ended up in a server ui due to the repo' simply run

```
sudo dpkg-reconfigure xserver-xorg
```

if you get an error saying xserver isn't installed' do

```
sudo apt-get install ubuntu-desktop
```

if you get an nvidia error' do

```
sudo apt-get remove nvidia-glx
```

then run the ubuntu-desktop command....

after that you will need to manually remove the driver from the repo in synaptic, this will intern replace the 180.51 with 180.44.

actually this still won't work.  you have to add the editing of the xorg.conf file in order to get multi video cards working.  It seems all installers are still bugged on this part of the install process.

You also may want to change the intrepid repository to read jaunty as people (like me) will blindly copy & paste it and have huge problems.  remember the original posters post is about sli and jaunty and no mention of intrepid, also other users will also be looking for the same help and the intrepid will cause a lot of extra issues.

Wish you success on your testing.
-=Mark=-

---

### Post by inobe on 2009-05-03
> **rmjohnson144 said:**
> actually this still won't work.  you have to add the editing of the xorg.conf file in order to get multi video cards working.  It seems all installers are still bugged on this part of the install process.

You also may want to change the intrepid repository to read jaunty as people (like me) will blindly copy & paste it and have huge problems.  remember the original posters post is about sli and jaunty and no mention of intrepid, also other users will also be looking for the same help and the intrepid will cause a lot of extra issues.

Wish you success on your testing.
-=Mark=-

post #39 covers getting a desktop if it's lost do to using avenard repo "9.04 users"

---

### Post by rmjohnson144 on 2009-05-03
> **inobe said:**
> post #39 covers getting a desktop if it's lost do to using avenard repo "9.04 users"

my post was in response to your post #39.  as it stands it will NOT work.  You absolutely have to edit xorg.conf or you will NOT get to the desktop.

You also have to change the repo link to jaunty(which will negate post #39 completely).  the intrepid link will do nothing but give problems over time.  This thread is specifically about jaunty not intrepid.  It would be like pointing someone with Windows Vista to XP updates.  It's just not going to work properly.

also, it might be much more beneficial to post updates by editing your first post rather than replying on people to search several pages of posts to figure out a fix that could have been avoided altogether if the original info is accurate.

-=Mark=-

---

### Post by inobe on 2009-05-03
thanks for explaining 

i did another check on that site and discovered 

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

edit: fresh installing 9.04 now to confirm this.

---

### Post by inobe on 2009-05-03
> **inobe said:**
> thanks for explaining 

i did another check on that site and discovered 

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

edit: fresh installing 9.04 now to confirm this.

i installed kubuntu 9.04 x64 bit, i did the system updates, activated thew 180.44 driver then added the 9.04 jaunty repo, then did

```
sudo apt-get update
```


**edit:"for jaunty 9.04 only"**



i then received the update notification, applied updates and rebooted to a desktop running 180.51 driver.



it works like a charm

add key

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key
```

add repo

```
echo "deb http://www.avenard.org/files/ubuntu-repos jaunty release" | sudo tee /etc/apt/sources.list.d/avenard.list



```

in terminal.

---

### Post by Keneo on 2009-05-14
I got SLI working on ubuntu by just changing 2 lines in my Xorg.conf
namey adding these lines 

BusID "05:00:0"
Option "SLI"

in my Device section
(the 5 is because lspci | grep VGA told me that my graphics card was eathe in position 04:00.0 or 05:00.0. 
After trying 4 Xorg told me in the Xorg.0.log file to try 5, and it worked :)

(also notice, the option "SLI" is not needed, but it will make your sli setup actually work in sli mode, and not 2 seperate cards)

SLI mode only supports 1 screen, so, for people like me, with a dualscreen setup, you have to put 
Option "SLI" "OFF"

to use your 2 screens, put it to "ON" to play a game in single screen mode :)
(after restarting X every time ofcourse)

also see this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241)

---

### Post by pcpain on 2009-08-05
To inobe,

I tried your method and it worked really well. I have a video card of Gigabyte Nvidia GeForce 9500GT to be installed to Ubuntu 9.0.4. I have tried other methods and suggestions for over 2 months, but none worked.

Thank you for the posting! :D

---

