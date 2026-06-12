---
title: "Home Server with Linux"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by bmir88 on 2010-01-22
I was lucky enough to get a desktop computer from my parents that I thought I had a use for. Well its been sitting in my house now since I got it and turns out I did not have an initial use for it, until Rapidshare entered my life and I find myself with over 4 terabytes of movies/tv shows/software etc. The desktop is a Dell Optiplex 760 with a Intel Core 2 Duo 2.93GHz and 8gb of ram, 2TB HDD and an ATI Radeon HD3450 256MB video card that was no longer needed at the office. I would like to set up a home server/nas. I would like this machine to be the primary machine where I download my movies/tv shows etc from my rapidshare account. I have multiple HTPC's running in my house and would like to stream content from the server directly to these other machines, both Windows and OS X. I would ideally like to have the desktop sitting down in the basement and have access to it remotely to set up Rapidshare downloads, so is there a VNC compatible version for Linux that will work cross platform? Any help is greatly appreciated and below are just a few more questions if anyone can help with those. 

1. Whiich distro would be better for running this type of set up? Ubuntu or Xubuntu?
2. Does Linux have a download manager for Rapidshare like Flashget for Windows, or Speed Download for OS X? Also most of the rapidshare files come in .rar format. Is there a UnrarX or Winrar equivalent for Linux distros?
3. Is the hardware I listed above going to give me any problems for this type of set up? Is the hardware compatible with Linux?

Thanks a bunch! Cheers!

---

### Post by randumnumber on 2010-01-22
I highly recommend you take a look at MythTV installed over a Ubuntu os. MythTV has a front end back end option so you can have your server in the closet or whereever and have it stream over a lan network to your HTPC systems, it however requires you to have the capture cards installed into the system you are serving from. there is a os called mythbuntu which is a very lightweight xfce ubuntu with mythtv built directly into the os. I use a single pc setup where the front end and backend are on the same computer and i can capture live tv and browse my movie collection and watch it on my television. 

You could also just set the system up as a server and browse from your HTPCs to the movie / tv directory. in that case you would need to just install ubuntu on it and perhaps do some samba (samba is what ubuntu uses to comm. with windows file sharing) configuration.  the server version of ubuntu is just a command prompt. with a machine this powerful you should be able to run a normal version of ubuntu, it will have all the options you need to create a home server.

for part 2 and 3 of your question i suggest googling

rapidshare ubuntu and ubuntu hardware compatability guide

---

### Post by Linux000 on 2010-01-22
1. Mythbuntu for streaming, but it doesn't make much of a main machine. If you have mythbuntu on the HTPC's you could use Ubuntu and the nfs-kernel-server package (manual config) to make a share.

2.Not sure

3. ATI should work fine, but for future reference Nvidia has better drivers.

---

### Post by whitethorn on 2010-01-22
1) With your computer you can use ubuntu or xubuntu doesn't make much of a difference.  
2) To download with Rapidshare look into JDownloader and Tucan, I find JDownloader works better.
3) I don't think you should have any compatability with your hardware, try out the livecd to be sure.

---

### Post by HermanAB on 2010-01-22
Howdy,

For home use, I would always suggest using regular desktop Ubuntu.  The server version is really aimed at using in a data centre where the machine will never have a screen or keyboard.

With regular Ubuntu, you will have a desktop to use when you are right at it and if you install ssh-server, then you can access it remotely from Linux or Windows (Google for Xming and PuTTY).  

With SSH, you can securely run graphical programs remotely.  You can also run the gnome taskbar remotely and then go click happy just like normal:

$ ssh -X -C -c blowfish user@serveripaddress gnome-panel

You will end up with a remote taskbar that you can dock on the side of the screen for example and then use the menus to select remote programs and they will run transparently on your local desktop.  This is especially cool with Windows of course.

VNC is mainly a Windows thing.  It works on Linux too, but it is a serious security risk.  You can search these forums for tales of woe - many users got their machines hacked after playing with VNC.  It is also possible to tunnel VNC over SSH to secure it, but it is rather pointless, since SSH by itself can do everything you need already - and much more that VNC cannot do.

---

### Post by k64 on 2010-01-22
Apache, MySQL, and PHP, plus a WYSIWYG editor to create a Web site to access the home server's storage.

---

### Post by bmir88 on 2010-01-23
Bump

---

### Post by Bridgette on 2010-01-23
Hi
 
I like the advice, after trying to get the server edition working, with hardware incompatability and USB issues i am about to turn to the desktop version and then load apache, Mysql PHP to use it as a server, I find the command line just too much when trying to move around loading drivers and compilers etc, are there any downsides to loading the desktop version other than it doesnt automatically load the above software automatically, is it manually hard to load the above software through the desktop ?
 
Thanks
Bree

---

