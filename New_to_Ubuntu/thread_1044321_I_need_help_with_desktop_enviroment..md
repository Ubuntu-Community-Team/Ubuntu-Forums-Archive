---
title: "I need help with desktop enviroment."
date: 2009-01-19
forum: New to Ubuntu
---

### Post by ds dude on 2009-01-19
Hello, I'm new here to Hi All!!

I'm learning about Ubuntu and what to be apart of it.  I want it to grow and to be successful (already is).

How do I install KDE4 on my desktop? I want to try it out and learn about it.  Also, I have Linux on my flash drive, if I install KDE4 on it, will it save?  I read the current issue of Linux magazine and found out that 8.10 Live has a feature of saving information on it. Is this true?

Also, I would like to research and find bugs/glitches, I really feel like this can be a hobby for me.

Thank you, I'll try to be active.  :)

EDIT: My computer is only 2 years old.  I put my flash drive in my computer, but it doesn't recognize it right away.  And I can't go into the boot menu? Does anyone know how to fix this problem?  I'm on a Sony VAIO VGC-V620G.

---

### Post by davideotape on 2009-01-19
First of all, I assume you are using the Gnome desktop environment. This comes with the standard distrubution of Ubuntu, and most people I know use it. If so, then you want to look here: [https://help.ubuntu.com/community/InstallingKDE]("https://help.ubuntu.com/community/InstallingKDE")

As far as I'm aware, if you type this:

```
sudo apt-get kubuntu-desktop
```

into your terminal, it should do the rest for you. If you ever want to go back to Gnome after installing KDE, you can change the session from the login window.

Hope that helps :)

David

---

### Post by tarps87 on 2009-01-19
You will probably need to enable the usb in the bios, to do this you will need to enter the bios settings using the key or key combinations displayed when the computer boots.
(Try F2 or F3)

If you want to use KDE you can download Kubuntu or install it on Ubuntu by running the command
```
sudo apt-get install kubuntu-desktop
```

The live cd can not save information but you can create a live usb version that can, this can be done for either the Ubuntu or Kubuntu live cd

---

### Post by mlentink on 2009-01-19
Any particular reason to run it off of a flash-drive?

If you really want to experience Ubuntu, do a full install, preferably in a dual-boot setup or through Wubi.

---

### Post by ds dude on 2009-01-19
Thank you for all your help.  I have ubuntu on my laptop with full install.  I just had a flash drive laying around, and thought it would be cool to have Linux on it.  

I'm running Linux through the desktop as I type, so I fixed it, thanks to tarps87.  I don't have permission to use the terminal, what could be the cause of this?

---

### Post by emarkd on 2009-01-19
> **ds dude said:**
> I don't have permission to use the terminal

What does this mean?  Are you getting an error when you click "terminal" from the applications menu?

---

### Post by meindian523 on 2009-01-19
You have permission to use the terminal,but you have to enter your own password(if you are the only user on your system for system sensitive tasks such as installing applications)

If you are not the only user on your system,and not the first user of the system either,then you need to login to the account which was first created(the administrator account) and run the command given from terminal from there.

Or,preferably,ask the owner of the administration account to install kubuntu-desktop for you.Refer the For newbies link in my signature.

---

### Post by tarps87 on 2009-01-19
The command sudo gives you root/admin privileges, you should be able to type you password in and run the command.
If you mean you can't open the terminal this is something different, try pressing ctrl+alt+F2

---

### Post by ds dude on 2009-01-19
Okay, it doesn't seem I have space for kde4.  I'm on 2gig SanDisk cruzer.  When you get a menu saying, Gdm, Kdm on it.  Which one do I click?


EDIT: Well I have kde4 installed, but not the gdm or kdm.  When I try to install to kde4 again, it says invalid operation.

---

### Post by emarkd on 2009-01-19
Gdm = Gnome which is the default Ubuntu environment
Kdm = KDE which is the default Kubuntu environment

Your choice.

---

### Post by meindian523 on 2009-01-19
GDM if you want the dafault GNOME environment,KDM if you want KDE.

EDIT: emarkd got there first.

---

### Post by snowpine on 2009-01-19
Check out Kubuntu. It is Ubuntu with KDE, and should fit on your 2gb flash drive.

---

### Post by ds dude on 2009-01-19
Oh great, well how do I get back to that menu?  I try to reinstall kde4 but it says invalid operation.

---

### Post by meindian523 on 2009-01-19
ds dude:
Please post a screenshot of where you are stuck,if that's possible.And if I'm right about where you are,you should be able to get back to the login screen by pressing Ctrl+Alt+Backspace.

---

### Post by ds dude on 2009-01-19
I'm so sorry if I'm making this harder than it is.:(

Here is a screen shot.

---

### Post by oldos2er on 2009-01-19
You need to run "sudo dpkg --configure -a" in a terminal.

---

### Post by ds dude on 2009-01-19
Yeah, but I need to be a superuser, how do I do that?

I tried googling, but I don't think I'm doing it right.

EDIT: BTW, ubuntu on the USB is not saving changes.  I googled, and it said I have to reinstall it with some program?  Is this true? Or is there an easier way to do this.

---

### Post by snowpine on 2009-01-19
> **ds dude said:**
> Yeah, but I need to be a superuser, how do I do that?

I tried googling, but I don't think I'm doing it right.

Typing 'sudo' at the beginning of a terminal command gives you temporary superuser rights.

```

sudo dpkg --configure -a

```

---

### Post by ds dude on 2009-01-19
Lol, when I do that then nothing happens, just gives me a blank line.  It's as if it doesn't respond or something.

EDIT: Hold on, I'm trying to fix it. I think I got it working.

EDIT2: It says something is taking place in the terminal, then I was able to type in it, so I went to session and didn't see kde4.

Should I have waited? Because it looked like it was done.

---

### Post by snowpine on 2009-01-19
Now that you've reconfigured dpkg, you can try installing KDE again.

Or, you can start fresh with Kubuntu as I originally suggested, since your drive is so small. :)

---

### Post by ds dude on 2009-01-19
Well I'm really learning a lot right now.  I don't want to hassle to the download.

Okay, snowpine, I tried to type "kdm" in the terminal, but it says that I must be at root user.  So I type "sudo -i" and then type in the terminal "kdm."  When I do this I get "Invalid operation kubuntu-desktop."

---

### Post by snowpine on 2009-01-19
Right, so now you can do this:

```
sudo apt-get install kubuntu-desktop
```

You already tried this, but it failed the first time, right?
Now that you've (hopefully) resolved the error message, you can try again...

(edit) ps type 'sudo kdm' to run kdm as "the root user".

---

### Post by ds dude on 2009-01-19
Yeah, I thought I had kde4, because in the terminal is said something about "ls is now taking place..." then a line down it says "root@ubuntu~$" you know the admin and stuff.  So I thought it was completed, but it wasn't.  So I need to try to install kde4 again, let it overwrite whatever it needs to overwrite, then whatever is left out, it will put in, because I X'ed out of the terminal.

EDIT: Snowpine, I'm installing it right now, do you have msn? Or pigdin?  I'll add you! :)

Okay, found the big problem, I don't have space on my drive, probably because I kept installing kde4 so many times.  Anyway to delete all those installations?

---

### Post by ds dude on 2009-01-19
Okay, i have installed kde4, this is what the process was:

The following extra packages will be installed:
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data khelpcenter4 libaudio2 libclucene0ldbl libmysqlclient15off
  libphonon4 libpq5 libqimageblitz4 libqt4-dbus libqt4-designer libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0
  mysql-common phonon phonon-backend-gstreamer qt4-qtconfig raptor-utils
  redland-utils soprano-daemon
Suggested packages:
  kdebase kdepasswd nas libqt4-dev phonon-backend-xine phonon-backend-vlc
  phonon-backend-mplayer
The following NEW packages will be installed:
  kde-icons-oxygen kdebase-runtime kdebase-runtime-bin-kde4
  kdebase-runtime-data kdebase-runtime-data-common kdelibs-bin kdelibs5
  kdelibs5-data kdm khelpcenter4 libaudio2 libclucene0ldbl libmysqlclient15off
  libphonon4 libpq5 libqimageblitz4 libqt4-dbus libqt4-designer libqt4-network
  libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-svg libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0
  libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0
  mysql-common phonon phonon-backend-gstreamer qt4-qtconfig raptor-utils
  redland-utils soprano-daemon
0 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 50.6MB of archives.
After this operation, 137MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kde-icons-oxygen 4:4.1.2-0ubuntu6 [13.8MB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqtcore4 4.4.3-0ubuntu1 [2085kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-xml 4.4.3-0ubuntu1 [112kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-dbus 4.4.3-0ubuntu1 [216kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libaudio2 1.9.1-4 [80.3kB]       
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqtgui4 4.4.3-0ubuntu1 [4286kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libphonon4 4:4.2.0-0ubuntu1 [121kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-script 4.4.3-0ubuntu1 [420kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-designer 4.4.3-0ubuntu1 [2073kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-network 4.4.3-0ubuntu1 [437kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-sql 4.4.3-0ubuntu1 [109kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-qt3support 4.4.3-0ubuntu1 [1366kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-svg 4.4.3-0ubuntu1 [158kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libclucene0ldbl 0.9.20-3 [376kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libraptor1 1.4.17-1 [155kB]     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main mysql-common 5.0.67-0ubuntu6 [60.7kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libmysqlclient15off 5.0.67-0ubuntu6 [1841kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libpq5 8.3.4-2.2 [281kB]        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main librasqal0 0.9.15-2 [102kB]     
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main librdf0 1.0.7-1 [128kB]         
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main soprano-daemon 2.1.1+dfsg.1-0ubuntu1 [144kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libsoprano4 2.1.1+dfsg.1-0ubuntu1 [492kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libstreams0 0.5.11-1ubuntu2 [92.8kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libstreamanalyzer0 0.5.11-1ubuntu2 [282kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-opengl 4.4.3-0ubuntu1 [161kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main phonon-backend-gstreamer 4:4.2.0-0ubuntu1 [92.1kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main phonon 4:4.2.0-0ubuntu1 [7104B] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdelibs5-data 4:4.1.2-0ubuntu10 [3107kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdelibs-bin 4:4.1.2-0ubuntu10 [372kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdelibs5 4:4.1.2-0ubuntu10 [9518kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libstrigiqtdbusclient0 0.5.11-1ubuntu2 [46.3kB]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdebase-runtime-bin-kde4 4:4.1.2-0ubuntu6 [65.8kB]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdebase-runtime-data-common 4:4.1.2-0ubuntu6 [349kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdebase-runtime-data 4:4.1.2-0ubuntu6 [3095kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdebase-runtime 4:4.1.2-0ubuntu6 [1565kB]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqimageblitz4 1:0.0.4-4 [60.5kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main kdm 4:4.1.2-0ubuntu12 [861kB]   
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main khelpcenter4 4:4.1.2-0ubuntu6 [1864kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main libqt4-sql-mysql 4.4.3-0ubuntu1 [33.7kB]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main qt4-qtconfig 4.4.3-0ubuntu1 [109kB]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main raptor-utils 1.4.17-1 [17.8kB]  
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main redland-utils 1.0.7-1 [63.5kB]  
Fetched 50.6MB in 1min50s (460kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package kde-icons-oxygen.
(Reading database ... 102335 files and directories currently installed.)
Unpacking kde-icons-oxygen (from .../kde-icons-oxygen_4%3a4.1.2-0ubuntu6_all.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9.1-4_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libphonon4.
Unpacking libphonon4 (from .../libphonon4_4%3a4.2.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-svg.
Unpacking libqt4-svg (from .../libqt4-svg_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libclucene0ldbl.
Unpacking libclucene0ldbl (from .../libclucene0ldbl_0.9.20-3_i386.deb) ...
Selecting previously deselected package libraptor1.
Unpacking libraptor1 (from .../libraptor1_1.4.17-1_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from .../mysql-common_5.0.67-0ubuntu6_all.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from .../libmysqlclient15off_5.0.67-0ubuntu6_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.4-2.2_i386.deb) ...
Selecting previously deselected package librasqal0.
Unpacking librasqal0 (from .../librasqal0_0.9.15-2_i386.deb) ...
Selecting previously deselected package librdf0.
Unpacking librdf0 (from .../librdf0_1.0.7-1_i386.deb) ...
Selecting previously deselected package soprano-daemon.
Unpacking soprano-daemon (from .../soprano-daemon_2.1.1+dfsg.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libsoprano4.
Unpacking libsoprano4 (from .../libsoprano4_2.1.1+dfsg.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libstreams0.
Unpacking libstreams0 (from .../libstreams0_0.5.11-1ubuntu2_i386.deb) ...
Selecting previously deselected package libstreamanalyzer0.
Unpacking libstreamanalyzer0 (from .../libstreamanalyzer0_0.5.11-1ubuntu2_i386.deb) ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package phonon-backend-gstreamer.
Unpacking phonon-backend-gstreamer (from .../phonon-backend-gstreamer_4%3a4.2.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package phonon.
Unpacking phonon (from .../phonon_4%3a4.2.0-0ubuntu1_all.deb) ...
Selecting previously deselected package kdelibs5-data.
Unpacking kdelibs5-data (from .../kdelibs5-data_4%3a4.1.2-0ubuntu10_all.deb) ...
Selecting previously deselected package kdelibs-bin.
Unpacking kdelibs-bin (from .../kdelibs-bin_4%3a4.1.2-0ubuntu10_i386.deb) ...
Selecting previously deselected package kdelibs5.
Unpacking kdelibs5 (from .../kdelibs5_4%3a4.1.2-0ubuntu10_i386.deb) ...
Selecting previously deselected package libstrigiqtdbusclient0.
Unpacking libstrigiqtdbusclient0 (from .../libstrigiqtdbusclient0_0.5.11-1ubuntu2_i386.deb) ...
Selecting previously deselected package kdebase-runtime-bin-kde4.
Unpacking kdebase-runtime-bin-kde4 (from .../kdebase-runtime-bin-kde4_4%3a4.1.2-0ubuntu6_i386.deb) ...
Selecting previously deselected package kdebase-runtime-data-common.
Unpacking kdebase-runtime-data-common (from .../kdebase-runtime-data-common_4%3a4.1.2-0ubuntu6_all.deb) ...
Selecting previously deselected package kdebase-runtime-data.
Unpacking kdebase-runtime-data (from .../kdebase-runtime-data_4%3a4.1.2-0ubuntu6_all.deb) ...
Selecting previously deselected package kdebase-runtime.
Unpacking kdebase-runtime (from .../kdebase-runtime_4%3a4.1.2-0ubuntu6_i386.deb) ...
Selecting previously deselected package libqimageblitz4.
Unpacking libqimageblitz4 (from .../libqimageblitz4_1%3a0.0.4-4_i386.deb) ...
Selecting previously deselected package kdm.
Unpacking kdm (from .../kdm_4%3a4.1.2-0ubuntu12_i386.deb) ...
Selecting previously deselected package khelpcenter4.
Unpacking khelpcenter4 (from .../khelpcenter4_4%3a4.1.2-0ubuntu6_i386.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package qt4-qtconfig.
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4.4.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package raptor-utils.
Unpacking raptor-utils (from .../raptor-utils_1.4.17-1_i386.deb) ...
Selecting previously deselected package redland-utils.
Unpacking redland-utils (from .../redland-utils_1.0.7-1_i386.deb) ...
Processing triggers for man-db ...
Setting up kde-icons-oxygen (4:4.1.2-0ubuntu6) ...
Setting up libqtcore4 (4.4.3-0ubuntu1) ...

Setting up libqt4-xml (4.4.3-0ubuntu1) ...

Setting up libqt4-dbus (4.4.3-0ubuntu1) ...

Setting up libaudio2 (1.9.1-4) ...

Setting up libqtgui4 (4.4.3-0ubuntu1) ...

Setting up libphonon4 (4:4.2.0-0ubuntu1) ...

Setting up libqt4-script (4.4.3-0ubuntu1) ...

Setting up libqt4-designer (4.4.3-0ubuntu1) ...

Setting up libqt4-network (4.4.3-0ubuntu1) ...

Setting up libqt4-sql (4.4.3-0ubuntu1) ...

Setting up libqt4-qt3support (4.4.3-0ubuntu1) ...

Setting up libqt4-svg (4.4.3-0ubuntu1) ...

Setting up libclucene0ldbl (0.9.20-3) ...

Setting up libraptor1 (1.4.17-1) ...

Setting up mysql-common (5.0.67-0ubuntu6) ...
Setting up libmysqlclient15off (5.0.67-0ubuntu6) ...

Setting up libpq5 (8.3.4-2.2) ...

Setting up librasqal0 (0.9.15-2) ...

Setting up librdf0 (1.0.7-1) ...

Setting up libstreams0 (0.5.11-1ubuntu2) ...

Setting up libstreamanalyzer0 (0.5.11-1ubuntu2) ...

Setting up libqt4-opengl (4.4.3-0ubuntu1) ...

Setting up phonon-backend-gstreamer (4:4.2.0-0ubuntu1) ...
Setting up phonon (4:4.2.0-0ubuntu1) ...
Setting up kdelibs5-data (4:4.1.2-0ubuntu10) ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'


Setting up libstrigiqtdbusclient0 (0.5.11-1ubuntu2) ...

Setting up kdebase-runtime-data-common (4:4.1.2-0ubuntu6) ...
Setting up kdebase-runtime-data (4:4.1.2-0ubuntu6) ...
Setting up libqimageblitz4 (1:0.0.4-4) ...

Setting up libqt4-sql-mysql (4.4.3-0ubuntu1) ...
Setting up qt4-qtconfig (4.4.3-0ubuntu1) ...

Setting up raptor-utils (1.4.17-1) ...
Setting up redland-utils (1.0.7-1) ...
Setting up soprano-daemon (2.1.1+dfsg.1-0ubuntu1) ...
Setting up libsoprano4 (2.1.1+dfsg.1-0ubuntu1) ...

Setting up kdelibs-bin (4:4.1.2-0ubuntu10) ...
Setting up kdelibs5 (4:4.1.2-0ubuntu10) ...

Setting up kdebase-runtime-bin-kde4 (4:4.1.2-0ubuntu6) ...
Setting up kdebase-runtime (4:4.1.2-0ubuntu6) ...

Setting up kdm (4:4.1.2-0ubuntu12) ...

Setting up khelpcenter4 (4:4.1.2-0ubuntu6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

The terminal is still open, what do I do now?

BTW,  sorry for double posting:(

---

### Post by gjoellee on 2009-01-19
> **davideotape said:**
> First of all, I assume you are using the Gnome desktop environment. This comes with the standard distrubution of Ubuntu, and most people I know use it. If so, then you want to look here: [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

As far as I'm aware, if you type this:

```
sudo apt-get kubuntu-desktop
```into your terminal, it should do the rest for you. If you ever want to go back to Gnome after installing KDE, you can change the session from the login window.

Hope that helps :)

David

There is a difference between Kubuntu, and just KDE 4!
```
sudo apt-get install kde4
```
Note: You might not need the "4" after "kde"

---

### Post by ds dude on 2009-01-19
This is what is says, when I type the command line for kde.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4
root@ubuntu:~# sudo apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde has no installation candidate
root@ubuntu:~#

---

### Post by gjoellee on 2009-01-19
> **ds dude said:**
> 
BTW,  sorry for double postin:(g

Nothing bad about double posting. I guess you are finished installing now. You can close the terminal window. You might want to learn a little about the terminal. It is smart, because it some day may save you for a lot of time! Check this link: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by ds dude on 2009-01-19
Okay, I'll learn a lot about Linix terminal.  I also get magazines whenever I can.:)

Also, I am done? I get a lot of errors like "the package doesn't exist" and stuff.  did you look at my previous post?

---

### Post by oldos2er on 2009-01-19
You need to log out, select KDE from the sessions menu, then log back in.

---

### Post by ds dude on 2009-01-19
Also, when I change the session, i don't see an option for kde, so, i don't think it installed, I tried again, and got this:


ubuntu@ubuntu:~$ sudo apt-get install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kde is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install kde4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4
ubuntu@ubuntu:~$ sudo apt-get install kde3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde3
ubuntu@ubuntu:~$

---

### Post by ds dude on 2009-01-19
Also, just to stick in one topic.

I have 8.10 Live on a flashdrive, when I look into the Linux directory, I see a casper folder, which is used to make Ubuntu persistent.  Whenever, though, I log off, the settings reset.  How can I make it so I can save my settings?

---

### Post by oldos2er on 2009-01-19
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by ds dude on 2009-01-19
Here:

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security m

I found this thread: [http://ubuntuforums.org/showthread.php?t=824040]("http://ubuntuforums.org/showthread.php?t=824040")

I did "sudo apt-get upddate" and updated.  I tried to install KDE4 again and it it says: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde4

I'm trying: sudo apt-get install kubuntu-kde4-desktop , so far it's loading up, I'll see if it works or not.  However these problems above make me curious.

---

### Post by ds dude on 2009-01-19
Okay, I'm at the part where my terminal is blue, and it says Package Configuration, it says Default Display manager and gives me the option to choose gdm and kdm, which one do I choose?

---

### Post by oldos2er on 2009-01-19
Your sources.list is a mess. Go into System, Administration, Software Sources, make sure all the boxes under 'Downloadable from the Internet' are checked; and uncheck the box under 'Installable from CD/DVD-ROM.'

 When you're prompted to reload the list, do so. Then try installing kde again.

---

### Post by ds dude on 2009-01-19
Well, everything installed normally.  I typing "kdm" it did all the stuff, and said ls deferred is now taking place, I exited and I couldn't see the kde4 option in the session.

What am I seriously doing wrong?  It can't be this hard.

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

This is my source list after modifying and checking/unchecking.

---

### Post by oldos2er on 2009-01-19
You still don't have the universe and multiverse repositories. Open a terminal and type this

 ```
gksu gedit /etc/apt/sources.list
```

 Remove the comment marks (#) from these lines:

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe

 and

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

 Add these lines at the bottom of the file:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

 Save and close the file. Now run:

 ```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by tarps87 on 2009-01-20
This thread is getting a little confusing now so I'll atempt to sum it up.
kubuntu-desktop is a package containing kde4 and all the programs from a default Kubuntu install
kde4 is just the kde4 desktop management package

Usually installing kubuntu-desktop will get it up and running.

It maybe easier to start again and use the live usb creater on the Kubuntu desktop cd, you will need to download/install the package while using the live cd to use it usb-creator
Optionally you can boot using the Ubuntu cd which contains the live usb creator by default and create it using the kubuntu cd.
You will need to click make persistent, I will try to get some screen shots to make it easier to follow. I am at work so this may take a while.

---

