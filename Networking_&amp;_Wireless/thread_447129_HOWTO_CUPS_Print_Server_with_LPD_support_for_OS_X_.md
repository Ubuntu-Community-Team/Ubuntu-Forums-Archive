---
title: "HOWTO: CUPS Print Server with LPD support for OS X clients"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by UltraMathMan on 2007-05-17
Just some background, actual guide starts below:

The purpose of this guide is to describe the steps it took me to setup a print server with CUPS to serve approximately 130 Apple OS X clients via the LPD protocol. I work at an elementary school for academically &#8220;at risk&#8221; children, which was upgrading an OS X server to run READ 180 Enterprise Edition. As previous versions of this software had been rather temperamental, the school was looking to move most services off the server, yeah I know printing isn't especially processor intensive,  but I saw this as a good opportunity to experiment with setting up a small server, and to introduce Linux to the tech people there (as well as put an old 450Mhz [312MB RAM] Power Mac G4 Cube to better use). The point was to set things up as to be able to simply change the IP on the new Linux server to the IP of the old print server, without having to change the print information on each of the laptops in the building. After many hours of reading [CUPS SAM]("http://cups.org/doc-1.1/sam.html"), forums, and nearly nonexistent Google results I've finally managed to get things up and running, better than they were on the Dual Core G5, with 2GB RAM. So, to set up this CUPS server I did the following.  

Guide:
First of all, I assume no responsibility for any damage the following may cause, the only claim I make is that this worked for me. Second I make no assumptions of being a CUPS or printing guru, though I will try to offer any help that I am able to give. With that out of the way let's begin.

I assume at this point that you already have a working install of Ubuntu server, this method was done in 6.10, but should be similar (or exact) to other versions.


_**Step 1: Dependencies**_

I should probably note at this point that we will be installing OpenSSL and CUPS 1.2.10 from source, rather than from the repositories. During my install, I found that I kept getting encryption errors with the repository install which were resolved when I built the software from source with some special options.

(Make sure you have Universe and Multiverse repositories uncommented in /etc/apt/sources.list and that you do sudo aptitude update before beginning)

So to begin, make sure you have everything needed installed (and install what you don't) with ```
sudo aptitude install build-essential libpng12-0 libtiff4 zlib1g zlibc libjpeg62 checkinstall lynx slocate
``` build-essential and checkinstall provide the framework to compile and install software, lynx is a text based web-browser, slocate is provides the locate command to find files and folders, and the rest are libraries required to make full use of CUPS.


_**Step 2: Installing OpenSSL and CUPS 1.2.10 from source**_

First download the tarballs from [OpenSSL]("http://www.openssl.org/source/") (I used version 0.9.8e) and [CUPS 1.2.10]("http://cups.org/software.php?VERSION=1.2.10") (the tar.gz one). ```
wget http://ftp.easysw.com/pub/cups/1.2.10/cups-1.2.10-source.tar.gz
``` and ```
wget http://www.openssl.org/source/openssl-0.9.8e.tar.gz
```

Next unpack the archives into you current (home) directory with ```
tar -zxvf cups-1.2.10-source.tar.gz
``` and ```
tar -zxvf openssl-0.9.8e.tar.gz
```

Now we'll start installing OpenSSL. First do a ```
cd openssl-0.9.8e
``` to get into the directory, then compile and make it with ```
./configure && make
``` then install it with ```
sudo checkinstall -D
``` which installs it as a .deb package which then can be easily removed, if necessary, with dpkg.

Update the lists of files installed with ```
sudo /etc/cron.daily/slocate
``` so you will be able to find the newly installed files with locate.

Now that OpenSSL is installed, let's move onto CUPS.

First navigate to the CUPS directory with ```
cd ~/cups-1.2.10
``` Now compile CUPS with the special options to enable SSL ```
/configure --enable-ssl \
    --with-openssl-includes=/usr/local/ssl/include/openssl \
    --with-openssl-libs=/usr/lib/ssl/
```
Make sure these are the right paths to the openssl-includes and openssl-libs by finding them with ```
locate ssl
```
Now continue with ```
make
``` and finally ```
sudo checkinstall -D
```**When running checkinstall, don't breeze through the menus!** You'll need to change the package name to cupsys to satisfy dependency requirements in aptitude (and most likely apt-get). Changing the name here makes installing software dependent on CUPS *much* easier.
Hooray, CUPS is now installed!
_**Step 3: Configuring CUPS**_

First things first, make a backup of the original cupsd.conf file with ```
sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf.backup
``` just in case something goes wrong. 

Now then, change ```
# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock
``` to ```
# Only listen for connections from the local machine.
Listen 631
Listen /var/run/cups/cups.sock
``` and in ```
# Restrict access to the server...
``` ```
# Restrict access to the admin pages...
``` and ```
# Restrict access to configuration files...
``` change all instances of```
Allow localhost
``` to ```
Allow @LOCAL
``` so you can access and administer the server remotely. 

[B]**NOTE: Do NOT enable Listen 515 in addition to Listen 631, it will prevent the LPD backend from binding to the port and you will not be able to print!
[/B]
_**Step 4: CUPS-LPD and INETD**_

Almost done &#8211; now we need to install the cups-lpd backend to handle incoming LPD requests, for those of you interested, the request is sent from the printer to port 515 on the server where cups-lpd picks it up and sends it to CUPS via port 631, hence why we don't want CUPS listening directly on 515. The cups-lpd backend is installed with CUPS, but do a ```
locate cups-lpd
``` just to make sure &#8211; note the path here as well, you'll need to verify it later. Now install inetd to run the cups-lpd daemon ```
sudo aptitude install inetd
``` 

(I am purposely not using xinetd here as I was having some trouble with it, but is should work as well). Now that inetd is installed we need to configure it so it will load cups-lpd.  We need to edit the inetd.conf file, I prefer pico but any editor will work. ```
sudo pico /etc/inetd.conf
``` will open the file &#8211; use the arrow key to navigate to the section at the end labled &#8220;#:OTHER: Other services&#8221;  and edit so it appears as follows ```
#:OTHER: Other services
printer stream tcp nowait lp /usr/lib/cups/daemon/cups-lpd cups-lpd
``` making sure that /usr/lib/cups/daemon/cups-lpd is the path to your cup-lpd file. 

SECURITY NOTICE
[QUOTE=CUPS SAM]cups-lpd currently does not perform any access control based on the settings in cupsd.conf or in the hosts.allow or hosts.deny files used by TCP wrappers. Therefore, running cups-lpd on your server will allow any computer on your network (and perhaps the entire Internet) to print to your server.
While xinetd has built-in access control support, you should use the TCP wrappers package with inetd to limit access to only those computers that should be able to print through your server.
[/QUOTE]
This server is only available in the LAN, so I didn't worry too much about this.

At this point you'll need to reload inetd so that it will re-read the configuration with ```
sudo /etc/init.d/inetd restart
```

_**Step 5: Finishing Touches**_

You'll notice if you attempt to install anything which depends on CUPS aptitude will also attempt to install cupsys-common, cupsys-client, and cupsys-bsd. I say attempt because these installs will fail, but I think they are taken care of by the source install of CUPS as I have had no problems with anything else which depends on them working. Once they fail if you leave them installed you won't get errors when installing other programs for which they are dependencies.

At this point it's probably a good idea to install cupsys-driver-gutenprint to get additional drivers, so do ```
sudo aptitude install cupsys-driver-gutenprint
``` 

You should now be able to add printers remotely through a web browser by navigating to &#8220;ip of server:631&#8221;. Remember to set one of your printers as the default printer.

On the client side simply use OS X printer utility to add printers as LPD/LPR with the name of the printer as the queue. 

Hope this helps someone!

---

### Post by mcstayinskool on 2007-08-20
Many thanks for this detailed HOWTO! I am trying to do exactly what you describe in your HOWTO, but have gotten stuck. Could you read this thread and see if you can help?
[http://ubuntuforums.org/showthread.php?p=3222011](http://ubuntuforums.org/showthread.php?p=3222011)

also, I should note that `sudo checkinstall -D` failed for me on both openssl and cups, so I ended up just doing a `make install` instead to get it to work.

cheers,
#!/ben

---

