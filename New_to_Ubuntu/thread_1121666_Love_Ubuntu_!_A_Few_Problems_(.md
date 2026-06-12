---
title: "Love Ubuntu ! A Few Problems :("
date: 2009-04-10
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-10
I love this operating system!
I just have a few issues I need to resolve before making the full switch over from windows.
1. flash player will not install. I have tried a few different free flash options and I still can not view my own webpage videos. example video I can't view here: [http://www.wittyvideos.net/play.php?vid=119](http://www.wittyvideos.net/play.php?vid=119) ( for some reason I am not allowed to upload a 52kb .png image to this thread to show you the exact problem, so I will describe it. I Download this file "install_flash_player_10_linux.deb" I click on file, "package installer" opens up and says "Error: Wrong archetecture 'i386'" )
2. need guidance on connecting Ubuntu to my home network ( 5 windows computers )
3. sound volume is not as loud as windows....like my music :P (tried switching between the mixers to no avail )
4. I use a video grabber program to get videos for my website, and it is windows based only, wish I could make it run in linux, if not I need to find a free linux video grabber.
Just a note I used Wubi to install my version of Ubuntu, not sure if this makes a difference.
Thank you in advance for any help provided on these issues,
Dave

---

### Post by Penguin Guy on 2009-04-10
1: Open the flash file with Firefox
2: Install samba
4: Install wine

---

### Post by Paqman on 2009-04-10
> **drdave69 said:**
> 
1. flash player will not install.


I wouldn't bother with the free Flash alternatives. A good package to install early on is ubuntu-restricted-extras [(Click to install)](apt:ubuntu-restricted-extras). It will set up Flash, Java, MS fonts, etc all in one step.

> 
2. need guidance on connecting Ubuntu to my home network ( 5 windows computers )


You should be able to brows e through Places > Network to your Windows home network. To share a folder in Ubuntu just right click > Share folder. You'll want to share using SMB.

> 
3. sound volume is not as loud as windows....like my music :P (tried switching between the mixers to no avail )


I've noticed that too. I just turn my speakers up. Sorry for the supremely unhelpful answer!

> 
4. I use a video grabber program to get videos for my website, and it is windows based only, wish I could make it run in linux, if not I need to find a free linux video grabber.


What sort of video? There's browser plugins for Firefox that will grab Flash videos off YouTube, etc. Make sure you're not ripping off somebody else's stuff though. Most people will give you permission to use their stuff if you actually ask.

---

### Post by ashmew2 on 2009-04-10
I'd recommend using Wine to grab videos since you must be well versed with the Windows program you use.

Btw , IMO , You should install ubuntu separately , not using Wubi i mean. Standalone..You can always dual boot..

---

### Post by riza hylviu on 2009-04-10
for the flash player open synaptic package manager and type flash player and install flashplugin-nonfree

---

### Post by Dougie187 on 2009-04-10
> **drdave69 said:**
> 
3. sound volume is not as loud as windows....like my music :P (tried switching between the mixers to no avail )

I am not sure how much this helps. But I from what I have seen applications typically have their own independent audio volume levels. First thing you should do, is turn the volume control in the system tray all the way up, and then after that, turn up the volume in the audio player you are using. This might help you our with this issue.

---

### Post by Nagrom_17 on 2009-04-10
1. not sure if its the same but when I installed flash through Firefox plug-in it didn't work. you need to uninstall it from there and close Firefox then install it using the terminal(applications > accessories > terminal) then type the following
```
$ sudo apt-get install flashplugin-nonfree
```
then you should be good (source: [http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/]("http://www.cyberciti.biz/faq/ubuntu-linux-how-to-install-flash-player-for-firefox/")

2.is it wired? mine is wired and it can connect to all our windows computer but only through our Internet router, when i just plug it into the splitter with all the others it wont recognize it.
To check whether its working you can go to Places > Network then you should see the name of your computer there and a Windows Network too, click on that then on the name of the workgroup you want to access and finally the computer you are looking for and it should work.

3.i cant help you there I haven't needed to mess around with my sound yet

4.you can try using WINE which will run windows programs on Linux, its not perfect but from what I've found its pretty good. you can get it using the add/remove utility under the applications menu(note you may have to change the filter of shown programs to all open-source to see it which is located top, center of the add/remove window) just search wine and it should come up.

I hope you get your problems fixed ubuntu is fun once you get to know how to work it then you can do almost anything :D

---

### Post by konqueror7 on 2009-04-10
try using 'DownloadHelper', its a video grabber extension for firefox...

as for your home network, i don't know the setup,,,but the configuration is pretty much the same when using wired/router config...

as for the audio, i think there has not been a solution to that (been also trying to do that),,,but ended up playing my mp3s using SMPlayer, with volume amplification of 200%...

---

### Post by Paqman on 2009-04-10
> **ashmew2 said:**
> 
Btw , IMO , You should install ubuntu separately , not using Wubi i mean. Standalone..You can always dual boot..

I disagree. Wubi is great. The only real reason to avoid Wubi is if you need hibernation or there's a chance of power outages.

---

### Post by LowSky on 2009-04-10
> **Paqman said:**
> I disagree. Wubi is great. The only real reason to avoid Wubi is if you need hibernation or there's a chance of power outages.

Chance of power outages....lol

I dont know about you but I don't like to take chances with my computer. That one of the many reasons I think Wubi is a crappy solution.

---

### Post by drdave69 on 2009-04-10
thanks for the fast replies :)
It seems that i would be better off installing ubuntu without wubi.
I have a Dell xps 400.
System Info:
Processor: GenuineIntel / CPUs: 2 / Model Name:  Intel(R) Pentium(R) D CPU 2.80GHz / Frequency: 2793.011 MHz / L2 Cache: 1024 KB
Memory: 2007 MiB
Graphics: GeForce 7300 LE

I want to dual boot with windows.
Which file should I choose?

Ubuntu 8.10

    * ubuntu-8.10-alternate-amd64.iso.torrent
    * ubuntu-8.10-alternate-i386.iso.torrent
    * ubuntu-8.10-desktop-amd64.iso.torrent
    * ubuntu-8.10-desktop-i386.iso.torrent
    * ubuntu-8.10-server-amd64.iso.torrent
    * ubuntu-8.10-server-i386.iso.torrent
    * New: IPv6 only torrents for users of IPv6 (learn more about IPv6)

Ubuntu 8.04

    * ubuntu-8.04.2-alternate-amd64.iso.torrent
    * ubuntu-8.04.2-alternate-i386.iso.torrent
    * ubuntu-8.04.2-desktop-amd64.iso.torrent
    * ubuntu-8.04.2-desktop-i386.iso.torrent
    * ubuntu-8.04.2-server-amd64.iso.torrent
    * ubuntu-8.04.2-server-i386.iso.torrent

---

### Post by Paqman on 2009-04-10
Normally this one:
```

ubuntu-8.10-desktop-amd64.iso.torrent

```

8.04 is the Long Term Support release version, which is better for a machine where stability is more important than having the latest features.

If you hold off for two weeks, you'll be able to download the next version, 9.04 Jaunty Jackelope. If you install 8.10 right now, you'll be able to upgrade to 9.04 when it's released.

---

### Post by ubulaptop on 2009-04-10
sound / volume problems:

try to connect to remote speakers! It works with me, and you can get the volume quite high up.;)

---

### Post by krzysz00 on 2009-04-10
gtkRecordMyDesktop is a good desktop recorder for screencasts

---

### Post by ashmew2 on 2009-04-10
[QUOTE=Paqman;7047805]Normally this one:
```

ubuntu-8.10-desktop-amd64.iso.torrent

```

I think he is better off with ubuntu-8.10-desktop-i386.iso.torrent

amd64 has some issues , for instance it wont run dosbox or dosemu..It didnt run on 8.04 at least..

---

### Post by ashmew2 on 2009-04-10
> **Paqman said:**
> I disagree. Wubi is great. The only real reason to avoid Wubi is if you need hibernation or there's a chance of power outages.

Quoting from wikipedia : 

Limitations
[LIST=1]
[*]* Hibernation is not supported.
[*]* Wubi filesystem is more vulnerable to hard reboots.      (unplugging the power) than a normal filesystem.
[*]    * Since Wubi installs Ubuntu on the same file partition as Windows, Ubuntu may see a slight degradation in performance over time due to FAT32/NTFS file fragmentation, which could possibly be alleviated via defragging the disk.
[/LIST]

---

### Post by Paqman on 2009-04-10
> **ashmew2 said:**
> 
amd64 has some issues , for instance it wont run dosbox or dosemu..It didnt run on 8.04 at least..

64-bit used to have issues a couple of years ago, but not any more. I have DOSBox on my machine, installed and working without any issues at all.

---

### Post by Paqman on 2009-04-10
> **ashmew2 said:**
> Quoting from wikipedia : 

Limitations
[LIST=1]
[*]* Hibernation is not supported.
[*]* Wubi filesystem is more vulnerable to hard reboots.      (unplugging the power) than a normal filesystem.
[*]    * Since Wubi installs Ubuntu on the same file partition as Windows, Ubuntu may see a slight degradation in performance over time due to FAT32/NTFS file fragmentation, which could possibly be alleviated via defragging the disk.
[/LIST]

Er, isn't that pretty much what I said? NTFS fragmentation notwithstanding. Both Wubi and Ubuntu are pretty up front about hibernation and power outages being a limitation.

I stand by my original statement: Wubi is fantastic. Give it a test drive some time, it's hard not to be impressed at how easy it makes installing/uninstalling.

---

### Post by 3rdalbum on 2009-04-10
If by "video grabber" you mean something to extract the raw video files from Youtube, Megavideo, Tudou, Youku, Blip.tv etc (anything that uses a Flash-based player), then you don't need one. When you start loading the video it will buffer the content to the /tmp directory. Just press Play and then Pause in the web browser, and wait for the video to be fully buffered.

Then you can copy or move the file from /tmp to wherever you want it in your home directory, rename it, and play it with VLC or Totem.

Unlike all these video grabbing programs for Windows, this method will work with absolutely any Flash video even if it's embedded in a different website.

---

### Post by bruce2000 on 2009-04-10
> **drdave69 said:**
> 
3. sound volume is not as loud as windows....like my music :P (tried switching between the mixers to no avail )


I found I could increase the volume by installing Gnome Alsa Mixer

To install it hit Alt-F2 and type:

```

sudo apt-get install gnome-alsamixer

```

It's found in Application/Sound&Video

Adjust the sliders to crank up the volume

---

### Post by ashmew2 on 2009-04-10
> **Paqman said:**
> Er, isn't that pretty much what I said? NTFS fragmentation notwithstanding. Both Wubi and Ubuntu are pretty up front about hibernation and power outages being a limitation.

I stand by my original statement: Wubi is fantastic. Give it a test drive some time, it's hard not to be impressed at how easy it makes installing/uninstalling.

But you have to rely on Windows to use it!

---

### Post by Paqman on 2009-04-11
> **ashmew2 said:**
> But you have to rely on Windows to use it!

No you don't. You only use Windows to *install* it. Once installed it's a fully standalone system. Wubi is not a VM.

---

### Post by drdave69 on 2009-04-12
> **3rdalbum said:**
> If by "video grabber" you mean something to extract the raw video files from Youtube, Megavideo, Tudou, Youku, Blip.tv etc (anything that uses a Flash-based player), then you don't need one. When you start loading the video it will buffer the content to the /tmp directory. Just press Play and then Pause in the web browser, and wait for the video to be fully buffered.

Then you can copy or move the file from /tmp to wherever you want it in your home directory, rename it, and play it with VLC or Totem.

Unlike all these video grabbing programs for Windows, this method will work with absolutely any Flash video even if it's embedded in a different website.
GREAT info !!! just tried it & it fulfils all my needs ! 
Thank You,
Dave

---

### Post by ashmew2 on 2009-04-12
> **Paqman said:**
> No you don't. You only use Windows to *install* it. Once installed it's a fully standalone system. Wubi is not a VM.

What if you install Wubi and then use it for a day and decide to delete all Windows system files and use only Wubi as the sole OS on your system...is it possible ? And doesnt Wubi store info inside Windows files..

---

### Post by lavinog on 2009-04-12
> **drdave69 said:**
> 
1. flash player will not install.

If you are planning to use ubuntu 64, I would recomend using the 64 bit Flash alpha from adobe...it has alot less issues than the one in the repositories (the ones in the repositories use a 32bit wrapper) 
Download the file from here:
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
extract the file, and copy the file to the plugin folder (note, if you installed the plugin from the repository you need to remove it first)
```
tar xvzf ~/Desktop/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz
sudo cp -v ~/Desktop/libflashplayer.so /usr/lib/mozilla/plugins
```
restart firefox and go to tools>addons>plugins and verify shockwave flash is listed

> 
2. need guidance on connecting Ubuntu to my home network ( 5 windows computers )

It used to be that you had to install a samba package...It also use to be that there was a menu to enable samba access to windows computers
> 
3. sound volume is not as loud as windows....like my music :P (tried switching between the mixers to no avail )

This tends to be an issue with alsa drivers...many times switching to oss drivers will improve the volume issue. If you want to mess with trying out oss, do it at a point that you wont mind having to reinstall ubuntu, because you can be likely to mess things up to the point that a reinstall is the best fix.

---

