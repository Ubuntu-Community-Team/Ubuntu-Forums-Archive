---
title: "How do I Install Plustek backends into Sane?"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by the.scarecrow on 2009-01-10
I have a Dell Latitude D600 that has Hardy 8.04 installed and it works brilliantly. I do not duel boot other operating systems.

I have a CanoScan LiDE 70 as a hangover from a previous operating system and I know that getting this scanner to work in Ubuntu is next to impossible so I will never buy another Canon product!

However, I still have my old Parallel Port Plustek OpticPro 4831P scanner and it reportedly works 100% if I use this backend to Sane:
[HTML]http://www.gjaeger.de/scanner/downloads/plustek-pp-0.43-12.tar.gz[/HTML]

The problem is that when I use Applications>Graphics>XSane Image Scanner, I get the message "no devices available"

So I downloaded it to my desktop and then extracted it to my desktop. I get a folder called "plustek-pp-0.43-12" that contains four sub-folders "backend, doc, include and sanei" but I can't find any understandable instructions on how I install this backend into Sane.

Along the way I have changed BIOS to make my Parallel Port Bi-Directional, I edited file /etc/sane.d/dll.conf and removed the # infront of the #plustek_pp statement and I copied all the files from the backend folder I downloaded into the file /etc/sane.d, having made a backup of sane.d first. If I enter "man sane-plustek_pp" into Terminal I get a list of all the options available OK.

Still I just get the message "no devices available" when I try to access the scanner. I have run out of ideas now and hours of searching the net have not lead me to finding an understandable method of installing these drivers. I would be really pleased to solve this problem as scanning is the "last frontier" for me to cross and reach Ubuntia.

---

### Post by the.scarecrow on 2009-01-11
Any ideas anyone?

---

### Post by the.scarecrow on 2009-01-12
Tum-tee-tum-dee-dummmm....:(

---

### Post by Daveth on 2009-01-12
I guess you probably need to build it from source code. I got my Canon MP610 multi-function device just last friday, and it prints and scans just fine, but i did have to build sane from source. I had never built from source before but it was easy. I used this

[http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

as my guide, downloading a night build. When un-zipped, this folder also contained a sane-backends folder etc, so i guess the thing you have is the same. The only other thing it might be is a postscript printer defintion file (.ppd)- I guess you need to peep inside to see.
Good luck.

---

### Post by the.scarecrow on 2009-01-14
Thanks Daveth for you help and advice. I had a look at the link you suggest but unfortunately it is very complicated and not directly applicable to the Plustek or the Parallel Port.

I have never attempted most of the steps to install so I would be unlikely to be able to adapt the instructions for my particular scanner. As such it represents too much of a risk, I don't want to have to re-install my present setup.

However, I have been intending to install Ubuntu 8.10 on a spare hard drive I have as a test bed installation also duel booting with Win XP. I could then try out this backend installation on that then if it all goes wrong I can quickly re-install Ubuntu in 30mins.

Thanks again for your interest, I don't seem to have the thanks option to select on your post though.

---

### Post by alienexplorers on 2009-01-14
The Plustek_PP drivers are already installed in Sane in Ubuntu 8.04 and 8.10...
It should be setup to use the Parport (SPP, EPP) system so it is setup for parellel port usage.  

Do you have your parellel port in your BIOS set to EPP.  If not set it to that.  I have a parellel port scanner and needed to use EPP to get it to work since it required 2 way communication with the port.

[http://ubuntuforums.org/showthread.php?t=32632]("http://ubuntuforums.org/showthread.php?t=32632")

---

### Post by the.scarecrow on 2009-01-15
> **alienexplorers said:**
> The Plustek_PP drivers are already installed in Sane in Ubuntu 8.04 and 8.10...
It should be setup to use the Parport (SPP, EPP) system so it is setup for parellel port usage.  

Do you have your parellel port in your BIOS set to EPP.  If not set it to that.  I have a parellel port scanner and needed to use EPP to get it to work since it required 2 way communication with the port.

[http://ubuntuforums.org/showthread.php?t=32632]("http://ubuntuforums.org/showthread.php?t=32632")

In BIOS I have these options, none of which work with the scanner yet:
BIOS A14, Parallel Mode:
Bi-directional = PS/2 compatible (I'm currently using this)
ECP = port default
Normal = AT-compatible
Disabled

I followed your link, I tried $ modprobe ppdev in terminal but get no response and the scanner is still not found.

I also tried 
> $ sane-find-scanner -p
The program 'sane-find-scanner' is currently not installed.  You can install it by typing:
sudo apt-get install sane-utils
bash: sane-find-scanner: command not found

So I am still stuck on this one, thanks for your help though.

---

### Post by alienexplorers on 2009-01-15
Leave the BIOS at Bi-Directional.  Load from termilal:
> sudo apt-get install sane-utils
Then run the command:
> sane-find-scanner -p
if that does not work try adding sudo in front of the command.

---

### Post by the.scarecrow on 2009-01-15
I tried, here are the results:

> ~$ sudo apt-get install sane-utils
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libamrnb3 libamrwb3
Use 'apt-get autoremove' to remove them.
Suggested packages:
  unpaper
The following NEW packages will be installed:
  sane-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 128kB of archives.
After this operation, 344kB of additional disk space will be used.
Get:1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/universe sane-utils 1.0.19-1ubuntu3 [128kB]
Fetched 128kB in 5s (23.2kB/s)     
Selecting previously deselected package sane-utils.
(Reading database ... 144347 files and directories currently installed.)
Unpacking sane-utils (from .../sane-utils_1.0.19-1ubuntu3_i386.deb) ...
Setting up sane-utils (1.0.19-1ubuntu3) ...
Adding saned group and user...

~$ 

~$ sane-find-scanner -p

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
~$ 


using sudo sane-find-scanner -p, had the same result.

---

### Post by alienexplorers on 2009-01-15
Try running these commands in terminal and post the results:
> ls /dev/lp*

and of

lsmod | grep lp


Try reading this:
[http://ubuntuforums.org/showthread.php?t=292708]("http://ubuntuforums.org/showthread.php?t=292708")

---

### Post by the.scarecrow on 2009-01-15
Here are the results

> ~$ ls /dev/lp*
/dev/lp0
:~$ lsmod | grep lp
lp                     12324  0 
parport                37832  3 ppdev,lp,parport_pc
:~$ 

That thread ends without any results so I'm reluctant to follow it without knowing where it all may end.

Anyway I've got to go now, will pick up again tomorrow.

thanks

---

### Post by the.scarecrow on 2009-01-16
I'm back.

---

### Post by the.scarecrow on 2009-01-17
Someone must know how to install these backend files into the Sane application. The Sane website refers to instructions that don't exist on how to do the installation.

---

### Post by the.scarecrow on 2009-01-18
Bump.

---

### Post by the.scarecrow on 2009-01-20
Bump

---

### Post by the.scarecrow on 2009-01-25
This is all a bit crazy. I have the correct drivers from the Sane website, that site says the Plustek scanner works 100% but no backend installation instructions seem to exist.

The best I found were several years old and for Suze. I tried to follow them but the differences were too great for me to handle.

I can solve this problem in an hour or so by re-installing Windows XP, downloading the windows drivers from Plustek and start scanning, but I am determined to move forward, not backwards.

Please help if you can.

---

### Post by union two levers on 2009-03-07
thanks for this info, i am a complete novice and have a mp610 which is not scanning so i will have a go using your suggestion...never built from source before

---

### Post by the.scarecrow on 2009-03-08
I regret that my solution is to go back to duel booting WinXP just to use a scanner, the Canon LiDE70 works on that so bit of a cop out really.

I will have to wait for an Ubuntu based solution cos installing backends in Sane it beyond me and seems to leave the community stumped too.

---

### Post by desertdog on 2009-03-09
Scarecrow,
Try this:
Go to /etc/sane.d/dll.conf. plustek_pp is commented out. Remove the # in front of it and save the file. That should hopefully work. You might have to reboot to get the sane daemon to restart and recognize your scanner.

(In other words, try $gksu gedit /etc/sane.d/dll.conf).

I hope this works for you. If it doesn't, post your problem on the sane mailing list. Gerhard will probably answer your question.

---

### Post by the.scarecrow on 2009-03-10
> **desertdog said:**
> Scarecrow,
Try this:
Go to /etc/sane.d/dll.conf. plustek_pp is commented out. Remove the # in front of it and save the file. That should hopefully work. You might have to reboot to get the sane daemon to restart and recognize your scanner.

(In other words, try $gksu gedit /etc/sane.d/dll.conf).

I hope this works for you. If it doesn't, post your problem on the sane mailing list. Gerhard will probably answer your question.

Thanks for the suggestion but this doesn't work. This is an old thread and I was using Hardy at the time and did this early on. I am certain that I must install the Sane back-end I downloaded but I can't find out how this is done.

Since then I have re-installed WinXP pro and moved to Intrepid so my dll.conf file had reverted to #plustek_pp. I just deleted the # and re-booted to try again but Sane still doesn't find the scanner.

I will try asking on the Sane mailing list, I haven't tried that.

Thanks

---

