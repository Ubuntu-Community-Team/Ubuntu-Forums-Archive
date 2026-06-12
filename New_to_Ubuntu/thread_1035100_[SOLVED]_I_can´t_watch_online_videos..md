---
title: "[SOLVED] I can´t watch online videos."
date: 2009-01-09
forum: New to Ubuntu
---

### Post by gronater on 2009-01-09
Hi,

I got a problem with watching online videos. He only show white or black.
Im using firefox. I´ve maked two screenshots of it.

From online watch the tv-serie Friends
[http://img244.imageshack.us/img244/3453/schermafdruk102theonewidf3.png](http://img244.imageshack.us/img244/3453/schermafdruk102theonewidf3.png)

From Youtube
[http://img140.imageshack.us/img140/9211/schermafdrukyoutubestarcd4.png](http://img140.imageshack.us/img140/9211/schermafdrukyoutubestarcd4.png)

---

### Post by tuxxy on 2009-01-09
Have you isntalled Flash? this is needed to view online videos and is provided in either the flashplugin-nonfree package or the ubuntu-restricted-extras package.  I would go with the second one if its fresh install as it will proivde java, codecs, flash and much more.

Search for ubuntu-resrticted-extras using Synaptic or enter the following in terminal, make sure you restart your browser after.

```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Michael.Godawski on 2009-01-09
Try what tuxxy suggested.

Don't you get a pop up from Firefox that there are additional plugins to install when you come the page with the video you want to watch?

---

### Post by swotie on 2009-01-09
There appear to be some users still havng issues installing Adobe Flash. If you tried installing it already and are having issues, read on. First of all, it's worth completely purging the package from your system, along with any others which may be interfering with it and then reinstall it again. Will both 32-Bit and 64-Bit users execute this command:

***sudo apt-get purge flashplugin-nonfree gnash gnash-common && sudo apt-get install flashplugin-nonfree***

---

### Post by gronater on 2009-01-09
I have already installed ubuntu-restricted-extras and i don´t get a pop-up from Firefox.

---

### Post by swotie on 2009-01-09
Installing Flash on Ubuntu Manually

Why this tutorial?
The easiest way to install Flash in Ubuntu is visiting a website that uses Flash and then following the Install missing plugins Firefox prompt. More details on that process here. 

Sometimes, for some reason, that process doesn't work. If so, here's a good backup plan. 

Download the Flash Player

Search for the phrase flash player download 


In the search results, you should find Adobe's download center. Click on that. 


The download center will offer you three download options&#8212;.tar.gz, .rpm, and YUM. You want to download the .tar.gz file. 


You should be prompted by your web browser what you want to do with the compressed file. Firefox's default is to open it with the archive manager. That's a good choice. If you are not offered a choice, then download the file to your desktop and double-click the .tar.gz; the archive manager application should launch. 

Prepare the download file for installation

Once the archive manager opens, click the Extract button. 


You'll be asked where to extract the compressed .tar.gz file to. In this example, I chose the desktop, but just put it somewhere you can easily find later. 

Install the extracted download file

Press Alt-F2. This will open up a Run Application dialogue. In the dialogue, type: 


***gksudo nautilus***


This will launch the file manager (Nautilus) as root (computer administrator), allowing you to make system-wide changes. 


Since you are making system-wide changes, you'll be prompted for your password. Enter it. 


Navigate to the download file's location. Note that the user in this administrative file manager session is root, and so the file manager will open to the location /root. If you put the file in /home/username/Desktop, you'll have to navigate to that location. In this case, I put it in /home/cynthia/Desktop, so I had to navigate to /home/cynthia/Desktop/install_flash_player_9_linux to get to the installer file. 


Once you're in the installer directory, double-click the flashplayer-installer file. You'll be asked how you want to run it. Select Run in Terminal. 


You'll be prompted in the terminal to press Enter to continue. Do that. 


Then you'll be asked to exit any browsers you have running. So close Firefox (or Opera, Epiphany, or whatever web browser you might be using). Then press Enter 


Then you'll be asked to enter the installation path. The installation path should be 
/usr/lib/firefox
then press Enter 


You'll be asked if you want to proceed with the installation. Press y then Enter 


Then you'll be asked if you want to perform another installation. Press n then Enter. The terminal window should close after that. 


Now you can delete the install_flash_player_9_linux folder, and Flash should now be installed for your web browser.[/QUOTE]

---

### Post by gronater on 2009-01-09
If i enter the installation path I got a warning:

WARNING: Please enter a valid installation path.

I type this = /usr/lib/firefox

---

### Post by jsroth on 2009-01-09
For some unknown reason you have to make the directory /usr/lib/firefox/components then the installer will work.

---

### Post by gronater on 2009-01-09
I got a new warning:

WARNING: /usr/lib/firefox/components is not a directory

---

### Post by jsroth on 2009-01-09
Sorry, my previous post doesn't seem to be clear enough.

I meant you have to do this before you run the installer:
```
sudo mkdir /usr/lib/firefox/components
```

Then just run the installer as before with the installation directory /usr/lib/firefox

---

### Post by gronater on 2009-01-09
oops, thx

I have downloaded it but I still cant watch videos

---

### Post by jsroth on 2009-01-09
Have you installed any other flash player that could interfer with the adobe-player? Normally the adobe-player works very well. And do you get any errors or is it just as black as before?

---

### Post by Terl on 2009-01-09
@gronater:  I noticed you have another thread where you describe having graphics issues (different than this issue).  Do you have that issue resolved?  Have you installed drivers for your graphics card?  I wonder if this is not some bigger issue affecting other things; as jsroth said, the flash player works quite well so I am a bit surprised.

---

### Post by swotie on 2009-01-09
try to browse /usr/lib and see what your firefox libary is called ....  by me it si called /usr/lib/firefox-3.0.5

---

### Post by gronater on 2009-01-09
i dont really know. How can i see if i have installed the good driver and if I have got another flash player?

---

### Post by swotie on 2009-01-09
try to browse /usr/lib and see what your firefox libary is called .... by me it is called /usr/lib/firefox-3.0.5 ... and use this path in the manual flash installation

---

### Post by gronater on 2009-01-09
Its just called /usr/lib/firefox/ then i got 3 maps called ´components´, ´extensions´ and ´plugins´. How can I remove adobe flash player? Then can I install it again.

---

### Post by swotie on 2009-01-09
I don't think you need to remove something .... just try the manuel installation ... it is working by me

---

### Post by wolfen69 on 2009-01-09
> **gronater said:**
> If i enter the installation path I got a warning:

WARNING: Please enter a valid installation path.

I type this = /usr/lib/firefox

it should be /usr/lib/mozilla

---

### Post by gronater on 2009-01-09
if I typ /usr/lib/mozilla i got the same problem.

if I download this i on my terminalscreen:

WARNING: A newer version of the Adobe Flash Player has been detected in
         /usr/lib/firefox/plugins.
         The installer will overwrite this existing binary.



----------- Install Action Summary -----------

Adobe Flash Player 10 will be installed in the following directory:

Browser installation directory = /usr/lib/firefox

Proceed with the installation? (y/n/q): y

Installation complete.


Perform another installation? (y/n):

---

### Post by swotie on 2009-01-09
Press N and restart your computer.

Do the flash work after restating the computer?

---

### Post by gronater on 2009-01-11
No it´s still not working

---

### Post by swotie on 2009-01-11
try to go: System>administration>synapic ... search > flash 10 ... 

is adobeflash-plugin mark with a green mark ?

---

### Post by gronater on 2009-01-11
Yes it is

---

### Post by swotie on 2009-01-11
hmm ... I must give up .. Another must take over ... sorry

---

### Post by gronater on 2009-01-11
thanks for helping

---

### Post by gronater on 2009-01-12
I have deleted everything that can conflict Adobe flash 10 and reinstalled adobe flash 10 and now he´s doing great.

---

