---
title: "Unable to install Adobe Flash player in Ubuntu 9.10"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Cool G5 on 2009-11-09
Hello,
I have been unable to install adobe flash player in ubuntu 9.10. I downloaded .deb from the official site but it points out to a missing dependency. I downloaded the tar.gz but was unable to get any installer within but got libflashplayer.so. What is this file? Does it needs to be copied somewhere?

---

### Post by MelDJ on 2009-11-09
install the flashplugin-installer package from synaptic?

---

### Post by Cool G5 on 2009-11-09
> **MelDJ said:**
> install the flashplugin-installer package from synaptic?

Getting this error:

[[IMG]http://img9.imageshack.us/img9/1072/adobepackagebroken.th.png[/IMG]](http://img9.imageshack.us/i/adobepackagebroken.png/)

---

### Post by MelDJ on 2009-11-09
the picture is too small for me to see. just take a screenshot and attach it to your post. or just copy and paste the error here

---

### Post by ibizatunes on 2009-11-09
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by marcopolo1981 on 2009-11-09
Hi Cool.

Are you running a 64bit system?
Is the .so file you downloaded from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) ?
If it is, that file needs to be copied to /usr/lib/firefox-addons/plugins/

Open a terminal and type 
sudo nautilus

Enter your password

navigate to /usr/lib/firefox-addons/plugins/ 

Copy or move that file to this folder and restart firefox. You should now be able to watch flash.

Please go to [http://www.youtube.com/watch?v=cyheJ480LYA](http://www.youtube.com/watch?v=cyheJ480LYA) to check.
You can actually go to any flash video, but this one is my current (and long time) favourite. :D

If you are running a 32 bit system, what dependency does it say is missing?

Try to add the 32bit libflashplayer.so file you downloaded to /usr/lib/firefox-addons/plugins/ and restart firefox.

---

### Post by Cool G5 on 2009-11-09
I forgot to uncheck the resize radio button while uploading to imageshack. I hope this one tell the story.

[[IMG]http://img410.imageshack.us/img410/1072/adobepackagebroken.th.png[/IMG]](http://img410.imageshack.us/i/adobepackagebroken.png/)

---

### Post by MelDJ on 2009-11-09
in terminal run sudo apt-get install -f then install flash

---

### Post by Cool G5 on 2009-11-09
I am on a 32bit system. Here is what I get when I try to install it via the terminal.

```
gaurav@gaurav-desktop:~/Downloads$ sudo dpkg --install install_flash_player_10_linux.deb 
[sudo] password for gaurav: 
(Reading database ... 114055 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
dpkg: dependency problems prevent configuration of adobe-flashplugin:
 adobe-flashplugin depends on libnspr4-dev; however:
  Package libnspr4-dev is not installed.
 adobe-flashplugin depends on libnss3-dev; however:
  Package libnss3-dev is not installed.
dpkg: error processing adobe-flashplugin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobe-flashplugin

```

---

### Post by Cool G5 on 2009-11-09
> **MelDJ said:**
> in terminal run sudo apt-get install -f then install flash

Done that & then proceeded installing via deb. Here is what I got.

```
gaurav@gaurav-desktop:~/Downloads$ sudo dpkg --install install_flash_player_10_linux.deb 
(Reading database ... 114256 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.32.18-1 (using install_flash_player_10_linux.deb) ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing install_flash_player_10_linux.deb (--install):
 subprocess new pre-removal script returned error exit status 2
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install_flash_player_10_linux.deb

```

---

### Post by MelDJ on 2009-11-09
did your run this command first sudo apt-get install -f?
do that first.
to install .deb packages, you just have to double click the package and press install package. 
see this link too: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by marcopolo1981 on 2009-11-09
Try typing this into a terminal:

sudo apt-get install libnspr4-dev libnss3-dev adobe-flashplugin

---

### Post by Hazey on 2009-11-09
Hi guy,

copy the libflashplayer.so to the /usr/lib/firefox(your version)/plugins folder. Don't forget to change the permissions, so you can execute it ("chmod 707 libflashplayer.so" its not the best, but the easiest way). Don't forget to restart ff.

You must execute all commands as Superuser (sudo or su).

Hazey

---

### Post by Cool G5 on 2009-11-09
> **MelDJ said:**
> did your run this command first sudo apt-get install -f?
do that first.
to install .deb packages, you just have to double click the package and press install package. 
see this link too: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

Yes, I did that.

I have posted the error on the previous page when I tried to install via the terminal. Upon double clicking the .deb package I get an error the package might be corrupted or you are not allowed to open this file. Check permissions of the file.

---

### Post by Cool G5 on 2009-11-09
> **marcopolo1981 said:**
> Try typing this into a terminal:

sudo apt-get install libnspr4-dev libnss3-dev adobe-flashplugin

On this I get,

```
sudo apt-get install libnspr4-dev libnss3-dev adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by MelDJ on 2009-11-09
try just clicking the .deb file to install and not using terminal and see what it says

---

### Post by Cool G5 on 2009-11-09
> **MelDJ said:**
> try just clicking the .deb file to install and not using terminal and see what it says

I already did that, check the #14 post above.

> Upon double clicking the .deb package I get an error the package might be corrupted or you are not allowed to open this file. Check permissions of the file. 		

---

### Post by MelDJ on 2009-11-09
try this thread: [http://ubuntuforums.org/showthread.php?t=1320250](http://ubuntuforums.org/showthread.php?t=1320250)

---

### Post by 3rdalbum on 2009-11-09
Download the 'adobe-flashplugin' package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and put it into /var/cache/archives/. (you need to do this as root/sudo). Now your package manager will work again.

---

### Post by Cool G5 on 2009-11-09
> **MelDJ said:**
> try this thread: [http://ubuntuforums.org/showthread.php?t=1320250](http://ubuntuforums.org/showthread.php?t=1320250)

Synaptic fails to open giving the following error:

```
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

---

### Post by Cool G5 on 2009-11-09
> **3rdalbum said:**
> Download the 'adobe-flashplugin' package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and put it into /var/cache/archives/. (you need to do this as root/sudo). Now your package manager will work again.

I downloaded flashplugin installer but just when I executed it by double-clicking, package installer gave;

```
The package might be corrupted or you are not allowed to open the file. Check the file permissions.
```

---

### Post by qianshiming on 2009-11-09
> **marcopolo1981 said:**
> Hi Cool.

Are you running a 64bit system?
Is the .so file you downloaded from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) ?
If it is, that file needs to be copied to /usr/lib/firefox-addons/plugins/

Open a terminal and type 
sudo nautilus

Enter your password

navigate to /usr/lib/firefox-addons/plugins/ 

Copy or move that file to this folder and restart firefox. You should now be able to watch flash.

Please go to [http://www.youtube.com/watch?v=cyheJ480LYA](http://www.youtube.com/watch?v=cyheJ480LYA) to check.
You can actually go to any flash video, but this one is my current (and long time) favourite. :D

If you are running a 32 bit system, what dependency does it say is missing?

Try to add the 32bit libflashplayer.so file you downloaded to /usr/lib/firefox-addons/plugins/ and restart firefox.

Thank you for your advice!
My system is 32 bit.
When I do the same things as 1# ,I meet the same problem too,so I install the dependency as the apt-get show,after that ,I get the a libflashplayer.so in /usr/lib/adobe-flashplugin/  ,and copy it to  /usr/lib/firefox-addons/plugin with change the permision to o+x .After these steps ,when I open the [www.youku.com](www.youku.com) ,I can see the Flash now !

Thanks !:lolflag:

---

### Post by cancerdude on 2009-11-09
For an easy way. Open FF in search bar click magnifying glass. Google page
will show. Click videos then follow. Late but Happy your Happy.

---

### Post by BrandonBan6 on 2009-11-09
I used the new Ubuntu Software Center to install Flash on both of my 9.10 systems (1 32 bit and 1 64 bit), I was able to install them without any issues. 

Just pull up the Ubuntu Software Center from the Applications menu, search "flash", click the adobe search result, click install and then reboot. Same with the Java platform.

---

### Post by Cool G5 on 2009-11-10
> **marcopolo1981 said:**
> Hi Cool.

Are you running a 64bit system?
Is the .so file you downloaded from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) ?
If it is, that file needs to be copied to /usr/lib/firefox-addons/plugins/

Open a terminal and type 
sudo nautilus

Enter your password

navigate to /usr/lib/firefox-addons/plugins/ 

Copy or move that file to this folder and restart firefox. You should now be able to watch flash.

Please go to [http://www.youtube.com/watch?v=cyheJ480LYA](http://www.youtube.com/watch?v=cyheJ480LYA) to check.
You can actually go to any flash video, but this one is my current (and long time) favourite. :D

If you are running a 32 bit system, what dependency does it say is missing?

Try to add the 32bit libflashplayer.so file you downloaded to /usr/lib/firefox-addons/plugins/ and restart firefox.

Thanks its working. :)
Your video plays smoothly too ;)

---

### Post by marcopolo1981 on 2009-11-10
To Cool G5 and qianshiming

Glad I could help and that it works now.

Mark

---

### Post by dzon65 on 2009-11-10
A fiend of mine had the same problem.Installing with the software center did the job.

---

### Post by opennick on 2009-11-10
Hope its gonna work this way : 
Download and Install **libnspr4-dev **from [B]
[http://launchpadlibrarian.net/30103827/libnspr4-dev_4.8-0ubuntu1_i386.deb](http://launchpadlibrarian.net/30103827/libnspr4-dev_4.8-0ubuntu1_i386.deb)
[/B]AND
 [B][http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29)


Thanks 

[/B]

---

### Post by opennick on 2009-11-10
Hope its gonna work this way : 
Download and Install **libnspr4-dev **from [B]
[http://launchpadlibrarian.net/301038...untu1_i386.deb]("http://launchpadlibrarian.net/30103827/libnspr4-dev_4.8-0ubuntu1_i386.deb")
[/B]AND
 [B][http://get.adobe.com/flashplayer/tha...nux_%28.deb%29]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")


Thanks 
[/B]

---

### Post by opennick on 2009-11-10
Hope its gonna work this way : 
Download and Install **libnspr4-dev **from [B]
[http://launchpadlibrarian.net/301038...untu1_i386.deb]("http://launchpadlibrarian.net/30103827/libnspr4-dev_4.8-0ubuntu1_i386.deb")
[/B]AND
 [B][http://get.adobe.com/flashplayer/tha...nux_%28.deb%29]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29")


Thanks 
[/B]

---

### Post by Cool G5 on 2009-11-11
@marcopolo1981 - Youtube works fine but when I load those flash games on Facebook, Firefox starts to crawl. Is it due to low system RAM? My system has just 432MB RAM while 64MB is reserved for onboard via graphics.

---

### Post by marcopolo1981 on 2009-11-11
@Cool
I have no problems playing facebook games, but I am using the x64 bit flash.
It may be your RAM, or it may that the 32 bit has a glitch. 
Try going to System>Administration>System Monitor and see if you can see how much of your RAM is actually in use while you play facebook games. It may be that you are using SWAP. If you are, you need more RAM. If not, the 32 bit flash has a problem.
Sorry I can't be of more help.

Mark

---

### Post by tance_bt on 2009-11-24
Hi, when i try to install flash player this eror is coming "Error: Dependency is not satisfiable: libnss3-dev". I can't open my farm vile!! If any one knowes the anser for my question pls. answer to me. BTW i have 32bit. OS (Ubuntu 9.10):sad:

---

