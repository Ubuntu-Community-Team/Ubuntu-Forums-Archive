---
title: "ULTIMATE Photo Kiosk Network!  HELP!!!"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by cfphotos on 2007-07-11
I'm new to Linux and Ubuntu, so I'd like some input on my setup.  I'll list a bunch of questions and if you can direct me to links or give me some advice, that would be awesome!  I need this up and running by July 18th.

First I would load my photos onto my laptop computer _(should I have Ubuntu installed on my laptop, or will WinXP be okay?) _.

I would then transfer my JPG files over my 802.11n wireless adapter to my server  _(Should I have Ubuntu Server or Desktop installed here?) _.  From here my assistant will use [JAlbum]("http://jalbum.net/") to create a photo web page to be shown over the network.

Now comes the complicated part that I'll need the most help with!

I want to set up my six workstations so they run directly off my server, so I don't have to install an operating system on each system.  _Do I need to set up the bios to boot off the network?_  _How do I do this?_

On the workstations customers will view their photos via Firefox, set up in kiosk mode.  They won't have access to a keyboard, only a mouse will be available.  _How do I set up the system to show my webpages on the server over Firefox?_  _How do I set it up so the workstations boot up to Firefox in kiosk mode with my photo page ready to show?_ _How do I keep customers from accessing anything, but the photo pages?_

If you can answer my questions, if you have a better way to do this, if you have some suggestions, please let me know.  I really want to start using Linux in all my applications, I'm tired of the limitations I've constantly been experiencing with MS Windows.

Here's a diagram I made to illustrate what I'd like to do:
[IMG]http://www.cfphotos.com/studio/network_plan.jpg[/IMG]


THANKS!!!

---

### Post by solar george on 2007-07-11
OK I can defiantly help with the firefox kisok side of things (I don't know about network booting though).

On each computer (assuming you have linux installed)

1. Add a new user and setup gdm to autologin as that user.

2. In that users /home/*username* add a file called .xsession containing the following text 
```
xsetroot -bitmap ~/cchange.xbm
~/firekiosk.sh

```
In my setup cchange.xbm is a monochrome bitmap background, you can leave this line out if you don't need a special background.

3. Create /home/*username*/firekiosk.sh and make it executable,
```
chmod +x ./firekioskk/sh
```
and enter this text into it,
```
while true;
 do 
  FFX=`pgrep -c firefox`
  #Only start one window
  if [ "$FFX" = "0" ]; then
    echo 'Starting Firefox' $FFX
        firefox &
    sleep 2
 fi
done

```

4. Login as that user and in the started firefox set the homepage to your server, go to about:config and change browser.sessionstore.enabled and browser.sessionstore.resume_from_crash to false.

5. Install the r-kiosk and autoresetbrowser addons.

Resart the Xserver (ctrl, alt + backspace) and you should be looking at a fullscreen firefox showing your webpage.
The autoresetbrowser addon will automatically restart firefox after 5 minutes of inactivity.

---

### Post by compwiz18 on 2007-07-11
Cool problem :)

Anyway, I would suggest that you install Apache (package apache2) on the server, for JAlbum to use.  You can then simply copy the albums in generates into /var/www, and set the Firefoxes in kiosk mode to open the server's address.  As for the laptop, you should install SSH (package openssh) on the server, and then you can set up remote file transfer via ssh to the server, where your assistant can open the pictures and JAlbumize them.

As for what to put on the laptop - I would use Ubuntu, but XP would be very possible too.  If you use Ubuntu, you can just click the Places menu, and choose Connect to server to connect to the server, and then and icon will appear on the Desktop, and you can just drag things in there.  If you go the XP route, you can use [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) (I think, never used it) to access the server.  I recommend SSH instead of FTP because it is more secure.

---

### Post by cfphotos on 2007-07-12
You guys rock!  This is helping me immensely!  I hope others will be able to use what we have here so far too.

Okay.... how easy is it to set up Thin Clients on Ubuntu 7.04 Network Edition?  I'm thinking this is the route I'd like to go with my kiosk viewing stations.

---

### Post by solar george on 2007-07-12
> Okay.... how easy is it to set up Thin Clients on Ubuntu 7.04 Network Edition? I'm thinking this is the route I'd like to go with my kiosk viewing stations.

You could try xubuntu - I believe that the alternate cd can still install LTSP automatically (there should be an option on the boot menu) - then you just need etherboot or similar to boot the kiosks.

Etherboot rom-o-matic - [http://rom-o-matic.net/](http://rom-o-matic.net/)

---

### Post by chepazzo on 2008-05-13
I am just starting to do something similar, but I would suggest installing ltsp and creating a kiosk image:

ltsp-build-client --kiosk --copy-sourceslist

fast
easy
works

Customize

you@server:~# sudo chroot /opt/ltsp/i386

/* This part does not work
 * any ideas?
 * edit the startup page:
 * root@server:/# vi /usr/lib/firefox-3.0b5/browserconfig.properties
 * edit the lines:
 *  browser.startup.homepage=
 *  browser.startup.homepage_reset=
 */

install flash:
root@server:/# cd /root
root@server:/root# apt-get update
root@server:/root# apt-get install wget
root@server:/root# wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
root@server:/root# tar -xzvf install_flash_player_9_linux.tar.gz
root@server:/root# cd install_flash_player_9_linux
root@server:/root/install_flash_player_9_linux# ./flashplayer-installer 
* firefox installed at /usr/lib/firefox-3.0b5 *
root@server:/root/install_flash_player_9_linux# cd /

exit chroot environment:
root@server:/# exit

update image:
you@server:~# sudo ltsp-update-image

Reboot clients!  

After that, you should be good to go.

If you want to maintain multiple chroot evironments so some terminals can boot into kiosk, while others boot into Ubuntu, things are a bit more complicated, but you just need to make sure all of your paths match in these files:
/etc/inetd.conf
/etc/ltsp/dhcpd.conf
and you need to use the -b and -p arguments in the update-image and build client commands.

Also, most non-kiosk settings are set in the /var/lib/tftpboot/ltsp/ directory instead of /opt/ltsp/i386/ so that you only need to reboot the client to realize the edits instead of using ltsp-update-image every time.  Kiosk images cannot take advantage of this.

I hope this helps.   I only just figured most of this out last night.

---

### Post by p858snake on 2008-05-14
if you run apache and mysql you could use zenphoto to generate your albums, all you need to do is create a folder in zenphotos album folder and then place images in there and it will create and display those photos as a single album and you can have as many albums as you want.

---

### Post by YogiPaolo on 2008-05-18
After an obsessive weekend, I just got LTSP running. I was finally able to get a desktop by disabling SSH tunneling. This is an acceptable workaround for my application, but I'd like to know what SSH tunnelling did not work, but I digress.

My plans for LTSP are similar to the project described in the  original post. I have 5 or six laptops I pulled out of various trash heaps. I plan to tear them down and build shiny new plexiglass cases for them and bolt them to various surfaces around my apartment. The plan is to use them as digital picture frames and/or displays for randomly mixed video and other goodies...

Anyway, I'm very interested in the --kiosk build option. I googled for this a bit and did not see any other references besides yours. Also, I'm not clear on how to set up multiple images for use on different clients. To save me some google time, would you please enlighten me with more tips?


I look forward to seeing how the projects in this post turn out. 

Thanks!

---

