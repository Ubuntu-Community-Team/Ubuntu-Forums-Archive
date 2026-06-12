---
title: "Installing Flash 404"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by skymera on 2008-12-04
Hello

I use Ubuntu 64bit.

When i sudo apt-get install flashplugin-nonfree i gets a 404 error when it searches for Flash9 on the Macromedia FTP.

Flash 10 is available but i can't install manually because i keep getting the "Architecture not supported"

How can i install Flash now?

```
 
scott@scott-desktop:~$ sudo apt-get install flashplugin-nonfree 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport msttcorefonts ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 96884 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--23:42:08--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.162.70
Connecting to fpdownload.macromedia.com|88.221.162.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
23:42:09 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

scott@scott-desktop:~$ 

```

---

### Post by jhenager on 2008-12-04
I get this:
jeff@jeff-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.

So it appears I already have it. Try again? That would be my first suggestion. Possibly a server down or it was swamped at the moment?
I believe I used Add/Remove to setup mine. That would what I'd try next.

---

### Post by skymera on 2008-12-04
I did try again.

The file doesn't exist.

---

### Post by Tatty on 2008-12-04
I would reccomend leaving it a short while then trying again.  It will probably be better for you in the long run to install it via synaptic rather than manually installing.  It may be that adobe has moved the path to their downloads, in which case a bug report may need to be filed against flashplugin-nonfree.

If you want to install it yourself then see this post [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by ktrnka on 2008-12-04
There is a Flash 10 64bit alpha. It has been getting great reviews and seems to be more stable than the 32bit version in Ubuntu.

Download the plugin [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")

These instructions are taken from adobe's site:

Installation

Linux

   1. Download the plugin to begin installation. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Quit your browser.
   4. Remove all existing Adobe Flash Player installations from the system.
   5. Unpackage the file. A directory with contains libflashplayer.so will be created.
   6. Copy libflashplayer.so to ~/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet.
   7. Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu.


Reference [http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html")

---

### Post by skymera on 2008-12-05
ah thank you very much!

I thought the 64bit Flash was all speculation. :)

---

### Post by ktrnka on 2008-12-05
FYI I had to copy the libflash.so to the /usr/lib/firefox-addons/plugins/ directory.

---

