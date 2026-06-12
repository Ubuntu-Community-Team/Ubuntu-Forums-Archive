---
title: "Correct root"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by bob brazie on 2009-07-08
9.04

Hello, I am running the file cnxtinstall.run in terminal which I downloaded from the driver web site to try to determine what modem is installed on my system to download the correct drivers.

After running it gives me the password number. When it comes time to enter the information on their web site it asks me for a user-name which is the root if I understand correctly. I enter: bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run (the file is on my desktop)

The web site will not take this and asks for both again and again.

Could you help with a proper root?

Thanks in advance. (Bob, new to ubuntu)

---

### Post by cariboo on 2009-07-08
Wouldn't it be better to contact Linuxant directly if you are having problems?

---

### Post by bob brazie on 2009-07-08
I did but haven't heard back from them in awhile.

I was trying to learn what was needed in the "Root" as a new-bee too.

---

### Post by Wim Sturkenboom on 2009-07-09
Hi Bob,

I think I'm missing something. On their website, you entered literally the full sentence '*_bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run_*' when it asked for username? I can imagine that the site does not like that.

What you entered there is the combination of a prompt (*bob@bob-laptop:~/Desktop$*) and a command (*sudo sh cnxtinstall.run*) and definitely not a username.

I don't know the website that you refer to; can you post the url? And can you post the instructions (or a link to them).

On a site note:
By default, Ubuntu has disabled the root account in the OS; it's still there and fully functional except that you can't login as root. It might be necessary to enable it for this exercise (just search this forum). Once you have done your full modem exercise, you can disable it again.
But lets first see the instructions.

---

### Post by abaden on 2009-07-09
You can always just assume root privileges by typing "sudo su -". Just make sure to "exit" after you're done, least you forget and keep working as root.


Alex

---

### Post by LookTJ on 2009-07-09
> **abaden said:**
> You can always just assume root privileges by typing "sudo su -". Just make sure to "exit" after you're done, least you forget and keep working as root.


Alexor ```
sudo -i
```:)

---

### Post by LookTJ on 2009-07-09
> **Wim Sturkenboom said:**
> Hi Bob,

I think I'm missing something. On their website, you entered literally the full sentence '*_bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run_*' when it asked for username? I can imagine that the site does not like that.

What you entered there is the combination of a prompt (*bob@bob-laptop:~/Desktop$*) and a command (*sudo sh cnxtinstall.run*) and definitely not a username.

I don't know the website that you refer to; can you post the url? And can you post the instructions (or a link to them).

On a site note:
By default, Ubuntu has disabled the root account in the OS; it's still there and fully functional except that you can't login as root. It might be necessary to enable it for this exercise (just search this forum). Once you have done your full modem exercise, you can disable it again.
But lets first see the instructions.
I think you got my comment here, after rereading the OP.

---

### Post by bob brazie on 2009-07-09
The install gives me the password but then it takes me to their web side and askes for a user name and password in order to down load the drivers.

It spicificly says: 

"Please enter root as username and the password given on the terminal where you launched the installer"
---------------------------

bob@bob-laptop:~$ cd /home/bob/Desktop
bob@bob-laptop:~/Desktop$ sh cnxtinstall.run
Verifying archive integrity... All good.
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.3
Please run this installer as root. You can probably do it with the
'sudo sh cnxtinstall.run' command.
bob@bob-laptop:~/Desktop$ sudo sh cnxtinstall.run
[sudo] password for bob: 
Verifying archive integrity... All good.
Uncompressing Linux drivers for Conexant modem chipsets Installer version 1.0.3
If the graphical installer fails to start, you could try the terminal
version that you can start with the following command:
---

sh cnxtinstall.run -- --tty

---
Alternatively, you could manually download and install the packages from the
following pages:
HSF: [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php)
HCF: [http://www.linuxant.com/drivers/hcf/full/downloads.php](http://www.linuxant.com/drivers/hcf/full/downloads.php)
DGC: [http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php)
RIPTIDE: [http://www.linuxant.com/drivers/riptide/downloads.phpALSA](http://www.linuxant.com/drivers/riptide/downloads.phpALSA) driver: [http://www.linuxant.com/alsa-driver](http://www.linuxant.com/alsa-driver)
Trying to launch a web browser, please wait...
The password requested by the installer is: e3aa59cb18811bc16655abf308d2706b
bob@bob-laptop:~/Desktop$

---

### Post by bob brazie on 2009-07-10
I heard from the Linuxant people finely and the password was literaly the word "root"
which was not too clear in the instructions. <g>

Thanks to everyone for their help.

Bob.

---

