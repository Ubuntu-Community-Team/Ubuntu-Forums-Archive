---
title: "Minimalism"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-05
I'm thinking of building a really minimal ubuntu...from the bottom up. If I use a ubuntu alternative live cd and don't install anything other than the bare essentials (Kernel Terminal etc), can I still get internet access to apt-get install stuff?
 
any advice greatlfully accepted :-)

---

### Post by snowpine on 2010-10-05
I've done this before and it is a lot of fun. :)

Here is the best how-to on the internet:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Spice Weasel on 2010-10-05
That link is nice... but SLiM (Simple Login Manager) is a much better choice for a Display/Login manager that is minimal if you find WDM too uncustomizable.

But WDM is probably user friendly with its GUI, SLiM uses a configuration text file... Depends if you feel like it or not.

---

### Post by HermanAB on 2010-10-05
Howdy,

I would start with an Ubuntu Server install and build the GUI stuff up from there.

---

### Post by bodhi.zazen on 2010-10-05
> **HermanAB said:**
> Howdy,

I would start with an Ubuntu Server install and build the GUI stuff up from there.

Naw, use the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Server CD is a larger download, includes the server kernel, and many packages you probably do not want.

(Server CD is old school or if you actually want a server).

---

### Post by Hippytaff on 2010-10-05
Thanks everyone...a project me thinks :-D

---

### Post by Hippytaff on 2010-10-05
One more thing...is it worth waiting for 10.10 before I do this?

---

### Post by NightwishFan on 2010-10-05
I would say no and use 10.04 for now. That is unless you are interested in the newer software. In my humble opinion the biggest advantage of Maverick is some of the new polish added by Canonical. (Also much better Gstreamer for playing media)

---

### Post by bodhi.zazen on 2010-10-05
> **Hippytaff said:**
> One more thing...is it worth waiting for 10.10 before I do this?

If you plan to "upgrade" , yes I would start with 10.10.

I typically consider Ubuntu as installation worthy as of the RC, YMMV.

---

### Post by Hippytaff on 2010-10-05
> I typically consider Ubuntu as installation worthy as of the RC, YMMV.

I know not what this means, but I'll take your advice anyway :-)

---

### Post by bodhi.zazen on 2010-10-05
RC = Release candidate, 1 week before the final release.

YMMV = Your Mileage May Vary

---

### Post by frenchn00b on 2010-10-05
> **Hippytaff said:**
> I'm thinking of building a really minimal ubuntu...from the bottom up. If I use a ubuntu alternative live cd and don't install anything other than the bare essentials (Kernel Terminal etc), can I still get internet access to apt-get install stuff?
 
any advice greatlfully accepted :-)

my script install the minimal, from server install, 

remove few X11 apsp if you do not need x11

```

clear 


echo " *********************************************" 
echo "Installer FVWM MAC OS X" 
echo  " Welcome to Debian / Ubuntu ! "
echo " *********************************************"

echo "Installation started of fvwm macosx $(date)"  >> /root/fvwmmacosx_installation.log


if [ "$1" = "-fstab" ] || [ "$1" = "-install" ] || [ "$1" = "--install" ]* || [ "$1" = "--fstab" ] ; then
	echo "*************"

	echo " I will configure /etc/fstab first."
	MOUNTED=`mount | grep "on /home"`
	cp /etc/fstab /root/fstab-backup

	echo " " >> /etc/fstab
	
	if  [ "$MOUNTED" = ""  ] ; then 
	echo "*************"

	echo "Plug a pendrive, wait display change, then press <ENTER>"  ; read kldsjfdsflkj
	dmesg
	echo "*************"

	printf "Enter the pendrive /dev/SDX number;  example: /dev/sda1 ; default is /dev/sdc1 :> " ;  read  SD
	[ "$SD" = "" ] && SD="sdc1"
	echo "${SD}       /media/pendrive       auto    user,rw,auto,umask=0000,uid=1000,gid=1000  0    0 has been added" >> /etc/fstab
	echo "${SD}       /media/pendrive       auto    user,rw,auto,umask=0000,uid=1000,gid=1000  0    0" 
	

	##		echo "/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0"  >> /etc/fstab
	echo "*************"
	printf "Enter the IP of the /home NFS server (you are the client to NFS server)  X:> " ;   read XP
 
	if [ "$XP" != "" ] ; then
		echo "${XP}:/home	/home	nfs	defaults	0	0 has been added to fstab"  >> /etc/fstab
		echo "${XP}:/home	/home	nfs	defaults	0	0" 
	fi
	
	echo "*************"
	printf "Enter the folder of /movies or other: (shared folder on the NFS server, you are the client) it will be into / (default: movies) :> " ;  read movies
	if [ "$movies" != "" ] ; then 
		echo "192.168.1.${XP}:/${movies}	/${movies}	nfs	defaults	0	0"  >> /etc/fstab
		echo "192.168.1.${XP}:/${movies}	/${movies}	nfs	defaults	0	0"
		mount ${movies} 
	fi
	echo "*************"

	printf "Enter username to get audio/video permissions :> "  ; read MYUSER

	mkdir /media/pendrive -p
	mkdir /${movies}
	mkdir  /home/shared

	
	mount /home
	mount ${movies}
		if [ "$MYUSER" != "" ] ; then 
			adduser $MYUSER audio 
			adduser $MYUSER video
			adduser $MYUSER cdrom 
			adduser $MYUSER plugdev 
		fi
	fi

		
	echo "*************"
	
	printf "Configuration of the /etc/fstab and first user performed. Please check the fstab."
	cat /etc/fstab

	echo "*************"
	printf "Type of install: type <ENTER> to normal or type <mini> for a minimum installation for fvwm mac os x with few extras :> " ; read INST
	printf "Press enter to install with apt-get all the packages <ENTER> "  ; read dklsfjfdsljk
	clear
	echo "Sure that the PC works flawless without bugs" 
	apt-get install  -f gpm xserver-xorg xinit xterm  fvwm aumix alsa imagemagick  trayer leafpad audacious2  rox-filer grun  abiword    x11-apps  xserver-xorg screen        feh  vim   libnotify-bin zenity  rxvt  mkisofs cdrecord  nfs-common portmap vim alsa    mencoder mplayer  xterm  file-roller    leafpad less alsa      system-config-printer unzip       mc     leafpad less alsa    linuxlogo fswebcam rsync zenity dialog eog   ssh   gftp aumix   evince    	abook eog  mplayer mutt  galeon   mc   wput      zenity   elinks   jfsutils  iceweasel aumix   elinks rtorrent  reportbug  abiword  htop portmap nfs-common ntp 
	
	apt-get install  -f -y gpm xserver-xorg xinit xterm  fvwm aumix alsa imagemagick 
	# need some emailing stuffs
	apt-get install -f -y sendmail-bin msmtp mutt fetchmail reportbug sux xscreensaver
	apt-get install -f -y conky


	echo "Now installing for a more testing debian install, more risks"
	if [ "minimum" != "$INST" ]*; then 
		apt-get install  galeon gpart gparted nmap hatari kadu gimp audacious2 amule -f -y
		apt-get -f -y install xcompmgr
		apt-get -f -y install transset-df  
		##apt-get install -f -y kspread 

	fi

	apt-get install -f -y lame 
	apt-get install -f -y libmp3lame0 ffmpeg
		
	echo " ***** INSTALLATION FINISHED ***** $(date)" 	

	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	
	echo "$(date) INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "$(date) INSTALLATION FINISHED !!!! "   > /dev/tty2

	echo "Installation finished fvwm macosx $(date)"  >> /root/fvwmmacosx_installation.log


	exit
fi


echo " "
mkdir /media/pendrive 
echo "Install the minimum required  packages" 
apt-get install fvwm aumix alsa imagemagick  trayer leafpad audacious2  rox-filer grun  abiword    x11-apps  
apt-get install habak   # has been removed from testing 
apt-get install feh conky  vim   libnotify-bin zenity  rxvt
apt-get install xserver-xorg screen
apt-get install eog mplayer mirage gimp kadu  rsync alsa
apt-get install xinit imagemagick fvwm rox-filer numlockx
apt-get install xinit xserver-xorg
apt-get install  x11-apps
apt-get install mkisofs cdrecord  nfs-common portmap vim alsa 
apt-get install  mencoder mplayer 
apt-get install xterm  file-roller
apt-get install lame  leafpad less alsa
apt-get install fetchmail sendmail-bin mutt msmtp abook
apt-get install  system-config-printer unzip
apt-get install fswebcam  rsync  
apt-get install linuxlogo


## not good :
##apt-get install dict-de-en dict



printf "\033[32m%10s\n\033[0m" "The date is now: $(date)"
echo "Installing gimp leafpad abiword hatari yes/no:"
read rep
if [ "$rep" = "yes" ] ; then
	apt-get install gimp leafpad abiword hatari mirage homebank
	apt-get install kspread  
	apt-get install iceweasel  
	apt-get install mplayer  xinit
fi

##/dev/sr0       /media/cdrom   udf,iso9660 user,noauto     0       0



```

---

