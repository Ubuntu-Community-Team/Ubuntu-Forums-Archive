---
title: "nvidia"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by ben889 on 2011-01-30
i have the nvidia driver that i need for 7000m not sure how to go about and install it though, its a bin file.
also i have tried the recommended drivers that unbuntu suggests but after i do i have no GUI and after i reboot I can hear the system start if i hit enter but no GUI
also i not using the laptop monitor does this matter? after the previous attempts i tried to fix it by instructions on a different post not sure what i did but it said "monitor 0".
as of right now i have no video controls to change any settings, also i need to have a vm for windows for school but i cant install the virtual I am guessing because I have the default video from the fresh ubuntu install. so if any on can give any advice is greatly appreciated.


need to know

do i need to fiscally uninstall the old driver?

how do i install the bin file?

and once its installed do i need to set the old crt as the primary monitor or will they both be active?

I'm running ubuntu 10.10 32 bit


thanks ben


also the driver i have is 
**260.19.36**

---

### Post by TeoBigusGeekus on 2011-01-31
You don't need to manually uninstall the driver from the repositories, installing the new one will take care of the old one.

To install a bin file, navigate to its folder, lets say /home/yourusername/nvidia
```
cd ~/nvidia
```
make the file executable
```
chmod +x nameoffile.bin
```
and execute it
```
sudo ./nameoffile.bin
```

Once installed and if everything goes OK and you can do a graphical login, open terminal again and give
gksu nvidia-settings
Make any changes you want in there, save to X configuration file and quit.

---

### Post by ben889 on 2011-01-31
thank you for the reply i did this before but with ubuntus recommended drivers and after i had the reboot i had no gui so if your still on can you tell me how to undo  it if i need?
 
 
thanks ben

---

### Post by realzippy on 2011-01-31
Can you post the output:

```
sudo lshw -C video
```

---

### Post by ben889 on 2011-01-31
yeah i will when i get home from school

---

### Post by ben889 on 2011-01-31
ok here is my outpost is this sufficient for my video card? i would like to be able to choose 24 32 colour and have a tv out.
 
thanks for the quick reply s  ben 


*-display               
       description: VGA compatible controller
       product: C67 [GeForce 7000M / nForce 610M]
       vendor: nVidia Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:17 memory:f1000000-f1ffffff memory:d0000000-dfffffff memory:f0000000-f0ffffff memory:80000000-8001ffff

---

### Post by ben889 on 2011-02-01
sorry for my ignorance but I am trying to run those codes that you listed but its telling me no such directory i have the bin in my home folder and the file is labeled 
NVIDIA-Linux-x86-260.19.36.run 
can some one please simplify it more for me?

thanks Ben

---

### Post by Perfect Storm on 2011-02-01
Remember that Linux is case sensitive, it could be the case if it can't find it.


You can use the command ls to see in the current directory:
```
ls
```

for all files (also hideen);
```
ls -a
```

---

### Post by realzippy on 2011-02-01
I am pretty sure that the manually installed driver (It is the same)
won't help.

Basically you had to do to install:

1.Blacklist the nouveau module (free nvidia driver)
See the nvidia driver [README]("http://us.download.nvidia.com/XFree86/Linux-x86/260.19.36/README/commonproblems.html#nouveau") for more detailed instructions.
2.Stop X server:
    Press Alt+Ctrl+F1
    Log in at shell with your username/password
    Run:
    ```
sudo service gdm stop
```
    Navigate to your *NvidiaXXXX.run* file.If it is on the Desktop:
    ```
cd Desktop
```
    Afaik "chmod +x" is not necessary.
    ```
sudo sh NVIDIA-Linux-x86-260.19.36.run
``` (type only *sudo sh NV* and  hit "TAB" to autocomplete)
    "Yes" to all questions during installation.
    ```
sudo reboot
```

---

### Post by ben889 on 2011-02-01
So your telling me that the driver i have wont make any difference?

if thats the case then how would i go about to getting TV out?


thanks Ben

---

### Post by realzippy on 2011-02-01
*"So your telling me that the driver i have wont make any difference?"*

Run eg:
```
glxinfo | grep OpenGL
```
to see which nvidia driver is running..
when it is the same version as your downloaded driver,then there will be no difference of course.

*"if thats the case then how would i go about to getting TV out?"*

Thought you had no display at all (only hear login-sound) and can`t install the driver.
As I understand now,you have the nvidia driver installed,running and
only problems using the TV-out of your graphics-card?

Please try to specify a little...

---

### Post by ben889 on 2011-02-01
no i had no screen the previous times i tried to install the recommended drivers i had the gui right before i took your instructions and did something wrong oops. now i am booting from the live cd to get back on the forums to see the instructions again to see where i messed up. 

at this point im tired of reinstalling the os but i will if i have to so any more help from all you informational people would be great


thanks

---

### Post by realzippy on 2011-02-01
A fresh install is done in 20 minutes,and has 1 big advantage:

We all know the status of your system....

After a fresh install run:
```
sudo apt-get update
sudo apt-get upgrade
```
Then install the nvidia driver offered in System/Administration/Hardwaredrivers.
If you then get a black screen after reboot,post again..get you 
out of there then.

---

### Post by ben889 on 2011-02-01
well i making amok of things but im having fun i did google to find out how to uninstall the nvidia drivers but i had no GUI so i did a reinstall.doing updates as i type this.
what is the difference between update and upgrade?



thanks Ben

---

### Post by TeoBigusGeekus on 2011-02-01
_sudo apt-get update:_ searches your installed packages and finds the ones that need to be updated according to info from the official repositories. No actual change happens in your system.

_sudo apt-get upgrade:_ according to the latest update list, newer versions of your packages are downloaded and installed. That's when the actual change happens.

---

### Post by ben889 on 2011-02-01
well thanks for all the help and info  im kind of weary of installing the video drivers through the aditional driver apt, haven't had much luck with it.

---

### Post by TeoBigusGeekus on 2011-02-01
> **ben889 said:**
> well thanks for all the help and info  im kind of weary of installing the video drivers through the aditional driver apt, haven't had much luck with it.

Well, it depends on what you want to do with your pc. If you're into gaming, you're gonna need them. If you want to work with it, then the nouveau drivers are perfect.
Compiz and desktop effects are cool, but they only speed down your system.
I have them disabled in my maverick installation, despite the fact that my laptop could "hold" them.
They have however one use: impressing windows users and converting them to linux...:p

---

### Post by ben889 on 2011-02-01
well im not into gaming really any more but it would  be nice to play some once in a while but what i really want is my tv out i used to use this as a media pc and i would like to continue that with ubuntu.



thanks Ben

---

### Post by beew on 2011-02-01
> **TeoBigusGeekus said:**
> Well, it depends on what you want to do with your pc. If you're into gaming, you're gonna need them. If you want to work with it, then the nouveau drivers are perfect.
Compiz and desktop effects are cool, but they only speed down your system.
I have them disabled in my maverick installation, despite the fact that my laptop could "hold" them.
They have however one use: impressing windows users and converting them to linux...:p

You would need the proprietary drivers too if you watch high definition videos. That includes something just on youtube.

BTW, I thik compiz is just cool, I don't care about impressing Windows users. Some people may think decoration is a waste of resources when it comes to computing environment but they probably wouldn't insist the same thing about their own home (no desgin or decoration beyond basic functionality) :)

---

### Post by realzippy on 2011-02-01
> **ben889 said:**
> well thanks for all the help and info  im kind of weary of installing the video drivers through the aditional driver apt, haven't had much luck with it.

After your system is upgraded,you will have different kernel versions to choose from during boot.Also there is a *recovery mode* to boot with each kernel.
Can you confirm *this* when rebooting?

---

### Post by ben889 on 2011-02-01
okay so with my 7000m nividia what driver should i get?
how do i install this so i dont get the black screen after i reboot?
and where should i get the driver synaptic, ubuntu software center, or the additional driver app.


thanks Ben

---

### Post by realzippy on 2011-02-01
Additional drivers app...

...if  installed the Nvidia Driver,not booting:

1. Boot into Recovery mode (GRUB). Start failsafe-X.
2. When you're in, go to System > Administration > Additional Drivers to deactivate the nVidia driver,reboot.

---

### Post by ben889 on 2011-02-01
ok so if i get the black screen do i get to the recovery mode by crtl alt f1?
because after i do this i usally only have a blinking cursor

---

### Post by realzippy on 2011-02-01
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by ben889 on 2011-02-01
ok i tried that was hitting escape like crazy just booted into the normal desktop also i dont see where it says grub loading



thanks Ben

---

### Post by realzippy on 2011-02-01
NOTE: Users of Ubuntu Karmic (9.10) and higher will need to press and hold the left Shift key instead of Escape in step 4, and may not see the "Grub loading, please wait..." message in step 3. 


[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)



..till tomorrow I am out...

---

### Post by ben889 on 2011-02-02
ok so this is what i have been able to manage so far, i have set the modprob black list and i have installed both available drivers from ubuntus additional driver app  i installed the recommended one and then went into a terminal and stopped gdm rebooted and no gui so i reinstalled the os and this time i tried the other available one stopped gdm reboot and same thing happens and both times i reboot i get up to the flash screen and that is where it flickers over on the broken laptop monitor and thats it nothing on either moniter.


help pleas i really dont want to put windows back on her


thanks Ben

---

### Post by realzippy on 2011-02-02
The laptop monitor is broken,means physically broken?

If not (laptop's monitor not working),then what happens when you disconnect the exterenal monitor?
You never said that you are booting in a dual monitor setup......

---

### Post by ben889 on 2011-02-02
I had mentioned it in my first post. The last time i messed with the drivers i was getting a bunch of time out ranges.
Do you think its outputting to only one monitor?

---

### Post by realzippy on 2011-02-02
You have not.You asked something about a second monitor....

**So unplug your 2nd monitor** until the **NVIDIA drivers are working correctly** on the laptop's monitor.
Then you can add another monitor,decide what you want (2 displays,cloned display,or what?) and achieve to set this up.But before make your video driver work without 2nd monitor connected!

---

### Post by ben889 on 2011-02-02
Cant do that all i get from the laptop monitor is just a flash of light once in a while.
The Laptop was free but broken from a friend drinking and walking and falling i replaced the cd/ hd and i only have one slot of the dual channel memory working but it does work to a extent.
If i go and disconnect the laptop monitor will it default my crt? i know there is nothing in the bios to disable it.

but anyway thanks for the help this is far the best linux forum I have ever been on (another reason i want to stay with ubuntu).

---

### Post by realzippy on 2011-02-02
OMG.
So the laptop's screen is PHYSICALLY broken,correct?
Please confirm this.

---

### Post by ben889 on 2011-02-02
yeah i has a pretty good crack running down it. my desktop the board fried cheap pcchip board, i only have to put up with this laptop for another 7 months till i bring my school computer home and hopefully by that time i will have enough knowledge to tackle any issues that i come across.

---

### Post by realzippy on 2011-02-02
If you not install any nvidia drivers,the external monitor is working?

---

### Post by rajeev1204 on 2011-02-02
> **ben889 said:**
> i have the nvidia driver that i need for 7000m not sure how to go about and install it though, its a bin file.
also i have tried the recommended drivers that unbuntu suggests but after i do i have no GUI and after i reboot I can hear the system start if i hit enter but no GUI
also i not using the laptop monitor does this matter? after the previous attempts i tried to fix it by instructions on a different post not sure what i did but it said "monitor 0".

and once its installed do i need to set the old crt as the primary monitor or will they both be active?




also the driver i have is 
**260.19.36**

Hi, when you say that you tried installing the ubuntu suggested driver means that you had display active on 1 monitor.This was on the external monitor ?

---

### Post by ben889 on 2011-02-02
yeah it worked fine with the default driver. but when i installed the recommended driver i will get the splash screen at low res and then nothing i know it going into the os i can hear it start but cant see anything also i get time out ranges that i can see on the external.

---

### Post by realzippy on 2011-02-02
You notice that it took hours,more than 30 posts to get the information
that your laptop screen is physically broken?
Every attempt to get the nvidia driver working by editing the monitor sections of the xorg.conf file,
which would be the next step ,is impossible because you cannot type blindly. 
So what does it mean:

*yeah it worked fine with the default drivers*

DOES THIS MEAN your external monitor works with default driver as primary monitor,laptop screen off because broken**????**

---

### Post by ben889 on 2011-02-02
ok so your telling me that it cant be done?
 
it had worked when i had any brand of windows.
 
and i didnt know that i should of specified that my laptop screen wasnt working as i posted that i was using a crt and also i had now problems when running vista or windows so i didnt know it would be a issue.

---

### Post by realzippy on 2011-02-02
No,it can be done.(I think).
Basic idea is to create a xorg.conf with default driver running,then modifying file that it fits for nvidia-driver.

But:
Problem is that we cannot edit the xorg.conf file since you cannot see anything with nvidia driver installed.Correct?
If this is correct,you had to return to default drivers....since
you not seem to be able to run the recovery mode due to the broken display,this means:
Fresh install.

---

### Post by ben889 on 2011-02-02
would i be able to edit the xorg file after i install the driver or wont it be there till i reboot?
 
also if i physically removed the laptop monitor making my crt default would that work?

---

### Post by rajeev1204 on 2011-02-02
> **ben889 said:**
> would i be able to edit the xorg file after i install the driver or wont it be there till i reboot?
 
also if i physically removed the laptop monitor making my crt default would that work?


How on earth will you physically remove the laptop screen?? Break it apart ? Please  dont . :)

Ok  so from what i understand, you get a low resolution splash screen on the second monitor but later ends with a blinking light on the monitor as if monitor is sleep mode.

So tell me what type of monitor is this.How is it connected?

---

### Post by realzippy on 2011-02-02
[I]would i be able to edit the xorg file after i install the driver or wont it be there till i reboot?

also if i physically removed the laptop monitor making my crt default would that work?

[/I]
1.yes.you have to.

2.No,do not think so.But would not harm,when you are skilled mechanic -no warranty ;-)

We (the nvidia driver) need this xorg.conf file to work.
The default driver runs without this file,but it is possible to generate
a xorg.conf under the default driver,which we use as basic file and modify it.
So we need a fresh install.

---

### Post by rajeev1204 on 2011-02-02
[QUOTE=realzippy;10421592][I]would i be able to edit the xorg file after i install the driver or wont it be there till i reboot?

also if i physically removed the laptop monitor making my crt default would that work?

[/I]
1.yes.you have to.

2.No,do not think so.But would not harm,when you are skilled mechanic -no warranty ;-)

We (the nvidia driver) need this xorg.conf file to work.
The default driver runs without this file,but it is possible to generate
a xorg.conf under the default driver,which we use as basic file and modify it.
So we need a fresh install to start this project,or 
... you  blindly type when you hear the login-sound:



Zippy please remove this steps, its extremely dangerous to do anything of this sort.
......

---

### Post by rajeev1204 on 2011-02-02
Press the function key fn on the laptop with the f5 or f7 keys to get display to an external monitor.

This is how projectors work.

  i dont think xinerama is the option for him,it splits desktop into 2 monitors .It works just the same on windows for external monitors / projectors.

Same on linux, try Fn + f5 or whichever f button has a screen logo on it.

---

### Post by realzippy on 2011-02-02
*Zippy please remove this steps, its extremely dangerous to do anything of this sort.*

The alternative is a fresh install.
In this special situation this is ok.But you are right,will remove it
soon,so it won't harm anybody else's data when doing the same...

---

### Post by realzippy on 2011-02-02
*dont think xinerama is the option for him*

Twinview.
But since OP wrote about "out of range" screen need to edit xorg.conf is likely.
Anyway hope you are right with Fn + F5...

---

### Post by rajeev1204 on 2011-02-02
> **realzippy said:**
> *dont think xinerama is the option for him*

Twinview.
But since OP wrote about "out of range" screen need to edit xorg.conf is likely.
Anyway hope you are right with Fn + F5...


Yes its a little confusing, but if he sees the out of range, then recovery mode should get a console prompt, later the xorg can be edited but i dont have much idea on that.

Copy paste probably from online docs.Iam waiting for him to respond.

---

### Post by ben889 on 2011-02-02
after i have the updated drivers installed i can still get to recovery or a terminal so shouldnt i be able to revert to the old drivers and through the terminal shouldnt i be able to edit the xorg file? and just with me getting the splash screen and a recovery, and the terminal screen wouldnt that suggest that its still outputing to my external monitor. could it just be out of range?

---

### Post by rajeev1204 on 2011-02-02
> **ben889 said:**
> after i have the updated drivers installed i can still get to recovery or a terminal so shouldnt i be able to revert to the old drivers and through the terminal shouldnt i be able to edit the xorg file? and just with me getting the splash screen and a recovery, and the terminal screen wouldnt that suggest that its still outputing to my external monitor. could it just be out of range?


Absolutely right. Btw, did you try the fn + f5 keys ?

---

### Post by cariboo on 2011-02-02
> **ben889 said:**
> i have the nvidia driver that i need for 7000m not sure how to go about and install it though, its a bin file.
also i have tried the recommended drivers that unbuntu suggests but after i do i have no GUI and after i reboot I can hear the system start if i hit enter but no GUI
also i not using the laptop monitor does this matter? after the previous attempts i tried to fix it by instructions on a different post not sure what i did but it said "monitor 0".
as of right now i have no video controls to change any settings, also i need to have a vm for windows for school but i cant install the virtual I am guessing because I have the default video from the fresh ubuntu install. so if any on can give any advice is greatly appreciated.


need to know

do i need to fiscally uninstall the old driver?

how do i install the bin file?

and once its installed do i need to set the old crt as the primary monitor or will they both be active?

I'm running ubuntu 10.10 32 bit


thanks ben


also the driver i have is 
**260.19.36**

Why not just run:

```
sudo nvidia-xconfig
```

in a terminal, then open the new xorg file in a text editor, and set the horizontal and vertical refresh rates of the crt to the manufacuters specified rates, press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

I have a LG crt here, and the horizontal and vertical refresh rates look like this:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics T710BH"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection
```

You have to find the specifications for your monitor to get the correct rates, as they are different, for almost all crts

---

### Post by ben889 on 2011-02-02
yeah the function keys didnt do any thing
 
 
 
so far this has been painful but not as much as it could be thanks for the help and quick replys
 
Ben

---

### Post by realzippy on 2011-02-02
> **ben889 said:**
> after i have the updated drivers installed i can still get to recovery or a terminal so shouldnt i be able to revert to the old drivers and through the terminal shouldnt i be able to edit the xorg file? and just with me getting the splash screen and a recovery, and the terminal screen wouldnt that suggest that its still outputing to my external monitor. could it just be out of range?


Yesterday I asked you for recovery mode...gave you a link,corrected you.(post #22 - post #27)
Why did you not say that you CAN access recovery mode???????????????????

Things would have been easy.
So yeah,add a valid Hsync line to xorg.conf monitor section and you should be done.

---

### Post by ben889 on 2011-02-02
> **rajeev1204 said:**
> How on earth will you physically remove the laptop screen?? Break it apart ? Please dont . :)
 
Ok so from what i understand, you get a low resolution splash screen on the second monitor but later ends with a blinking light on the monitor as if monitor is sleep mode.
 
So tell me what type of monitor is this.How is it connected?
 
 
sorry in school.  It is a view sonic a litle old but works.
 
By blinking light you mean a blinking cursor?

---

### Post by ben889 on 2011-02-02
> **realzippy said:**
> NOTE: Users of Ubuntu Karmic (9.10) and higher will need to press and hold the left Shift key instead of Escape in step 4, and may not see the "Grub loading, please wait..." message in step 3. 
 
 
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
 
 
 
..till tomorrow I am out...
 
 
at first i wasnt getting the recovery mode geuss i was hitting esc at the wrong time and once i did get it i didnt reply that i got to the recovery mode because you said that till tommorow your out plus im a little ADD so once i progressed i was concentraiting on other things sorry i should have posted this morning with that
 
sorry i saw looked back over the post and seen that your were still giving me advice even after you said you were out till tommorow, at one point i stopped looking at who was helping and just looking for solutions

---

### Post by realzippy on 2011-02-02
So run recovery/failsafe mode and edit the xorg.conf monitor section as cariboo suggested in post #50.
If problems,post your /etc/X11/xorg.conf....

---

### Post by ben889 on 2011-02-03
hey if i run a virtual can i recreate and solve whats going on?
or would a dual boot be better?

i figure mess with a virtual or dual boot till i get it right and then mark everything down and the do it to the other

---

### Post by realzippy on 2011-02-04
...you cannot install nvidia drivers in a virtual machine,since the graphics card is also: virtual.

---

### Post by ben889 on 2011-02-04
ok then ill dual boot it till i get it right

---

### Post by ben889 on 2011-02-16
> **cariboo907 said:**
> Why not just run:

```
sudo nvidia-xconfig
```in a terminal, then open the new xorg file in a text editor, and set the horizontal and vertical refresh rates of the crt to the manufacuters specified rates, press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```I have a LG crt here, and the horizontal and vertical refresh rates look like this:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG Electronics T710BH"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection
```You have to find the specifications for your monitor to get the correct rates, as they are different, for almost all crts

i was wrong my moniter is a envision 775e but the problem now is trying to find my specs on it.

so far this is all i found


[FONT=Verdana, Arial,  Helvetica, sans-serif][SIZE=1][COLOR=#000099]**Cabinet Color**[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Bezel:   Silver; Back Cover/Base:  Dark Charcoal[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**CRT: **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Size                             (Diagonal): 17” (43.2cm)[/SIZE][/FONT]                                                                                               [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Pure                             Flat[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Viewable                            Image Size (Diagonal) **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]16.0”                             (40.6cm)[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Pre-set                            Display Area **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]300mm                             x 230mm[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Signal                            Input **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Video:                             0.7Vp-p, RGB analog[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Compatibility **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]VESA,                             SXGA, XGA, SVGA, VGA[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Scan                            Frequency **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Horizontal:                             30K~72KHz[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Pixel                            Frequency **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]110MHz[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Max.                            Resolution: **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]1280                             x 1024 @ 60Hz[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Factory                            pre-set Mode **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]6[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**User                            Programmable Mode **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]10[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Power                            Source **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Universal                             100~240 Vac, 50Hz / 60Hz[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Power                            Consumption **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]120                             Watts (Max.)[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#990000]**[COLOR=#000099]EPA                            ENERGY STAR® [/COLOR]**[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Yes[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Video                            Signal Connectors **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]15-pin                             mini D-sub Male[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Front                            Panel Controls: **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]On/Off                             Switch, Menu, Exit, Up, Down Keys, Contrast, Brightness[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**OSD                            Function: **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Contrast,                             Brightness, H-size, H-center, V-size, V-center, Zoom,  Pinchusion,                            Trapezoid, Pin-balance, Parallelogram, Rotation, 6500K, 9300K,                            User’s Color, Degauss, H/V Moire Reduce, Recall, Language,                            Exit[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**OSD                            Languages **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]English,                             German, French, Spanish, Italian, & Portuguese[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Plug                            & Play **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]VESA                             DDC1/2B[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Emissions                            Standard **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]MPRII[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Regulations **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]UL,                             FCC, FDA, CSA, TUV / GS[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Weight **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Net:35.2lbs                             (16kgs); Gross: 42.9lbs (19.5kgs)[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Dimensions                            (WxHxD mm) **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Monitor:                             410x402x420; Carton: 570x540x537[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Dimensions                            (WxHxD inches) **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]Monitor:                             16x15.7x16.4; Carton: 22.4x21.2x21.2[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Loading                            Quantity w/o pallet **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]20’                             = 160 pcs; 40’ = 352 pcs; 40’ HQ = 435 pcs[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**Loading                            Quantity w/ pallet **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]20’                             = 160 pcs; 40’ = 352 pcs; 40’ HQ = 352 pcs[/SIZE][/FONT]                                                                      [FONT=Verdana, Arial, Helvetica,  sans-serif][SIZE=1][COLOR=#000099]**UPC Code **[/COLOR][/SIZE][/FONT]                         [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=1]685417752140 [/SIZE][/FONT]

---

### Post by ben889 on 2011-02-17
OK hope you guys are still paying attention. here is what i did unplugged broken laptop monitor, dual boot windows 7 with ubuntu 10.10 both fresh installs with system updates. in ubuntu installed recommended driver through the driver app reboot no GUI went to terminal typed 
sudo start failsafe-x reply
start: rejected send message, 1 marked rules; type="method-call" sender=":1.41"(uid=1000 pid=1747 com="start) interface="com.ubuntu.upstart0-6. job" member "uid=0 pid=1 com=" /sbin/init")

still in terminal so

sudo nvidia-xconfig        =said something about a back up

gksu gedit /etc/x11/xorg.conf       =gtk-warning ** cannot open display

so in recovery i tried to run it in failsafe and the reply i got was no screens found.

did i do something wrong?  what should i do now i have windows i can fall back on but i dont want to have to.



Thanks Ben

---

### Post by realzippy on 2011-02-17
So ubuntu runs on external monitor fine,but after installing the
nvidia-driver you cannot login?
If this is correct,start recovery mode,drop to shell,delete xorg.conf from
X11:

```
sudo mv /etc/X11/xorg.conf ~/Desktop/xorg.conf.nvidia
```

This should make your system boot again and moves the xorg.conf file
to your Desktop,now named *xorg.conf.nvidia* (post it's content later on).
Further instructions when this has worked.

---

### Post by ben889 on 2011-02-17
Thanks zippy i was hoping you were out there. I am at school now will try when i get home

---

### Post by ben889 on 2011-02-17
Thanks zippy but it didn't work i get cannot stat no such file or directory

---

### Post by realzippy on 2011-02-18
The xorg.conf has to exist,if you installed the nvidia driver...
Typo  (eg the capital "X") ? Please try again.
If still no luck,you have to install Ubuntu again;I cannot help you out without display.
Make all updates,but do not install the nvidia driver;then we can go on.

Where you are from?
Just asking because of the time difference....

---

### Post by ben889 on 2011-02-18
im from Pennsylvania not sure if i set the region when i signed up

---

### Post by ben889 on 2011-02-18
still no luck. cant i just reinstall the default nvidia driver?



sudo add-apt-repository ppa:xorg-edgers/nouveau
sudo aptitude update && sudo aptitude install xserver-xorg-video-nouveau

---

### Post by ben889 on 2011-02-19
OK zippy i officially release you from this problem (until the next one). apparently i was that tired yesterday when i pulled the cable out of the lap top monitor i put it back in when i was putting the laptop together, so i figured today i would pull the screen back out to get the numbers and see if i could find one on ebay and there it was plugged back in. so this is solved 

but really don't go any where im bound to screw something up 


thanks for all the help so far guys

Ben

---

### Post by Atuan on 2011-02-21
Hello there. While this thread is marked as [SOLVED], there is no technical solution to Ben's problem. I'm having the same exact issue, so I'll pick it up where he left off with my information.

I have a Vaio VGNS2645 with a PHYSICALLY DESTROYED monitor. I depend on external output for seeing, but I can do a few things since a very small portion of the screen is visible. Lots of guessing.

My machine also worked with Ubuntu default drivers. Worked fine with external input. But I needed to install Compiz as reccommened by another thread for another problem. Brightness settings would not turn down on this machine, but I digress...

Machine also starts up in 'console' mode. Prompts me for User/pass. I do it and then use startx to get going on my DE.

I ran sudo nvidia-xconfig and it made a new xorg.conf
I checked etc/X11/xorg.conf
Its empty. Nothing in it. I checked the backup xorg.conf.backup and it was also empty.

Results from sudo lshw -C video

```
user@pcname:~$ sudo lshw -C video
[sudo] password for user: 
  *-display              
       description: VGA compatible controller
       product: G86 [GeForce 8400M GS]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:ca000000-caffffff memory:d0000000-dfffffff memory:c8000000-c9ffffff ioport:2000(size=128)
```

Results from glxinfo | grep OpenGL

```
user@pc:~$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400M GS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.28
OpenGL shading language version string: (null)
OpenGL extensions:
```

Currently on driver 173 because I thought hopping from latest to a lower one may do something. It did nothing.

---

### Post by realzippy on 2011-02-21
[I]I ran sudo nvidia-xconfig and it made a new xorg.conf
I checked etc/X11/xorg.conf
Its empty. Nothing in it. I checked the backup xorg.conf.backup and it was also empty.[/I]

....remove the file and try again:

```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> [I]I ran sudo nvidia-xconfig and it made a new xorg.conf
I checked etc/X11/xorg.conf
Its empty. Nothing in it. I checked the backup xorg.conf.backup and it was also empty.[/I]

....remove the file and try again:

```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
```

Heres the readout from xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 07:06:38 PDT 2010
 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
 
Section "Files"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection
 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Also about halfway through getting you your requested info, my screen flashes and I saw what I think said **BAD DRIVER**. Not sure, I couldn't read it, but would make sense. Then it reloaded the desktop environment and left me at the login screen to reenter my session.

---

### Post by realzippy on 2011-02-21
Ehm,I do not understand:
..can you log in now?Gnome running?

..sorry,but also do not understand completely:

*I depend on external output for seeing, but I can do a few things since a very small portion of the screen is visible. Lots of guessing.*


"small portion" on your broken laptop screen or on external monitor ?

---

### Post by ben889 on 2011-02-21
Sorry for me it was simpler than i thought. I guess nvidia will only default to one screen at a time so once i physically unplugged my laptop monitor it defaulted to the external monitor, and once it defaulted i can select twinveiw and my TV out works

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> Ehm,I do not understand:
..can you log in now?Gnome running?

..sorry,but also do not understand completely:

*I depend on external output for seeing, but I can do a few things since a very small portion of the screen is visible. Lots of guessing.*


"small portion" on your broken laptop screen or on external monitor ?

small portion on broken laptop screen. 

Restarted my computer to be greeted with console start again. :(
Good news though. Nvidia control panel started to recognize my external monitor and I managed to set it up and get it so it'd make my external monitor my primary display.

Thanks for all your help in this thread, zippy. Is there any way I can stop it from starting on console like it does, or do I have to deal with it?

---

### Post by realzippy on 2011-02-21
..you mean,you have to log in and type
```
startx
```

?

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> ..you mean,you have to log in and type
```
startx
```

?

yes

---

### Post by realzippy on 2011-02-21
..after making your dual screen settings in *nvidia-settings*,
have you hit "SaveToXConfigurationFile" ?

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> ..after making your dual screen settings in *nvidia-settings*,
have you hit "SaveToXConfigurationFile" ?

yes, then I restarted.

---

### Post by realzippy on 2011-02-21
For startx issue try:

```
sudo update-rc.d gdm defaults

```

Can't you adjust brightness directly on the external monitor?

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> For startx issue try:

```
sudo update-rc.d gdm defaults

```

Can't you adjust brightness directly on the external monitor?

Bright/contrast on monitor is set up for the desktop and is already pretty low. But I fixed that problem through the nvidia utility.

terminal loadout
```
update-rc.d: warning: /etc/init.d/gdm missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/gdm ...
   /etc/rc0.d/K20gdm -> ../init.d/gdm
   /etc/rc1.d/K20gdm -> ../init.d/gdm
   /etc/rc6.d/K20gdm -> ../init.d/gdm
   /etc/rc2.d/S20gdm -> ../init.d/gdm
   /etc/rc3.d/S20gdm -> ../init.d/gdm
   /etc/rc4.d/S20gdm -> ../init.d/gdm
   /etc/rc5.d/S20gdm -> ../init.d/gdm

```

restarting.

Edit: Still starts up like terminal. Asks me to log in then I use startx.

---

### Post by realzippy on 2011-02-21
.....I suggest to update the nvidia driver.
There was a [bug in 173.xx]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/391768"),therefore 180 was made.Go with 260.xx... :
system/administration/additionalDrivers  offers nvidia-current?

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> .....I suggest to update the nvidia driver.
There was a [bug in 173.xx]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/391768"),therefore 180 was made.Go with 260.xx... :
system/administration/additionalDrivers  offers nvidia-current?

Yes, it offers nvidia-current. I have that one activated and in use.

---

### Post by realzippy on 2011-02-21
Thought you were on 173.xx.....
Anyway,I am running out of time (real life calling..);
I am back in 8-9 hours,sorry.
Remember a few "always have to startx" issues/threads in the past,
so google is your friend...;maybe you have found/tried something
till tonight..cy

---

### Post by Atuan on 2011-02-21
> **realzippy said:**
> Thought you were on 173.xx.....
Anyway,I am running out of time (real life calling..);
I am back in 8-9 hours,sorry.
Remember a few "always have to startx" issues/threads in the past,
so google is your friend...;maybe you have found/tried something
till tonight..cy

Thank you for your help. Going to head to bed and look for solutions in the morning. have fun and thanks!

---

