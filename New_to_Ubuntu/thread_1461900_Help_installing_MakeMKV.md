---
title: "Help installing MakeMKV"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by eggowaffles on 2010-04-24
Hey guys, pretty new to Linux/Ubuntu and would really like to become a more avid user. One thing that I can't go without though is ripping my movies. I'm currently trying to install MakeMKV ([http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)) and am having problems. I followed the steps and commands there but have yet to get a .tar.gz file to successfully install. It looked like all went well during the terminal installation but then afterwards when trying to navigate to the folder I cannot find the program anywhere and have even done searches. If anyone could tell me where that would be awesome. Thanks!

---

### Post by 2hot6ft2 on 2010-04-24
Welcome to the forum.

Most will recommend handbrake and it makes mkv files. I would suggest giving it a shot. I'll take a look at makemkv and post back unless someone does it first.

Here's the home page for it [http://handbrake.fr/](http://handbrake.fr/)

If you want it you can add it from it's PPA like this:

Installing handbrake in 9.10
Open a terminal
Applications > Accessories > Terminal
and run these one at a time
```
sudo add-apt-repository ppa:handbrake-ubuntu/ppa
```
You will have to enter your password which wont be displayed just type it in and hit Enter
```
sudo apt-get update
```
```
sudo apt-get install handbrake-gtk
```

There's also avidemux
Info from Synaptic Package Manager
> Avidemux is a free video editor designed for simple cutting, filtering and
encoding tasks. It supports many file types, including AVI, DVD compatible
MPEG files, MP4 and ASF, using a variety of codecs. Tasks can be automated
using projects, job queue and powerful scripting capabilities.
You can install it either by searching for it in
System > Administration > Synaptic Package Manager
or by using
```
sudo apt-get install avidemux
```
They will be in
Applications > Sound and Video > Handbrake
and
Applications > Sound and Video > Avidemux

---

### Post by 2hot6ft2 on 2010-04-24
I was wrong and thought the package was for arch. See post # 5 for how to install it.

---

### Post by eggowaffles on 2010-04-24
Awesome I appreciate the quick replies, good community to get into. I have worked with handbrake and that is what I use to primarily use. I do like the program a lot when I am converting videos from one format to another however when I do DVD ripping I have found to have much better luck with quality and speed when using MakeMKV and it remove copy right protection. But I will definitely be installing handbrake on here as well so still a great tip because it's that many more commands I got to learn.

And sorry, what did you mean its for arch?

---

### Post by 2hot6ft2 on 2010-04-25
> **eggowaffles said:**
> 
And sorry, what did you mean its for arch?
I was wrong. I thought it was for Arch linux.

I was busy doing some things on another forum so sorry for the delay.

I did some searching and managed to install it so here's how. Actually it's the same as on the download page but I found one that made it more clear.

Download both of these and save them to your Downloads folder
[MakeMKV Binaries download]("http://www.makemkv.com/download/makemkv_v1.5.4_beta_bin.tar.gz")
[MakeMKV Source download]("http://www.makemkv.com/download/makemkv_v1.5.4_beta_oss.tar.gz")

then
Go to
Places > Downloads
Right click on them both one at a time and select Extract here, then
Open a terminal
Applications > Accessories > Terminal
and run these
```
sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev
```
```
cd ~/Downloads/makemkv_v1.5.4_beta_oss
```
```
make -f makefile.linux
```
it will take a while so wait for it to return to the prompt which will end with
makemkv_v1.5.4_beta_oss$
```
sudo make -f makefile.linux install
```
```
cd ~/Downloads/makemkv_v1.5.4_beta_bin
```
```
make -f makefile.linux
```
That brings up the terms of use. Use the down arrow key to scroll thru them to the bottom and hit the q (Q) hey to return to the terminal. Type in yes and hit Enter to accept them.
```
sudo make -f makefile.linux install
```
All done installing. Now you can start it with
```
makemkv
```
It doesn't create a menu item for it so to create one.
In the top left panel next to Applications
Right click on the Ubuntu Logo and select Edit Menus
In the left side select Sound & Video and click anywhere in the right side.

On the right click on New Item
Fill it in like this
Type: Application
Name: MakeMKV
Command: /usr/bin/makemkv
Comment: Can be whatever you want like DVD Ripper

You can click on the launcher picture and pick another one of your choice.
Click OK
All done now it's in the menu in
Applications > Sound & Video > MakeMKV

Here's something else you may find interesting.
[Ubuntu Help pages BluRay And HDDVD]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD")

Have fun
:guitar:

---

### Post by eggowaffles on 2010-04-25
Omg man thank you so much! You are awesome! I love the step by step and really appreciate how quick you have been with the help. Really look forward to learning more and thanks for showing me how to add it to the applications menu. Are there any books or anything you recommend for learning the ins and outs of linux?

---

### Post by Zookalicious on 2010-08-03
Great tutorial 2hot! This works very nicely for me so far on two BR's (Planet Terror and Law Abiding Citizen). 

Too bad it's shareware :/ Anyone know of a good open source alternative?

---

### Post by lovswr on 2010-12-28
2hot you are a freaken genius!  :popcorn:  The community need more users like you.  My hat is off & Kudos Sir.

---

### Post by myth01 on 2011-01-04
Really really good guide 2hot.  There should be more like these, perfectly aimed at the non-geek.

---

### Post by newtonuk on 2011-02-16
Thank you for the walk through!

It still amazes me as a very casual linux user that people still have to go through this to make things work!

I also found this link to using the correct icon if this helps anyone:

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=544](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=544)

BR

---

### Post by bigbadbradman on 2011-02-17
So I installed v1.6.2. How do I upgrade to v1.6.5?

---

### Post by handband2 on 2011-04-13
Here is something that I use to install MakeMKV:
```

## ** UPDATE ** to newest version - Download Files - http://www.makemkv.com/download/
wget http://www.makemkv.com/download/makemkv_v1.6.7_bin.tar.gz
wget http://www.makemkv.com/download/makemkv_v1.6.7_oss.tar.gz

## Install required packages on Ubuntu
sudo apt-get install libgl1-mesa-dev
sudo apt-get install build-essential libc6-dev libssl-dev libqt4-dev

## Unzip Files and Remove tarballs
tar -xvvf makemkv*oss.tar.gz
tar -xvvf makemkv*bin.tar.gz
rm makemkv*oss.tar.gz
rm makemkv*bin.tar.gz

## Build OSS and BIN
cd makemkv*_oss/
make -f makefile.linux
sudo make -f makefile.linux install
cd ../makemkv*_bin/
make -f makefile.linux
sudo make -f makefile.linux install
cd ..

## Copy Icons & Create Menu
sudo cp -r makemkv*oss/makemkvgui/src/img/ /usr/share/pixmaps/makemkv

sudo cat > /usr/share/applications/makemkv.desktop << EOB
[Desktop Entry]
Name=MakeMKV
Comment=Convert Blu-Ray and DVD to MKV
Type=Application
Exec=/usr/bin/makemkv
Icon=/usr/share/pixmaps/makemkv/64/mkv_icon.png
Terminal=false
Categories=AudioVideo;Audio;Video;
EOB

## Remove Directories
sudo rm -r makemkv*_oss/
sudo rm -r makemkv*_bin/

```

---

### Post by philipg on 2012-03-20
instructions for v1.7.2 install [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

---

### Post by handband2 on 2012-03-24
Here is a good site for MakeMKV:
[https://www.ebower.com/docs/ubuntu-bluray/#MakeMKV](https://www.ebower.com/docs/ubuntu-bluray/#MakeMKV)

---

### Post by twipley on 2012-04-25
Thanks for the inspiration, handband2.

I am using something similar to install MakeMKV:

```
# first off, download both the binary and the source packages
# over at:	http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224

# then, this script file, placed into the same folder as downloaded package files, is to be "ran in terminal;"

sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev

tar -xf makemkv*oss.tar.gz && tar -xf makemkv*bin.tar.gz

cd ./makemkv*_oss
make -f makefile.linux && sudo make -f makefile.linux install

cd ../makemkv*_bin
make -f makefile.linux && sudo make -f makefile.linux install

cd ..
sudo rm -r makemkv*_oss && sudo rm -r makemkv*_bin

```

---

### Post by handband2 on 2012-05-03
Here is the new way I install MakeMKV from [[COLOR="Blue"]**eBower.com**[/COLOR]]("https://www.ebower.com/docs/ubuntu-bluray/"):
 
[SIZE="2"]**Repository Install**[/SIZE]
```
sudo add-apt-repository ppa:ubuntu-ebower/ebower
sudo apt-get update
sudo apt-get install makemkv-install
sudo makemkv-install 1.7.4
```

[SIZE="2"]**Manual Install**[/SIZE]
```
mkdir makemkv
cd makemkv
wget https://www.ebower.com/docs/ubuntu-bluray/makemkv-install
chmod +x makemkv-install
sh ./makemkv-install 1.7.4
```

Activation key for Beta users:
[http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053](http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053)

---

### Post by andrew.46 on 2012-05-03
It is a little aside of the point of this thread but some might be interested to know that it is now possible to watch non-bd+ blurays directly with either vlc or MPlayer rather than ripping to disk or streaming through MakeMKV.

---

