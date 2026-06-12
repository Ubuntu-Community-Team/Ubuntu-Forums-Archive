---
title: "Alternative Programs"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Kwijt on 2010-05-14
Hey,

I just ordered new hardware for my desktop and decided to install Ubuntu instead of Windows.
 
But first I would like to know some good alternatives to the Windows programs I use.
I like simple, clean applications and I'd rather not use WINE.

I can also use help to replace/remove included Ubuntu applications (like Totem, Rhythmbox, Empathy, Gwibber, Transmission and Evolution)

- IrfanView   --> WINE?
- Winamp [cPro - Hi-Fi 73]("http://skinconsortium.com/index.php?page=ViewDownload&itemID=129")   --> ? (check link, it's  precisely what I need)
- XPlay/Ipod Manager (NO media-player!)   --> gtkpod?
- Live Messenger   --> ?
- EasyGPS   --> ?
- WinRAR   --> p7zip-rar
 - µTorrent   -->  Deluge
- Soulseek   --> Nicotine+
- ed2k client   --> aMule
- Guitar Pro   --> TuxGuitar

- Dreamweaver   --> Aptana Studio
- Photoshop --> GIMP
- Fireworks --> ?
- Illustrator --> Inkscape
- Lightroom   --> LightZone

- Audacity
- Thunderbird + Lightning
- Avidemux

Thanks!

---

### Post by lkraemer on 2010-05-14
Irfanview works just fine under WINE in Ubuntu.

Wine needs winecfg ran so that .wine is created in /home/user,
so the subdirectory exists, If Wine has been configured. Skip to 1A Below:

1.  This is with a clean configuration directory.

$ winecfg

1A:
Once the .wine directory is built the configuration tool will start and you can set a virtual desktop in the graphics tab if you wish.

Install the MFC42.dll from a Windows XP box, if it does not already exist, or install WineTricks.

You will need a native MFC42.dll in ~/.wine/drive_c/windows/system32 before the install will work.

2.  Installing IrfanView with:

$ wine iview423_setup.exe

Delete the I_view32.ini file in ~/.wine/drive_c/Program Files/IrfanView

3.  Change the ICON by Right clicking on the Desktop Icon and then clicking on he displayed ICON. Change to /usr/share/pixmaps/wine.svg
OR Download Irfanview.PNG
Other ICON choices are located at /usr/share/icons and lower subdirectories.....





The information on the winehq.org on how to install IrfanView 4.25 in wine is quite useful:

1. Get the mfc42.dll file from a Windows machine and copy it to the system32 folder in .wine.

2. Install IrfanView 4.25. Then go to the .wine>...>irfanview folder and delete i_view32.ini

Done!



And if you should want MS Paint:
[http://ubuntuforums.org/showthread.php?t=660408&highlight=MS+Paint&page=3](http://ubuntuforums.org/showthread.php?t=660408&highlight=MS+Paint&page=3)
Posting #30

lk

---

### Post by halitech on 2010-05-14
Check here: [http://www.osalt.com/](http://www.osalt.com/)

---

### Post by bumanie on 2010-05-14
These links should help.

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

[http://www.linux.ie/newusers/alternatives.php](http://www.linux.ie/newusers/alternatives.php)

---

### Post by Black Hawk on 2010-05-14
- Dreamveawer -- NVU
- Irfanveiw   -- Irfanview (wine)
- Live messenger -- empathy (installed by default), amsn, emesene
- Winamp -- XMMS or XMMS2,
- Ipod software -- Banshee, rythembox, amarok
- uTorrent - Deluge
- CrapCleaner -- have a look here: [http://ubuntuforums.org/showthread.php?t=14092](http://ubuntuforums.org/showthread.php?t=14092)

** Comments **

NVU
-----
haven't used it much, did'nt really need or like it, then again i didn't like DW either.

Irfanview
----------
haven't really found a good replacement for it. You can run it with an api extention called wine (makes some windows software work on linux)
this may or may not work, and if you get it to work you should be careful not to update wine unless you need it for some other software. To install irfanview in wine you first need to install wine and some windows dlls. This can be done by running a command in the terminal. 

The terminal is found under applications - accesories, terminal.
The command looks big and scary, but don't worry all it does is:
1) Installs wine
2) Downloads winetricks, a handy utility for downloading extra wine stuff like dlls.
3) Runs winetricks and downloads the needed dlls

And now the command.

```
 sudo apt-get install -y wine && wget http://www.kegel.com/wine/winetricks && chmod +x winetricks && ./winetricks MFC42 comctl32 
```

You should now be able to download and install irfanview like you would in windows.

XMMS
----- 
xmms an old audio player. It looks like winamp 2.x, but it still works. XMMS2 has a variety of different guis to choose from. Have a look here: [http://xmms2.org/wiki/Clients](http://xmms2.org/wiki/Clients)

Ipod software
-------------
Any of the one's i lsted should work, try them out. I've found amarok to be a little unstable. I don't have an ipod so i can't tell you anything definitive.

Torrent client
----------------
Deluge is my favorite GUI torrent client on linux. It's also possible to run utorrent in wine, but you might expreience stability issues.

Hope this helps

---

### Post by Zintha on 2010-05-14
you'll never get a messenger like MSN Live one.

I use mine obsessively sometimes and the closest match is aMSN but some fonts here and there and alignment and scales of stuff bug me.

I know it doesn't seem helpful but if you install aMSN and don't like it because its not quite the same, don't bother looking further!

---

### Post by Kwijt on 2010-05-26
I finally got my new hardware!

Ubuntu installed and running, I tried out some of the software and here are the results:

VLC installed without a problem but I can't choose it as standard to view multimedia, solved by changing file open with preferences, but have to do it with all different file types and sometimes it uses totem again.

The same for thunderbird, easy install and easy profile migration from windows.

For messenger I now use emesene, it looks and feels the best, but I miss a chat log function like in live messenger and webcam-record function like in amsn and msn webcam recorder. Another problem; I don't seem to receive messages from people who I accepted but aren't in my list anymore.

For dreamweaver I installed bluefish because I used nvu in windows and didn't like it, but I haven't tested bluefish yet.

Same for gtkpod, tuxguitar, nicotine+ and deluge, installed but not yet tested.

I tried installing irfanview with wine, but didn't succeed with that, installed wine with the command, added the repository from their website, installed winetricks, changed the downloaded irfanview installer to executable and tried to run, but nothing happened.

---

### Post by Kwijt on 2010-05-27
> **Black Hawk said:**
> 
- CrapCleaner -- have a look here: [http://ubuntuforums.org/showthread.php?t=14092](http://ubuntuforums.org/showthread.php?t=14092)


The link doesn't seem to work..

---

### Post by Kwijt on 2010-05-27
> **lkraemer said:**
> Irfanview works just fine under WINE in Ubuntu.

Wine needs winecfg ran so that .wine is created in /home/user,
so the subdirectory exists, If Wine has been configured. Skip to 1A Below:

1.  This is with a clean configuration directory.

$ winecfg

1A:
Once the .wine directory is built the configuration tool will start and you can set a virtual desktop in the graphics tab if you wish.

Install the MFC42.dll from a Windows XP box, if it does not already exist, or install WineTricks.

You will need a native MFC42.dll in ~/.wine/drive_c/windows/system32 before the install will work.

2.  Installing IrfanView with:

$ wine iview423_setup.exe

Delete the I_view32.ini file in ~/.wine/drive_c/Program Files/IrfanView

3.  Change the ICON by Right clicking on the Desktop Icon and then clicking on he displayed ICON. Change to /usr/share/pixmaps/wine.svg
OR Download Irfanview.PNG
Other ICON choices are located at /usr/share/icons and lower subdirectories.....





The information on the winehq.org on how to install IrfanView 4.25 in wine is quite useful:

1. Get the mfc42.dll file from a Windows machine and copy it to the system32 folder in .wine.

2. Install IrfanView 4.25. Then go to the .wine>...>irfanview folder and delete i_view32.ini

Done!


lk
I installed wine like mentioned on their website, ran the config, checked if winetricks was available, downloaded mfc42.dll and placed it in the right folder, downloaded irfanview installer, but nothing happened after it tried to load it.

---

### Post by Kwijt on 2010-05-27
> **Kwijt said:**
> Hey,

I can also use help to replace/remove included Ubuntu applications (like Totem, Rhythmbox, Empathy, Gwibber, Transmission and Evolution)

Thanks!

When I tried to completely remove evolution I accidentally removed some system packages and had to reinstall Ubuntu (luckily it doesn't take as long as a windows install), so now I would like to know how it is possible to remove the integrated Evolution/Empathy and use Thunderbird/Emesene instead, whilst keeping the panel object functional.

---

### Post by ManiDhillon on 2010-05-27
Dreamweaver = Kompozer
PhotoShop = GIMP (close)
WinRAR = p7zip-full, p7zip-rar
WinAmp = Audacious
uTorrent = Vuze (same gui)

And most important is that when you wipe out your Windows installation and install Ubuntu or any other Linux distro, you automatically start finding open source programs for your need.

---

### Post by anaconda on 2010-05-27
PhotoShop = Krita

Actually photoshop CS2 works very well in wine. CS4 can also be made to work, but not as well.

---

### Post by Kwijt on 2010-05-27
> **ManiDhillon said:**
> Dreamweaver = Kompozer
PhotoShop = GIMP (close)
WinRAR = p7zip-full, p7zip-rar
WinAmp = Audacious
uTorrent = Vuze (same gui)

And most important is that when you wipe out your Windows installation and install Ubuntu or any other Linux distro, you automatically start finding open source programs for your need.

I really don't like Kompozer and NVU, so I'm going to try to install and test Aptana Studio, to bad there isn't a package/repository for it.
For gimp the same, but I fear it's the only alternative at the moment.
I have the experience with 7zip that it doesn't open/extract all rar/zip files proper.
I used Vuze in the past, but replaced it with µTorrent, and now use Deluge on ubuntu.
Audacious seems to be a nice application, but does it have an interface/skin like the cPro Hi-Fi 73?

---

### Post by Kwijt on 2010-05-27
> **anaconda said:**
> PhotoShop = Krita

Actually photoshop CS2 works very well in wine. CS4 can also be made to work, but not as well.

Thanks! I'll check it out later.
PS. Is it possible to open previous made psd files?

---

### Post by Kwijt on 2010-05-27
> **ManiDhillon said:**
> And most important is that when you wipe out your Windows installation and install Ubuntu or any other Linux distro, you automatically start finding open source programs for your need.

Are there any repositories I can add to find more programs through the Ubuntu Software Center?

---

### Post by Kwijt on 2010-05-27
I think I'm going to skip messenger and use no IM any more, is there a way to remove the integrated buttons (without removing the network/sound icons) ?

---

### Post by jerome1232 on 2010-05-27
I just use unrar and rar to handle rar files.

---

### Post by Kwijt on 2010-05-27
> **jerome1232 said:**
> I just use unrar and rar to handle rar files.
  Are these free?

---

### Post by jerome1232 on 2010-05-27
Yes, they let the default archive manager handle rar's, I don't use rar's extensively so I don't know how robust those programs are.

---

### Post by jerenept on 2010-05-27
> **Kwijt said:**
> Are there any repositories I can add to find more programs through the Ubuntu Software Center?
GetDeb - go to [www.getdeb.net]("http://www.getdeb.net")
they have a convenient package that installs the PPA's (repos)

---

### Post by ManiDhillon on 2010-05-27
> **Kwijt said:**
> I really don't like Kompozer and NVU, so I'm going to try to install and test Aptana Studio, to bad there isn't a package/repository for it.
For gimp the same, but I fear it's the only alternative at the moment.
I have the experience with 7zip that it doesn't open/extract all rar/zip files proper.
I used Vuze in the past, but replaced it with µTorrent, and now use Deluge on ubuntu.
Audacious seems to be a nice application, but does it have an interface/skin like the cPro Hi-Fi 73?


First for Kompozer or NVU or Apanta, nothing is good in web designing. The best way is the hands on approach by using any text editor. I use Kompozer only for some fast work but when I have to do some good work then I always prefer coding in VIM.

Second p7zip-full and p7zip-rar, when installed open each and every rar, 7z or zip or other common compression format without any problem.

Well I suggested Vuze to you because you were asking about uTorrent and it's the closest in GUI and functionality to uTorrent.

And yes there are many repos which you can add to your apt/synaptic list like medibuntu for media codecs. All you have to do is follow jerenept's example or whenever you search a program, on their home page they will show if they have any repo for ubuntu.
Some programs when installed automatically add their repos like Skype and Opera web browser.
Some you can add manually like Bisigi themes and XBMC media center. All is up to you at end.

---

### Post by Kwijt on 2010-05-28
> **jerenept said:**
> GetDeb - go to [www.getdeb.net]("http://www.getdeb.net")
they have a convenient package that installs the PPA's (repos)

The website doesn't load, are the web services still down?

---

### Post by Kwijt on 2010-05-28
> **ManiDhillon said:**
> First for Kompozer or NVU or Apanta, nothing is good in web designing. The best way is the hands on approach by using any text editor. I use Kompozer only for some fast work but when I have to do some good work then I always prefer coding in VIM.
Yes, but I like the Dreamweaver interface, it's clean and easy to set-up, especially the file/ftp manager. I wrote most of my code in notepad and used Dreamweaver to clean it up and make it more readable, so I don't need a WYSIWYG-function.

> **ManiDhillon said:**
> Second p7zip-full and p7zip-rar, when installed open each and every rar, 7z or zip or other common compression format without any problem.
Installed, thanks!

> **ManiDhillon said:**
> Well I suggested Vuze to you because you were asking about uTorrent and it's the closest in GUI and functionality to uTorrent.
As I remember Vuze it was more a mediacenter than a BitTorrent-client, maybe things changed?

---

### Post by Kwijt on 2010-05-28
> **Kwijt said:**
> When I tried to completely remove evolution I accidentally removed some system packages and had to reinstall Ubuntu (luckily it doesn't take as long as a windows install), so now I would like to know how it is possible to remove the integrated Evolution/Empathy and use Thunderbird/Emesene instead, whilst keeping the panel object functional.

Is it possible to remove 1 (email/chat/micro-blogs) and 2 (account/chat), and put 3 (task bar) next to the workspace? And all this without messing up Ubuntu and keeping the other buttons.

---

### Post by ManiDhillon on 2010-05-28
[quote=Kwijt]As I remember Vuze it was more a mediacenter than a BitTorrent-client, maybe things changed?[/quote]
Well it still is media oriented but the bittorrent interface is almost same as of uTorrent.

[quote=Kwijt]Is it possible to remove 1 (email/chat/micro-blogs) and 2 (account/chat), and put 3 (task bar) next to the workspace? And all this without messing up Ubuntu and keeping the other buttons.[/quote]
Well I use Pidgin for IM and Thunderbird for mail and Pidgin is automatically integrated in mail and chat notification icon.
I am posting a screen shot.

---

