---
title: "a real head scratcher"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by freestylin599 on 2009-04-10
a real problem is what i have got.  I downloaded 9.04 jaunty because my atheros wireless card was not working on my 8.10 and it worked was getting wireless internet and all the good stuff so i decide to run the package updates and they all install, like 300 of them successfully i restart and i have no internet connection.  i am sitting next to my router and i am still not getting connection and on the drop down bars in the top right hand corner i have no connection and it wont let me choose my wireless network like last night, what happened

---

### Post by eeeandrew on 2009-04-10
Hi, I also use an Atheros card and have had this problem. Mine is the Ar5007EG. I've found that everytime there is a kernel update the driver needs to be reinstalled. If you kept a copy of the source file for the driver you need to follow the initial install instructions again. Are you using the madwifi driver? If so I have kept a copy of those instructions in a text file and can give you a list of the necessary commands.

Alternatively, if you did not initially install a madwifi driver and had it working out the box(lucky you, thats never happened for me) then you may wish to switch back to the older kernel. I don't know the exact option but you should be able to do this on one of the bIOS screens and choosing your previous kernel. I'm not sure of the kernel codes for jaunty so perhaps someone could add to this with those instructions.

Hope this helps,
Andrew

---

### Post by freestylin599 on 2009-04-10
i am using the madwifi driver how do i get it back

---

### Post by eeeandrew on 2009-04-10
Do you have a copy saved on your computer? If not go to the madwifi site and download the driver for your chipset. I'll copy paste instructions from the help file I downloaded at the madwifi site.

> Assuming that you're inside the MadWifi directory, execute the following scripts to remove the current modules from your system and its memory:

cd scripts
./madwifi-unload
./find-madwifi-modules.sh $(uname -r)
cd ..

You should then be asked if you are sure that you want to remove the old modules.
Building MadWifi ¶

Now that you have the MadWifi code, it's time to compile it into the actual driver. Thankfully, this is easy.

Assuming that you've met all of the requirements above, and you're inside the MadWifi directory, you can just type:

make

Which will start the build process. Watch for any questions you might be prompted to answer - when it finishes, quickly scan through for any errors. If everything went according to plan, you can proceed to the next step. Make sure you have all the Requirements or the build process may fail.
Installing MadWifi ¶

This step will take the built MadWifi, and install it on your system. Once again, make does all of the work for you.

This step needs to be done as root, so either type su and enter root's password, or if you have it set up (e.g. Ubuntu), prefix the following command with sudo.

To install the driver, type:

make install

This will copy all of the modules, tools and man pages to the correct directories on your system. You've now completed the basic install.
Loading the MadWifi Module ¶

This step will load the MadWifi driver module into your running system. This essentially lets all other software know how to talk to your MadWifi hardware.

This step needs to be done as root, so either type su and enter root's password, or if you have it set up (e.g. Ubuntu), prefix the following command with sudo.

To load the driver module, type:

modprobe ath_pci

If after running this command ifconfig doesn't show the additional wireless interface you might need to reboot

---

### Post by freestylin599 on 2009-04-10
no where do i get the package to install it

---

### Post by eeeandrew on 2009-04-10
This is a link to the ubtuntu community docs site with a link and complete instructions for the wifi driver I downloaded with full instructions. The relevant part is at the bottom of the page under manually installed drivers 2). you should run:

> sudo lspci 

and check to find your cards name and model. If you find its not an AR5007 or AR2425 series chip then search on madwifi for your chipset. The good news is that the link is for a stable HAL which should continue to work. However, this needs to be reinstalled every time you upgrade your kernel. So keep a copy of the driver and possibly look to save the text from the quote in my previous post which should allow you to reinstall the driver when necessary.

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

[http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192)

Hope this is helpful,
Andrew

---

