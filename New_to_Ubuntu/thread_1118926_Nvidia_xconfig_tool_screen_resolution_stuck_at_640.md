---
title: "Nvidia xconfig tool screen resolution stuck at 640x480"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by jcm1107 on 2009-04-07
Hi I used nvidia x config tool to fix this before but I need help doing it again, I just can't remember how I did it. I am new to Ubuntu and just don't know much about using the terminals and stuff. Will someone please walk me through this. I have downloaded Nvidia-Linux-x86-180.44-pkg1.run
I just don't know how to get it to work and the nvidia site's instructions are a little complicated for me. Thanks!

---

### Post by Claus7 on 2009-04-07
Hello,

so you want to install the restricted driver from the nvidia site. I hope you the best.

In order to do so you have to make your screen black:
sudo /etc/init.d/gdm stop

don't worry if your screen disappears. This is what should do. Now if you are lucky you will see the command prompt ready at your disposal. If it doesn't want to appear then press : Ctrl+Alt+F1

then you will have your command prompt. Navigate to where you downloaded the file Nvidia-Linux-x86-180.44-pkg1.run and do:
```
chmod 755 Nvidia-Linux-x86-180.44-pkg1.run
sudo ./Nvidia-Linux-x86-180.44-pkg1.run
```

then you will be guided to the rest. Then restart your computer and I hope that everything will be ok.
I do not remember if instead of restarting you can type :
sudo /etc/init.d/gdm start

but you will find out.

Just two notices:
I hope that your graphics card driver is included in this version of file you have downloaded.

Have in mind that you can enable the same thing from synaptic, unless you have found out that it's not working. I think that you should go to synaptic first.

Now if everything is ok you should go to System -> System Administration -> Nvidia X Settings and configure accordingly.

Regards!

---

### Post by jcm1107 on 2009-04-07
> **Claus7 said:**
> Hello,

so you want to install the restricted driver from the nvidia site. I hope you the best.

In order to do so you have to make your screen black:
sudo /etc/init.d/gdm stop

don't worry if your screen disappears. This is what should do. Now if you are lucky you will see the command prompt ready at your disposal. If it doesn't want to appear then press : Ctrl+Alt+F1

then you will have your command prompt. Navigate to where you downloaded the file Nvidia-Linux-x86-180.44-pkg1.run and do:
```
chmod 755 Nvidia-Linux-x86-180.44-pkg1.run
sudo ./Nvidia-Linux-x86-180.44-pkg1.run
```

then you will be guided to the rest. Then restart your computer and I hope that everything will be ok.
I do not remember if instead of restarting you can type :
sudo /etc/init.d/gdm start

but you will find out.

Just two notices:
I hope that your graphics card driver is included in this version of file you have downloaded.

Have in mind that you can enable the same thing from synaptic, unless you have found out that it's not working. I think that you should go to synaptic first.

Now if everything is ok you should go to System -> System Administration -> Nvidia X Settings and configure accordingly.

Regards!


How can I do it from a terminal and synaptic, that is how I did it before I just don't know what I typed in where to find it. The download is in firefox and my desktop my user name is justin. Could you give me a command that I can copy and paste and please tell me where to copy and paste it at. I am just new and don't know what I need to type in yet. I know if I can get some help I will learn in time, but I need the help until then. Thanks

---

### Post by Claus7 on 2009-04-07
Hello,

so if you did it from synaptic I would advice you to do it again from there.

From synaptic you will choose a general package that comprises the driver of your graphics card. Now the procedure you have to follow in order to be sure is:

i)identify the model of your graphics card
lspci
ii)find in which kernel your graphics card is
now with your model in had go to synaptic and type nvidia
there you will see some glx files. if you click them in the description in the down window it has some graphics card models (this for nvidia cards for ati I think that you should type ati). See in which you can find yours.
If for example you recognize your graphics card to be in glx 96 install all the packages with the 96 label. Maybe this will require you to uninstall some other packages. Don't worry. It's normal. 
iii)install all the files affiliated to this kernel
you just did it with step ii
iv)reboot and probably you are half finished.

How you will be able to configure your xorg.conf file, still I miss. I was lucky that I had an old one and tampering with this and that I was able in the end to put it right. Maybe the nvidia settings might help you : System -> System Administration -> Nvidia Settings

Yet you might have to configure it manually...

Regards!

---

### Post by jcm1107 on 2009-04-08
> **Claus7 said:**
> Hello,

so if you did it from synaptic I would advice you to do it again from there.

From synaptic you will choose a general package that comprises the driver of your graphics card. Now the procedure you have to follow in order to be sure is:

i)identify the model of your graphics card
lspci
ii)find in which kernel your graphics card is
now with your model in had go to synaptic and type nvidia
there you will see some glx files. if you click them in the description in the down window it has some graphics card models (this for nvidia cards for ati I think that you should type ati). See in which you can find yours.
If for example you recognize your graphics card to be in glx 96 install all the packages with the 96 label. Maybe this will require you to uninstall some other packages. Don't worry. It's normal. 
iii)install all the files affiliated to this kernel
you just did it with step ii
iv)reboot and probably you are half finished.

How you will be able to configure your xorg.conf file, still I miss. I was lucky that I had an old one and tampering with this and that I was able in the end to put it right. Maybe the nvidia settings might help you : System -> System Administration -> Nvidia Settings

Yet you might have to configure it manually...

Regards!

Ok here is what I have XfXnFORCE 630i motherboard with 7150 GeForce graphics. I am not using a graphics card just what the motherboard has. Could you tell me what I need to do? I got the Nvidia x server settings to come up but this is what it says,

 You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

I have tried to run sudo nvidia-xconfig and it does this

justin@ubuntu:~$ sudo nvidia-xconfig
[sudo] password for justin: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

justin@ubuntu:~$ 

so what do I need to do to get it working? I am lost! Thanks

---

### Post by Claus7 on 2009-04-08
Hello,

if you were able to configure your graphics card only from this command you said, I would be very surprised...

So check first if the driver of your card is installed:
dpkg --list | grep -i nvidia

and post the output here.
Now it would be nice to see your xorg.conf file as well, yet I do not expect much from it.

And also it would be nice to know which version of ubuntu you are using.

From what I can get you should configure your xorg.conf file manually which is not such a trivial task for a new user like you. I mean that you should do some "experiments" first. Yet, we should ensure which version of ubuntu you have and if "any" driver of your card is installed.

Regards!

---

### Post by jcm1107 on 2009-04-08
> **Claus7 said:**
> Hello,

if you were able to configure your graphics card only from this command you said, I would be very surprised...

So check first if the driver of your card is installed:
dpkg --list | grep -i nvidia

and post the output here.
Now it would be nice to see your xorg.conf file as well, yet I do not expect much from it.

And also it would be nice to know which version of ubuntu you are using.

From what I can get you should configure your xorg.conf file manually which is not such a trivial task for a new user like you. I mean that you should do some "experiments" first. Yet, we should ensure which version of ubuntu you have and if "any" driver of your card is installed.

Regards!

Here are the results of dpkg --list  grep -i nvidia 

and by the way I am using 8.04 Hardy. I may have manually edited the xconfig file the last time. I know I was looking at how to do  it, but I am pretty sure I just used the nvidia drivers and tools to adjust my resolution. I just can not get them to work anymore, an update to intrepid is what messed stuff all up. It was running great until I tried to upgrade, so I erased that installation and reinstalled 8.04 hardy because I know I had it working awsome just don't know what I did to get it to work. But I know I didn't have to go into that black screen you were talking about. I tried that and it said that Nvidia-linux-x86-180.44.pkg1.run wasn't a command or it couldn't run it or something I forget. Ok well here is your info and thanks for helping!!!

justin@ubuntu:~$ dpkg --list | grep -i nvidia
rc  nvidia-glx-new                             169.12+2.6.24.16-23.56            NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  nvidia-kernel-common                       20051028+1ubuntu8                 NVIDIA binary kernel module common files
ii  nvidia-settings                            1.0+20080304-0ubuntu1.1           Tool of configuring the NVIDIA graphics driv
ii  nvidia-xconfig                             1.0+20070502-1ubuntu1             The NVIDIA X Configuration Tool
justin@ubuntu:~$

---

### Post by jcm1107 on 2009-04-08
Ok I got it to work by runing it from the Ctrl+Alt+F1 screen I had to remove all drivers first and reinstall this one it is working but will not let me save my settings to the xorg file. I will have to work on this latter I have to go to work. Can you tell me how to manually edit it? I think I had to edit it to let the nvidia tool save settings there. How do I find and acess the xorg.config file? I can't find it but I have to go now. Thanks

this is what it says when trying to save the current settings from the nvidia tool:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

This is what I need help with now.I just want to make sure to save the current settings so it is not going back to low resolutions.

---

### Post by Claus7 on 2009-04-09
Hello,

glad you solved you problem. It is possible after an upgrdade to have problems. 

Now if I can make out correctly what you did is:
i)remove everything Nvidia from synaptic
ii)change the file name you downloaded to executable (that's why it was complaining before about being a regular file and not an executable one.
iii)then install that file while you have killed before your x server (black screen)

Now in order to ran and install the file you downloaded is better to do so as root, meaning that you have to type sudo in front of the installation command. I do not understand why it doesn't allow you to save the configurations once and for all. When I had to execute this file it always urged me before to do it as root. 
If nvidia settings as you say cannot do that then I would try the command:
gksudo nvidia-settings

if it complains that it does not exist then go to synaptic and install the program with the same name.

As your last message sais, in order to find all your xorg.conf.xxx files you have to go to /etc/X11 directory (open a terminal and type cd /etc/X11/). 
So if you want to configure something manually there, then you have to open the xorg.conf file with a text editor of your choise as root and do the modifications you think are necessary. If you mess something there you have to have in mind that your graphical environment in the next boot might not work so if you have a mediocre graphical environment is best to keep a backup of it (your last xorg.conf file before the modification) and cp it back to normal as root.

You are welcome, 
glad if I was able to help,
Regards!

---

### Post by Jakey_TheSnake on 2009-04-09
NB: as a pointer, you can find your previously typed terminal commands simply by pressing the up arrow when in the terminal, it will scroll through from most recent to oldest =)

---

### Post by jcm1107 on 2009-04-10
My problem is back again! Like I said it worked great then I messed it up, I know its my fault because I am new to this. I was trying to get my wireless internet back and enabled something that caused this to happen again. The wireless worked when I first installed and updated everything then I disabled everything to get my screen so I can see it and now I don't have either one working. Somehow my screen is at a decent resolution right now but not the optimum of 1440x900. I think it is because I told it what monitor I have and it is leting it work somewhat. But anyway the new drivers worked great. I need to reinstall and get them back. I tried to again and I think my problem is I am not able to change the directory to my desktop. I got there before but I can't now for the life of me. I tried:

cd ~
cd /desktop
cd /home/justin/desktop

and I just can't get there when in that "black screen"

Also is there anyway to see what driver I need to keep when it is finally working
and what driver does Ubuntu 8.04 use default for wireless, because it used to work perfect. I need a good step by step walk through all this, just because I am new to Ubuntu. I know I can get the hang of it and I really enjoy all these problems for some reasone I like to try to figure out computers even though its being a pain in the neck. My Nvidia driver is downloaded to my desktop the name is

NVIDIA-Linux-x86-180.44-pkg1.run

How do I run this? I think before I typed sudo sh NVIDIA-Linux-x86-180.44-pkg1.run
but I was able to get to my desktop in the command lines that time I can't do it again. I tried the ubuntu manual and did what it said and it wasn't working.

---

### Post by Claus7 on 2009-04-10
Hello,

really doing all these things I have lost you a little. This is not at all bad that you are trying to experiment, yet you do not give us a clear picture on what you are doing.

So to your problem now: You want to install the drivers from the nvidia web site (if I have understood correctly).

Download them somewhere. My preference would be to your Desktop. Now before you do anything else you have to make the file you downloaded executable otherwise it won't be installed no matter what.

Open a terminal and type:
```
cd ~/Desktop
```

and then:
```
chmod 755 NVIDIA-Linux-x86-180.44-pkg1.run
```

That way you have made your Nvidia_bla_bla executable. Now you cannot run it by just...running it. You have to kill your xserver first (sorry this is not my fault). In order to do so you have to type:

```
sudo /etc/init.d/gdm stop
```

now you will get a black screen. If you do not get your command prompt then type : Ctrl+Alt+F1

and navigate to your Desktop:
```
cd ~/Desktop/
```

and as root run the executable you have created:
```
sudo ./Nvidia-Linux-x86-180.44-pkg1.run
```
and provide your password.

Do exactly this steps and then report what problems you have. Otherwise I won't be able to understand what you are doing. Keep also some notes so as the next time to be able to do the same things without loosing time for unecessary steps.

EDIT: I have no idea how wireless works. Yet, I do not think that it should have any relevance with your grapics card. You might have changed something else. Perhaps someone else might be able to help you in this.

Regards!

---

### Post by jcm1107 on 2009-04-10
Ok first thanks!! I got it to install! This is how I did it with everything disabled, I opened a terninal typed:

Code:
cd ~/Desktop

Code:
chmod 755 NVIDIA-Linux-x86-180.44-pkg1.run

Code:
sudo /etc/init.d/gdm stop

this took me to the black screen but I had no command line so I hit Ctrl+Alt+F1
I then typed

Code:
cd ~/Desktop

chmod 755 NVIDIA-Linux-x86-180.44-pkg1.run

it then said an error message I think it was not a valid location
I then typed 

Code:
sudo NVIDIA-Linux-x86-180.44-pkg1.run

and it started installing and asked a few questions that I had to say ok or no it then installed and worked!!! Thanks!!!

---

### Post by jcm1107 on 2009-04-10
How do I get my commands in those boxes like you did? Just wanted to know for next time so they are easier for others to read. Thanks

---

### Post by suomalainen on 2009-04-10
Yesterday I had a smilar problem with screen resolution.


I don't know if this will help your situation but when I'm having problems with the "xorg.conf", I follow the advice listed within this file, i.e.:

"# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg"

If you look inside the xorg.conf file you'll see this statement. When I run the sudo command it has fixed my problems.

---

### Post by Claus7 on 2009-04-10
Hello,

glad you were able to solve once again the problem you were facing and be able (I think) to do the same if it arises again.

> **jcm1107 said:**
> Ok first thanks!! I got it to install! This is how I did it with everything disabled, I opened a terninal typed:....


chmod 755 NVIDIA-Linux-x86-180.44-pkg1.run

it then said an error message I think it was not a valid location
I then typed ...

You didn't have to give once again the rights for this file. If you look at your post you have changed the permissions of the file twice, which was not needed (it doesn't matter of cource, this means that it is not bad). Yet, I would advice you to see a little bit better what you did, so as to undertand exactly what those commands do. I understand that you are a new user, yet don't just copy and paste them.

> **jcm1107 said:**
> How do I get my commands in those boxes like you did? Just wanted to know for next time so they are easier for others to read. Thanks
You have to select with the mouse the text you want to be put in a box, and hit the icon on the left of #, just above the text you are writing.

> **suomalainen said:**
> Yesterday I had a smilar problem with screen resolution.


I don't know if this will help your situation but when I'm having problems with the "xorg.conf", I follow the advice listed within this file, i.e.:

"# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg"

If you look inside the xorg.conf file you'll see this statement. When I run the sudo command it has fixed my problems.

Not bad for earlier versions of ubuntu. Yet, in newer ones this command does not do the trick any more.

Regards!

---

### Post by jcm1107 on 2009-04-11
I see what you mean about me giving the file rights twice, its just that when I typed it into the terminal it did't do anything and I just thought I would try doing it again from the 'black' screen and since I put it in twice and it worked I put that on here because it is exactly how I put it in. I am seeing how these codes work a little, I was on another site and it was telling about those numbers you put in front of it were to give it read and write permissions, I know I will learn how to use this it's just I am new to having to type in commands and they have to be exact or they don't work, like I think with trying to get to desktop I was always forgeting to capitalize the D in desktop, stupid of me but hey I am new to this. Thanks for all the help I really aprieciate it and now I know how to fix this if and when it gets messed up again and mabe someone will read this with the same problem as me. THANKS!!!!!

---

### Post by jcm1107 on 2009-04-16
Found out that I don't need the new 180.44 driver! I got the 169.12 running and it is working just fine, so did the 180.44 also, but I found a better way to get my graphics driver working with my wireless, through synaptic! This is the steps exactly after installing a fresh ubuntu 8.04 and doing all the updates

1:go to synaptic and check mark nvidia-settings
also check nvidia-xconfig

2: click apply

3:go to system-administration-hardware drivers open that

4:enable nvidia accelerated graphics driver

5: after the nvidia driver gets done it will prompt for restart, so when it is finished, close the hardware drivers window and restart the computer

6: go to system-administration-nvidia x server settings and adjust resolution all you want!!!!!

---

