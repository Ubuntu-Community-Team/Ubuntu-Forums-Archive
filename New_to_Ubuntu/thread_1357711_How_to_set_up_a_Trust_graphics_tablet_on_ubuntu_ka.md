---
title: "How to set up a Trust graphics tablet on ubuntu karmic."
date: 2009-12-17
forum: New to Ubuntu
---

### Post by techno-mole on 2009-12-17
[COLOR="Red"]********** UPDATE 15th October 2010 **********[/COLOR]

UP until last night the wizardpen driver wasn't working for a lot of people in maverick, however due to some work by Negora and Dr Mo the driver is now working on maverick, at least for me, you can install the driver already if you have the drmo ppa installed, if not you can add the ppa mentioned in this thread and install the driver using synaptic.

I would recommend removing any other versions of the wizardpen driver before installing the new one.

Please also consider adding your tablet information to this page ---> [https://wiki.ubuntu.com/GraphicsTablet]("https://wiki.ubuntu.com/GraphicsTablet")
and please see this for more information ---> [https://lists.launchpad.net/wizardpen-testers/msg00000.html]("https://lists.launchpad.net/wizardpen-testers/msg00000.html")



[COLOR="Red"]****** UPDATE 5th May - 2010 ******[/COLOR]

As of 10.4 (lucid lynx) getting the trust tb-6300 (the tablet I use) to work is pretty easy, and as far as I know the other tablets listed in this post and the wiki should also work, with minimal tweaking.

You still need to make sure the following are installed as well 
```
sudo aptitude install xutils libx11-dev libxext-dev x-dev build-essential xautomation xinput xserver-xorg-dev
```

So for lucid add this to your sources list - ppa:doctormo/xorg-wizardpen I normally do this through synaptic, once added reload and look for the wizardpen entry, just type wizardpen into the quick search filed.

Install the driver, then reboot just to make sure, or restart the session and you should be good to go.

If you want to adjust the way your tablet behaves then you need to edit the ----> 70-wizardpen.conf file this can be found here ----> /usr/lib/X11/xorg.conf.d it may be in a different place to me, so if you can't find it there look here ---> /etc/xorg.conf.d

You can either edit as root or copy the file to your home directory and edit it there (this is what I did, I also saved the original file first, in case of issues) 

This is my config file for reference, this works for the Trust-tb-6300, and it works really well for me, so hopefully it will work for others.

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```

You can also use the method below and install from bzr, but as far as I know the bzr version is the same as the version from the ppa

[COLOR="Red"] ****************************************************[/COLOR]


[COLOR="Red"] If you experience problems with anything relating to the wizardpen driver and your tablet by all means post in this thread and those of us that keep an eye on it will try and help, any bugs you feel there are you really will be helping by posting bug reports on the wizardpen section of launchpad, the links are in this thread, thank you[/COLOR]


[COLOR="Red"]****** UPDATE 28th March 2010 - I have added this section for people wanting to set up a trust tablet (using the wizardpen driver) on lucid beta, it should be okay for the rc of lucid as well ? ******[/COLOR]

First make sure these packages are installed - 
```
sudo aptitude install xutils libx11-dev libxext-dev x-dev build-essential xautomation xinput xserver-xorg-dev
```

these steps are also mentioned in the wizardpen wiki [wizardpen wiki]("https://help.ubuntu.com/community/TabletSetupWizardpen")

Next run the following in terminal - 
```
sudo apt-get install bzr

```

then this - 
```
bzr branch lp:wizardpen
```

You may get a message about letting bzr know about your id etc, don't worry about it and let things run, you should then end up with a folder in your home directory named "wizardpen" 

Next - cd to the wizardpen folder, open erminal and type -
```
cd /home/YOUR USER NAME/wizardpen
```

Next run the following - 
```
sudo ./autogen.sh
```

you may get an error about autoconf not being found, so you if you open synaptic and look for "autoconf" and you should see that lucid is using a later version, all I did was to install one of the versions that comes up as obsolete, this seemed to work.

you may also get a message about "libtoolize" not being found, again open synaptic and look for "libtool" and install it.

then repeat the step above (remember you need to be in the wizardpen folder) - 
```
sudo ./autogen.sh
```

hopefully there won't be anymore issues.

Next run the following in terminal - 
```
dpkg-buildpackage -rfakeroot
```

what should happen is a .deb package should be built in your home directory, it will match your systems architecture, eg - if you run 64bit it will build a 64bit.deb.

next run the .deb (which will be something like this - xserver-xorg-input-wizardpen_0.7.1-0ubuntu3_amd64.deb) you can either double click it or run - sudo dpkg -i ../xserver-xorg-input-wizardpen_0.7.1-0ubuntu3_amd64.deb etc

this should be all you need to do, there is no need to edit xorg.comf or create fdi files, as from what I can gather lucid doesn't use hal anymore it's all udev rules etc now, I think (I'm not pretending to understand it)

I have my trust tablet working in lucid beta 1 and it's very smooth in operation, if I'm honest it seems to be working better than in karmic etc.

If you run into trouble I will try and help as much as I can, for other versions, eg - karmic you should probably follow the bits below this, as I originally wrote this how to for karmic.

Hope this helps.

Cheers.
[COLOR="Red"]
**************************************************************************

[/COLOR]

Hello, this is my first how to, so if I get things wrong please feel free to give your input.

This how to is a result of my efforts to set up my Trust 6300 slimline graphics tablet on karmic koala, if you are running a different version of ubuntu then you should read through the info in the link below, as this will probably be more helpful.

This should work for the following tablets, with some tweaking.

```
# Acecad Flair II GT-504
#

DigiPro 5.5×4&#8221; Graphics Tablet
# Digital Ink Pad (A4 format)
# G-pen
# Genius Wizardpen
# Genius Mousepen
# Genius
# iBall
# Manhattan
# Pentagram
# QWare
# Trust TB-3100
# Trust TB-5300
# Trust TB-6300
# UC-LOGIC
# iBall Tablet PF8060 
```

i originally tried to use this how to - ```
https://help.ubuntu.com/community/TabletSetupWizardpen
```

and eventually I did use part of it for the installation of the " wizard pen " driver.

so to begin.

Part 1 - driver installation.

This is simple enough (even for me)

download the wizard pen driver, I'm using the alpha version which is mentioned on the page I have linked.
( I have attached the file so you don't have to go hunting)

Important ! - before following the steps below you need to install some things, so run the follwoing code in a terminal
```
sudo aptitude install xutils libx11-dev libxext-dev x-dev build-essential xautomation xinput xserver-xorg-dev
```

to install the driver this is what I did, put the file in your home directory, or where ever you like (I tend to install everything from my home directory rather than the desktop)

then extract the archive (I normally right click and select extract here, I forget the command line way of doing it)

once extracted open a terminal and cd to the wizard pen file -
```
cd /home/your user name/wizardpen-0.7.0-alpha2
``` and press enter.

now you need to run the following -
```
sudo ./configure --with-xorg-module-dir=/usr/lib/xorg/modules && make
&& make install
```

and providing you don't have any issues (fingers crossed) you can check the installation by running the following - 
```
ls /usr/lib/xorg/modules/input/wizardpen_drv.*
```

you should get this if everything went okay - 
```
/usr/lib/xorg/modules/input/wizardpen_drv.la
/usr/lib/xorg/modules/input/wizardpen_drv.so
```

if you did then the fun begins, now if you have read through the wiki entry I linked then you will be thinking oh s*&t (I did) but fear not it's actually quite simple because you don't need to mess with xorg at all, and I don't think you need to in karmic ?

Part 2 - setting up udev, if your device is usb.

plug your tablet in (if you haven't already)
and run this in a terminal - 
```
cat /sys/bus/usb/devices/*/product
```

the output should look something like this - 
```
Tablet WP5540U
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
EHCI Host Controller
```

here is mine for reference, as your's may be different - 
```
A815
KU990 
USB2.0-CRW
HS USB FlashDisk
Basics Desktop  
USB Trackball
Tablet WP8060U - this is my trust 6300 slim line usb tablet
EHCI Host Controller
EHCI Host Controller
OHCI Host Controller
OHCI Host Controller

```

now we need to add a udev rule - Please note that the SYSFS{product} is tablet specific so see the output from the above command ( this one - cat /sys/bus/usb/devices/*/product)

now open a terminal (if you don't have one open) and run the following - 
```
sudo bash
```

and then this - 
```
echo 'BUS=="usb", KERNEL=="event*", SYSFS{product}=="Tablet WP8060U", NAME="input/%k", SYMLINK+="tablet-event", MODE="0666"' >> /etc/udev/rules.d/010_local.rules
```

Note ! the section in the above code that says - SYSFS{product}=="Tablet WP8060U" needs to match your tablet 

now this -  
```
exit
```
 
Wait a second ! -  because according to the wiki you should run the code below to restart udev, but running this will give you some messages about invoking scripts if you are using karmic.

```
sudo /etc/init.d/udev restart
```

so instead of the code above, if you're using karmic try this - 
```
service udev restart
```

if this is wrong please feel free to let me know and I'll amend it.
Note ! if - service udev restart, doesn't work then you could always resort to restarting your session.

now you will need to check to make sure the syslink has been created so run the following code - 
```
ls -la /dev/tablet-event
```

if you get a line of output then everything is okay, unless it says something really bad :-)

Part 3 - calibration

now this step is where i had some interesting results, but feel free to have ago.

first cd to the calibrate folder in the driver file, so in terminal run the following - 
```
cd /home/your user name/wizardpen-0.7.0-alpha2/calibrate
```

then run - 
```
make
```

then - 
```
sudo ./wizardpen-calibrate /dev/tablet-event
```

now providing everything went okay you should now have some instructions to follow, so follow away, and save the last 12 lines of the output in a text file, you will need them.

this is where things got a little odd for me, because when a adjusted the fdi file (which we will create in a little while) with the dimensions that the calibrate tool gave i had great difficulty using my tablet because for some reason the dimensions weren't right, I ran the calibrate tool a number of times trying different corners and always the same result, so if you have trouble then maybe you should try the steps I will outline in a minute.

so if you get funky coordinates for your tablet and is the same as mine, that being a trust 6300 slim line usb tablet, then try this, which is taken from the wiki - 

Tablet W8060U (UC-Logic): 
```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
EndSection
```

copy and paste the above or just keep it handy some where, you will need the bits that say top x etc etc.

now on to the fdi file, which is where the wiki could do with updating, mainly because it doesn't mention and fdi file, so I'm going to use this thread for the creation of the fdi file (the fdi file in this thread is for a different tablet, but we will adjust it to work for the trust 6300 tablet, and it may well work for other tablets)- ```
http://ubuntuforums.org/showthread.php?p=8506008
``` PS - thanks to drpjkurian

right now (I'm going to do things a little differently) open gedit or your choice of text editor.

and copy and paste the following into it - 
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="NAME OF YOUR TABLET">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
                <merge key="input.x11_options.TopX" type="string">5619</merge>
                <merge key="input.x11_options.TopY" type="string">6554</merge>
                <merge key="input.x11_options.BottomX" type="string">29405</merge>
                <merge key="input.x11_options.BottomY" type="string">29671</merge>
                <merge key="input.x11_options.MaxX" type="string">29405</merge>
                <merge key="input.x11_options.MaxY" type="string">29671</merge>
                </match>
            </device>
            </deviceinfo>
```

Please note that where it says " the name of your tablet " in the above code you will need to put the name of your tablet, if you didn't make note of it you can run the following - 
```
grep -i name /proc/bus/input/devices
```

now once thats done you need to save the file and name it the following - 
```
99-x11-wizardpen.fdi
``` 
and right click on it and select copy

and then you will need to put this file in the right place, so this is how I did it, in a terminal run - 
```
gksudo nautilus
```
and enter your password, then you will need to navigate to the following folder in your file system - 
```
/etc/hal/fdi/policy/
``` once there right click and select paste, and this should put the file in the right place, and the reason you need to do gksudo nautilus is because you need to be root to make changes to the file system.

now with that done it's the moment of truth, reboot you system and keep your fingers crossed :-) and if I have written this out right and not made any mistakes your trust 6300 tablet should work.

Some points to note, the fdi file may well work for other tablets, but you will need to change the tablet name to match yours, and the x,y and z coordinates, the other thing is that this fdi file doesn't give you pressure sensitivity, which if you're like me you will want, so what to do ?

well it's easy enough, you need to add some extra lines to the fdi file.
you will have to find out what sort of pressure ranges your tablet has, the trust 6300 (the one i have) has 1024 ranges of pressure, so open the fdi file in your text editor, we are going to add some new lines  - ```
 <merge key="input.x11_options.topZ" type="string">6</merge>
      <merge key="input.x11_options.bottomZ" type="string">1024</merge>
      <merge key="input.x11_options.maxZ" type="string">1024</merge>
```

these lines need to be put in the right place, so to make it easy, if you have the same tablet as me (did i mention it was the trust 6300 slimline tablet) here is my fdi file, which works like a charm for me, I should point out that you may well get this fdi file to work for other tablets if you tweak the x,y and z coordinates to match your tablets dimensions.
my fdi file - 
```
<?xml version="1.0" encoding="ISO-8859-1" ?>

<deviceinfo version="0.2">
  <device>
        <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.topZ" type="string">6</merge>
      <merge key="input.x11_options.bottomZ" type="string">1024</merge>
      <merge key="input.x11_options.maxZ" type="string">1024</merge>
      <merge key="input.x11_options.TopX" type="string">1946</merge>
      <merge key="input.x11_options.TopY" type="string">2861</merge>
      <merge key="input.x11_options.BottomX" type="string">32747</merge>
      <merge key="input.x11_options.BottomY" type="string">32762</merge>
      <merge key="input.x11_options.MaxX" type="string">32747</merge>
      <merge key="input.x11_options.MaxY" type="string">32762</merge>
    </match>
  </device>
</deviceinfo>
```

you can see that the new lines have been added to the start of the file and relate to the z axis, which is basically the stylus.

the lines that have 1024 and 6 relate to the pressure, 1024 being the maximum and 6 being the minimum.

I have tweaked mine a little because i noticed that if i set the lower end too low, then i would activate the left click events, so you may want to adjust this, once edited copy the fdi file into the - /etc/hal/fdi/policy/ folder and just over write the old one, the reboot and you should have pressure sensitivity, at least in gimp.

one last thing to get the tablet to work in gimp (I'm not sure about other applications) you will need to adjust a few things in gimp.

so open gimp (if you use it) and go to input devices, --> edit --> preferences --> input devices, click on " configure extended input devices " and in the window that should pop up you should see the option that says device, and if go through this you should see your tablet, uc logic etc etc, now I have mine set like this - 
```
Mode - screen
X - 1
Y - 2
Pressure - 3
``` the other options I have left alone.

you can add other things to the fdi file to do various things, there is a read me in the wizard pen archive.

I hope you find this how to useful :-)

cheers.

---

### Post by drpjkurian on 2009-12-17
Hi Technomole

Thank you for sharing your expertise

With regards
Dr Kurian

---

### Post by henriquemaia on 2009-12-20
Thanks so much for this easy to follow howto! Now my tablet is working :KS

---

### Post by sandrock50 on 2009-12-31
Hi, i am completely new to the ubuntu OS (well not really that new), but i have only gotten as far as getting the internet to work and getting my work done and following very simple instructions on how to do things. I can't quite get my trust tablet tb-5300's pressure sensitivity to work. I have put done everything here and changed the pressure ranges to fit my tablet and it still doesn't work

---

### Post by techno-mole on 2009-12-31
what does your fdi file look like ?

it may be that you need to change the lines of it about to get the pressure to work, also what app are you using it with ? 

so far i have only managed to get mine to work the way it should with gimp, and adobe elements, through wine and through a virtual machine.

it does work with other apps, inkscape for example, but its use is limited a little, I havent really looked into getting it to work with other apps, other than those I mentioned as i dont use them.

post your fdi file and i will have a look and see if i can figure it out, also what is the exact make of your tablet ? and how does it show up on the system.

cheers

---

### Post by sandrock50 on 2010-01-01
This is how my .fdi looks like. I am using a Trust TB-5300 UC logic tablet WP5540U. The programs i want to use the tablet with is GIMP and sai

Code:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
		<merge key="input.x11_options.topZ" type="string">10</merge>
		<merge key="input.x11_options.bottomZ" type="string">512</merge>
		<merge key="input.x11_options.maxZ" type="string">512</merge>                
		<merge key="input.x11_options.TopX" type="string">2387</merge>
                <merge key="input.x11_options.TopY" type="string">3582</merge>
                <merge key="input.x11_options.BottomX" type="string">30453</merge>
                <merge key="input.x11_options.BottomY" type="string">29450</merge>
                <merge key="input.x11_options.MaxX" type="string">30453</merge>
                <merge key="input.x11_options.MaxY" type="string">29450</merge>
                </match>
            </device>
            </deviceinfo>

---

### Post by sandrock50 on 2010-01-01
> **sandrock50 said:**
> This is how my .fdi looks like. I am using a Trust TB-5300 UC logic tablet WP5540U. The programs i want to use the tablet with is GIMP and sai

Code:

<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <!-- in Step 2 specified previously                        -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>

                <!-- Modify these configuration accordingly -->
                <!-- See CONFIGURATION OPTIONS section for the full-set of -->
                <!-- configurable options                                  -->
		<merge key="input.x11_options.topZ" type="string">10</merge>
		<merge key="input.x11_options.bottomZ" type="string">512</merge>
		<merge key="input.x11_options.maxZ" type="string">512</merge>                
		<merge key="input.x11_options.TopX" type="string">2387</merge>
                <merge key="input.x11_options.TopY" type="string">3582</merge>
                <merge key="input.x11_options.BottomX" type="string">30453</merge>
                <merge key="input.x11_options.BottomY" type="string">29450</merge>
                <merge key="input.x11_options.MaxX" type="string">30453</merge>
                <merge key="input.x11_options.MaxY" type="string">29450</merge>
                </match>
            </device>
            </deviceinfo>

i got rid of the chunk in the middle and added a line that i missed and it still doesn't work :(

---

### Post by techno-mole on 2010-01-02
okay, ive had alook at the fdi file you posted, and to be honest i cant see anything wrong with it (im not an expert)

heres what yours should look like - 
```
<?xml version="1.0" encoding="ISO-8859-1" ?>

<deviceinfo version="0.2">
  <device>
        <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.topZ" type="string">10</merge>
      <merge key="input.x11_options.bottomZ" type="string">512</merge>
      <merge key="input.x11_options.maxZ" type="string">512</merge>
      <merge key="input.x11_options.TopX" type="string">2387</merge>
      <merge key="input.x11_options.TopY" type="string">3582</merge>
      <merge key="input.x11_options.BottomX" type="string">30453</merge>
      <merge key="input.x11_options.BottomY" type="string">29450</merge>
      <merge key="input.x11_options.MaxX" type="string">30453</merge>
      <merge key="input.x11_options.MaxY" type="string">29450</merge>
    </match>
  </device>
</deviceinfo>
```

have you tried adjusting the lower end of the pressure setting ? - try reducing it from 10 down to 5 etc, i did tweak mine a little, its now on 6 i think.

the other thing you could try is adjusting the gimp settings, once you have adjusted the settings make sure you select save, and then again on the " save input device settings now " option.

have you bee restarting the system after making changes to the fdi file ? i did this a couple of times and found it wasnt working, but then i figured out that you have to restart to load the new changes.

i will have a look around to see what else it might be, but for now i cant really see any reason why it wouldnt work, at least for gimp, im not familiar with sai ?

have you had a look at this thread - [http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)  it might help.

---

### Post by sandrock50 on 2010-01-02
ive checked that thread and added a bit onto the end, i have also tweaked the parameters for the pressure several times and reseting in between but still no luck
heres what it looks like now : 
<?xml version="1.0" encoding="ISO-8859-1" ?>
            <deviceinfo version="0.2">
            <device>
                <!-- This MUST match with the name of your tablet obtained -->
                <match key="info.product" contains="UC-LOGIC Tablet WP5540U">
                <merge key="input.x11_driver" type="string">wizardpen</merge>
		<merge key="input.x11_options.Type" type="string">stylus</merge>
                <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
		<merge key="input.x11_options.topZ" type="string">4</merge>
		<merge key="input.x11_options.bottomZ" type="string">512</merge>
		<merge key="input.x11_options.maxZ" type="string">512</merge>                
		<merge key="input.x11_options.TopX" type="string">2387</merge>
                <merge key="input.x11_options.TopY" type="string">3582</merge>
                <merge key="input.x11_options.BottomX" type="string">30453</merge>
                <merge key="input.x11_options.BottomY" type="string">29450</merge>
                <merge key="input.x11_options.MaxX" type="string">30453</merge>
                <merge key="input.x11_options.MaxY" type="string">29450</merge>
		<merge key="info.product" type="string">stylus</merge>
      		<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>                
		</match>
            </device>
            </deviceinfo>

---

### Post by Favux on 2010-01-02
Hi,

I've got a couple of thoughts.

First you have a duplicate:
```
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge> 
```
Try removing the second one.  Also place your coordinates after the stylus and SendCoreEvents lines.  Then see if it works after a reboot.

Then do we know all the tablets have 512 level of pressure?  Simplify the .fdi too:
```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<deviceinfo version="0.2">
<device>
<!-- This MUST match with the name of your tablet obtained -->
<match key="info.product" contains="UC-LOGIC Tablet WP5540U">
<merge key="input.x11_driver" type="string">wizardpen</merge>
<merge key="input.x11_options.Type" type="string">stylus</merge>
<merge key="info.product" type="string">stylus</merge>
<merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
</match>
</device>
</deviceinfo> 
```
And then see what the output of:
```
xinput --list
```
and the Xorg.0.log in /var/log/ say about the coordinates/pressure level with just the WizrdPen driver.  The Xorg.0.log will also point out errors.

Also if it says there are 512 of pressure (z axis) what if 0 is a level?  Then 512 levels would be 0 to 511 correct?  So maybe 511 or 1023 or 255 in the .fdi?

---

### Post by frenkiel on 2010-01-06
hi,
I installed today a TRUST TB-7300 tablet
on Karmic, following the instructions above, and it almost works, excepting:
1/ I'm unable to set it in relative mode. The command:
xinput set-mode "Trust Tablet" relative
returns:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  14
  Current serial number in output stream:  14

(idem with "absolute")

2/ all buttons act as "button 1"

what do you suggest?

---

### Post by techno-mole on 2010-01-09
I'm not sure what you mean by relative mode ?

I don't think I covered that, was it from the wiki entry ?

---

### Post by frenkiel on 2010-01-10
Google ave me this link:
[http://tldp.org/HOWTO/Wacom-Tablet-HOWTO-5.html](http://tldp.org/HOWTO/Wacom-Tablet-HOWTO-5.html), where you can read:
If you set a device in mode absolute, this means, that the active area of the tablet will be mapped to the screen. Every time you go down to the tablet at the same point with an absolute device the pointer will appear at the same point of the screen.

If you set a device in mode relative, you will get the well known behavior of a mouse. This means, that if you take the mouse off from the surface, move it and go down again, the pointer does (ideally) not move. 

BTW, after updating my xorg.conf, the 3 buttons work, but the cursor speed is so high
that it's very difficult to use the pen, and
I don't know how to adjust the speed
("xinput set-ptr-feedback" do nothing)

---

### Post by techno-mole on 2010-01-10
curious, this is how my tablet behaves, with out having to set it as relative or not ?

my tablet behaves the same under karmic as it does under xp (i dual boot) i used xp to see if the tablet is working as it should, and apart from the keys around the side of the tablet (which i dont use anyway) it works perfectly.

im probably wrong but the link you posted goes into a load of stuff i havent seen before, and its things i havent had to do with my tablet, the hot to you linked seems very complex, considering that all i did to get mine working was the steps i first posted.

again you mentioned that you updated your xorg.conf to get the buttons on the pen to work, mine worked straight of, my stylus only has 2 and they work how i want them, basically like a left or right click of a mouse, left clicking allows me to move things about, and right clicking brings up a menu of various things.

maybe i was just lucky ?

what does your tablet show up as when you run this in a terminal ? 
```
cat /sys/bus/usb/devices/*/product
``` if that doesnt work try this - ```
grep -i name /proc/bus/input/devices
```

cheers.

---

### Post by frenkiel on 2010-01-10
rather curious indeed: I tried again to stick to your step 1, i.e. I removed from xorg.conf
all sections related to the tablet. The result was that the 3 buttons actually worked, but the pointer disn't move at all !
  > cat /sys/bus/usb/devices/*/product
gives
> FreeAgentDesktop
Media Tablet
1.3M DigitalCAM
Business Inkjet 1200
Generic RNDIS
USB Receiver
EHCI Host Controller
EHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller

  and 
> grep -i name /proc/bus/input/devices
  gives
> ...
N: Name="WALTOP International Corp. Media Tablet"
...

I'll now check what happens with XP, as I didn't do it up to now

---

### Post by techno-mole on 2010-01-10
thats interesting, i had thought it might come up with a similar name to mine (and other peoples) it would seem that perhaps your tablet is made by another company and branded as a trust, as mine is ? 

this may be part of the problem, if the 7300 is made by some one else (maybe a recent change) then the driver that i use and others are also using may not go all the way to allowing you to set yours up exactly as you want, as far as i can tell the wizard pen driver will work with the following tablets - 
```
# Acecad Flair II GT-504
#

DigiPro 5.5×4” Graphics Tablet
# Digital Ink Pad (A4 format)
# G-pen
# Genius Wizardpen
# Genius Mousepen
# Genius Easypen i405
# Genius
# iBall
# Manhattan
# Pentagram
# QWare
# Trust TB-3100
# Trust TB-5300
# Trust TB-6300
# UC-LOGIC
# iBall Tablet PF8060
#

AIPTEK HyperPen 10000 U 
```

but as far as i know this is up to date info (quite recent i think ?) and it may well be the case that your tablet isnt going to work any better than it does at the moment.

if it was me and the thing was working, eg the coordinates were okay, and matched the screen size etc and i had pressure sensitivity i would most likely leave the relative/absolute settings and see how you get on, it may be that some one else will pick up on this who also uses the same tablet and knows how to get it to work.

this may sound daft, but have you tries lowering the mouse pointer speed ?

under --> preferences --> mouse ? i dont know if this will actually change the pointer speed when you use the tablet, but it might be worth a go if your system is reading the stylus as a mouse type device.

in the wizard pen archive there is also a read me that details some other options you can add to the fdi file, a couple of those are related to the pointer speed, i think, you could try adding them to the fdi file and see what happens.

---

### Post by frenkiel on 2010-01-10
> have you tries lowering the mouse pointer speed
as I said, yes, and by several ways, but none of them work(xinput, xset m, preferences-> mouse)
Can you give the exact reference for the 
readme? The only one I found is in the wizardpen
package, and I tried all it's recipes

---

### Post by techno-mole on 2010-01-10
i take it you have looked at the wiki entry as well ?

if not heres the link - [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

as for the read me, i was referring to the one in the wizard pen archive, i have attached it.

i dont really know what else to suggest, i only got my tablet a couple of months ago, and to be honest after a little bit of messing (less than you have had to do by the sounds of it) i have left it alone as it works.

there are a couple of people you could try as well, both have commented on this thread.

drpjkurian and Favux may be able to assist you better than myself, so it might be worth asking them.

---

### Post by frenkiel on 2010-01-10
by "wizardpen archive", I suppose you mean 
the tar ball. If it is the case, I actually
tried all its recommendations, as I said.
As for the link 
  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

a big number of the given links are broken, as for example the one for Gimp...

---

### Post by techno-mole on 2010-01-11
i agree the wiki does need updating, links fixed etc.

gimp is fairly easy to set up, i gave instructions on how to do it, although i cant remember where i got the instructions from, but its not really going to help you much.

i did use the wiki to set my tablet for inkscape, and it works well, but i cant get it to work for krita or kolourpaint, it behaves very strangely.

this my not be the best idea in the world but have you considered using a different driver ? i think there is a wacom driver in the repo's if not a quick search will most likely find it, there is also a .deb mentioned in the wiki for genius tablets, but it might be worth a punt at seeing if one of those drivers works better, or at least will allow you more control than this one does.

its a shame really as in my opinion this is why more people dont take up ubuntu (or other linux flavour) if peoples gizmo's dont work correctly or at all in some cases then why would they switch ? i dont think its the fault of linux or ubuntu, i think the blame lies with the hardware makers, maybe they should be a little broadminded with their drivers, or at least let others have a look at the drivers to see if they can be used to make linux versions.

im sorry i havent been much help.

---

### Post by frenkiel on 2010-01-11
> gimp is fairly easy to set up
it seems so, but for me, it behaves curiously: as long as I DON'T configure the
extended input, I can use the tablet. as soon
as I configure the extended input, nothing works neither the tablet nor the mouse) !
It's actually better with inkscape.
> have you considered using a different driver
It's exactly what I was going to do (with
wacom and aiptek drivers) I'll give the result here.
Anyway, thanks very much for your cooperation.

---

### Post by techno-mole on 2010-01-12
i was going to suggest using one of the genius drivers from the wiki - [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

the reason being that i noticed that in the calibration section there is mention of a waltop international corp slim tablet and just after that section the wiki also mentions a genius g-pen f610 and in brackets it has (waltop slim tablet)

this may be something to consider, technically the driver is for genius tablets, but if they are made by the same company theres a chance that that driver may well work for your tablet, with some tweaking perhaps ?

cheers.

---

### Post by AdamBaker on 2010-04-05
I tried out the suggestions for Lucid using the Kubuntu beta1 live CD and have some observations
1) You need to enable universe in /etc/apt/sources.list, otherwise you can't find xautomation
2) As well as the packages listed there are a few others defined as build-depends and you also need xutils-dev
3) The packaging files are now in a separate branch in bzr so after you cd into the wizardpen checkout you need to do
```

bzr branch lp:~doctormo/wizardpen/debian-packing
mv debian-packing debian

```4) I couldn't get it to work without doing apt-get remove xserver-xorg-input-wacom even though I still have that package installed on Karmic where the tablet is working fine.

---

### Post by zephid on 2010-04-06
I am having a problem with my Trust Slimline TB-6030, I am running Ubuntu Lucid, and I have tried installing wizardpen from the bzr source, as @AdamBaker wrote.
But for some reason my cursor is just locked to the top-left corner of the screen, the buttons on the pen works, but it wont move.
If I move the cursor to the bottom of the screen using my mouse, and try to use my pen, it will jump up to the top-left corner and just stay there.

Any suggestions?

PS. It works fine in Windows 7.

---

### Post by techno-mole on 2010-04-07
mine is the same at present, I had managed to build the driver, and get it working on lucid beta 1 (I used the fakeroot and created a .deb package) but due to a small problem I had to re-install lucid, and thinking I had backed up the packages i created I didn't check first, and as it turns out I hadn't backed up the files.

And now I cant get it to build on lucid, it fails with the following error -

```
make[3]: Entering directory `/home/techno-mole/wizardpen/man'
make[3]: *** No rule to make target `wizardpen.@DRIVER_MAN_SUFFIX@', needed by `all-am'. Stop.
make[3]: Leaving directory `/home/techno-mole/wizardpen/man'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/techno-mole/wizardpen'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/techno-mole/wizardpen'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

as for the cursor getting stuck in the top left, this happens for me as well, with out the driver installed, there is a fix on launchpad, but it didn't work for me, I have posted a bug report for my issue, but have a look at the following for a possible solution to the cursor issue
[launchpad bug]("https://bugs.launchpad.net/wizardpen/+bug/526003")

PS - sorry I haven't updated the how to, will get to it shortly.

---

### Post by EseNoy on 2010-04-07
I have the same problem... I've compiled today following instructions ([https://bugs.launchpad.net/wizardpen/+bug/526003](https://bugs.launchpad.net/wizardpen/+bug/526003)), but cursor stills getting stuck on upper left corner. 

I've tried to add:
```
Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection
```

but my keyboard did not work anymore [-X ...

And at the end of bug report it says:

Changed in wizardpen:
status:	 New &#8594; Fix Released (2010-03-23)

](*,) <--(I compiled it today!!)


Any fix or workaround? It really the truth out there?

Thanks in advance!!

---

### Post by techno-mole on 2010-04-07
How did you compile ?

did you use this from the faq for wizardpen ? - [launchpad wizardpen faq]("https://answers.launchpad.net/wizardpen/+faq/1021")

I would have a go at this, if you haven't already, otherwise I have no idea how you might solve the issue, other than adding a post to the existing bug.

I can't really help as I can't build the packages, I keep getting the same error, and I have informed the wizardpen team, but as yet no joy, but then I am using a beta so I expect to have some problems, it should work for karmic, so give it a go and as long as you get no errors whilst building it you should end up with a .deb (name xserver-xorg-input-wizardpen or similar) after you have installed using the .deb reboot the system and see what happens.

if you get the same as this - 
```
make[3]: Entering directory `/home/techno-mole/wizardpen/man'
make[3]: *** No rule to make target `wizardpen.@DRIVER_MAN_SUFFIX@', needed by `all-am'. Stop.
make[3]: Leaving directory `/home/techno-mole/wizardpen/man'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/techno-mole/wizardpen'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/techno-mole/wizardpen'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

then please add a post to the bug report I started on launchpad - [launchpad bug]("https://bugs.launchpad.net/wizardpen/+bug/552617")

Cheers.

---

### Post by EseNoy on 2010-04-09
I'm thinking seriously about buying a Wacom tablet, Wizardpen drivers are a real headache every new distribution... 

techno-mole:

yes, I installed the drivers following the instructions of  launchpad wizardpen faq... 

and more, I reinstalled Lucid from scratch, to have clean packages and configs. After that I had some little troubles of dependencies; I solved the dependencies problems, and compiled wizardpen .deb without more incidences.

But, again, the cursor stills going to upper-left corner, and buttons seems to work :confused: . I don't know how can I help to solve the issue... awaiting suggestions ;) .

---

### Post by techno-mole on 2010-04-10
the best advice I can give is add your issue to the list of bugs on launchpad, or as you are having similar issue to me I would suggest adding a comment to the bugs I have filed on launchpad - 

[wizardpen on launchpad]("https://launchpad.net/wizardpen")

I would go out and buy a wacom tablet just yet, it may well work better, but theres a chance it wont, and to be honest the more people that post bugs and such like the more likely the drivers will improve.

I bought my genius tablet because after some research I found it to be the one that would most likely work and more to the point work how I wanted, I read a fair amount of bug reports and such like regarding wacom tablets as well.

Half of the problem I think is that lucid is changing the way it uses things, for example in karmic you were adding fdi files and working with hal, from what I can gather hal is being depreciated, which is causing some problems at the moment, hopefully it won't be too long before the issues are resolved, you also have to take into consideration that lucid is a beta at present (not long to go though for the rc) so things are still being changed, case in point, for beta 1 I built the driver and it ran sweet as a nut, but it doesn't want to play on beta 2, so I'm guessing something has changed.

I have had issues with the nouveau nvidia packages, they just don't work on my system, so I had to remove them just to get basic functions, I would just post bugs as you find them, and attach your xorg.0.logs etc and see what happens.
(the logs can be found at var/log/)
Cheers.

---

### Post by kuckie on 2010-05-02
hey guys,

I spend most of my sunday trying to get my tablet work with the instructions provided here... very frustrated now. :(

The thing is, I have the exact same tablet as in the OP, copied all settings, tried to calibrate myself, etc...

It "somehow" works, but the pointer is stuck in the top-left corner of my screen, moving only a few pixels and back. 

Here are my xorg.conf as well as my fdi, hopefully somebody can give me a hint. Cheers.

```

<?xml version="1.0" encoding="ISO-8859-1" ?>

<deviceinfo version="0.2">
  <device>
        <!-- This MUST match with the name of your tablet -->
    <match key="info.product" contains="UC-LOGIC Tablet WP8060U">
      <merge key="input.x11_driver" type="string">wizardpen</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.topZ" type="string">6</merge>
      <merge key="input.x11_options.bottomZ" type="string">1024</merge>
      <merge key="input.x11_options.maxZ" type="string">1024</merge>
      <merge key="input.x11_options.TopX" type="string">1946</merge>
      <merge key="input.x11_options.TopY" type="string">2861</merge>
      <merge key="input.x11_options.BottomX" type="string">32747</merge>
      <merge key="input.x11_options.BottomY" type="string">32762</merge>
      <merge key="input.x11_options.MaxX" type="string">32747</merge>
      <merge key="input.x11_options.MaxY" type="string">32762</merge>
    </match>
  </device>
</deviceinfo>

```

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice "WizardPen Tablet" "AlwaysCore"
#    InputDevice "Tablet" "AlwaysCore"
#InputDevice     "Tablet"     "SendCoreEvents"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
EndSection

#Section "InputDevice"
 #       Identifier  "Tablet"
  #     Option "Name" "UC-LOGIC Tablet WP8060U"
   #    Option "SendCoreEvents" "true"
	#Driver          "wizardpen"
#        Option          "Device"        "/dev/input/by-id/usb-UC-LOGIC_Tablet_WP8060U-event-mouse"
 #       Option          "TopX"          "1848"
  #      Option          "TopY"          "2137"
   #     Option          "BottomX"       "30862"
    #    Option          "BottomY"       "30731"
#EndSection
```

Edit: I´m on 10.04 64bit

---

### Post by Favux on 2010-05-02
Hi kuckie,

Welcome to Ubuntu forums!

In Lucid HAL and the .fdi files are no more.  The .fdi's are replaced by .conf's in xorg.conf.d.

Did you install the Ubuntu package xserver-xorg-input-wizardpen 0.7.3-1ubuntu1 through Synaptic Package Manager or was it preinstalled.

Since configuration is through .conf files in xorg.conf.d or in xorg.conf check to see if there is wizardpen.conf supplied by the package.  I should be in "/usr/lib/X11/xorg.conf.d/".  Post it's name, location and contents and we can see if we can add the options you need to it.  If that fails we can do it through the xorg.conf.

Hope this helps.

---

### Post by kuckie on 2010-05-04
Hi Favux,

thanks for your answer. I will have a closer look on your suggestions/hints next weekend, as I have much work to do this week. Just in case you were wondering if I had given up or some.. :)

Greetings, Kuckie.

---

### Post by techno-mole on 2010-05-05
For lucid just add the ppa and install using synaptic, thats all you need to do now - ppa ---> ppa:doctormo/xorg-wizardpen add that to your sources list and then reload (sudo apt-get update) etc

if you want to add extra bits and bobs then you will need to edit the following file, which is located here ----> /usr/lib/X11/xorg.conf.d

the file you need is named ----> 70-wizardpen.conf

you can either copy it to your home directory and edit or use gedit as root and adjust, for reference here is mine (this is for a trust tb-6300)

```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
Option "TopX" "2199"
   Option "TopY" "3598"
   Option "BottomX" "30325"
   Option "BottomY" "29278"
   Option "TopZ" "10"
   Option "BottomZ" "1023"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""
EndSection
```

I will update the first page, apologies - techno-mole.

---

### Post by negora on 2010-05-05
Ops, I hadn't found this thread in my last search (I opened a new one, sorry). I'm also using Ubuntu 10.04 (Lucid) 64-bit but am unable to avoid a weird behaviour of the pen.

I've installed the pre-compiled driver from the DoctorMo repository. Leaving everything "as is" the X server seems not to be able to detect my tablet properly, in spite that there's one 70-wizardpen.conf file into /usr/lib/X11/xorg.conf.d . Maybe I'm wrong, but I believe that my tablet is detected as a simple touch-pad, according to some information from /var/log/Xorg.0.log and also to its behaviour, because I need to press the pen against the tablet in order to move the cursor.

Well, I've tried editing the main configuration file instead: /etc/X11/xorg.conf . I've added these lines:
```

Section "InputDevice"
    Identifier      "Tablet0"
    Driver          "wizardpen"
    Option          "Device" "/dev/input/event6"
    Option          "TopX" "2650"
    Option          "TopY" "3563"
    Option          "TopZ" "10
    Option          "BottomX" "30733"
    Option          "BottomY" "29715"
    Option          "BottomZ" "511"
EndSection
```

After doing so, things have turned better. The pen and tablet dimensions have been detected properly and I've been able to move the cursor without the need of pressing.

However, I'm facing a problem which I'm being unable to solve :S . When I press the tip it's like if apart of one click, the pen "sent" another kind of event (the left thumb button event specifically). In Firefox for example it clicks and, at the same time, it takes me one page back. Also the other 2 buttons act weird.

In the X.org log file, every time that I connect the tablet it reports on detecting 2 devices: /dev/input/event6 and /dev/input/mouse2 . I'm a beginner with Linux, but I guess that "mouse2" is the origin of my head aches, because the server detects it as a regular mouse. After checking the file 70-wizardpen.conf, I've seen that it blocks the events coming from "/dev/mouse*" devices associated to this tablet assigning no driver. So is it a confirmation that "mouse2" is causing all this mess?

I've tried to block it from the file xorg.conf in a similar fashion, leaving the Driver parameter in blank. No luck however.

Has anyone an idea which could be of help? Thank you a lot :) .

---

### Post by negora on 2010-05-06
Ummm... Does the last driver from the DoctorMo repository make a device or soft link at /dev/tablet-event to you all? Because in my case that doesn't exist and I must set /dev/input/event6 instead.

---

### Post by techno-mole on 2010-05-06
have you looked on the wizardpen section on launchpad ?

it may be worth you asking on there - [wizardpen on launchpad]("https://launchpad.net/wizardpen")

as far as I know with the - xserver-xorg-input-wizardpen version 0.7.3 driver all you need to do is install it and as long as the driver loads it should work, with no need to edit the xorg.conf etc although you do have the option of adding extra lines to the 70-wizardpen.conf file

You might try and see what this gives you, and make a note of it and post it on launchpad along with you xorg.0.log 

unplug the tablet and then run the following in terminal

```
sudo udevadm monitor --property
```

then plug your tablet in and you should get some output, make a note of it and post that on launchpad as well.

sorry I cant be of much help, but posting a bug report is probably the best way to go, unless some one knows whats up with your tablet.

---

### Post by negora on 2010-05-06
**techno-mole:** Hello! First of all, thank you for answer.

I'm going to try what you comment and submit a ticket on LaunchPad. I was resisting to do that because I thought that it was a very concrete problem of my computer configuration.

It's really curious. My intuition said that the tablet was being detected "twice": on one hand as a tablet and, on the other, as a regular mouse. There were some "proofs" like when I was using Firefox (it clicked and took me one page back at the same time) or when I moved the cursor, since it acted very goofy.

I believe that I've got a confirmation of all this a few minutes ago. I've executed "xev" to see which events were caught by X and, when I pressed the tip of the pen or pushed one of its buttons, it got every pressing and releasing event twice! Each one with different key codes:

Tip => Button 1 & Button 8
Button A => Button 2 & Button 9
Button B => Button 3 & Button 10

I guess that's a demonstration that something weird is happening here. I guess that /dev/input/mouse2 is not blocked in spite of the udev rules set by the wizardpen package installation and, thus, it's still active and interfering.

---

### Post by negora on 2010-05-06
More information...

I've realized that my tablet isn't affected by the rules at /usr/lib/X11/xorg.conf.d/70-wizardpen.conf . I've seen the logs from other users who have successfully configured their tablets and they have at least 3 entries of type "Applying InputClass" into their logs. However I've only one:

```

(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/event6)
(**) UC-LOGIC Tablet WP8060U: Applying InputClass "evdev pointer catchall"
(**) UC-LOGIC Tablet WP8060U: always reports core events
(**) UC-LOGIC Tablet WP8060U: Device: "/dev/input/event6"
(II) UC-LOGIC Tablet WP8060U: Found 10 mouse buttons
(II) UC-LOGIC Tablet WP8060U: Found scroll wheel(s)
(II) UC-LOGIC Tablet WP8060U: Found relative axes
(II) UC-LOGIC Tablet WP8060U: Found x and y relative axes
(II) UC-LOGIC Tablet WP8060U: Found absolute axes
(II) UC-LOGIC Tablet WP8060U: Found x and y absolute axes
(II) UC-LOGIC Tablet WP8060U: Found absolute touchpad.
(II) UC-LOGIC Tablet WP8060U: Configuring as touchpad
(**) UC-LOGIC Tablet WP8060U: YAxisMapping: buttons 4 and 5
(**) UC-LOGIC Tablet WP8060U: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP8060U" (type: TOUCHPAD)
(WW) UC-LOGIC Tablet WP8060U: touchpads, tablets and touchscreens ignore relative axes.
(II) UC-LOGIC Tablet WP8060U: initialized for absolute axes.
(II) config/udev: Adding input device UC-LOGIC Tablet WP8060U (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)

```

In other words, the appropriate rules aren't parsed by my X sever and it assigns the default one, called "evdev pointer catchall" and located at /usr/lib/X11/xorg.conf.d/05-evdev.conf, to my tablet.

Why is 70-wizardpen.conf ignored for my device in spite of being in the same directory that 05-evdev.conf? So curious.

PS: Thus, my supositions of two drivers controlling the same device seems to be wrong.

---

### Post by negora on 2010-05-07
**techno-mole:** Hello again! I've finally submitted a bug on the LauchPad of the WizardPen driver, hoping to get results from the original source. I've found another person with the same problem (exact one indeed), which gives me some comfort that I'm not alone, he he he. Thanks for you advice. As soon as I get an answer, I'm reporting here in case that it's of help for other users.

---

### Post by victorgb on 2010-05-07
Hello to all I have not posted in a looooong time.

I have been with Ubuntu from 6.04 just had to dump windows.
Anyway this the first time I have been stuck in a long time.
I have a genius mousepen 8 x 6 recognized in my system as WP8060U.
I have tried many instructions but with no avail.
Any suggestions how to start over. Is there a .deb download for this
tablet of mine ? its a fairly common one it worked well in 9.10.

Kind regards
Victor
South Africa

---

### Post by negora on 2010-05-07
**victorgb:** In the wiki you can find all the necessary information: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) . Read the first part (as of March 2010...) because it corresponds to the last version of Ubuntu. Maybe you're lucky and just installing the package from DoctorMo's repository your tablet works at the first attempt.

I also have a tablet identified as WP8060U but am having problems to make it work in the last version of Ubuntu.

---

### Post by kuckie on 2010-05-08
oh my goodness, it just works. out of the box, no tuning, everything works perfektly, even better than on my windows machine w/ the manufacturers driver (regarding pressure sensity). thank you guys so much! :guitar:

only question remains, how to configure the "hotkeys" on the pad?

---

### Post by techno-mole on 2010-05-10
>  	
Re: How to set up a Trust graphics tablet on ubuntu karmic.

oh my goodness, it just works. out of the box, no tuning, everything works perfektly, even better than on my windows machine w/ the manufacturers driver (regarding pressure sensity). thank you guys so much!

only question remains, how to configure the "hotkeys" on the pad? 

As far as I know for tablets that have hot keys around the edges, as mine does they dont work, and I'm not sure you can get them working under linux/ubuntu unless some one knows something I don't, although I have to say I have never actually used those keys, even when I tested the tablet under windows.

---

### Post by techno-mole on 2010-05-10
>  Re: How to set up a Trust graphics tablet on ubuntu karmic.
Hello to all I have not posted in a looooong time.

I have been with Ubuntu from 6.04 just had to dump windows.
Anyway this the first time I have been stuck in a long time.
I have a genius mousepen 8 x 6 recognized in my system as WP8060U.
I have tried many instructions but with no avail.
Any suggestions how to start over. Is there a .deb download for this
tablet of mine ? its a fairly common one it worked well in 9.10.

Kind regards
Victor
South Africa

read the first post in this thread, as of lucid you only need to add the repo and then install using synaptic, then you can edit a file for extra tweaking if you feel the need.

---

### Post by negora on 2010-05-10
**techno-mole:** Finally I've been able to solve it through many try/error tests. It was caused because my tablet isn't recognized as a tablet but as a pointer, so the rules at /usr/lib/X11/xorg.conf.d/70-wizardpen.conf didn't work.

Here it's the link to the solution submitted on LaunchPad: [https://bugs.launchpad.net/wizardpen/+bug/576610](https://bugs.launchpad.net/wizardpen/+bug/576610) .

---

### Post by techno-mole on 2010-05-12
Glad you got it sorted out, it is a lot easier (imo) in lucid to get the wizardpen driver installed and configured in a way that's easy for most to do.

I do think that those of us that don't use wacom tablets should maybe try and at least pool what we know, even if it is just from experience (I know very little about udev rules and the like, but I can test) the more people that decide to go with a wacom tablet (which is up to them) the harder it will be for those of us that use non wacom tablets.

The main reason I went with my tb-6300 was because of the price, it cost me £50 new, the nearest wacom that had the same features as the tb-6300 was over around £100, which when you have kids (like I do) is a lot to shell out, so the tb-6300 was the best deal.

I don't like the idea of people having to pay more for a peripheral just so they can get it working on a Linux system, and again the more support for devices there is (wacom included) the more people will see Ubuntu/Linux as a viable option for an os that isn't windows.

Cheers

---

### Post by Pernilio on 2010-06-11
> **Favux said:**
> Hi kuckie,

Welcome to Ubuntu forums!

In Lucid HAL and the .fdi files are no more.  The .fdi's are replaced by .conf's in xorg.conf.d.

Did you install the Ubuntu package xserver-xorg-input-wizardpen 0.7.3-1ubuntu1 through Synaptic Package Manager or was it preinstalled.

Since configuration is through .conf files in xorg.conf.d or in xorg.conf check to see if there is wizardpen.conf supplied by the package.  I should be in "/usr/lib/X11/xorg.conf.d/".  Post it's name, location and contents and we can see if we can add the options you need to it.  If that fails we can do it through the xorg.conf.

Hope this helps.

Then, how can i configure the ScreenX and ScreenY Options? (before they were in /etc/hal/fdi/policy/99-x11-wizardpen.fdi)

Actually, when i draw a square in the tablet, in the screen i see a rentangle :(

The options TopX, TopY, BottomX and BottomY work perfect in 70-wizardpen.conf file. I tried to add options ScreenX and ScreenY, but dont work. I think that these options dont exists :)

Thanks

(I have Unbuntu 10.04 amd64)

---

### Post by mcolak on 2010-08-12
I have Trust tb-6300 It work for me too

---

