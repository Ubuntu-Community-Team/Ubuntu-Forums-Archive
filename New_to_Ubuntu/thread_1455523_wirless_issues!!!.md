---
title: "wirless issues!!!"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by jcfuwbs on 2010-04-16
Ok, i'm new (which is quite apparent) to anything linux based or otherwise. I have been a windows based user my entire life but having grown tires of the windows issues i have converted to Ubuntu. I cannot get my wireless to work so i am on another computer until i can get the wireless to work. I have tried several steps to get my wireless to work such as going to System>admin>drivers it gave me a list of drivers and i chose to install the broadcom b43 wireless driver re booted and it still shows as inactive when i return to the drivers on the machine. My laptop is a Hp Pavillion dv8000 and it has a BCM4318 wireless LAN controller from broadcom as the wireless card.  i have the newest version of ubuntu available since i downloaded and installed today Any help or suggestions would be great. I am not sure if the info i provided was enough or even helpful But thanks for your time anyhow!
 
any advice would be great!
 
 
oh i also tried to extract the driver from my CD via cabextract but is says it cant install it so i downloaded it and tried to extract it via Cdrom but it wont extract!

---

### Post by roger_1960 on 2010-04-16
Hi

Silly question perhaps, but have you right clicked the network icon in the top right panel and checked the "enable wireless" box?

---

### Post by anewguy on 2010-04-16
Well, you've been trying the right things - trying to get the "built-in" drivers to work.  However, since you have been unsuccessful so far, there is another way - loading the Windows drivers to Ubuntu.  I'm going to assume you have the LiveCD from which you installed Ubuntu.  Have that ready as you'll need that.

Also, we need the Windows driver files - should be something similar to bcmwl5.inf and .sys (might be bcmwl5a or something similar).  Put those on a medium you can use on the Ubuntu computer - perhaps burn to a CD or put on a USB flash drive.

With the LiveCD in hand as well as the driver files, start up your Ubuntu machine.  Once booted, do the following:

- copy the driver files to your desktop

- put in the LiveCD -> if a message comes up about a CD with packages being found, just cancel the question about going to package manager.

- via "Places", navigate the CD to the /pool/main/n folder

- open the ndiswrapper folder

- double-click on each of the files there (should be 2 - one for common, one for utilities) to install them.

- open a terminal window and do the following:

sudo ndiswrapper -l <press enter>  That's a lower case "L" for "List"

If anything is returned, you must sudo ndiswrapper -e xxxxxx <press enter> where xxxxxx is the driver name shown in the list.  Repeat this until the no list is return from the sudo ndiswrapper -l

sudo gedit /etc/modules <press enter>  This will open the /etc/modules file in an editor.  Navigate to the end of the file and add this as a new line:

ndiswrapper

save the file and exit the editor

sudo gedit /etc/modprobe.d/blacklist.conf <press enter>.  This calls up the editor again on the blacklist.conf file - a file containing kernel modules we don't want loaded.  Navigate to the end of this file and add the following new lines:

blacklist b43
blacklist ssb
blacklist b43-legacy
blacklist bcm43xx

save the file and exit the editor.

Now we can actually work on loading the driver:

cd Desktop

sudo ndiswrapper -i xxxxxxx.inf <press enter>  That's a lower case "I" (for insert).  Replace xxxxxxx.inf with the actual name of your driver .inf file (such as bcmwl5.inf)

sudo ndiswrapper -l <press enter>  That's a lower case "L" for "list" again.  It should show the drive installed and the device found.

sudo depmod -a <press enter>

sudo modprobe ndiswrapper <press enter>

sudo ndiswrapper -m

Now, reboot.  When your computer is back up check under the network manager icon to see if you can see wireless networks now.

Dave ;)

---

### Post by trig on 2010-04-16
my brothere had a similar problem, and he had to check the little turn it off and back on then check the little box ans it worked.

---

### Post by jcfuwbs on 2010-04-16
yes the wireless is enabled but ever since i installed ubuntu the blue light indicating my wireless is on has not been on i'm in the process of doing things anewguys way :-) already 8 hours into stress yay me

---

### Post by jcfuwbs on 2010-04-16
ok few issues 
 
when i type in the black list commands it will not allow me to save 
 
and my drivers are in a EXE format for some reason and i cannot get to the .inf files!

---

### Post by IndyGunFreak on 2010-04-16
I don't use Broadcom.. but doing some searching I believe the file you're looking for is bcmwl6.inf .. IF that is the case(trust but verify), its in this zip file....

[http://download.cnet.com/Broadcom-WLAN-4318-Driver-4-102-15-56-zip/3000-2112_4-209977.html](http://download.cnet.com/Broadcom-WLAN-4318-Driver-4-102-15-56-zip/3000-2112_4-209977.html)

Hope that helps.. for the blacklist commands,. make sure you're running sudo gedit and that you have root access to edit the file.

---

### Post by anewguy on 2010-04-16
> **jcfuwbs said:**
> ok few issues 
 
when i type in the black list commands it will not allow me to save 
 
and my drivers are in a EXE format for some reason and i cannot get to the .inf files!

If you need the driver files let me know and I can get them for you.  Also, as mentioned above, be sure you put the "sudo " in front of everything like I showed - the blacklist file is just one of thousands owned by root, and you need superuser rights to access them - that what the "sudo " in front of the command does - gives you temporary superuser priviledges.  

dave ;)

---

