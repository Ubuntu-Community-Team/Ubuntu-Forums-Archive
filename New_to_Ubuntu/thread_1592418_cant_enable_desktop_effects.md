---
title: "cant enable desktop effects"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-10
since the last couple of updates i cant enable ccsm and enable desktop effects. cant rotate cube etc. any ideas how to fix/tks

---

### Post by cariboo on 2010-10-10
We still can't guess what graphics drivers you're using. More info please.

---

### Post by jnorthr on 2010-10-10
some graphics cards do not have the capabilities to support open GL api calls. This was my case so i could not use extended desktop candy. What is your graphics card ?

---

### Post by rburkartjo on 2010-10-10
how do i check on my graphic card not effects fine until the last set of updates for 10.10/tks

note here is link i checked out
and if i use the first command i get the gears

[http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/](http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/)

---

### Post by dodo3773 on 2010-10-10
> **rburkartjo said:**
> how do i check on my graphic card not effects fine until the last set of updates for 10.10/tks

note here is link i checked out
and if i use the first command i get the gears

[http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/](http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/)

Did you do an upgrade or a clean install? I just did the upgrade and what I had to do was go into synaptic package manager and search for anything marked compiz and uninstall it. Then I ran the command at the link that you mentioned above and everything is working now. I guess something broke while upgrading. Maybe that is what happened when you updated as well.

---

### Post by rburkartjo on 2010-10-10
dodo good idea will try that

---

### Post by rburkartjo on 2010-10-10
dodo that didnt work i am lost no big deal just would like to fix/tks again for the idea

---

### Post by rburkartjo on 2010-10-10
and dodo i did an upgrade been using 10.10 since the last alpha only problem i have had is with x and that was fixed in in the beta 
i will see if any upcoming updates will fix unless anyone else as another idea

---

### Post by dodo3773 on 2010-10-10
> **rburkartjo said:**
> and dodo i did an upgrade been using 10.10 since the last alpha only problem i have had is with x and that was fixed in in the beta 
i will see if any upcoming updates will fix unless anyone else as another idea

I also went to system - administration - additional drivers then I hit the remove button. Rebooted then enabled it then rebooted again. 

Found that here
[URL="http://ubuntuforums.org/showthread.php?t=1592245"]
http://ubuntuforums.org/showthread.php?t=1592245[/URL]

---

### Post by rburkartjo on 2010-10-10
dodo that didnt do it. again i really appreciate you going the extra mile no big deal if i cant get to work just bugs me that i cant figure out why

---

### Post by DayLite on 2010-10-11
Help me too :confused:

I upgraded to Ubuntu 10.10 from Ubuntu 10.04 on my Latitude D600. My  Graphic card is,
V**GA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)**

I lost all my desktop effects, I did have the wavy windows, cube etc. When I checked for a driver it says non available.

You can read details at my thread at: [http://ubuntuforums.org/showthread.php?t=1592564](http://ubuntuforums.org/showthread.php?t=1592564)

---

### Post by DayLite on 2010-10-11
I applied the instructions found at: [http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/](http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/)

This is from my terminal:

> joan@joan-laptop:~$ sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core emerald compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager
[sudo] password for joan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packages
joan@joan-laptop:~$ 


How do I correct this? I am very new to Ubuntu and do not understand the terminal, please help in simple basic instructions.

---

### Post by rburkartjo on 2010-10-11
day that is what i get also

---

### Post by DayLite on 2010-10-11
> **rburkartjo said:**
> day that is what i get also
 Well, it is encouraging to know I am not alone, but I hope there is somebody on this forum that reads this and helps.

---

### Post by rburkartjo on 2010-10-11
day nice to know our sanity is not going hopefully someone finds a fix or future updates  fix

---

### Post by DayLite on 2010-10-11
> **rburkartjo said:**
> day nice to know our sanity is not going hopefully someone finds a fix or future updates  fix

I'm just thankful the problem is with my laptop. Learned my lesson, I won't upgrade my desktop, it works fine.  'Why fix what is not broken', not 'variety is the spice of life'.

Ahh, a little humor. :confused:

---

### Post by dodo3773 on 2010-10-11
> **DayLite said:**
> I applied the instructions found at: [http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/](http://ranjith.zfs.in/install-compiz-fusion-ubuntu-10-10-maverik-meerkat/)

This is from my terminal:



How do I correct this? I am very new to Ubuntu and do not understand the terminal, please help in simple basic instructions.
  I got the same thing. What I did was to go into the software center or synaptic if you prefer and remove everything that came up when I searched for    compiz    then I ran the command at the blog link above. That is what did it for me.

---

### Post by dodo3773 on 2010-10-11
> **DayLite said:**
> I'm just thankful the problem is with my laptop. Learned my lesson, I won't upgrade my desktop, it works fine.  'Why fix what is not broken', not 'variety is the spice of life'.

Ahh, a little humor. :confused:

Just did a clean install. Wiped my upgraded version and started over. Some things are better but all in all I really liked 10.04 much better. I am going to go back to it today. Too many freezes for me. maybe after about 3 or 4 months of updates I will come back and try it again.

---

### Post by andrewthomas on 2010-10-11
There is nothing wrong with the state of the compiz packages in the repo

check the versions that you have installed with 
```
dpkg-query -l compiz*
```> ats@antec:~$ dpkg-query -l compiz*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  compiz                            1:0.8.6-0ubuntu9                  OpenGL window and compositing manager
ii  compiz-core                       1:0.8.6-0ubuntu9                  OpenGL window and compositing manager
un  compiz-core-abiversion-20091102   <none>                            (no description available)
ii  compiz-fusion-bcop                0.8.4-1                           Compiz Fusion option code generator
ii  compiz-fusion-plugins-extra       0.8.6-0ubuntu1                    Collection of extra plugins from OpenCompositing for Compiz
ii  compiz-fusion-plugins-main        0.8.6-0ubuntu2                    Compiz Fusion plugins - main collection
ii  compiz-gnome                      1:0.8.6-0ubuntu9                  OpenGL window and compositing manager - GNOME window decorator
un  compiz-gtk                        <none>                            (no description available)
un  compiz-kde                        <none>                            (no description available)
ii  compiz-plugins                    1:0.8.6-0ubuntu9                  OpenGL window and compositing manager - plugins
un  compiz-wrapper                    <none>                            (no description available)
ii  compizconfig-backend-gconf        0.8.4-1ubuntu5                    Compiz Fusion configuration system - gconf backend
ii  compizconfig-settings-manager     0.8.2-0ubuntu1                    Compiz configuration settings manager
ats@antec:~$ 


---

### Post by DayLite on 2010-10-11
> **dodo3773 said:**
> Just did a clean install. Wiped my upgraded version and started over. Some things are better but all in all I really liked 10.04 much better. I am going to go back to it today. Too many freezes for me. maybe after about 3 or 4 months of updates I will come back and try it again.

Instruct me how to do it? I have partitioned my hard drive, one side is Windows XP and the other side is Ubuntu. How do I return to 10.04.

---

### Post by Quackers on 2010-10-11
If you go to Synaptic Package Manager and look at the bottom left of the screen does it mention broken packages? If so, click on Edit in the menu bar and select Fix broken packages. See if that helps.

---

### Post by DayLite on 2010-10-11
> **Quackers said:**
> If you go to Synaptic Package Manager and look at the bottom left of the screen does it mention broken packages? If so, click on Edit in the menu bar and select Fix broken packages. See if that helps.

Just checked 0 missing.

---

### Post by dodo3773 on 2010-10-11
> **DayLite said:**
> Instruct me how to do it? I have partitioned my hard drive, one side is Windows XP and the other side is Ubuntu. How do I return to 10.04.

Just delete the Ubuntu partitions from the live cd then reinstall Ubuntu for a dual boot. Just like you did the first time (well unless you used the wubi installer). It should be pretty easy to find out which ones are Ubuntu based on the file systems. Usually Windows will be NTFS or FAT32 or Fat or something like that. Ubuntu partitions will be ext4 ext3 and will be labeled as swap root etc.

---

### Post by Tumpster on 2010-10-11
I'm having similar problems, running a 512MB EVGA Nvidia 9800GTX+ that did compiz just fine in 10.04. All drivers are installed from Nvidia, I did it myself manually with the driver package.

---

### Post by shunoob on 2010-10-11
For anyone using Ubuntu Tweak:

I upgraded my laptop this morning at school, and updated, and soon found that compiz was broken. Since I remembered that I was using the PPA's provided by Ubuntu Tweak(for Compiz), I thought that might be it. So you can try disabling the PPA "PPA for compiz packagers", then uninstalling/removing+purge every compiz package in Synaptic, then reinstall the ones provided by Canonical.

After that, I got compiz and all my desktop effects back. It worked for me(though that might not be the issue for everyone).

---

### Post by rburkartjo on 2010-10-11
shun, dont have that ppa enabled good idea though maybe it will work for someone. tks for sharing

---

### Post by DayLite on 2010-10-11
> **shunoob said:**
>  then reinstall the ones provided by Canonical.

Where do you find the ones provided by Canonical?

---

### Post by Cavsfan on 2010-10-12
I decided to uninstall compiz and cairo-dock and emerald. They were working fine, but thought I would mess something up just for the heck of it.

I have gotten rid of everything, but **dpkg-query -l cairo*** shows this:

Can't figure out why.
```
cavsfan@cavsfan-desktop:~$ dpkg-query -l cairo*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
un  cairo-5c                                              <none>                                                (no description available)
un  cairo-dock                                            <none>                                                (no description available)
un  cairo-dock-core                                       <none>                                                (no description available)
un  cairo-dock-data                                       <none>                                                (no description available)
un  cairo-dock-plug-ins                                   <none>                                                (no description available)
un  cairo-dock-plug-ins-data                              <none>                                                (no description available)
un  cairo-dock-plug-ins-integration                       <none>                                                (no description available)
```Nothing shows as installed in Synaptic for any of it.
There were a few things that had "rc" beside them and I purged those and above is all that shows.
I have nVidia driver 260.19.06 installed and it worked fine, but I could not get desktop effects.
It would freeze when I brought up Simple CompizConfig Settings Manager and click on anything.

---

### Post by Cavsfan on 2010-10-12
I also have this ppa **[http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu)** **Maverick** isn't this the canonical one?

---

### Post by Tumpster on 2010-10-12
> **shunoob said:**
> For anyone using Ubuntu Tweak:

I upgraded my laptop this morning at school, and updated, and soon found that compiz was broken. Since I remembered that I was using the PPA's provided by Ubuntu Tweak(for Compiz), I thought that might be it. So you can try disabling the PPA "PPA for compiz packagers", then uninstalling/removing+purge every compiz package in Synaptic, then reinstall the ones provided by Canonical.

After that, I got compiz and all my desktop effects back. It worked for me(though that might not be the issue for everyone).

Tried this to no success, anyone have any other ideas?

---

### Post by Cornbreadly on 2010-10-13
I am getting it too.  Have ubuntu tweak, virtualbox, docky.  Had cool windows management system and decided to try the new realease.  Upgraded unstead of a clean install.  I would love to avoid the clean install.

*Tried removing ppa for tweak, removing all compiz packacges, then reinstalling using canonical sources
*[Does this have anything to do with it]("http://forum.virtualbox.org/viewtopic.php?f=3&t=35218&start=15")?  Virtualbox being installed?

---

### Post by rburkartjo on 2010-10-14
corn dont have virtualbox installed but it was worth a shot

---

### Post by ephestione on 2010-10-14
fast feedback.
Found this thread as I was having this problem, right after upgrade to maverick final extra effects worked, but at the next reboot after that they weren't anymore, and couldn't enable them.
Dodo said to remove and reinstall compiz but that didn't help. Then I remembered that inside Ubuntu Tweak I enabled the "last compiz packages" repository. Disabling it , updating and reinstalling compiz solved.
And I'm using a good toshiba satellite which has anyway a crappy intel integrated card, so...

---

### Post by rburkartjo on 2010-10-14
okay this is how i fixed. no sure what did it
first opened spm and uninstalled anything with compiz in the name

next went to home opened hiddened folders opened gconf/apps and removed the compiz folder

next opened ubuntu software center and removed anything with compiz in the name

opened the ubuntu software center again and reinstalled anything with compiz in the same with the exception of the one for kde

then click on the desktop  change desktop background/visual effects
clicked on extra or custom and it worked. 

desktop effects were enabled as well as ubuntu tweak

---

### Post by rburkartjo on 2010-10-14
ephe i had done the samething. sounds like your fix was easier but i couldnt access tweak would not open. so i couldnt disable. had to do it the way i did to access tweak

---

### Post by DayLite on 2010-10-14
> **rburkartjo said:**
> okay this is how i fixed. no sure what did it
first opened spm and uninstalled anything with compiz in the name

next went to home opened hiddened folders opened gconf/apps and removed the compiz folder

next opened ubuntu software center and removed anything with compiz in the name

opened the ubuntu software center again and reinstalled anything with compiz in the same with the exception of the one for kde

then click on the desktop  change desktop background/visual effects
clicked on extra or custom and it worked. 

desktop effects were enabled as well as ubuntu tweak

Followed your steps, did not work :confused:

---

### Post by Marceau on 2010-10-14
I followed all suggestions in this thread and still cannot get Compiz to run.

When doing compiz --replace in the terminal, I get the following:

```
marceau@computer:~$ compiz --replace
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
kde-window-decorator(3201) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"
kde-window-decorator(3199) KWD::KDecorationPlugins::loadPlugin: kwin : path  ""  for  "kwin3_oxygen"
kde4-window-decorator: Could not enable decorations on display ":0.0"
i915_program_error: Exceeded max nr indirect texture lookups (5 out of 4)

Launching fallback window manager

```

I'm not sure what this all means, but the one thing that I find odd is that it refers to kde4-window-decorator. I'm on straight Ubuntu, which uses Gnome. What's up?

---

### Post by rburkartjo on 2010-10-14
marc did you remove the kde windows decorators

good luck let me know how you fare
i spend over 7 hrs total to correct the problem with compiz and
ubuntu tweak
all i know is that it worked for me
maybe try this open spm remove all compiz programs use the mark for complete removal
then open the ubuntu software center and if any still show as being on your computer
then go to the gconf file and delete the whole file
then back to software center and reinstall anything with compiz that does not ref kde

---

### Post by DayLite on 2010-10-14
> **rburkartjo said:**
> marc did you remove the kde windows decorators

good luck let me know how you fare
i spend over 7 hrs total to correct the problem with compiz and
ubuntu tweak
all i know is that it worked for me
maybe try this open spm remove all compiz programs use the mark for complete removal
then open the ubuntu software center and if any still show as being on your computer
then go to the gconf file and delete the whole file
then back to software center and reinstall anything with compiz that does not ref kde

I did, 'just so' and it didn't work for me :confused:

---

### Post by rburkartjo on 2010-10-14
day if you find out how to do please post you fix somewhere on the forms others are having the same problem. sorry what i did to fix didnt work for you

---

### Post by carlosjimy on 2010-10-14
Hi everyone!
You should review this post:

[http://ubuntuforums.org/showthread.php?p=9959374](http://ubuntuforums.org/showthread.php?p=9959374)

Work it for you?

Bye!

---

### Post by DayLite on 2010-10-14
> **rburkartjo said:**
>  sorry what i did to fix didnt work for you

That's ok, I appreciate that you shared it. If I ever do find a solution I will post to this group. On launchpad I did read that there is problems with compiz and so far no updates to deal with it. My guess is, at least for me, there is no problem with my graphic card needing a driver but all has to do with compiz.

---

### Post by Tumpster on 2010-10-16
> **rburkartjo said:**
> marc did you remove the kde windows decorators

good luck let me know how you fare
i spend over 7 hrs total to correct the problem with compiz and
ubuntu tweak
all i know is that it worked for me
maybe try this open spm remove all compiz programs use the mark for complete removal
then open the ubuntu software center and if any still show as being on your computer
then go to the gconf file and delete the whole file
then back to software center and reinstall anything with compiz that does not ref kde

I've tried all three methods to no success, any other ideas?

---

### Post by Tumpster on 2010-10-20
Anything from anybody?

---

### Post by Marceau on 2010-10-20
> **Tumpster said:**
> Anything from anybody?

Well I finally managed to get compiz up and running.

The problem in my case was that for some reason, compiz was installed with kde decorator instead of gnome. I'm guessing that, with my system running gnome, it did not mesh well.

I went into synaptic, checked for compiz again, and found a mention of kde. When uninstalling, synaptic itself automatically installed the required gnome components. All's been fine since then.

Not sure if you've tried this, but perhaps you might see a useful error message when you type "compiz --replace" in the terminal.

---

### Post by trikster_x on 2010-10-20
EDIT:  I got it working!!!

so here is what I had to do:

Remove EVERYthing compiz related:  Go to synaptic, type in "compiz" in the search bar, and ANYTHING that is installed, completely remove.

Close synaptic.

If you are using the ppa or any other compiz related repos, disable those in your software sources list.

run:
```
sudo apt-get autoclean
```

then back to synaptic and reload your package info. (in synaptic, "EDIT>>reload package information")

Finally type in "compiz" in the synaptic search bar and install "compiz config settings manager" (this will automatically check everything needed for compiz).  

Then you can install any of the tools you would normally install, like emerald or fusion icon.

I hope this helps anyone else having this problem.

---

### Post by Casey R on 2010-10-20
Having exactly the same problem here regarding Compiz. Only since this morning's update.

---

### Post by Casey R on 2010-10-20
Getting rid of the Compiz PPA fixes it :)

---

