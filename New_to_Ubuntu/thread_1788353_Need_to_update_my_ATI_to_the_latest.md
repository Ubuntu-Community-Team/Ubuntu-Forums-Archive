---
title: "Need to update my ATI to the latest"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by mikee55 on 2011-06-22
Hi all, I downloaded a Shell script file which is supposed to be a driver update for my Radeon Catalyst 3000 card. But I don't know what to do with it.

Mike

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> Hi all, I downloaded a Shell script file which is supposed to be a driver update for my Radeon Catalyst 3000 card. But I don't know what to do with it.

Mike

to run it do:

```
sudo chmod +x /path/to/file/ati-driver-installer-11-6-x86.x86_64
```then

```
sudo sh /path/to/file/ati-driver-installer-11-6-x86.x86_64
```but I have no comment about what it does and whether you have the right dribver installation script, etc. Nothing in the repositories that work for you?

---

### Post by mikee55 on 2011-06-22
sudo chmod +x /Home/tux folder/ati-driver-installer-11-6-x86.x86_64
chmod: cannot access `/Home/tux': No such file or directory
chmod: cannot access `folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory
  I think I need to figure out why I always get 

cannot access       No such file or directory

Mike

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> sudo chmod +x /Home/tux folder/ati-driver-installer-11-6-x86.x86_64
chmod: cannot access `/Home/tux': No such file or directory
chmod: cannot access `folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory
  I think I need to figure out why I always get 

cannot access       No such file or directory

Mike


just a bit of syntax i think.....

if you have a file or folder with a space in the name you need to preceed the space in the command with a backslash otherwise you confuse the command line interface so try

```
sudo chmod +x /Home/tux\ folder/ati-driver-installer-11-6-x86.x86_64
```

---

### Post by mikee55 on 2011-06-22
Same thing???
Mike

sudo chmod +x /Home/tux\ folder/ati-driver-installer-11-6-x86.x86_64
chmod: cannot access `/Home/tux folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> Same thing???
Mike

sudo chmod +x /Home/tux\ folder/ati-driver-installer-11-6-x86.x86_64
chmod: cannot access `/Home/tux folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory

yeah, i was just looking at that path I blindly changed for you.... I dont think /Home/.... will be correct. Sorry i never spotted it first time round

will be:

/home/*YourUsername*/....

My apols for not spotting first time

---

### Post by iclestu on 2011-06-22
remember that "/home/" is not that same as "/Home/"

---

### Post by mikee55 on 2011-06-22
sudo chmod +x /home/tux\ folder/ati-driver-installer-11-6-x86.x86_64
> sudo sh /home/tux\ ati-driver-installer-11-6-x86.x86_64


did nothing, pass?

Mike

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> sudo chmod +x /home/tux\ folder/ati-driver-installer-11-6-x86.x86_64
> sudo sh /home/tux\ ati-driver-installer-11-6-x86.x86_64


did nothing, pass?

Mike

you need to be careful to get the filepaths exactly correct.... I THINK this is your file path....

```
sudo chmod +x /home**/yourUserName/**tux\ folder/ati-driver-installer-11-6-x86.x86_64
``````
sudo sh /home/**yourUserName**/tux\ folder/ati-driver-installer-11-6-x86.x86_64
```

---

### Post by iclestu on 2011-06-22
i guess as a work around you could move the script to your home folder using nautilus then just dispense with the path altogether and start a new terminal

if you do ```
ls
``` and can see the ati-driver-installer-11-6-x86.x86_64.sh file you could just do

```
sudo chmod +x ati-driver-installer-11-6-x86.x86_64.run
``````

sudo sh ati-driver-installer-11-6-x86.x86_64.run
```

---

### Post by iclestu on 2011-06-22
or 

```
./ati-driver-installer-11-6-x86.x86_64.run
```

---

### Post by mikee55 on 2011-06-22
tux@tux-System-Product-Name:~$ sudo chmod +x /home/tux\ folder/ati-driver-installer-11-6-x86.x86_64 
chmod: cannot access `/home/tux folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory
tux@tux-System-Product-Name:~$ 

Pass???? Sorry

Mike

---

### Post by Perfect Storm on 2011-06-22
easier if you write the commands and then drag the file into the terminal. It will write you the destination and file for you.

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> tux@tux-System-Product-Name:~$ sudo chmod +x /home/tux\ folder/ati-driver-installer-11-6-x86.x86_64 
chmod: cannot access `/home/tux folder/ati-driver-installer-11-6-x86.x86_64': No such file or directory
tux@tux-System-Product-Name:~$ 

Pass???? Sorry

Mike

I think you are still missing your username.....

step by step lets find this file!

do

```
cd /home
```then
```
ls
```it should list the home directories which, should be named as the users names. no? if so then do ```
cd /home/YOURUSERNAME/
```then ```
ls
```and post the results here! We are going to find this file!

---

### Post by iclestu on 2011-06-22
> **Artificial Intelligence said:**
> easier if you write the commands and then drag the file into the terminal. It will write you the destination and file for you.


LOL!!!! I NEVER EVER knew this!


COOL!

yeah - do that!!! :)

---

### Post by iclestu on 2011-06-22
that means you type

```
chmod +x 
```

in a terminal then drag the file and press enter

then follow it up with 

```
.
```

then drag again!

I like this new discovery AI!!!

---

### Post by mikee55 on 2011-06-22
tux@tux-System-Product-Name:~$ cd /home
tux@tux-System-Product-Name:/home$ ls
tux
tux@tux-System-Product-Name:/home$ cd /home/tux/
tux@tux-System-Product-Name:~$ ls
2011-06-22-11-57-25.013-VirtualBox-6514.log  Downloads  Public          Ubuntu One                                electricsheep-2011-06-03  makesheep.sh
Desktop                                      Music      Screenshot.png  Videos                                    examples.desktop
Documents                                    Pictures   Templates       ati-driver-installer-11-6-x86.x86_64.run  gmediafinder-downloads
tux@tux-System-Product-Name:~$ 


Mike :)

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> tux@tux-System-Product-Name:~$ cd /home
tux@tux-System-Product-Name:/home$ ls
tux
tux@tux-System-Product-Name:/home$ cd /home/tux/
tux@tux-System-Product-Name:~$ ls
2011-06-22-11-57-25.013-VirtualBox-6514.log  Downloads  Public          Ubuntu One                                electricsheep-2011-06-03  makesheep.sh
Desktop                                      Music      Screenshot.png  Videos                                    examples.desktop
Documents                                    Pictures   Templates       ati-driver-installer-11-6-x86.x86_64.run  gmediafinder-downloads
tux@tux-System-Product-Name:~$ 


Mike :)

ok, it right there!

from that directory u just want:

```
sudo chmod +x ati-driver-installer-11-6-x86.x86_64.run
``````
./ati-driver-installer-11-6-x86.x86_64.run
```

---

### Post by mikee55 on 2011-06-22
> tux@tux-System-Product-Name:~$ chmod +x
chmod: missing operand after `+x'
Try `chmod --help' for more information.
tux@tux-System-Product-Name:~$ 


Mike ???

---

### Post by mikee55 on 2011-06-22
> tux@tux-System-Product-Name:~$ sudo chmod +x ati-driver-installer-11-6-x86.x86_64.run
[sudo] password for tux: 
tux@tux-System-Product-Name:~$ ./ati-driver-installer-11-6-x86.x86_64.run
Created directory fglrx-install.F73Gnz
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.861.................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
See /usr/share/ati/fglrx-install.log for installation details.
Removing temporary directory: fglrx-install.F73Gnz
tux@tux-System-Product-Name:~$ 


Mike

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> Mike ???


its not showing the full command! you need ALL the command

sudo chmod +x ati-driver-installer-11-6-x86.x86_64.run
not just the 

sudo chmod +x

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> Mike


looks like you done!!!!

the script ran

Thank the maker!!! :)

---

### Post by Perfect Storm on 2011-06-22
I am no ATI (I only use Nvidia) but hows the driver handle kernel upgrades when you install the ATI driver manually?


Also shouldn't the driver be installed as superuser do?

---

### Post by mikee55 on 2011-06-22
Ooops, I have basic driver only.1280 x 1024 instead of 1650 x 1280. A load of hastle for Gnome 3?

Mike

---

### Post by iclestu on 2011-06-22
> **mikee55 said:**
> Ooops, I have basic driver only.1280 x 1024 instead of 1650 x 1280. A load of hastle for Gnome 3?

Mike

As i sed at outset, my friend, I can help you run that script but no comment as to whether it is the right driver. Are you sure there is no 'supported' solution for your graphics card/chipset?

Folks on here are pretty knowledgeable about these things...

---

### Post by Perfect Storm on 2011-06-22
> **mikee55 said:**
> Ooops, I have basic driver only.1280 x 1024 instead of 1650 x 1280. A load of hastle for Gnome 3?

Mike

You may want to read this: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

There's a section regarding the latest driver.

---

### Post by mikee55 on 2011-06-22
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html)

This works, now I got to run Gnome 3 setup again.


Thanks:guitar::lolflag:

And fix Jack!

Mike

---

