---
title: "install updates for 7.10 &amp; 8.04"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by orwellus on 2009-03-03
Hello

You know how when you install Ubuntu, one of the first thing it does is tell you that there are 237 updates available. So you have to spend an addition couple of hours downloading and installing these updates. 

I was wondering if I could download these updates from somewhere and save them onto a cd or flashdrive. That way, if I install, or reinstall, Ubuntu I can just pop the cd in and it install all these updates.

If possible, I would like to get the ones for Gutsy 7.10 and Hardy 8.04

Thanks

---

### Post by civillian on 2009-03-03
This is one possible way of doing it (although it might take a while, if you have to install the packages manually...)
[http://theunixgeek.blogspot.com/2008/08/installing-ubuntu-packages-offline.html](http://theunixgeek.blogspot.com/2008/08/installing-ubuntu-packages-offline.html)

Another option is to install all of your preferred applications and updates then use aptoncd to save all your installed packages to a CD then use that CD as a repository for apt-get/synaptic.

However it would probably be easier just to install all the updates from the ubuntu servers using the command
```
sudo apt-get install dist-update
```
or let the update manager work in the background on its own until it asks to reboot etc.

One last suggestion would be to install all the updates and your preferred applications then make an image of the clean system (with updates applied) which you can just restore to your computer when and if you need to. (This can be done using partimage)

Hope one of these suggestions helps you out!
Civ

---

### Post by hichamroudi on 2009-03-14
I am newbie in ubuntu world... I had the same poblem of offline update need. Now I am trying this solution I am downloading update packages now.I guess it would work - I tried this procedure with ADD/REMOVE APPS to fetch softwares packages and installed them offline and it worked great-.

1- click on the update icon in the above panel.
2- click on Install update.
3- cancel downloading before any file is completed.An *error occurred* pop up window will tell you :

The following details are provided:

W: Failed to fetch [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com)...
W: Failed to fetch [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com)...
W: Failed to fetch [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com)...
...
...
4- copy the list of URL addresses and paste them into a new txt file.
5- in the menu of Gedit click Search> Replace. (to replace the sentence of [COLOR="Red"]W: Failed to fetch[/COLOR] http...... with the word [COLOR="SeaGreen"]wget[/COLOR] .   *apply change in all URLs *)
6-In order to download the packages Copy all urls in a terminal.or do it step by step.

(you may create a folder named update in your home/name/ or in a pen drive, go to that directory in terminal then paste the command+URLs : wget http......)

after download you will type the command in a terminal in any machine you want to update off-line:

```
hexham@JacKALOPe§ **sudo dpkg -i [COLOR="Red"]/pathtofolder/[/COLOR]*.deb**
```



e.g:Here are all update packages urls for my ubuntu (Intrepid-Ibix 8.10) modified and saved into 2 txt files.

NB:You can burn update/software packages to CD/DVD.

---

### Post by hichamroudi on 2009-03-14
YES. It worked as I guessed before.


 My old Kernel version of 2.6.27.7 is now 2.6.27.11 (All system and programs were updated Off-line in 10 minutes.

If you encountered any problem such as the **unmet dependencies problems** just type in terminal the command that enables you to fix it:

```
sudo apt-get install -f
```

It will told you either remove or install something you may remove or fetch it easily afterwards.

           [CENTER]*****************************************

HOWEVER, there stay another choice for users that need an updated
 ubuntu dist CD, which is SUPER UBUNTU last release is 11.2008.

for more info: [http://hacktolive.org](http://hacktolive.org)

[/CENTER]
*HEXHAM*

---

