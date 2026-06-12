---
title: "Installing BCM94311MCG wlan mini-PCI Ubuntu 7.10 - Broadcom wifi on a HP dv9000"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by jlandaw on 2008-04-21
I'm making this Thread to Help others with the problem I had installing my BCM94311MCG wlan mini-PCI.

I have a HP dv9000 (dv9428nr) Running Ubuntu 7.10

I do believe this will work with almost all hp dv's

Everything I put in here i have taken form other thread/forums, but none were set up in a way that a noob (Beginner) could follow easily.

First we need to do a few things.

You need to have a internet connection, wired since your wifi is not working yet :)

whenever you see the command "*sudo*" you will have to enter you password (the characters will not appear as you type.)
[COLOR="DarkRed"]
Step 1[/COLOR]
[INDENT]You will need to download the drivers we will use later.
Download it[ [COLOR="Blue"]here[/COLOR]]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz"). It is free,just click the free button, and then click download via ******** (******** can be any one of the choices)[/INDENT]

[COLOR="DarkRed"]Step 2[/COLOR]
[INDENT]You do not have to download the next file, we will do later on, in the instillation.
Go [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=93482") and write down the latest stable release number. On April 21, 2008 the release  number was 1.52[/INDENT]

[COLOR="DarkRed"]Step 3[/COLOR]
[INDENT]If you enabled the restricted drivers disable them

System --> Administration --> Restricted Drivers Manager

I guess if you never tried to use them you could try before going thru this...[/INDENT]

[COLOR="DarkRed"]Step 4[/COLOR]
[INDENT]Next we need to uninstall ndiswrapper & bcm43xx-fwcutter

Open a Terminal (Applications --> Accessories --> Terminal)

[COLOR="Red"]**Copy each line into the terminal separately**[/COLOR]
(you can use ctrl+c to copy out of Firefox, but you have to use either ctrl+alt+v or shift+insert to paste into the terminal.)

```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9

sudo apt-get remove bcm43xx-fwcutter
```

The step is complete even if it does not remove anything (you may not have had those packets installed)
[/INDENT]

[COLOR="DarkRed"]Step 5[/COLOR]
[INDENT]Now you need to Blacklist the bcm43xx file

In the terminal you can put the following line and a text editor will pop up with the file we need to edit.

```
sudo gedit /etc/modprobe.d/blacklist
```

At the end add
```
blacklist bcm43xx
```
Do not put a # in front of it.
Save the file and close the editor
[/INDENT]

[COLOR="DarkRed"]Step 6[/COLOR]
[INDENT]If you are reading this from the web and you have not saved it or printed it, you may want to bookmark this page...(I always leave the page open and press shutdown. After you reboot, if you open Firefox it will ask you if you want to resort the session, click yes and you will be right back here....)

Reboot your computer,
[/INDENT]

[COLOR="DarkRed"]Step 7[/COLOR]
[INDENT]Lets get the drivers ready to use
Find the file you downloaded and move it to your home folder

your home folder is /home/[COLOR="Red"]yourusername
[/COLOR]
Just in case you missed it... [COLOR="Red"]yourusername[/COLOR] is your "username"... whatever you use to log on...
You can right click it wherever it is and then go to home from places and paste it

next open a terminal and type
```
tar -xzvf WLANBroadcom.tar.gz
```
Check and see, there should be a folder in you home folder called WLANBroadcom

you could also accomplish this by extracting the download to you home folder...[/INDENT]

[COLOR="DarkRed"]Step 8[/COLOR]
[INDENT]The next step is going to take some editing on your part, 

First type in the terminal the following```
uname -r
```and write down or copy to text editor (Application--> Accessories--> Text Editor)
the output
you should get something like;

2.6.22-14-generic
[/INDENT]

[COLOR="DarkRed"]Step 9[/COLOR]

Install ndiswrapper from source

[INDENT] Now you need to edit five things the following before you put it into the terminal

```
sudo apt-get update

sudo apt-get install build-essential

sudo apt-get install linux-headers-[COLOR="Red"]`uname -r`[/COLOR]

sudo ln -s /usr/src/linux-[COLOR="Red"]`uname -r`[/COLOR] /lib/modules/[COLOR="Red"]`uname -r`[/COLOR]/build

mkdir -p ~/bcm43xx/ndiswrapper

cd ~/bcm43xx/ndiswrapper

sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-[COLOR="Red"]1.52[/COLOR].tar.gz

tar xvzf ndiswrapper-[COLOR="Red"]1.52[/COLOR].tar.gz

cd ndiswrapper*

make distclean
make
sudo make install
```

All three 'uname -r' need to be replaced with the output you got in step 8 (no " quotes should be in the code)

ie on the third line i put 

sudo apt-get install linux-headers-2.6.22-14-generic

The other two highlighted items need to be the release number you got in step 2
If it is still 1.52 just leave them like that. [/INDENT]

[COLOR="DarkRed"]Step 10[/COLOR]
[INDENT] Now we are going to install the drivers

In the terminal type

```
cd /home/[COLOR="Red"]yourusername[/COLOR]/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```

Again [COLOR="Red"]yourusername[/COLOR] is your "username"
[/INDENT]

[COLOR="DarkRed"]Step 11[/COLOR]
[INDENT]Now we need to add ndiswrapper to the modules file
```
sudo gedit /etc/modules
```

just add the following at the end of the file and save and close it.
```
ndiswrapper
```
[/INDENT]

[COLOR="DarkRed"]Step 12[/COLOR]
[INDENT]
Enter in terminal
```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```

Now you can reboot again, and it should work.

Enjoy[/INDENT]

---

### Post by leo_rockway on 2008-04-21
As I don't believe in using ndiswrapper, I'm going to explain how to make this card work with the b43 drivers:

```

wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
../../b43-fwcutter-011/b43-fwcutter -w &#8220;$FIRMWARE_INSTALL_DIR&#8221; wl_apsta.o
```

(It might be necessary to install build-essential)

My solution uses the b43 drivers, since bcm43xx is deprecated.

There's more information about this in my blog [0]

I have been using bcm43xx in Feisty and Gutsy without a problem and now b43 in hardy, so I don't think it's necessary to use ndiswrapper at all.

[0] [http://leorockway.wordpress.com/2008/03/23/exit-gutsy-enter-hardy-ii/](http://leorockway.wordpress.com/2008/03/23/exit-gutsy-enter-hardy-ii/)

---

### Post by jlandaw on 2008-04-27
I'd love to use your method... if it would worked

I tried it and had not luck.

---

