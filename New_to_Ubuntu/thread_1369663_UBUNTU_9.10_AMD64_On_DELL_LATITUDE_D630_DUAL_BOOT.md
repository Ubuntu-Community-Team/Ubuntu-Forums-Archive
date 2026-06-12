---
title: "UBUNTU 9.10 AMD64 On DELL LATITUDE D630 DUAL BOOT"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by RBarak on 2010-01-01
[FONT=&quot](pdf with pics attached)
[/FONT][SIZE=1](also in doc format)[/SIZE]
[FONT=&quot]
[/FONT]
[FONT=&quot]Hello,[/FONT]
  [FONT=&quot]I’m a seriously dumm newbie who just wanted to stop using Windows. Here is how I did it:[/FONT]
  
  
  [FONT=&quot]STEP 1 – PARTITION THE HARD DRIVE[/FONT]
  [FONT=&quot]I used the program “partition magic” to split my hard drive in two.[/FONT]
  
  [FONT=&quot]STEP 2 – INSTALL UBUNTU[/FONT]
  I installed “side by side” with windows (well, just in case…)
  The installation program showed my partitions in three colors: one that already has windows, one for Ubuntu, and one for what’s left. I gave Ubuntu 15 Giga.
  Languages: English and Hebrew (there’s a button on the bottom to check the language)
   
  STEP 3 – GET WIFI
  Log on to regular internet (I know, it sucks).
  Go to: System – Administration – Hardware Drivers. Install the 2nd driver. It’s called Broadcom STA Wireless Driver.
   
  [FONT=&quot]STEP 4 – FIX MEDIA STUFF: MP3, MPEG, MP4, DVD…[/FONT]
  [FONT=&quot]First connect to the internet.[/FONT]
  [FONT=&quot]Try to open an mp3 file. It asks you if you want it to search for the plug. Say yes. Then choose and install: [/FONT][FONT=&quot]gstreamer0.10-fluendo-mp3 [/FONT]
  [FONT=&quot]Try to open an mp4 file. It asks you if you want it to search for the plug. Say yes. Then choose and install:[/FONT]
  [FONT=&quot]gstreamer0.10-plugins-bad[/FONT]
  [FONT=&quot]Try to play a DVD. By now everything should work. If it doesn’t, let it search for a plug. You can also search and install the following file: [/FONT][FONT=&quot]libdvdcss2_1.2.10-1_amd64.deb (.deb files –right click and open with GDebi Package installer)[/FONT]
   
  [FONT=&quot]STEP 5 – SETTING THE PRINTER[/FONT]
  [FONT=&quot]I was lucky here. I have an HP printer [/FONT][FONT=&quot](HP1018 ). HP are very nice. They give you printer drivers at:[/FONT]
  [[COLOR=blue][FONT=&quot]http://hplipopensource.com/hplip-web/index.html[/FONT][/COLOR]]("http://hplipopensource.com/hplip-web/index.html") 
  Click “download HPLIP”
  [FONT=&quot]Follow instructions and download the right file (My file was: hplip-3.9.12.run).[/FONT]
  [FONT=&quot]Connect to the internet.[/FONT]
  [FONT=&quot]In terminal write:[/FONT]
  [COLOR=blue][FONT=&quot]sh hplip-3.9.12.run[/FONT][/COLOR]
  [FONT=&quot]Then follow instructions. (Mine were: -a[/FONT][FONT=&quot]-y. After the download finished I had to restart the computer, go back to terminal and write [/FONT][COLOR=blue]hp-setup. [/COLOR][FONT=&quot]It me[/FONT]ssed around a bit, asking to install the needed plugin. I let it and in a few minutes it was working).
  [FONT=&quot]STEP 8 GET FLASH PLAYER[/FONT]
  Go to Applications - Ubuntu software center.
  Search and install Flash.
  
  
  [FONT=&quot]GENERAL ADVICE[/FONT]
  [FONT=&quot]If you need a program always try to find it at [/FONT]Ubuntu software center (under Applications)
  If it’s not there get a .deb file. They usually install automatically if you [FONT=&quot]right click and open with GDebi Package installer.[/FONT]
  [FONT=&quot]If that’s not possible try to find a tutorial that begins with “sudo apt-get install”[/FONT]
  [FONT=&quot]Otherwise you’re on your own at installation.[/FONT]
  
  [FONT=&quot]OPTIONAL STEPS (FONTS, STYPE, HEBRW FONTS, WINE, NERO, ETC):[/FONT]
  [FONT=&quot]STEP 9 FONTS[/FONT]
  [FONT=&quot]Ok, if you want to add fonts. The directory is: /USR/SHARE/FONTS[/FONT]
  [FONT=&quot]If you just want a few Microsoft office fonts for Open office go:[/FONT]
  [COLOR=blue][FONT=&quot]$sudo apt-get install msttcorefonts[/FONT][/COLOR]
  
  [FONT=&quot]STEP 10 GET SKYPE[/FONT]
  Download from skype.com.
  skype-ubuntu-intrepid_2.1.0.47-1_amd64.deb [FONT=&quot](.deb files –right click and open with GDebi Package installer)[/FONT]
  Go to System – Preferences – Sound – Input and switch from microphone1 to microphone2
  
  
  [FONT=&quot]STEP 11 GET HEBREW FONTS[/FONT]
  [FONT=&quot]I found instructions at: [https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto).[/FONT]
  [FONT=&quot]Basically:[/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install culmus xfonts-efont-unicode xfonts-efont-unicode-ib xfonts-intl-european msttcorefonts[/FONT][/COLOR]
  [FONT=&quot]Also:[/FONT]
  [FONT=&quot]Openoffice.org Hebrew support [/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install openoffice.org-l10n-he[/FONT][/COLOR]
  [FONT=&quot]Hebrew standalone spell checker [/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install hspell hspell-gui[/FONT][/COLOR]
  [FONT=&quot]Hebrew support for Emacs [/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install emacs-intl-fonts[/FONT][/COLOR]
  [FONT=&quot]Hebrew support for KOffice [/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install koffice-i18n-he[/FONT][/COLOR]
  
  [FONT=&quot]STEP 12 GET NERO[/FONT]
  [FONT=&quot]I just love it and I bought the latest version at nero.com. The file was called nerolinux-4.0.0.0-x86_64.deb[/FONT]
  
  [FONT=&quot]STEP 13 GET WINE[/FONT]
  [FONT=&quot]Wine allows Linux to run Windows programs (don’t kill me, please). There is a short video at [/FONT][FONT=&quot][http://www.youtube.com/watch?v=P_DcHfEnQnU](http://www.youtube.com/watch?v=P_DcHfEnQnU)[/FONT]
  [FONT=&quot]The command is:[/FONT]
  [COLOR=blue][FONT=&quot]sudo apt-get install wine[/FONT][/COLOR]
  [FONT=&quot]After this you can open programs by right clicking and opening with wine.[/FONT]
  
  [FONT=&quot]STEP 14 GET [/FONT][FONT=&quot]WINETRIX[/FONT]
  [COLOR=blue][FONT=&quot]wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)[/FONT][/COLOR]
  [COLOR=blue][FONT=&quot]sh winetricks corefonts vcrun6[/FONT][/COLOR]
  
  [FONT=&quot]STEP 15 WINDOWS FONTS FOR WINE[/FONT]
  [FONT=&quot]Copy all the fonts from window (c:\windows\fonts) to wine (/home/YOURUSERNAME/.wine/drive_c/windows/Fonts)[/FONT]
  
  [FONT=&quot]*There are two things I haven’t figured out yet: is there a version of Dazuko for my Ubuntu? And How do I get Hebrew not to write backwards in Wine.[/FONT]
  [FONT=&quot]**I just wanted to say how thankful I am for all those forums and tutorial, without which I couldn’t get started.[/FONT]

---

### Post by ikt on 2010-01-02
> **RBarak said:**
>   [FONT=&quot]*There are two things I haven’t figured out yet: is there a version of Dazuko for my Ubuntu?[/FONT]

Dazuko? The program that allows anti-virus programs to scan in real time?

---

### Post by RBarak on 2011-10-05
Hi,
As you all know a new Ubuntu is coming next week and then I'll redo the howto.
Today I'm writing Hebrew instructions for the 10.10 Ubuntu.
Click here to read:
[http://ubuntuforums.org/showthread.php?p=11311955#post11311955](http://ubuntuforums.org/showthread.php?p=11311955#post11311955)

---

### Post by oldos2er on 2011-10-05
Closed, necromancy.

---

