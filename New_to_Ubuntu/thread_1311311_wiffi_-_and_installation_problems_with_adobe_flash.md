---
title: "wiffi - and installation problems with adobe flash and wine"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by lucem auspicio on 2009-11-02
Originally Posted by **lucem auspicio** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8218858#post8218858") 				
 				[I]Hello everyone 

I am new in linux, in addition I don't know about computer either, I have a portatil pc hp pavilion dv8000, the sticker said it is a AMD turion64, graphics by radeon xpress and it has 2G of RAM. Based on this I install a iso of ubuntu 9.10 64bits, problems that I have, ubuntu didn't recognise wifi, I can not see videos because I tried to install adobe flash for different ways, installing the palyer 10 linux rpm, in the windows that appeared I clicked on /./usr/lib/flash-plugin/ then i clicked setup, then it start with #!/bin/bash

# These are the standard browser locations as found within Red Hat, Mandrake
# and SuSE Linux, and the tarball installers. 

when this message finished I save and closed it, then I turn off the cpu thern I run firefox but doesn't work, I also tried ubuntu software application but the message said not available for your hardware architecture, I also tried to install wine with this application and this time appeared a message: package dependecies cannot be resolved and...

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time. 


any light about this that can help would be very welcome


by the way I am not familiar with forums either so I appologise if I made mistakes posting this information too

thanks[/I]

---

### Post by mrboojive on 2009-11-02
The easiest way to install Flash is to go to a terminal and enter: ```
sudo apt-get install flashplugin-nonfree
```
That command will install the 32 bit version of Flash along with a wrapper so that it will work on your 64 bit system. Alternatively, since you are on 64 bit, you could go to the Adobe Labs website ([http://labs.adobe.com/](http://labs.adobe.com/)) and download the alpha version of the native 64 bit Flash player. Although it is an alpha, it is very stable. The download from there is a .tar.gz file containing a .so file. You would need to extract the .so file and then place it in the .mozilla/plugins/ folder in your home directory.

The first step to enabling your wireless card is to go to System > Administration > Hardware Drivers. Are there any drivers there for wireless cards? If so, try to enable them. If not, do you know what brand or model of wireless card you have? If you don't know what wireless card you have, go to the terminal and enter the command ```
lspci | grep Network
``` and post the results of that here and hopefully someone can help you.

Also note that RPM files do not work on Ubuntu. RPM files are used by Red Hat, SuSE, and some other distros. However, Ubuntu is based on Debian, which uses DEB files instead of RPM files. As a Linux beginner, there are very few situations where you will manually need to download a package file. You should probably stick to installing things from the Ubuntu repositories using the Software Center, Synaptic, or the terminal. But if you come across a situation where you need to download a package manually, you should be downloading a DEB file instead of an RPM file.

---

### Post by lucem auspicio on 2009-11-02
dear [mrboojive]("http://ubuntuforums.org/member.php?u=500497")
thank you very much for your help, I tried with the code 
sudo apt-get install flashplugin-nonfree that you recommend me, however  I got the following message    	 	 	 	 	 	  E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 





**I also try the alpha version, I download the so file, but I don't know how to place it in the .mozilla/plugins/ folder, where is this directory????**




About System > Administration > Hardware Drivers, I did it and the drivers is    	 	 	 	 	 	  broadcom b43 wireless driver
 fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.


then I open the terminal application in accesories and followed the instructions.. I put Ubuntu 9.10 ISO in the cd dom and paste the command **sudo apt-get install b43-fwcutter that I found in internet after look for **broadcom b43 wireless driver ...  and it seems to install the necessary files, I going to turn off the cp to know if it works


again thank

 very much lucem auspicio

---

### Post by mrboojive on 2009-11-02
That error means you had Synaptic or the restricted drivers manager or some other program that can install things open at the time. Try closing all the open programs and entering the command again. Or you can use the one you downloaded. .mozilla/plugins/ is a hidden folder in your home folder. Go to your home directory under the Places menu. Then press control + H to show hidden files. Then copy the .so file to .mozilla/plugins. You may need to create the plugins folder under .mozilla.

---

### Post by lucem auspicio on 2009-11-02
Thanks....  [mrboojive]("http://ubuntuforums.org/member.php?u=500497")

 after turn off the cp I click again hardward drivers and activated the already installed files then the light of my wireless device turn on.. after this I change some paramether and voila ...now I have internet wireless.

I did what you suggested   ...Then press control + H to show hidden files ... **I found **mozilla  then i found two directories firefox and extension, plugins was not in any of these.

I am very grateful

---

### Post by mrboojive on 2009-11-02
If you don't have a plugins folder under .mozilla, you need to create it. Go into .mozilla, create a new folder, and name it "plugins." Then put the .so file you downloaded into the plugins folder. Restart your browser and Flash should work.

---

### Post by lucem auspicio on 2009-11-02
excellent it works.... did you known something about wine HQ?  I couldn't install either  by the way some program that allows me to use my webcam maxell or genius and the printer doesn't work ...ubuntu recognise lexmark series 1200 but mine is x1270 and I click test print page and didn't work 

sorry if I am give you so much work, but finilly I feel I can live without windows

thank you [mrboojive]("http://ubuntuforums.org/member.php?u=500497")

---

### Post by mrboojive on 2009-11-02
If you want to install Wine, you can do ```
sudo apt-get install wine1.2
``` which will get you a very up to date version of Wine. I don't know much about webcams or printers. I believe most webcams should work automatically with Ubuntu. If just want to do video chatting with your webcam, you can use Empathy, which is installed by default. If you want to take pictures or videos with your webcam, there's a program called Cheese you can install. Just do ```
sudo apt-get install cheese
```You should probably try searching Google or these forums to see if you can find anything about setting up your printer.

---

### Post by lucem auspicio on 2009-11-02
Dear [mrboojive]("http://ubuntuforums.org/member.php?u=500497")
 
Thank for your help, I also have been looking for solution and I found the opcion to download cheese from application/ ubuntu software center ... search cheese but it said : not availble in the current date and if I use the terminal it said:

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?  the same error happened with wine and alien too in this case with alien it said that it was not able to fine the package, you told me that I probably had synaptic open... it was rigth so I close and run the code again and the message was: E: Couldn't find package cheese, and these errors were the same to alien, and wine

any idea, I really appreciate your help

again very kind

---

### Post by mrboojive on 2009-11-02
You're also going to get that error if you have the Software Center open. Try closing all of your open programs, then open a terminal and type in```
sudo apt-get update
``` followed by ```
sudo apt-get install cheese
```

---

### Post by lucem auspicio on 2009-11-03
Ok I did it, I closed everything and paste the code now it is in 63% waiting for headers and keep there ... I have done this before and it takes a lot of time and when it finished  many of the items said error but now I guess it was because I have opened other applications so I will tell you tomorrow if it works.. good night and thank you for your invaluable help

---

### Post by lucem auspicio on 2009-11-03
8 hours later the process was in a 66% and I present the following message:
  	 	 	 	 	 	  Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/main Packages      
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/restricted Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/restricted Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/main Sources       
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/multiverse Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/universe Sources   
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/universe Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic/multiverse Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/main Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/restricted Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/restricted Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/main Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/multiverse Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/universe Sources  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/universe Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-updates/multiverse Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-backports/main Packages  
   Connection failed  
 Err [http://cr.archive.ubuntu.com](http://cr.archive.ubuntu.com) karmic-backports/restricted Packages  
   Connection failed 





any idea ... what do I did wrong???/

---

### Post by lucem auspicio on 2009-11-04
No it doesn't work I don't know what do I doing wrong 
 
any idea, please

---

### Post by mrboojive on 2009-11-04
Something is wrong with the server that your computer is trying to get updates from. Go to System > Administration > Software Sources and use the drop down box next to where it says "Download from" to select a different server.

---

### Post by lucem auspicio on 2009-11-04
[mrboojive]("http://ubuntuforums.org/member.php?u=500497") you did it again, thank you very much... I change the server and now I am able to download the files,  one more questions if it is possible ... I have a amd64 bits, I was reading teh ubuntu pocket guide and reference and the author said that if I had a 64 bit equipment but less than 4 G of RAM it was not worthy to download Ubuntu 64bit because It could have installing trouble... and in that case is better to install the 32 bit version .... what do you think???


again thank you very much you deserve more beans

---

### Post by x C0MMAND0 x on 2009-11-04
If you don't have more than 3.2gb or ram or so, you won't really have any benefit to having 64bit installation.  Having said that, it's not going to hurt you to have a 64bit OS even if you aren't utilizing it.

Think of it as having a car that can go 200mph, but you never drive it above 80mph.  Does it hurt anything to still have the car instead of getting one that tops out at 120mph?  Not at all.

Since you already have it installed there's no reason to downgrade to a 32bit install, in my opinion.

---

### Post by mrboojive on 2009-11-05
Yes, there's no reason for you to do a re-install. In the past, Flash and Java and some other programs have had problems on 64-bit, but I think those issues are basically all worked out now. Plus, if you ever come across a program that is 32-bit only, you will still be able to run it from your 64-bit setup.

---

### Post by lucem auspicio on 2009-11-05
Thank you very much [mrboojive]("http://ubuntuforums.org/member.php?u=500497") and [x C0MMAND0 x]("http://ubuntuforums.org/member.php?u=394170"), I have windows 7 and ubuntu in the main disk, I have to 2 hdisc in my cp but today I formatted the hdisc (where the software was)  and installed ubuntu 9.10 64bits.  Until now I am very happy with Ubuntu, I resolved most of the problems like see videos made for windows.  I need to resolve some inconvenient with the printer, but now I get wireless,  a some softwares like Wine ... however I still have to figure out how to install bioedit and mega, with wine and alien.

I am following the instructions of wine web  [http://www.wine-reviews.net/applications/bioedit-biological-sequence-alignment-editor-on-linux-with-wine.html](http://www.wine-reviews.net/applications/bioedit-biological-sequence-alignment-editor-on-linux-with-wine.html), I download bioedit which was zipped and I clicked on the exe file and it was installed but it didn't run I am going to try with mega which is a rpm file

again thank you very much both of you

---

