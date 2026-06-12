---
title: "help me; installing belkin wireless desktop card (FSD6001_ver3)"
date: 2005-11-21
forum: Networking &amp; Wireless
---

### Post by Sir Frederic on 2005-11-21
i believe this card has a realtek 8180 chip;
i have tried both the belkin driver .inf file and also the one from the realek site but nothing appears to work.
take into account that i am really new to linux and know virtually nothing so i could have been doing this the wrong way and i really need an every-step-of-the-way type tutorial
i am using ubuntu 5.10.

also ndiswrapper appears to work fine except when i check for installed drivers it always tels me 'no drivers installed' or something like that.

help me please or i may be forced back to windows permanently.

---

### Post by carlosqueso on 2005-11-21
Have you tried navigating to the directory that has the driver and typing:

sudo ndiswrapper -i <driver's .INF file>

I don't know if you've already done that...but that's all I know

---

### Post by Lambert on 2005-11-21
You're very new to linux and this may be a challenge. 

1. Looking at the list of known cards that work with ndiswraper, I don't see your card in the list. Only v2. So your card/driver may not work with ndiswrapper.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

But this is what I would suggest.
1. Make a directory in your home folder called drivers and copy all the files that are in the drivers folder on your cd (.sys .dll .inf etc...) to this directory.  Sometimes this solves the problem as it seems the files are linked somehow.

Wiki page on ndiswrapper 
[https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29)

2. I show your card supported by a linux driver but it is not in a .deb format so it will have to be compiled. Being new this is the challenging part as it can be confusing. But it's a good learning experience.

[http://linux-wless.passys.nl/query_part.php?brandname=Belkin&zoek=brandname](http://linux-wless.passys.nl/query_part.php?brandname=Belkin&zoek=brandname)

I know very little about compiling so here is some information you can read.

[https://wiki.ubuntu.com/CompilingEasyHowTo?highlight=%28compiling%29](https://wiki.ubuntu.com/CompilingEasyHowTo?highlight=%28compiling%29)
[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/)

If you download the .tar.gz file, look for a README file as it will have install instructions.

Or cousre search the forums with terms such as realtek or rtl8180 or your card/model number to see if there is something more to help you.

I know this is probably not what you wanted to see. gnu/linux has something different to offer then windows and sometimes there is a learning curve (if you're used to windows). Some hardware offers obstacles such as your card.  I took the route of buying a card with better support and I haven't looked back.

best of wishes with what ever you do

---

### Post by aznboi on 2005-11-21
make sure u have the latest version of ndiswrapper by doing the following:
```
apt-get install ndiswrapper-utils
```

This is verrryyy important and I didnt get my card working till I got hte latest version... I thought i had it but turns out i didnt...lol...

then i followed this guide and had my wifi card running great:
```
http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Install_Windows_driver
```

---

### Post by Sir Frederic on 2005-11-21
Thanks for the help guys - havent fixed the problem yet but just wanted to say dont advise me to apt get anything as without the wireless working i can't do that. (i am currently booting into windows to access the internet)

---

### Post by aznboi on 2005-11-22
u can connect it to an ethernet card to get it to the internet

---

### Post by Lambert on 2005-11-22
If you don't have a wired connection while logged in to ubuntu then you can go [here]("http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils") on a different machine.

Go to the download section and pick what version. Probably the i386 version. It will take you to a list of mirrors. Pick the first one in the list under Europe. Copy it to disk and then copyt it in a directory on your ubuntu machine. /home/<name>/downloads or something similar.

Open a terminal and move to the directory where you saved the download.

```
cd /home/<name>/path_to_directory
``` 
then

```
sudo dpkg -i ndiswrapper-utils_1.1-4ubuntu2_i386.deb
``` 
Quick tip. the terminal can auto type for you. if you type sudo dpkg -i ndis [tab] [tab] it will scan the directory you're in and fill in the rest of the name. If you have more then 1 that matches then it will give you a list. Add a couple more letters and hit [tab] [tab] again.

This will install the latest ndiswrapper-util on your machine. Then follow the instructions of installing a driver.

While you're at it you can also grab the gui front end of ndiswrapper. Follow the same steps for downloading and copy to your machine. After you install the above package install this one.

[http://packages.ubuntu.com/breezy/net/ndisgtk]("http://packages.ubuntu.com/breezy/net/ndisgtk")

```
sudo dpkg -i ndisgtk....deb
``` 
This gives you a graphical interface to installing drivers. You start it by going to system>admin>windows wireless drivers.

---

