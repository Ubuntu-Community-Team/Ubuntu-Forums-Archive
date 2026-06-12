---
title: "Upgraded to 9.04 Nvidia problems"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Gregz on 2009-06-17
I just rebooted and it went to low graphics. need to restart xserver.

I have tried to install driver,but When I get to stop gnome init.d (not entered like that) does not work. I have got it to work but install quits at xserver or x something is running and cannot install. I have run into this before but cannot find paper I wrote solution on.

---

### Post by jbrown96 on 2009-06-17
you could also try ```
sudo init 3
``` which should shut down the X server. the problem that I've run into before is with wireless. You may need some extra packages or need to download some kernel headers from Nvidia, and when you kill X, wireless connections are gone -- because network-manager isn't running. If you use a wired connection you should be fine though. You could also try booting the recovery kernel, but that might add the kernel module to the wrong kernel. At the grub menu, you could highlight your most current kernel (should be default), and press e to edit then e to edit the second line and add "single" without the quotes to the end. This will prevent the X server from starting.

I just realized that I had a similar problem. Just a couple day ago, I downloaded the 185.xx version and couldn't get it to install at all. Maybe it's not supported? I ended up installing the 180.xx version from the hardware driver manager, which has worked fine, although I would like to have the current version.

---

### Post by Gregz on 2009-06-17
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
    1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

[COLOR="Red"](I did this and its up to date)
[/COLOR]
4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

[COLOR="Red"](This will not work at all)[/COLOR][COLOR="Red"](update this is done)[/COLOR]

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

[COLOR="Red"](nor this)[/COLOR] [COLOR="Red"](update this is done)[/COLOR][COLOR="Red"][/COLOR]

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
    7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
    7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
        -------------------------------------------------------------------------------------------------------
        If you used Envy to attempt a previous nvidia install please run this command now before you go on:

        sudo envy --uninstall-all 
        sudo dpkg -P envy 
        sudo envyng --uninstall-all
        sudo dpkg -P envyng
        In Depth Instructions on Envy and EnvyNG install/uninstall [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu)




        -------------------------------------------------------------------------------------------------------
        If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

        sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

        -------------------------------------------------------------------------------------------------------
        If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

        sudo nvidia-installer --uninstall

        -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

[COLOR="Red"](This does not work. Had trouble with this before and can't remember work around)[/COLOR]

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

[COLOR="Red"]( It will start this but quits cause x is running)[/COLOR]

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

Optional But recommended:
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     [http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)[COLOR="Red"][/COLOR]

---

### Post by Technoviking on 2009-06-17
Some of the Ubuntu X developers have made a ppa with some updated video drivers (including nvidia-graphics-drivers-185.18.14). I would suggest trying this before install manually.

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Instruction for installing NVidia manually can be found here:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

T-V

---

