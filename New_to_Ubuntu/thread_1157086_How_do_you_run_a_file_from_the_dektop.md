---
title: "How do you run a file from the dektop?"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by Canucker25 on 2009-05-12
I am just over an hour into my first Linux install ever. So please forgive me if I know absolutely nothing about anything. 

I am trying to install drivers for my graphics card and I just finished downloading "ati-driver-installer-9-3-x86.x86_64.run" but when I double click it on my desktop I get an error.

 "gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again"

I proceeded to search the forums and someone said to type this in the terminal 

"sudo sh ati-driver-installer-9-3-x86.x86_64.run"

but that does not work. 

What am I doing wrong?

---

### Post by leandromartinez98 on 2009-05-12
Try this in the terminal:

chmod +x ati-driver-installer-9-3-x86.x86_64.run

./ati-driver-installer-9-3-x86.x86_64.run

The first command turns the file into an executable. The second
runs the executable. Actually, after the first command, you should
be able to double click it on your desktop.

The first command can also be done using the GUI: right-click
the file, choose Properties, go to Permissions and check the
box "Allow executing..."

---

### Post by Canucker25 on 2009-05-12
Thank you. I was able to run it although I don't know if it installed or not.

---

### Post by leandromartinez98 on 2009-05-12
> **Canucker25 said:**
> Thank you. I was able to run it although I don't know if it installed or not.

Probably not, because these ATI installers require you to give various "next" before installing.

Try running it from the terminal, as I first suggested, and post here
the output.

One reason for problems is that you need root provileges to run it, so use:

sudo ./ati-driver-installer-9-3-x86.x86_64.run

---

### Post by Canucker25 on 2009-05-12
> **leandromartinez98 said:**
> Probably not, because these ATI installers require you to give various "next" before installing.

Try running it from the terminal, as I first suggested, and post here
the output.

One reason for problems is that you need root provileges to run it, so use:

sudo ./ati-driver-installer-9-3-x86.x86_64.run

owen@owen-desktop:~$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
sudo: ./ati-driver-installer-9-3-x86.x86_64.run: command not found
owen@owen-desktop:~$

Any idea what the problem is?

---

### Post by gandaran on 2009-05-12
look move the .run file to home/user directory and run it from there or cd the terminal to desktop if installing from desktop, then type in terminal
```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```
should work if terminal is in the right directory and check that the file name is correct.

---

### Post by pastalavista on 2009-05-12
Since the file is on the desktop, you'll need to cd into the desktop before it will recognize the command. ```
cd Desktop
``` and run the command when the prompt says [owen@owen-desktop:~/Desktop$ the ~$ means you are in your home directory. The command should look like this:

owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86_64.run

...notice the Desktop directory is capitalized.

edit: since you've moved it, run the ./ command at the ~$ prompt

---

### Post by Canucker25 on 2009-05-12
> **gandaran said:**
> look move the .run file to home/user directory and run it from there or cd the terminal to desktop if installing from desktop, then type in terminal
```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
```should work if terminal is in the right directory and check that the file name is correct.

Alright I tried that and all that happened was a new folder appeared for a few seconds then went away and my computer made a bit of noise. Nothing else.

---

### Post by Canucker25 on 2009-05-12
> **pastalavista said:**
> Since the file is on the desktop, you'll need to cd into the desktop before it will recognize the command. ```
cd Desktop
``` and run the command when the prompt says [owen@owen-desktop:~/Desktop$ the ~$ means you are in your home directory. The command should look like this:

owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86_64.run

...notice the Desktop directory is capitalized.

edit: since you've moved it, run the ./ command at the ~$ prompt

I tried what you said and this is what happened.

owen@owen-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
owen@owen-desktop:~$ cd Desktop
owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.bsgmSs
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.bsgmSs
owen@owen-desktop:~/Desktop$

---

### Post by pastalavista on 2009-05-12
> **Canucker25 said:**
> I tried what you said and this is what happened.

owen@owen-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
owen@owen-desktop:~$ cd Desktop
owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.bsgmSs
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.bsgmSs
owen@owen-desktop:~/Desktop$

Well, it ran. Did you disable the open-source driver first?

```
sudo rmmod ath5k_pci
```

and try the install again

---

### Post by leandromartinez98 on 2009-05-12
> **pastalavista said:**
> Well, it ran. Did you disable the open-source driver first?

```
sudo rmmod ath5k_pci
```

and try the install again

No, I don't think this is the problem, I've installed these
drivers many times and naver had to do that. 

Canucker25, are you sure you have downloaded the correct
driver to your platform? Doesn't your computer has 64bit
architecture?

---

### Post by Canucker25 on 2009-05-12
> **pastalavista said:**
> Well, it ran. Did you disable the open-source driver first?

```
sudo rmmod ath5k_pci
```and try the install again

owen@owen-desktop:~$ sudo rmmod ath5k_pci
[sudo] password for owen: 
ERROR: Module ath5k_pci does not exist in /proc/modules
owen@owen-desktop:~$

---

### Post by Canucker25 on 2009-05-12
> **leandromartinez98 said:**
> No, I don't think this is the problem, I've installed these
drivers many times and naver had to do that. 

Canucker25, are you sure you have downloaded the correct
driver to your platform? Doesn't your computer has 64bit
architecture?

There is only 1 driver for Linux and it's the one I downloaded.

[B] 	ATI Catalyst&#8482; Display Driver

 	[/B]

 	      	

 	          [B] 	Version

[/B] 
	      	9.3  	           	[B] 	Operating System(s)

	[/B] 	      	Linux x86; Linux x86_64

---

### Post by leandromartinez98 on 2009-05-12
I'm out of ideas...

---

### Post by ashmew2 on 2009-05-12
Hello Canucker25 , What is your Ati Card ?

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Hello Canucker25 , What is your Ati Card ? 

The card I have in this PC is a Radeon 9550 256mb 128-bit DDR AGP but for some reason my BIOS sees it as a 9600pro if that makes a difference.

---

### Post by ashmew2 on 2009-05-12
And you downloaded and installed a 32 Bit Jaunty ? i mean the i386 one ?

---

### Post by ashmew2 on 2009-05-12
Okay , this wont probably help at all but open up a terminal and do :

```
sudo apt-get install build-essential linux-headers-`uname -r`
```

After that , try running that driver installer again. Ill be here for as long as possible ;)

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Okay , this wont probably help at all but open up a terminal and do :

```
sudo apt-get install build-essential linux-headers-`uname -r`
```After that , try running that driver installer again. Ill be here for as long as possible ;)

"owen@owen-desktop:~$ sudo apt-get install build-essential linux-headers- 'uname -r'
[sudo] password for owen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package uname -r
owen@owen-desktop:~$"

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> And you downloaded and installed a 32 Bit Jaunty ? i mean the i386 one ?

Which ever one was on the live CD.

---

### Post by ashmew2 on 2009-05-12
There's a difference between a  ' and ` . You can just copy paste the command i gave you into the terminal. The symbol i used is beside the 1 key on my keyboard. It prints ` and ~. The one you typed in the command was ' (The one from the inverted commas key)

Btw , i dont have an ATi card  , but im downloading the driver file same as yours ..Maybe i could find something useful ? :D I have a slow a$$ 256 k connection though so itll take some time ..

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> There's a difference between a  ' and ` . You can just copy paste the command i gave you into the terminal. The symbol i used is beside the 1 key on my keyboard. It prints ` and ~. The one you typed in the command was ' (The one from the inverted commas key)

Btw , i dont have an ATi card  , but im downloading the driver file same as yours ..Maybe i could find something useful ? :D I have a slow a$$ 256 k connection though so itll take some time ..

The command worked and everything downloaded but when I ran the file again I got the same error.

"owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.FHvlzX
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.FHvlzX
owen@owen-desktop:~/Desktop$"

---

### Post by Ragnar Bocephus on 2009-05-12
Don't bother with this.  The Catalyst 9.3 drivers aren't supported in Jaunty anymore due to xorg changes.  Also, r300-r500 series ATI cards are no longer supported with official drivers.

---

### Post by ashmew2 on 2009-05-12
Okay , Im still downloading the binary , ill get back asap..

---

### Post by Canucker25 on 2009-05-12
> **Ragnar Bocephus said:**
> Don't bother with this.  The Catalyst 9.3 drivers aren't supported in Jaunty anymore due to xorg changes.  Also, r300-r500 series ATI cards are no longer supported with official drivers.

So is there no way at all to get my card recognised?

---

### Post by Mortus Pryde on 2009-05-12
You should be able to still get Intrepid from what I hear, it supported for a while longer and supports the Catalyst 9.3. IMO its just as good as Jaunty if not a little slower and lacking some additional support Jaunty may have. Otherwise it is working great on my Thinkpad.

---

### Post by ashmew2 on 2009-05-12
Yeah well , i guess installing Intrepid would save you and me a lot of headaches :P I was just editing the ati installer sh file though but i dont really think that even if it gets past that error we are having , it will be broken at a later stage..

Intrepid's not that bad when you come to think of it..Plus you can always tweak and then add Jaunty repos and still get the latest software :D

---

### Post by Canucker25 on 2009-05-12
> **Mortus Pryde said:**
> You should be able to still get Intrepid from what I hear, it supported for a while longer and supports the Catalyst 9.3. IMO its just as good as Jaunty if not a little slower and lacking some additional support Jaunty may have. Otherwise it is working great on my Thinkpad.

Thanks for the suggestion. I'll definitely take note of it in the event that I cannot get this card to work with my current version. Although I would prefer a way for it to work with Jaunty.

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Yeah well , i guess installing Intrepid would save you and me a lot of headaches :P I was just editing the ati installer sh file though but i dont really think that even if it gets past that error we are having , it will be broken at a later stage..

Intrepid's not that bad when you come to think of it..Plus you can always tweak and then add Jaunty repos and still get the latest software :D

Is there somewhere I can get unofficial drivers that might work with Jaunty?

---

### Post by Ragnar Bocephus on 2009-05-12
What sort of problem are you having?  I have a Radeon 9600 and I'm using the open source drivers that came with Jaunty, and for my money they work better than any recent incarnation of Catalyst (fglrx) ever did...

---

### Post by Canucker25 on 2009-05-12
> **Ragnar Bocephus said:**
> What sort of problem are you having?  I have a Radeon 9600 and I'm using the open source drivers that came with Jaunty, and for my money they work better than any recent incarnation of Catalyst (fglrx) ever did...

How do you tell if jaunty even detects your videocard? I'm only assuming it's not because some of the graphics are choppy.

---

### Post by ashmew2 on 2009-05-12
Edit : I saved my original post..We'll use it as a last resort.

To test video card , in the terminal :

glxgears

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Edit : I saved my original post..We'll use it as a last resort.

To test video card , in the terminal :

glxgears

OK I did that and it's saying 237.295 FPS.  Does that mean it's detecting my card? 

Is there something like a device manager where I can see my card listed?

---

### Post by ashmew2 on 2009-05-12
Yeah
Also post the output of 
```
glxinfo | grep direct
```

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Yeah
Also post the output of 
```
glxinfo | grep direct
```

owen@owen-desktop:~$ glxinfo | grep direct
direct rendering: Yes
owen@owen-desktop:~$

---

### Post by ashmew2 on 2009-05-12
LOL...You have Direct Rendering..That's suposed to not work until you have 3d Support..Have you tried running Compiz ? And what are the graphic issues that you are facing , for which you wanted to install the ati driver, i mean ?

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> LOL...You have Direct Rendering..That's suposed to not work until you have 3d Support..Have you tried running Compiz ? And what are the graphic issues that you are facing , for which you wanted to install the ati driver, i mean ?

owen@owen-desktop:~$ Compiz
bash: Compiz: command not found


Most of the animated screen savers are very choppy and I also can't watch flash videos in full screen. I just wanted to make sure my card is working for when I get Wine up and running.

---

### Post by ashmew2 on 2009-05-12
Well i didnt mean Compiz like that. Click on System > Preferences > Appearance.
Click the Visual effects tab.

Try enabling Normal or Extra..Tell me if you can feel a difference ..If you can see the new effects etc , are they slow or are they at their normal speeds ? 

What are you planning on running with wine ?

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Well i didnt mean Compiz like that. Click on System > Preferences > Appearance.
Click the Visual effects tab.

Try enabling Normal or Extra..Tell me if you can feel a difference ..If you can see the new effects etc , are they slow or are they at their normal speeds ? 

What are you planning on running with wine ?

Okay I switched it from normal to Extra and I didn't notice any extra effects So I don't know if they were slow or not.

I plan on running a few games with Wine that I used to have on windows.

Is there somewhere I can see a list of all my hardware devices?

---

### Post by perlluver on 2009-05-12
> **Canucker25 said:**
> Okay I switched it from normal to Extra and I didn't notice any extra effects So I don't know if they were slow or not.

I plan on running a few games with Wine that I used to have on windows.

Is there somewhere I can see a list of all my hardware devices?

For a list of hardware devices, type this in a terminal. ```
lspci
```

---

### Post by ashmew2 on 2009-05-12
Ok...

1) I think that the Extra effects should be enabled because you got the output as Yes to Direct Rendering. The only way i can think now is using the proprietary ATi Driver..Maybe someone will come along eventually with a solution...Now i leave the choice to you..

In my opinion, you have two choices :

a)Stick with Jaunty ,  Revert to xorg 1.5 , maybe tweak a lot more of settings and maybe have a working 3D graphics with ATi's driver.

OR 

b)Uninstall Jaunty. Install Intrepid. Install the ATi Driver and maybe have a fully functional system.

2) What games are you gonna run ? If you think they are guna be as smooth as on Windows , they'll be not..If they are "Heavy" games , they wont probably work. So if you wanna stick to Gaming , Ill propose dual booting Windows with Ubuntu.

Just let me know what you think..If you decide to install intrepid , you might wanna wait for a day or two in case someone replies..

---

### Post by Canucker25 on 2009-05-12
> **perlluver said:**
> For a list of hardware devices, type this in a terminal. ```
lspci
```

"
owen@owen-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:09.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
02:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
owen@owen-desktop:~$"

Does that mean it's detected? if so why is everything so choppy?

---

### Post by perlluver on 2009-05-12
If you go to System>Administration>Hardware Drivers, does it say if there are any proprietary drivers in use?  If so, are they the ATI drivers?  Is flash choppy?  Or everything in general?

---

### Post by Canucker25 on 2009-05-12
> **ashmew2 said:**
> Ok...

1) I think that the Extra effects should be enabled because you got the output as Yes to Direct Rendering. The only way i can think now is using the proprietary ATi Driver..Maybe someone will come along eventually with a solution...Now i leave the choice to you..

In my opinion, you have two choices :

a)Stick with Jaunty ,  Revert to xorg 1.5 , maybe tweak a lot more of settings and maybe have a working 3D graphics with ATi's driver.

OR 

b)Uninstall Jaunty. Install Intrepid. Install the ATi Driver and maybe have a fully functional system.

2) What games are you gonna run ? If you think they are guna be as smooth as on Windows , they'll be not..If they are "Heavy" games , they wont probably work. So if you wanna stick to Gaming , Ill propose dual booting Windows with Ubuntu.

Just let me know what you think..If you decide to install intrepid , you might wanna wait for a day or two in case someone replies..

I'll probably stick with Jaunty. I already have a second computer with windows. Most of the games I want to play on this PC are 5-10 years old so hopefully they work.

---

### Post by Canucker25 on 2009-05-12
> **perlluver said:**
> If you go to System>Administration>Hardware Drivers, does it say if there are any proprietary drivers in use?  If so, are they the ATI drivers?  Is flash choppy?  Or everything in general?

"No proprietary drivers are in use on this system"

It's everything in general that's choppy.

---

### Post by Carl Hamlin on 2009-05-12
> **Canucker25 said:**
> owen@owen-desktop:~$ sudo ./ati-driver-installer-9-3-x86.x86_64.run
sudo: ./ati-driver-installer-9-3-x86.x86_64.run: command not found
owen@owen-desktop:~$

Any idea what the problem is?

Yep - if the file is on your desktop, then you should be running it from the desktop directory. try:

```

owen@owen-desktop:~$ cd Desktop
owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86.x86_64.run

```

EDIT 'installer' instead of 'instealler'.

---

### Post by Canucker25 on 2009-05-12
> **Carl Hamlin said:**
> Yep - if the file is on your desktop, then you should be running it from the desktop directory. try:

```

owen@owen-desktop:~$ cd Desktop
owen@owen-desktop:~/Desktop$ sudo ./ati-driver-installer-9-3-x86.x86_64.run

```EDIT 'installer' instead of 'instealler'.

Thanks for the suggestion but i have already tried that multiple times and this is what i get.

"Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro"

---

### Post by Canucker25 on 2009-05-12
anymore suggestions? I would really like to have a driver for this card.

---

### Post by Michael Dooley on 2009-05-12
Please see [COLOR="Red"][this]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")[/COLOR] page for installation instructions. You are trying to install Catalyst 9.3 I believe and that version of Catalyst won't run in Ubuntu 9.04. You need Catalyst 9.4.

The unofficial ATI Linux Driver Wiki has pages that contain step by step instructions to install the Catalyst drivers.

Good luck.

---

### Post by Don1500 on 2009-05-12
bUMP FOR THE LINK

---

### Post by Mortus Pryde on 2009-05-12
> **Michael Dooley said:**
> Please see [COLOR="Red"][this]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide")[/COLOR] page for installation instructions. You are trying to install Catalyst 9.3 I believe and that version of Catalyst won't run in Ubuntu 9.04. You need Catalyst 9.4.

The unofficial ATI Linux Driver Wiki has pages that contain step by step instructions to install the Catalyst drivers.

Good luck.

The problem with Catalyst 9.4 is that is no longer supports 300 through 500 series graphics cards. Thusly this will not work for the OP, infact if he tries its quite the pain to undo. I have been there, trust me on this one. ;)

---

### Post by Canucker25 on 2009-05-12
> **Mortus Pryde said:**
> The problem with Catalyst 9.4 is that is no longer supports 300 through 500 series graphics cards. Thusly this will not work for the OP, infact if he tries its quite the pain to undo. I have been there, trust me on this one. ;)

Thanks for the warning I just finished downloading 9.4 and was just about to run it. Is there anyway at all to even get an Open Source driver? My "hardware drivers" is empty.

---

### Post by Ragnar Bocephus on 2009-05-12
^ You already have the open source driver.  I would suggest turning off Desktop Effects (Compiz) and seeing if that makes a difference in the way video displays.

Your glxgears framerates seem to be abnormally low.  If you could post the complete output of glxinfo within code tags, that might help us diagnose the problem.

```
glxinfo
```

---

### Post by Canucker25 on 2009-05-12
> **Ragnar Bocephus said:**
> ^ You already have the open source driver.  I would suggest turning off Desktop Effects (Compiz) and seeing if that makes a difference in the way video displays.

Your glxgears framerates seem to be abnormally low.  If you could post the complete output of glxinfo within code tags, that might help us diagnose the problem.

```
glxinfo
```


```
owen@owen-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_MESAX_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_logic_op, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_compiled_vertex_array, GL_EXT_convolution, 
    GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_gpu_program_parameters, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_mirror_once, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_NV_vertex_program, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SGIX_depth_texture, 
    GL_SGIX_shadow_ambient, GL_SUN_multi_draw_arrays

16 GLX Visuals
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x6f 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x70 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x71 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x72 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x73 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x74 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x75 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x76 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x77 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x78 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x79 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x7a 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5d 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None

16 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x5e  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5f  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x60  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x61  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x62  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x63  0 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x64  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x65  0 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x66  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x67  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x68  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x69  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x6a  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6b  0 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x6c  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x6d  0 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow

owen@owen-desktop:~$ 

  
```

---

### Post by Canucker25 on 2009-05-12
bump.

---

### Post by Canucker25 on 2009-05-12
Okay, I give up. I'm currently downloading 8.04. I guess I'll try my luck when 9.10 get released in October. I have one more question if anyone cares to answer. 

Is it possible for me to downgrade to hardy without deleting all my current files?

---

### Post by ashmew2 on 2009-05-13
Well , You can save your home folder.

Dont format your /home.

Mount it as it is under Hardy (should be ext3 , ext4 wont do)

---

### Post by 3rdalbum on 2009-05-13
ATI cards don't give very good performance even if you have the official proprietary driver installed. (If you're going back to an older version of Ubuntu you will be able to enable the proprietary driver from the Hardware Drivers program).

If you will be in the market for a new computer in the near future, make sure you choose one with Nvidia graphics.

---

