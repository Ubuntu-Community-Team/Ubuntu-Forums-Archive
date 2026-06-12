---
title: "Another Flash problem"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Jdmisra81 on 2008-12-14
So I have been using Xubuntu for a couple of weeks now. 8.04, the alternate install CD is what I used to get started.

I had a huge amount of trouble getting Flash plugin to work with Firefox.

Finally this had worked
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz) ([http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz))
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

Now I had some problems with Xubuntu and decided to re-install from scratch.

But this time the same process won't work
This is what I get in the terminal window:

What changed?
jdmisra81@jdmisra81:~$ cd /tmp
jdmisra81@jdmisra81:/tmp$ wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz) ([http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz))
bash: syntax error near unexpected token `('
jdmisra81@jdmisra81:/tmp$ tar -zxvf flashplayer10_install_linux_070208.tar.gz
tar: flashplayer10_install_linux_070208.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
jdmisra81@jdmisra81:/tmp$ cd install_flash_player_10_linux
bash: cd: install_flash_player_10_linux: No such file or directory
jdmisra81@jdmisra81:/tmp$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory

---

### Post by Michael.Godawski on 2008-12-14
The file is not longer on this location > The requested URL /pub/l..._070208.tar.gz was not found on this server.
You have to search for a new download location on the macromedia site.

---

### Post by Jdmisra81 on 2008-12-14
How do I do that?

But weird, it seems like it's actually installed. 
jdmisra81@jdmisra81:/tmp$ sudo apt-get install flashplugin-nonfree
[sudo] password for jdmisra81: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.

But yet it doesn't work, if I go to youtube or another site like that it tells me I have to download flash.

---

### Post by Michael.Godawski on 2008-12-14
Try to download the latest release from here:
[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

there is even a deb file.

---

### Post by Jdmisra81 on 2008-12-14
Hmm
 Im not sure how to use the deb file. When I was using Ubuntu I had a package installer that would take care of things..but with Xubuntu it just keeps asking me what I want to use to open the file..And ..embarrassed to say, I'm not sure how yet 

Also I previously downlaoded the tar.gz

jdmisra81@jdmisra81:~$ cd /tmp
jdmisra81@jdmisra81:/tmp$ wget [http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)
--14:09:47--  [http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)
           => `flash_player_10_linux_dev.tar.gz'
Resolving download.macromedia.com... 96.7.115.191
Connecting to download.macromedia.com|96.7.115.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,039,904 (11M) [application/x-gzip]

100%[====================================>] 12,039,904   501.42K/s    ETA 00:00

14:10:10 (512.52 KB/s) - `flash_player_10_linux_dev.tar.gz' saved [12039904/1203

but im not sure what to do next

---

### Post by philinux on 2008-12-14
Why not just get the .deb file from the pull down. Save it to your desktop. Then just double click it to install. Make sure synaptic is not running at the same time.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Jdmisra81 on 2008-12-14
> **philinux said:**
> Why not just get the .deb file from the pull down. Save it to your desktop. Then just double click it to install. Make sure synaptic is not running at the same time.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
I've tried but nothing happens..I haven't the slightest idea as to why :(

---

### Post by Jdmisra81 on 2008-12-14
> **Jdmisra81 said:**
> I've tried but nothing happens..I haven't the slightest idea as to why :(
That is to say when I click it doesn't do anything. I know synaptic isn't running..

which is why im hoping to figure out how to install it in terminal - I got this far:


jdmisra81@jdmisra81:~$ cd /tmp
jdmisra81@jdmisra81:/tmp$ wget [http://download.macromedia.com/pub/f...nux_dev.tar.gz](http://download.macromedia.com/pub/f...nux_dev.tar.gz)
--14:09:47-- [http://download.macromedia.com/pub/f...nux_dev.tar.gz](http://download.macromedia.com/pub/f...nux_dev.tar.gz)
=> `flash_player_10_linux_dev.tar.gz'
Resolving download.macromedia.com... 96.7.115.191
Connecting to download.macromedia.com|96.7.115.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,039,904 (11M) [application/x-gzip]

100%[====================================>] 12,039,904 501.42K/s ETA 00:00

14:10:10 (512.52 KB/s) - `flash_player_10_linux_dev.tar.gz' saved [12039904/1203

---

### Post by Michael.Godawski on 2008-12-14
ok lets try this way.
Download the deb file to your Desktop

then in terminal navigate to the /home/Desktop using the cd command.

Then run 

```
sudo dpkg -i exactnameof_file.deb
```

---

### Post by philinux on 2008-12-14
> **Jdmisra81 said:**
> That is to say when I click it doesn't do anything. I know synaptic isn't running..

Try right click the .deb file and select open. If this isn't working reboot.

---

### Post by Jdmisra81 on 2008-12-14
i tried cd /home
jdmisra81@jdmisra81:/home$

so far so good

but cd /home/desktop
bash: cd: /home/desktop: No such file or directory

same thing , I tried cd /desktop

Im not sure what I'm doing wrong here :(

---

### Post by Jdmisra81 on 2008-12-14
Still nothing. Arg.

---

### Post by Michael.Godawski on 2008-12-14
Linux is case sensitive.

So type Desktop not desktop.

---

### Post by Jdmisra81 on 2008-12-14
Okay, it isntalled eventually ...says it's installed when I enter an about:plugins into the address bar in Firefox...

But still doesn't work. So frustrating! 

Is there a way to un-install it so I can try again from a clean start?

---

### Post by philinux on 2008-12-14
Use this in the terminal to see whats installed

sudo updatedb

then

locate libflashplayer.so

Are you using 32 or 64bit.

---

### Post by Michael.Godawski on 2008-12-14
Have you considered switching to the gnome desktop (Ubuntu)? It should be a lot easier to get the flash player to work. 

To remove:
```
sudo dpkg --purge exactnameof_file.deb
```

---

### Post by Jdmisra81 on 2008-12-14
Okay, it works...in the end, I thought to try updating Firefox, I think I had 2.0 before...

Thanks guys!

---

