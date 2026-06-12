---
title: "ubuntu 11.04 wifi problem!!!!!{HUGE PROBLEM]"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Dr. div11 on 2011-05-03
hey .. iam pretty new to ubuntu about 2 months back i dual booted my laptop with windows 7 and ubuntu 10.10... my pc config are..

Acer aspire 
i5 and gb ram..

..everything was fine including THE WIFI WHICH AUTOMATICALLY CONFIGURED ITSELF IN UBUNTU 11.04  

THE PROBLEM IS ABOUT 2 DAYS BACK I UPDATED IT TO UBUNTU 11.04 AND THE WIFI DOSENT SEEM TO WORK.. I DONT UNDERSTAND I HAVE TRIED EVERYTHING...  WIRELESS CONECTIONS ARE NOT SHOWN ANYWHERE.. UBUNTU 11.04 IS NOT DETECTING MY WIFI.. ..

PLEASE HELP.. MY WIRELESS CARD IS Broadcom 802.11n network adaptor..
 wifi was working fine in 10.10 and windows 7 and now ... nothing...no wireless networks..

please help..

---

### Post by Peter09 on 2011-05-03
Check your third party drivers

Super+A=>type additonal

run the application and see if there are any drivers which need to be installed. (You may need a wired connection)

---

### Post by Gunner2677 on 2011-05-03
First things first, try hardwiring into your network to see if you are able to download any drivers for your wireless card using Update Manager or Additional Drivers. If that doesn't work, start scouring the forums. There is ton off great info in here.

---

### Post by aias on 2011-05-03
This may sound strange but someone I know had the same problem.  The issue was that the battery was really low (or dying) and the BIOS seemed to have disabled the wireless card.  He couldn't get it in windows either. He ordered a new battery and once he put that in, the wireless started working again.  are you having similar issues?

---

### Post by MasterNetra on 2011-05-03
> **Dr. div11 said:**
> hey .. iam pretty new to ubuntu about 2 months back i dual booted my laptop with windows 7 and ubuntu 10.10... my pc config are..

Acer aspire 
i5 and gb ram..

..everything was fine including THE WIFI WHICH AUTOMATICALLY CONFIGURED ITSELF IN UBUNTU 11.04  

THE PROBLEM IS ABOUT 2 DAYS BACK I UPDATED IT TO UBUNTU 11.04 AND THE WIFI DOSENT SEEM TO WORK.. I DONT UNDERSTAND I HAVE TRIED EVERYTHING...  WIRELESS CONECTIONS ARE NOT SHOWN ANYWHERE.. UBUNTU 11.04 IS NOT DETECTING MY WIFI.. ..

PLEASE HELP.. MY WIRELESS CARD IS Broadcom 802.11n network adaptor..
 wifi was working fine in 10.10 and windows 7 and now ... nothing...no wireless networks..

please help..

bcmwl-kernel-source seems to be broke in natty, at least the version natty uses you will have to download Mavericks version: [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

After you remove the bcmwl-kernel-source package you have currently and install the one from maverick there be sure to go into synaptic and lock it to prevent it from upgrading back to the natty version.

Personally though I'm dropping back to 10.10 natty is too buggy for me. It looks as though the developers got in over their heads this time. Oh well should be ironed out at 11.10's release i would think.

---

### Post by Dr. div11 on 2011-05-03
> **Peter09 said:**
> Check your third party drivers

Super+A=>type additonal

run the application and see if there are any drivers which need to be installed. (You may need a wired connection)


  i am sorry but i am super new  and i did not understand much of what u said.

how to run that application

---

### Post by Dr. div11 on 2011-05-03
> **aias said:**
> This may sound strange but someone I know had the same problem.  The issue was that the battery was really low (or dying) and the BIOS seemed to have disabled the wireless card.  He couldn't get it in windows either. He ordered a new battery and once he put that in, the wireless started working again.  are you having similar issues?


.. no ... my laptop is pretty new..say 4 months or so...i dont tink there is a battery issue..

---

### Post by Dr. div11 on 2011-05-03
> **MasterNetra said:**
> bcmwl-kernel-source seems to be broke in natty, at least the version natty uses you will have to download Mavericks version: [http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

After you remove the bcmwl-kernel-source package you have currently and install the one from maverick there be sure to go into synaptic and lock it to prevent it from upgrading back to the natty version.

Personally though I'm dropping back to 10.10 natty is too buggy for me. It looks as though the developers got in over their heads this time. Oh well should be ironed out at 11.10's release i would think.





thanks for the link but which package should i download moreover.. HOW DO I FIRST REMOVE bcmwl-kernel-source package..

AND EVEN I AM CONSIDERING reverting back to  ubuntu 10.10

---

### Post by Peter09 on 2011-05-03
Run the application - just hit enter when its first in the list (it most probably will be the only one in the list)

Super is a key on your keyboard (sometimes has a little house, sometime has the Windows logo)

+A, type A while the super key is pressed.

then just start typing the name of the application ---- Additional Drivers

hit enter when its first in the list.

---

### Post by Dr. div11 on 2011-05-03
> **Peter09 said:**
> Run the application - just hit enter when its first in the list (it most probably will be the only one in the list)

Super is a key on your keyboard (sometimes has a little house, sometime has the Windows logo)

+A, type A while the super key is pressed.

then just start typing the name of the application ---- Additional Drivers

hit enter when its first in the list.

..
 funny and helpful..:).

---

### Post by orionds on 2011-05-07
I'm getting sick of Ubuntu 11.04 too.

Been trying to stick with it because it shows some speed advantage over previous versions.

Besides the wi-fi problem (which re-appeared with 11.04), I cannot get file sharing to work on my network. I can get it to work with system-config-samba if the other computer is running 10.10 or Linux Mint 10 but with both computers running 11.04 - no dice - no matter what I have tried so far. If any of you have a fix for this networking, I'd really appreciate it if you could let me have it. Thanks.

I hope when Linux Mint 11 comes out they have fixed both these problems. I wouldn't be surprised if after several months or a year Linux Mint overtakes Ubuntu.

---

### Post by orionds on 2011-05-10
I found the solution to my network folder share problem here:

[http://www.liberiangeek.net/2011/04/share-home-folder-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/share-home-folder-ubuntu-11-04-natty-narwhal/)

Note:
gksu gedit /etc/samba/smb.conf
"gksu" should be gksudo

---

### Post by orionds on 2011-05-10
> **Dr. div11 said:**
> hey .. iam pretty new to ubuntu about 2 months back i dual booted my laptop with windows 7 and ubuntu 10.10... my pc config are..

Acer aspire 
i5 and gb ram..

..everything was fine including THE WIFI WHICH AUTOMATICALLY CONFIGURED ITSELF IN UBUNTU 11.04  

THE PROBLEM IS ABOUT 2 DAYS BACK I UPDATED IT TO UBUNTU 11.04 AND THE WIFI DOSENT SEEM TO WORK.. I DONT UNDERSTAND I HAVE TRIED EVERYTHING...  WIRELESS CONECTIONS ARE NOT SHOWN ANYWHERE.. UBUNTU 11.04 IS NOT DETECTING MY WIFI.. ..

PLEASE HELP.. MY WIRELESS CARD IS Broadcom 802.11n network adaptor..
 wifi was working fine in 10.10 and windows 7 and now ... nothing...no wireless networks..

please help..
This might help with your wi-fi problems. It worked when I installed 10.04 and had no wi-fi.

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/541620]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620")

It's actually this post:

[Alan]("https://launchpad.net/%7Emrintegrity")             wrote             on 2010-04-22:                                                             [  #21]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/21")                                                         I would just  like to confirm that the  workaround suggested by Carsten seems to work  perfectly (so far).
 As root:
 mkdir -p /etc/Wireless/RT2860STA/
touch /etc/Wireless/RT2860STA/RT2860STA.dat
service network-manager restart
 It is then possible to connect via network manager.
 /Alan

The above are commands used in the terminal, so to get root privilege add "sudo" at the start of each line. You will be asked for your password. As you type, you won't see anything, so make sure the password is correct.

sudo mkdir -p /etc/Wireless/RT2860STA/
 sudo touch /etc/Wireless/RT2860STA/RT2860STA.dat
 sudo service network-manager restart

Let us know if it works.

---

### Post by Solstice Bahai on 2011-05-10
Like yourself, fairly new to Linux in general and Ubuntu in particular, and I to have an Acer Aspire 5740, I had Ubuntu 9.04 on it and wireless and wired did not even work.Took it to a friends place,downloaded 11.04 Natty Narwhal iso on to my friend's 'puter, then transferred it to usb stick,boot up from usb,making sure I was also connected to his wired connection, and lo&behold, it connected!!,during install of 11.04,and solved all the wireless problems as well.It might be an idea to try a re-install of 11.04 over a wired connection, and see if that solves your problem

---

### Post by beew on 2011-05-10
Which broadcom wifi card? I tested 11.04 on a netbook which has a broadcom 4312 (if I remember correctly) card and Additional Drivers offered the bwm driver and the sta driver, the first one didn't work but the second one (sta) worked out of the box.

---

### Post by josephmills on 2011-05-10
if at all you think that you need the b43 fwcutter or the b43sta please take a look at post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by prakash.thyagarajan on 2011-05-16
How can I uninstall 11.04 and Install 10.04 again.

---

