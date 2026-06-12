---
title: "installing programs on sd card?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by jdsam on 2009-11-11
New to ubuntu?
 
Have a netbook with a very samll 4gb ssd.
 
Is it possible to install programs on an SD card (like choosing an install directory in windows) or do programs need to be installed whereever the OS is installed?
 
Could someone point me to a link or some information on this?
 
Many thanks.

---

### Post by mrboojive on 2009-11-11
First off, just about anything is possible on Linux. However, are you sure that you actually need to put your programs on the SD card? An Ubuntu installation is only around 2 GB so you would have a lot of room to install extra programs. You would probably save yourself a lot of headache by installing all of your programs on your SSD and putting any documents, etc. you have onto your SD card.

Here is a thread that is somewhat related: [http://art.ubuntuforums.org/showthread.php?t=1288329](http://art.ubuntuforums.org/showthread.php?t=1288329)

---

### Post by jdsam on 2009-11-11
Thanks for the reply. The installation that came on my Dell mini is about 3gb and with open office it's almost full to the point where I am afraid to install updates.
 
One option is to wipe the dell preinstalled ubuntu and but some sort of netbook remix.
 
Would you recommend doing that?

---

### Post by mrboojive on 2009-11-11
I think reinstalling would probably be more trouble than it's worth. Have you tried uninstalling programs that came with it that you don't use? That is probably your best bet for freeing up some space. Also, does your Ubuntu have the Computer Janitor? System > Administration > Computer Janitor. That might help out a bit, too.

Installing updates is not going to take up more space because the updates replace files that are already on your machine. Just make sure you run the command ```
sudo apt-get clean
``` in the command line after updating. That will remove any update installation files that have been downloaded.

---

