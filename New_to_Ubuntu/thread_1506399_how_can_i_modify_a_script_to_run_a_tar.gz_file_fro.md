---
title: "how can i modify a script to run a tar.gz file from my local hard drive"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by mbuotidem on 2010-06-10
Hi, i'm new to Ubuntu and trying to convince my users to use it. However, i keep getting complaints about the interface and i went researching on how to give my Ubuntu a windows 7-like look and i stumbled on a site that has a script that does just that. 


well, unfortunately, my mobile broadband connection keeps cutting so a part in the script that needed to download a file could not download a file. When i got better internet, i downloaded the file.

I am hoping that i could edit the script to get the file from my hard drive instead of going to the internet to get it. 

here is the part of the script, i believe is involved:

```
# Action 1 - Get the theme tarball downloaded and extracted
wget http://web.lib.sun.ac.za/ubuntu/files/help/theme/gnome/win7.tar.gz
tar -xzvf $HOME/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

```

I need to redirect it to: /home/mbuotidem/Downloads/win7/win7.tar.gz 

which is where my downloaded copy of the file is.

please how do i do this?:confused:

i need a bit detailed instructions because i know nothing about scripting or programming.

---

### Post by ibuclaw on 2010-06-10
> **mbuotidem said:**
> 
```
# Action 1 - Get the theme tarball downloaded and extracted
wget http://web.lib.sun.ac.za/ubuntu/files/help/theme/gnome/win7.tar.gz
tar -xzvf $HOME/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

```

I need to redirect it to: /home/mbuotidem/Downloads/win7/win7.tar.gz 

which is where my downloaded copy of the file is.

please how do i do this?:confused:

i need a bit detailed instructions because i know nothing about scripting or programming.

Firstly, wget has a command switch "**-O**", used to tell the wprogram where to write the downloaded content.

Secondly, you cannot assume that the following directory already exists - $HOME/Downloads/win7 - so is probably best to create it using 'mkdir'

Lastly, change the the file in the tar extract command.
```

mkdir -p $HOME/Downloads/win7
wget http://web.lib.sun.ac.za/ubuntu/files/help/theme/gnome/win7.tar.gz -O $HOME/Downloads/win7/win7.tar.gz
tar -xzvf $HOME/Downloads/win7/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

```
Et Voila.

Regards
Iain

---

### Post by rsmitty on 2010-06-10
Seems to me that you already have the file stored on your hard drive. If that's the case, all you need to do is get rid of the whole wget line and change the path of the tar command. This results in:
 
```

# Action 1 - Get the theme tarball downloaded and extracted
tar -xzvf $HOME/mbuotidem/Downloads/win7/win7.tar.gz 
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

```
 
I'm not at a Ubuntu machine to test, but that seems right.

---

### Post by da burger on 2010-06-10
Without seeing the rest of the script I can't be sure but the script may assume that the file is in a certain place. So I would advise that you move the tar.gz to your home directory ```
mv /home/mbuotidem/Downloads/win7/win7.tar.gz $HOME
``` then just remove the wget line (which does the download).

So change that part of the script to ```
# Action 1 - Get the theme tarball downloaded and extracted
mv mv /home/mbuotidem/Downloads/win7/win7.tar.gz $HOME
tar -xzvf $HOME/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG
```

If anyone fancies correcting me on any of that please do.

---

### Post by sgosnell on 2010-06-10
Or just right-click on the desktop, select Change Desktop Background, click on the Theme tab, then Install, and navigate to the file, then confirm the install.  It will automatically install the theme and ask if you want to start using it.  You don't need a terminal to install themes, in fact that's the hardest way.

---

### Post by mbuotidem on 2010-06-11
> Secondly, you cannot assume that the following directory already exists - $HOME/Downloads/win7 - so is probably best to create it using 'mkdir'


First off, Thanks everyone for your replies. But Ibuclaw, it seems you did not really understand my post. I am not assuming that the directory exists. I already created it and it is in existence.

As rsmitty says, i already have the file on my hard drive. I just need to tell the script that it shouldn't bother to download it, but instead pick the file from my hard drive. 

That said, i tried your script and it tried to get the file from the web so i had to quit it.

I tried your code, rsmitty, but it didn't succeed. It returned an error.

I also tried da burger's suggestion but it also returned an error. Maybe i need to provide more information, so here is the entire script at the end of my post.

I also tried your suggestion, sgosnell but it didn't work. I think that is because there are a lot of other things that the script will do which will enable the theme to work.

Ok, enough said, here is the script's code:
```

#!/bin/bash
# After a clean Ubuntu installation this script installs the Win7 theme.
# It installs all the Windows 7 theme files globally so that they are available to all users.
# It sets up a Gnome Windows 7 theme script.
# It installs software to make Ubuntu on campus "fully loaded".

# Setup variables
RELEASE=`lsb_release -cs`
LOG="$HOME/.win7-setup.log"
OFF_CAMPUS="Y"
ARCH=`uname -m`

# Prep 1 - Remove previous theme tarball and folder
if [ -d $HOME/win7 ] ; then
	rm -rf $HOME/win7
fi
if [ -e $HOME/win7.tar.gz ] ; then
	rm -f $HOME/win7.tar.gz
fi

# Prep 2 - Backup gconf settings
tar -f win7-uninstall.tar.gz -cvz $HOME/.gconf
clear

# Check 1 - Is Zenity installed ?
if [ -x /usr/bin/zenity ] ; then
	echo "Zenity  installed: `date`." >> $LOG
	zenity --info \
	--width=600 \
	--no-wrap \
	--title="Windows 7 Theme Setup" \
	--text="The win7 theme installation will start now.\n\nPlease maxmise and watch the terminal in case you are needed to answer questions."
	else
	clear
	echo "Please install zenity."
	sleep 2
	exit 1
fi

# Check 2 - Is the system on the campus network ?
sudo ifconfig | grep "146.232"
if [ $? == 0 ] ; then
	OFF_CAMPUS="N"
	echo "System is on campus: `date`." >> $LOG
	else
	OFF_CAMPUS="Y"
	echo "System is off campus: `date`." >> $LOG
fi

# Check 3 - If on campus can we ping ftp.sun.ac.za
if [ $OFF_CAMPUS = "N" ] ; then
	echo "Checking network connection to campus ftp server."
	sleep 1
	ping -c 2 ftp.sun.ac.za
	if [ $? == 0 ] ; then 
		echo "ftp.sun.ac.za ping OK: `date`." >> $LOG
		else
		echo "ftp.sun.ac.za ping failed: `date`." >> $LOG
		zenity --error --title="Windows 7 Theme Setup" --text="Network error.\n\nPlease check network connection and proxy settings.\n\nAborting installation."
		exit 1
	fi
	else
	echo "No need to check campus ftp ping. The system is off campus." >> $LOG
fi

# Check 4 - Ubuntu release version
if [ ! $RELEASE == "lucid" ] ; then
	zenity --info --title="Windows 7 Theme Setup" --text="This theme only works with Ubuntu 10.04 LTS."
	echo "Unsupported $RELEASE: `date`." >> $LOG
	exit 1
	else
	echo "$RELEASE Ok: `date`." >> $LOG
fi

# Check 5 - Desktop session
if [ $DESKTOP_SESSION = "gnome" ] ; then
	echo "Gnome desktop OK: `date`." >> $LOG
	else
	zenity --info --title="Windows 7 Theme Setup" --text="Please use the Gnome desktop for the Win7 theme installation."
	echo "Gnome desktop not OK: `date`." >> $LOG
	sleep 2
	exit 1
fi

# Check 6 - Get installation permission
zenity --width=600 --no-wrap --question --title="Windows 7 Theme Setup" --text="All Win 7 theme checks are complete.\n\nAre you sure you want to continue ?\n\nClick No to cancel or Yes to continue."
if [ $? == 0 ] ; then
	echo "Win7 installation accepted by $USER: `date`." >> $LOG
	else
	echo "Win7 installation refused by $USER: `date`." >> $LOG
	clear
	exit 1
fi	


# Action 1 - Get the theme tarball downloaded and extracted
mkdir -p $HOME/Downloads/win7
wget http://web.lib.sun.ac.za/ubuntu/files/help/theme/gnome/win7.tar.gz -O $HOME/Downloads/win7/win7.tar.gz
tar -xzvf $HOME/Downloads/win7/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

# Action 2 - Setup software sources
sudo rm -f /var/lib/dpkg/lock
sudo rm -f /var/lib/apt/lists/lock
sudo dpkg --configure -a
if [ $OFF_CAMPUS = "N" ] ; then
	## On campus sofware update
	wget http://web.lib.sun.ac.za/ubuntu/files/deb/ubuntu-za-maties-$RELEASE.deb
	sudo dpkg -i ubuntu-za-maties-$RELEASE.deb
	sudo cp /etc/apt/sources.list.d/*.list /tmp/
	sudo rm -f /etc/apt/sources.list.d/*.list
	zenity --info --title="Windows 7 Theme Setup" --text="Your system software will be updated first, press Ok to continue."
	gconftool-2 -s /apps/update-notifier/auto_launch --type bool false
	sudo apt-get update
	sudo update-manager
	gconftool-2 -s /apps/update-notifier/auto_launch --type bool true
	gconftool-2 -s /apps/update-notifier/regular_auto_launch_interval --type int 0
	sudo cp /tmp/*.list /etc/apt/sources.list.d/
	echo "Maties Ubuntu software sources installed: `date`." >> $LOG
	else
	## Off campus sofware update
	zenity --info --title="Windows 7 Theme Setup" --text="Your system software will be updated first, press Ok to continue."
	gconftool-2 -s /apps/update-notifier/auto_launch --type bool false
	sudo apt-get update
	sudo update-manager
	gconftool-2 -s /apps/update-notifier/auto_launch --type bool true
	gconftool-2 -s /apps/update-notifier/regular_auto_launch_interval --type int 0
	echo "Using original installed Ubuntu software sources: `date`." >> $LOG	
fi

# Action 3 - Install required software
if [ $ARCH = "x86_64" ] ; then
	sudo aptitude install libc6-i386 ia32-libs
	echo "Installed 32 bit libraries for 64 bit system: `date`." >> $LOG
fi

sudo apt-get --yes install \
davmail \
emerald \
evolution-mapi \
lightning-extension \
ntp \
python \
python-software-properties \
python-xdg \
python-cairo \
python-gconf \
python-xlib \
thunderbird
echo "Installed required win7 theme software: `date`." >> $LOG

# Action 4 - Install theme software

## Install Gnomenu
sudo apt-get --yes --force-yes remove gnomenu
sudo dpkg -i $HOME/win7/debs/gnomenu_all.deb
echo "Installed Gnomenu software: `date`." >> $LOG

## Install Talika
if [ $ARCH = "x86_64" ] ; then
	sudo apt-get --yes --force-yes remove talika
	sudo dpkg -i $HOME/win7/debs/talika_amd64.deb
	echo "Installed 64 bit Talika software: `date`." >> $LOG
	else
	sudo apt-get --yes --force-yes remove talika
	sudo dpkg -i $HOME/win7/debs/talika_i386.deb
	echo "Installed 32 bit Talika software: `date`." >> $LOG
fi

## Install gtk2-oria engine
if [ $ARCH = "x86_64" ] ; then
	sudo apt-get --yes --force-yes remove gtk2-engine-oria-amd64
	sudo dpkg -i $HOME/win7/debs/gtk2-engine-oria_amd64.deb
	echo "Installed 64 bit gtk2-engine-oria software: `date`." >> $LOG
	else
	sudo apt-get --yes --force-yes remove gtk2-engine-oria-i386
	sudo dpkg -i $HOME/win7/debs/gtk2-engine-oria_i386.deb
	echo "Installed 32 bit gtk2-engine-oria software: `date`." >> $LOG
fi

# Action 5 - Install theme files
cd $HOME/win7

sudo tar -C /usr/share/icons/ -xzvf win7-icons.tar.gz
sudo chown -R root.root /usr/share/icons/
sudo chmod -R 0777 /usr/share/icons/

sudo tar -C /usr/share/fonts/truetype -xzvf win7-fonts.tar.gz
sudo chown -R root.root /usr/share/fonts/truetype/
sudo chmod -R 0777 /usr/share/fonts/truetype/

sudo tar -C /usr/share/sounds/ -xzvf win7-sounds.tar.gz
sudo chown -R root.root /usr/share/sounds/
sudo chmod -R 0777 /usr/share/sounds/

sudo tar -C /usr/share/gnomenu/Themes/Menu/ -xzvf gnomenu/menu/win7.tar.gz
sudo chown -R root.root /usr/share/gnomenu/Themes/Menu/
sudo chmod -R 0777 /usr/share/gnomenu/Themes/Menu/

sudo tar -C /usr/share/gnomenu/Themes/Button/ -xzvf gnomenu/button/win7.tar.gz
sudo chown -R root.root /usr/share/gnomenu/Themes/Button/
sudo chmod -R 0777 /usr/share/gnomenu/Themes/Button/

sudo tar -C /usr/share/gnomenu/Themes/Icon/ -xzvf gnomenu/icon/win7.tar.gz
sudo chown -R root.root /usr/share/gnomenu/Themes/Icon/
sudo chmod -R 0777 /usr/share/gnomenu/Themes/Icon/

sudo tar -C /usr/share/gnomenu/Themes/Sound/ -xzvf gnomenu/sound/win7.tar.gz
sudo chown -R root.root /usr/share/gnomenu/Themes/Sound/
sudo chmod -R 0777 /usr/share/gnomenu/Themes/Sound/

sudo tar -C /usr/share/themes/ -xzvf win7-gtk.tar.gz
sudo chown -R root.root /usr/share/themes/
sudo chmod -R 0777 /usr/share/themes/

sudo cp backgrounds/* /usr/share/backgrounds
sudo chown -R root.root /usr/share/backgrounds/
sudo chmod -R 0777 /usr/share/backgrounds/

sudo tar -C /usr/local/etc/ -xzvf win7-emerald.tar.gz
sudo chown -R root.root /usr/local/etc/
sudo chmod -R 0777 /usr/local/etc/

sudo cp -R /usr/local/etc/win7-emerald/win7/ /usr/share/emerald/theme/
sudo chown -R root.root /usr/share/emerald/theme/
sudo chmod -R 0777 /usr/share/emerald/theme/

sudo tar -C /usr/local/etc/ -xzvf win7-theme.tar.gz
sudo chown -R root.root /usr/local/etc/
sudo chmod -R 0777 /usr/local/etc/

sudo cp $HOME/win7/setup-win7-theme.sh /usr/local/bin/setup-win7-theme
sudo chmod 0755 /usr/local/bin/setup-win7-theme
sudo chown root.root /usr/local/bin/setup-win7-theme
echo "Installed win7 theme files: `date`." >> $LOG

# Action 6 - Inform user of win7 setup readme file
cp $HOME/win7/win7-read-me.html $HOME/Desktop/
zenity --info \
--width=450 \
--no-wrap \
--title="Windows 7 Theme Setup" \
--text="The Windows 7 theme files have been installed.\n\nAn instruction web page has been copied to your desktop folder.\n\nDouble click on it to find out how to setup the Windows 7 theme for your Ubuntu desktop."

## Ask the user about installing extra software ##
zenity --question \
--width=600 \
--no-wrap \
--title="Windows 7 Theme Setup" \
--text="The installation can continue to install extra software to make Ubuntu fully loaded.\n\nThis is not essential for the Windows 7 theme setup.\n\nClick No to cancel or Yes to continue."
if [ $? == 0 ] ; then
	echo "Extra software installation accepted: `date`." >> $LOG
	rm -f $HOME/win7-setup.sh
	sudo chmod 0755 $HOME/win7/install-extra-software.sh	
	sudo $HOME/win7/install-extra-software.sh
	exit 0
	else
	echo "Extra software installation refused: `date`." >> $LOG
	rm -f $HOME/win7-setup.sh
	exit 0
fi
```

Thanks all.

---

### Post by ibuclaw on 2010-06-11
> **mbuotidem said:**
> First off, Thanks everyone for your replies. But Ibuclaw, it seems you did not really understand my post. I am not assuming that the directory exists. I already created it and it is in existence.


OK, I re-read it.

I gauge that you already have the file downloaded then, and you want to distribute it to your "users" from your own workstation?

Question, are you all in the same network?

---

### Post by da burger on 2010-06-13
Hi,
I just noticed an error in my version of the script. Where it says ```
mv mv /home/mbuotidem/Downloads/win7/win7.tar.gz $HOME 
```Should actually be ```
mv /home/mbuotidem/Downloads/win7/win7.tar.gz $HOME
```. I accidentally typed mv twice. 
If that doesn't work can you post the exact error message.
PS I'm just about to read the script and see if I can work out what it does.

EDIT Just read the script and realized I made a few mistakes.
These modifications to the script should get it working.

1. Remove the following lines from #prep 1
```
if [ -e $HOME/win7.tar.gz ] ; then
	rm -f $HOME/win7.tar.gz
fi
```

2. Change #action 1 to the following
```

mkdir -p $HOME/Downloads/win7
mv /home/mbuotidem/Downloads/win7/win7.tar.gz $HOME/Downloads/win7
tar -xzvf $HOME/Downloads/win7/win7.tar.gz
echo "Downloaded and extracted theme tarball: `date`." >> $LOG

```

I'm assuming the tar.gz is still in /home/mbuotidem/Downloads/win7/win7.tar.gz.

If that returns an error please post it exactly.

Angus

---

### Post by d3v1150m471c on 2010-06-13
you could always try kubuntu, also. It's a bit harder on the system resources but definitely worth it. Great environment and widgets.

---

### Post by sgosnell on 2010-06-13
Again, modifying scripts and running things from the command line is the hard way to do this.  Ubuntu provides a nifty GUI that's easy to use.  Just right-click on the desktop, select Change Desktop Background, and install the theme you want by navigating to it, without even needing to extract the .gz file, as long as it's a proper theme file.  The OP's users would almost certainly prefer to do it this way, Windows users don't want to even think about using any command-line stuff.

---

### Post by mbuotidem on 2010-06-14
:guitar:thanks da burger! your code worked **perfectly**.i have attached a screenshot of my new desktop!

d3v1150m471c, i will try out Kubuntu soon. You see, i plan to introduce my linux, esp. Ubuntu to my alma mater since i have a measure of influence with the it staff there. But getting this to work was key because it will make transition very easy for the students and though they will eventually discover that there are not using windows, they will have already gotten used to it. When i get around to doing that, i will try Kubuntu.


sgnosell, as i believe i said earlier, i tried your method but it didn't work because there are a lot of other things the script has to do i guess! my users are not gonna have to worry about using the terminal because i will deploy the quick fix on my own!

and you may be a bit wrong about windows users not wanting to use terminal. i am a former windows user, knew about linux for a long time but didn't bother until i got fed up with the instability of my xp system and was unwilling to upgrade because my pocket was tight. and im enjoying using the terminal even though i often get "this command does not exist" and other such errors. heck! im even thinking of going into programming, learning something so that i could contribute to the community. If i were using windows, i would probably use something like visual studio as an ide but i don't know what to use for ubuntu. maybe i need to post a question on this in the forum.

once again, thanks Angus

---

### Post by sgosnell on 2010-06-14
What doesn't work?  What happens if you try to install the theme from the desktop?

I'm sure there are a few Windows users who aren't afraid of the command line, but they are few and far between.

---

