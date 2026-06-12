---
title: "Cisco linksys ae2500: Can't install ndsiwrapper 1-59 in Lubuntu 13.10"
date: 2014-04-04
forum: Networking &amp; Wireless
---

### Post by critikal17 on 2014-04-04
[COLOR=#000000][FONT=Arial]Hi all[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I just installed lubuntu saucy 13.10 on an old pc (pentium 4, 2.4 GHz) [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've got a problem since I can't install ndsiwrapper (version 1.59 package from sourceforge), I need it to be able to install my wifi usb-key (cisco linksys ae2500), unfortunately I can't connect my pc with an ethernet cable[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've been searching for 3 days on ubuntu forums and on the web but anyway I'm still unable to install it :-([/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I followed the procedure on the frech ubuntu forum [http://doc.ubuntu-fr.org/ndiswrapper](http://doc.ubuntu-fr.org/ndiswrapper) but it doesen't work  [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I can see my usb key with the command *lsusb*[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]- I get the driver .inf file and associate files from the cisco website and copy everything in a new directory 
I was able to unrar the tar.z archive in the terminal with *tar zxvf ndiswrapper-1.59.tar.gz*, then I go to the new directory[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]then I should run the command *make* and *sudo make uninstall* 

but I receive an error message telling me that the program 'make' is not installed (?????) I don't understand as this should launch the installation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I also tried the procedure described in the  INSTALL file in the archive containing ndiswrapper, this one is slightly different but doesen't work either, here it is:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]Download the latest version of the ndiswrapper sources from here and
extract it with the command[/B][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**  tar zxvf ndiswrapper-version.tar.gz**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]This will create ndiswrapper-version directory. Change to that
directory and run[/B][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]  make uninstall
  make[/B][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][B]Login as root and run
  make install[/B][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I've tried hundreds of command reading on differents ubuntu forums but cannot get it installed
 
maybe this is a problem of linux version (13.10 or a difference in Lubuntu) but the command 'make' does not exist or does not work for me (???)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
any help is more than welcome :-) !!!


thank you in advance[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]


notice: I've decided to quit windows for every OS I use but in the future I'll verify that any material I buy is linux-compatible ^^![/FONT][/COLOR]

---

### Post by critikal17 on 2014-04-04
kind the same problem as that;

[http://askubuntu.com/questions/404176/i-cant-install-ndiswrapper](http://askubuntu.com/questions/404176/i-cant-install-ndiswrapper)

---

### Post by ajgreeny on 2014-04-04
If the info in critikal17's post does not help, install **build-essentials** package, which is why the **make** command isn't working then use the method in my info below which is essentially what you've already done.
Download source from sourceforge :-
[http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files](http://sourceforge.net/projects/ndiswrapper/files/latest/download?source=files)

Install:-
ndisgtk, ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-source and ndiswrapper-utils-#.#
plus all dependencies.

Ensure you have installed the linux-header packages for your kernel version.

Extract the downloaded archive and cd to extracted ndiswrapper-#.## folder

Run these commands in order:-

make
sudo make install
sudo modprobe ndiswrapper

Wireless connection should now be available, assuming ndiswrapper is the needed module for your wireless adapter.

---

