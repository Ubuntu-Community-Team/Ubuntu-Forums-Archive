---
title: "Ati driver"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by garrydog on 2009-01-31
Hi
Can someone tell me how to do this please ,To install the ATI Proprietary Linux driver using the Automatic option, follow
these steps:
1 Launch the Terminal Application/Window and navigate to the ATI Propri-
    etary Linux driver download.
2 Enter the command sh ./ati-driver-installer-8.573-x86.x86_64 to launch the
    ATI Proprietary Linux driver installer.
The ATI Proprietary Linux Driver Setup dialog box is displayed

How do I find the terminal application/window .I allready have the driver on my desktop .

---

### Post by Martje_001 on 2009-01-31
If you have the file on your desktop, do the following:
```
cd ~/Desktop
sh filename.bin --build-pkg Ubuntu/8.10
sudo dpkg -i *.deb
```
Good luck. Only if you're on 8.10. If you're using another version; alter the command.

---

### Post by Bablefish on 2009-01-31
But a little warning, because this actually happened to me. I tried installing the same driver and it crashed my OS. I honestly had to do a reinstall to get it all working again.

---

### Post by garrydog on 2009-01-31
Tryed to put the command into the terminal,it asked for my password ,but i cannot type it in .

---

### Post by Muffinabus on 2009-01-31
> **garrydog said:**
> Tryed to put the command into the terminal,it asked for my password ,but i cannot type it in .

You are typing it in, it just doesn't give any indication that you are.  Type in your password and hit enter and it will work fine.

---

### Post by garrydog on 2009-01-31
after I put the command in ,it then wants the password but I am unable to type anything in .

---

### Post by garrydog on 2009-01-31
This is the output from the above command.



david@david-desktop:~$ cd ~/Desktop
david@david-desktop:~/Desktop$ sh filename.bin --build-pkg Ubuntu/8.10
sh: Can't open filename.bin
david@david-desktop:~/Desktop$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
david@david-desktop:~/Desktop$ 
david@david-desktop:~/Desktop$

---

### Post by zika on 2009-01-31
this is what makes my driver install:
go to the directory where You've downloaded Your driver. check if it has the extension .run. if it doesn't then do not follow my advice.
```
*backup Your /etc/X11/xorg.conf to a safe place*
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
*reboot*
```Your commands might be slight different but the idea is the same, if You are on 8.10 ... You will not see nothing change while You type the password but it is OK. secondline is just to allow that file to execute. I think that the problem You are having is that the file You've downloaded has the extension .run and if that is not the case then I'm wrong.

---

### Post by Martje_001 on 2009-01-31
I wasn't clear enough in my previous message I think.

1. Download the driver from ati.amd.com.
2. Place it on your desktop
3. Verify that the file is called **ati-driver-installer-9-1-x86.x86_64.run**
4. Go to a terminal and type:
```
cd ~/Desktop
sudo sh ati-driver-installer-9-1-x86.x86_64.run --build-pkg Ubuntu/8.10
```
5. Enter your password (it does not indicate your typing. Just type your password and press enter).
6. Enter:
```
sudo dpkg -i *.deb
```
[COLOR="Red"]This may break your system. Be careful. Don't fix if it ain't broken![/COLOR]

---

### Post by garrydog on 2009-02-01
Hi
I will try the above latter ,This all happened after an normal update ,downloaded the update then restart ,the screen was black with three green ubuntu across the top .
I could not sort that so I did a new install ,so i am back with the poor screen resolution again .
Thanks for all your help hope that it works ,will let you know .

---

### Post by garrydog on 2009-02-01
Hi Martje_100
Tryed as you suggested this is the readout.david@david-desktop:~$ cd ~/Desktop
david@david-desktop:~/Desktop$ sudo sh ati-driver-installer-9-1-x86.x86_64.run --build-pkg Ubuntu/8.10
[sudo] password for david: 
Unrecognized flag : --build-pkg
Makeself version 2.1.3 
 1) Getting help or info about ati-driver-installer-9-1-x86.x86_64.run :
  ati-driver-installer-9-1-x86.x86_64.run -h|--help                     Print this message
  ati-driver-installer-9-1-x86.x86_64.run -i|--info                     Print embedded info : title, default target directory, embedded script 
  ati-driver-installer-9-1-x86.x86_64.run -l|--list                     Print the list of files in the archive
  ati-driver-installer-9-1-x86.x86_64.run -c|--check                    Checks integrity of the archive
  ati-driver-installer-9-1-x86.x86_64.run --extract NewDirectory        Extract this package to NewDirectory only
 
 2) Running ati-driver-installer-9-1-x86.x86_64.run :
  ati-driver-installer-9-1-x86.x86_64.run [options] [additional arguments to embedded script] with following options (in that order)
  --keep                              Do not erase target directory after running the embedded script
  Following arguments will be passed to the embedded script:
  --install                           Install the driver(default)
  --listpkg                           List all the generatable packages 
  --buildpkg package                  Build "package" if generatable ("package" as returned by --listpkg)
  --buildandinstallpkg package        Build and Install "package" as returned by --listpkg

david@david-desktop:~/Desktop$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb
david@david-desktop:~/Desktop$ 

I restarted my computer but it is just the same .

---

### Post by Bankai56 on 2009-02-01
Did you ever try to install it through the normal restricted drivers manager. System > Administration > Restricted Drivers Manager
Is far easier.
If you get a blank screen just go to recovery mode and reset the x server should do fine again then.:D
I hope it works.

---

### Post by garrydog on 2009-02-01
Hi
Don't have a restricted drivers manager in system--administration? I am on ubuntu 8.10.

---

### Post by Bankai56 on 2009-02-01
Oh sorry. I was working in Windows the exact name is hardware drivers in system administration then click of your grafik card and then press activate.

---

### Post by zika on 2009-02-01
did You try the "script" I posted in #8?
it works for me ... :)
```
[COLOR=Red]open Terminal[/COLOR]
cd ~/Desktop
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
```

---

### Post by garrydog on 2009-02-01
Hi
If i do that and restart, I get the black screen and "cannot display this video mode".
Then i have to fix the xserver to get the desktop back ,but I still have 800x600 resolution ,I have done all this before and have had the ATI driver installed after much agro and all was wonderfull .But after a recent update from ubuntu the desktop went black ,and i have had to do a reinstall of ubuntu,now I don't know how I got the driver to install,I have the correct driver on my desktop.

---

### Post by marcgh on 2009-02-01
Hi,
I am just a day out of the same trouble as you. I fixed my display problem by downloading the ATI driver from this link:
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

Right above the driver download you will see a link to the how to install (PDF) file.
I applied it exactly but for some reason ATI did not put the correct filename in it.

Where you read :sh ./ati-driver-installer-8.573-x86.x86_64 (page 4 of 14) you should replace this with the actual driver name.

Don't do like me....restart before you can access ATI Catalyst.

However I have to tell you that some forum members adviced me to do it via the hardware drivers but it did just not worked for me.

---

### Post by zika on 2009-02-01
[COLOR=Red]0. get out of compiz and switch to metacity[/COLOR]
1. if You try this in place of Your xorg.conf what do You get?
```
Section "Device"
    Identifier    "Configured Video Device"
        Driver          "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
EndSection

Section "DRI"
        Mode            0666
EndSection
        
Section "Extensions"
        Option          "Composite" "Enable"
EndSection
```2. did You try to clean all the appearances of fglrx in Symantec? also, try this:```
cd /usr/share/ati
sudo chmod +x .fglrx-uninstall
sudo sh fglrx-uninstall.sh
```after this "cleaning" (1. + 2.) try another install.
3. try with this:```

cd ~/Desktop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo chmode +x ati-driver-installer-9-1-x86.x86_64.run
sudo sh ati-driver-installer-9-1-x86.x86_64.run
aticonfig --initial -f
```

---

### Post by garrydog on 2009-02-02
Hi zika
I put No3 into the terminal ,and the install page of the driver came up BRILL!,I then installed the driver and rebooted the computer .But on the normal boot the black screen is on again with "CANNOT DISPLAY THIS VIDEO MODE" on the sceen .I have had to start in recovery and xfix to get the desktop back,still can't change the screen resolution above 800x600 .
How do i find the ATI driver that i have installed? ,how do i get the thing to work?
Thanks .

---

### Post by zika on 2009-02-02
did You try Applications->ATI_Catalyst_Control Center?

---

### Post by garrydog on 2009-02-02
Hi its saying that the driver is not installed .As I cannot boot normaly only in recovery mode,will this stop the driver installing .

---

### Post by zika on 2009-02-02
sorry. I kind'a lost You. which of 5 lines in case 3. did You finish before You did reboot? what about 1. and 2.?
1. was intended to get You to use open-source ati driver so You could do 2. and clean all previous fglrx drivers and their remnants. then 3. would get You to use ati proprietary (newest) driver. last line would make required change in xorg.conf.  then You could reboot and (since it was installed) use amdcccle to set Your resolution and other effects.

(did You choose automatic in installation procedure for ATI ...?)

---

### Post by garrydog on 2009-02-02
Sorry Zika now compleatly lost,I have put No 1 from your previous post into the terminal this is the readout .
david@david-desktop:~$ Section "Device"
bash: Section: command not found
david@david-desktop:~$     Identifier    "Configured Video Device"
bash: Identifier: command not found
david@david-desktop:~$         Driver          "ati"
bash: Driver: command not found
david@david-desktop:~$ EndSection
bash: EndSection: command not found
david@david-desktop:~$ 
david@david-desktop:~$ Section "Monitor"
bash: Section: command not found
david@david-desktop:~$     Identifier    "Configured Monitor"
bash: Identifier: command not found
david@david-desktop:~$ EndSection
bash: EndSection: command not found
david@david-desktop:~$ 
david@david-desktop:~$ Section "Screen"
bash: Section: command not found
david@david-desktop:~$     Identifier    "Default Screen"
bash: Identifier: command not found
david@david-desktop:~$     Monitor        "Configured Monitor"
bash: Monitor: command not found
david@david-desktop:~$     Device        "Configured Video Device"
bash: Device: command not found
david@david-desktop:~$         DefaultDepth    24
bash: DefaultDepth: command not found
david@david-desktop:~$ EndSection
bash: EndSection: command not found
david@david-desktop:~$ 
david@david-desktop:~$ Section "DRI"
bash: Section: command not found
david@david-desktop:~$         Mode            0666
bash: Mode: command not found
david@david-desktop:~$ EndSection
bash: EndSection: command not found
david@david-desktop:~$         
david@david-desktop:~$ Section "Extensions"
bash: Section: command not found
david@david-desktop:~$         Option          "Composite" "Enable"
bash: Option: command not found
david@david-desktop:~$ EndSection

---

### Post by zika on 2009-02-02
no, You should have edited Your xorg.conf as it is written at the very beginning... not put text in 1. into terminal.
I'm afraid that, in this case, by trying to help You I could make more harm to Your installation than good. so I will stop here ...
the good part is that it seems that no harm is done, yet.

---

### Post by garrydog on 2009-02-02
Yes i did the automatic install,can you tell me how do I find amdcccle,is this the same as the ATI catalist control center?
Thanks .

---

### Post by zika on 2009-02-02
> **garrydog said:**
> Yes i did the automatic install,can you tell me how do I find amdcccle,is this the same as the ATI catalist control center?
Thanks .
yes. (look at the my post #20)_ _[http://ubuntuforums.org/showpost.php?p=6662236&postcount=20](http://ubuntuforums.org/showpost.php?p=6662236&postcount=20)

---

### Post by garrydog on 2009-02-02
Thanks for trying to help me ,I find it very dificult to do such a simple thing like installing a driver ,or just to get the screen resolution to work.Maybe its time to go back to windows ,pity though i think that ubuntu is brilliant when you can get it to work properly .
Thanks again for your help .

---

### Post by zika on 2009-02-02
> **garrydog said:**
> Thanks for trying to help me ,I find it very dificult to do such a simple thing like installing a driver ,or just to get the screen resolution to work.Maybe its time to go back to windows ,pity though i think that ubuntu is brilliant when you can get it to work properly .
Thanks again for your help .
no, going back to windows is not a good option ... ;)
did You try Catalyst? once You open it, go to Display_Manager and You'll get the option to set Your resolution. it's very similar to Windows ...

---

### Post by Bankai56 on 2009-02-02
the part with doesnt support video mode sounds fishy.
What type of resolution does your screen manage?
Sometimes its because of that that it doesnt work.
I did this in Ubuntu 8.04, but maybe it still works:
Go to synaptic and typ in the search field fglrx.
Now remove that. Then go into Hardware drivers and install it.
I dont know why but in 8.04 the same thing worked with envy and now that ati released the official drivers hardware drivers option is the only option.
Don't think about returning to windows yet. :D

---

### Post by garrydog on 2009-02-05
Had a rethink about going back to windows,I have put my 80gig hard drive back into my computer ,and reinstalled ubuntu onto it .
Being still on a screen resolution of 800x600 I have downloaded and installed the ATI driver from the ATI website,I have restarted my computer with a normal boot but once again the screen is black with"connot display this video mode".

My optimum screen resolution is 1280x1024 .

---

### Post by garrydog on 2009-02-05
As sugested in the ATI install setup I put into the terminal "aticonfig" and got a long readout as follows .What do I need to do with it ,can someone tell me please .

david@david-desktop:~$ aticonfig
Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.
  --initial=check
        Identifies if the fglrx driver is present in configuration file.

TV Options:
  --tvf, --tv-format-type=STRING
        Change the TV signal format.  STRING can be one of:
           NTSC-M 
           NTSC-JPN
           NTSC-N
           PAL-B
           PAL-COMB-N
           PAL-D
           PAL-G
           PAL-H
           PAL-I
           PAL-K
           PAL-K1
           PAL-L
           PAL-M
           PAL-N
           PAL-SECAM-D
           PAL-SECAM-K
           PAL-SECAM-K1
           PAL-SECAM-L
        Note: Not all graphics cards support every mode. Regional 
              settings are applicable. 
  --tvs, --tv-standard-type=STRING
        Change the TV standard for TV output.  STRING can be one of:
            VIDEO
            SCART
            YUV
 --tv-overscan={on|off}
       Enable or disable overscan mode for TVout
       Note, not all tv-formats support overscan. Try to 
       toggle overscan off before changing tv-format if 
       and error occurs. 
 --tv-info
         Print out the current tv geometry, tv format, and if the
         tv is physically connected. 
 --tv-geometry=WIDTHxHEIGHT{+|-}X{+|-}Y
              =WIDTHxHEIGHT
         Change the size and position of the TVout display. 
         WIDTH and HEIGHT are in percentage units. Please note
         that the valid range for WIDTH and HEIGHT depends on
         the tv-format selected. However, as a rule of thumb  
         WIDTH and HEIGHT are valid in the range [1,100]  
         X and Y are pixels offsets from centre 
         of the screen. X and Y are have variable ranges dependant 
         on ASIC. Use tv-info to get valid X and Y ranges 
         If tv-geometry is invoked with just width and height 
         then X and Y are assumed to be 0
         See example 5 below for a sample usage. 

FireGL Workstation Board Features:
  --app, --use-app-profile=STRING
        Change the application profile for a FireGL workstation board.
        STRING can be one of:
            default
            maya
            softimage-xsi
            softimage-3d
            houdini4.0
            houdini5.0
            houdini5.5
Screen-Related Options:
  --ovt, --overlay-type=STRING
        Change the overlay for the X server.  STRING can be one of:
            opengl
            Xv
            disable
  --ovon, --overlay-on={0|1}
        Choose which head the hardware overlay should be visible on.  The
        hardware overlay can be used for either OpenGL, video, pseudo-color
        or stereo.
  --lcd, --lcd-mode=STRING
        Change the LCD mode.  STRING can be one of:
            center
            full
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
            horizontal          2 screens - one framebuffer,
                                screen 1 right of screen 0
            horizontal,reverse  2 screens - one framebuffer,
                                screen 1 left of screen 0
            vertical            2 screens - one framebuffer,
                                screen 1 above of screen 0
            vertical,reverse    2 screens - one framebuffer,
                                screen 1 below of screen 0
        Note:  This option is not valid if '--initial=dual-head' is specified.
  --vs, --sync-vsync={on|off}
        Enable/disable sync buffer swaps with vsync.  Enable this option to
        prevent tearing during 3D rendering.
  --psc, --pseudo-color={on|off}
        Enable/disable pseudo-color visuals.  Enable this option to get 16-bit
        color support.
  --sm, --stereo-mode={active | horizontalInterleave | verticalInterleave | off}
        Enable/disable stereo support.  Enable active option only for
        applications that support the use of hardware 3D shutter glasses.
        For the use of horizontalInterleave and verticalInterleave modes
        specialized monitor equipment is required.
  --resolution=Screen#,W1xH1,W2xH2,W3xH3,...
        Set the modes for the specified screen.  You may specify several
        resolutions separated by commas.
        Screens start at 0.  You can use 1 for dual-head
  --hsync=Screen#,LOW-HIGH
        Change the horizontal sync range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --vrefresh=Screen#,LOW-HIGH
        Change the vertical refresh range of the specified monitor.  Make sure
        you know the capabilities of your monitor before changing this option.
        Screens start at 0.  You can use 1 for dual-head
  --hsync2=LOW-HIGH
        Change the horizontal sync range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --vrefresh2=LOW-HIGH
        Change the vertical refresh range of the second display.  Make sure you
        know the capabilities of your monitor before changing this option.
  --mode2=W1xH1,W2XH2,W3xH3,...
        Change the modes for the second display.  You may specify several
        resolutions separated by commas.  Only valid for clone and big desktop
        settings.
  --screen-layout={left|right|above|below}
        Set the secondary screen position for dual head.
  --screen-overlap=NUM
        Set the screen overlap region in big desktop mode to be NUM pixels.
  --force-monitor=STRING[,STRING...]
        Describe all displays that are to be enabled and/or disabled regardless
        of physical connection.  STRING can be one or more of the following
        set, separated by commas:
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            tmds2i
            nocrt1
            nocrt2
            nolvds
            notv
            notmds1
            notmds2
            notmds2i

POWERplay Options:
  Following options will not change the config file. 
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --lsp, --list-powerstates
        Print information about power states and exit.
  --set-powerstate=NUMBER
        Set a power state listed by --list-powerstates.
  --auto-powerstates=on|off
        Enable/disable automatic transitions between battery and performance
        modes on AC/DC transitions. This automatic mode is enabled by default,
        and may compete with atieventsd style power management.

Advanced Options:
  --sync-video={on|off}
        Enable/disable sync to vsync for AVIVO video.
        This option is enabled by default and is used to prevent
        video tearing. By disabling this option video is free to
        render as fast as the 3D engine can handle. In the case of
        choppy video try to disable sync-video.
  --tls={on|off}
        Enable/disable fast thread local storage.  Disable this option when
        virtual machines or WineX fail to work properly.
  --sb, --signal-block={on|off}
        Enable/disable signal blocking.  Disable this option when debugging a
        multi-threaded OpenGL application.
  --locked-userpages={on|off}
        Enable/disable locked user pages. Disable this option if the system
        hangs when running fgl_glxgears.
        User page lock is no longer available on AGP system now.
  --gcpu, --generic-cpu={on|off}
        Enable/disable generic CPU.  Use this option if the CPU is being
        reported improperly.  For example: If you have an AMD cpu that is
        being reported as Intel.
  --max-gart-size=NUMBER
        Set user-defined max GART size for non-AGP systems.
        Possible integer values are from 64 to 512 (mb).

Dynamic Display Management Options:
  Following options will not change the config file. They are
  used for querying driver, controller and adaptor information.
  These options will be effective immediately. Other options on 
  the same command line will be ignored.
  --enable-monitor=STRING,STRING
        Setting current monitor to be enabled. Only 2 displays
        can be enabled at the same time. Any displays
        that are not on the list will be disabled.
        STRING can be one of the following set, separated 
        by commas:
            none
            crt1
            crt2
            lvds
            tv
            tmds1
            tmds2
            auto   -- use default policy to enable the displays.
  --query-monitor
        This will return connected and enabled monitor information
  --swap-monitor
        This only works for big desktop setup. This will swap the
        contents on the two monitors.
  --swap-screens={on|off}
        Enable/disable swap heads in dual-head mode.
        This option works only in dual-head mode.

Pair mode options: 
  Following options are used for query add and remove pair modes. 
  These options will be effective immediately. Other options on   
  the same command line will be ignored.
  --list-pairmode 
        list all the current existing pair modes the driver can use.
  --add-pairmode=width0xheight0+width1xheight1
        Add one pair mode to the list. width0 and height0 are the 
        size of primary display and width1 and height1 for the 
        secondary  display.
  --remove-pairmode=index 
        Remove one pair mode from the list. User can get index by 
        list-pairmode.

External Events Daemon Options:
  Following options will not change the config file. They are
  used to send commands to the atieventsd external events daemon.
  --set-policy=STRING
        Sets the event policy for the daemon to be STRING.
        See the atieventsd(8) manpage for further details.

Display attribute options:
  Following options are used for query and set adjustment of 
  specific attribute for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1, lvds, tv, tmds1, crt2, tmds2, cv, tmds2i .
   The ATTRIBTYPE in options can be one of the following strings:
        brightness, contrast, saturation, hue, positionX, 
        positionY, sizeX, sizeY, overscan, videoStandard  
  --query-dispattrib=DISPLAYTYPE,ATTRIBTYPE 
        query the specific adjustment info of the specific display.
        if ATTRIBTYPE is not specified, all supported attribute 
        information will be printed out. 
  --set-dispattrib=DISPLAYTYPE,ATTRIBTYPE:VALUE 
        set the attribute value of the specific display.

Connector type options:
  Following options are used for query connector type 
  for specific display. These options will be 
  effective immediately. Other options on the same command line 
  will be ignored.
  The DISPLAYTYPE in options can be one of the following strings:
        crt1, lvds, tv, tmds1, crt2, tmds2, cv, tmds2i .
   --query-connectortype=DISPLAYTYPE 
        query the connector type of the specific display.

Component video dongle options:
  Following options are used for query and set dongles for a 
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvdongle
        query dongle setting informations of the component video.
  --set-cvdongle=VALUE
        set the custom override value of the CV dongle. 
  --reset-cvdongle
        reset the custom override setting(to zero)of the CV dongle.

Component video customized mode options:
  Following options are used for query and set customized mode for
  component video. These options will be effective immediately.
  Other options on the same command line will be ignored.
  --query-cvmode
        query customized modes for component video.
  --add-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEDHEIGHT,REFRESH.
        add a customized mode for component video.
  --validate-cvmode=WIDTH,HEIGHT,FLAGS,BASEWIDTH,BASEHEIGHT,REFRESH.
        validate a customized mode for component video.
  --delete-cvmode=INDEX 
        delete one customized mode for component video. 

Persistent Configuration Store (PCS) Options:
  Following options will not change the config file. They are
  used to manipulate the PCS database.  Due to their nature, these.
  commands may only be run by the root user. Note that the prefix
  and key names are not case-sensitive.
  --get-pcs-key=PREFIX,KEY
        Prints out the specified prefix and key from the PCS
        database.  The type of data will be shown along with
        the contents.
  --set-pcs-val=PREFIX,KEY,VALUE
        Sets an integer value at the specified prefix and key in
        the PCS database.  The value may be specified in hex by
        prefixing it with 0x or in octal by prefixing it with 0,
        otherwise the value is assumed to be in decimal.
  --set-pcs-str=PREFIX,KEY,STRING
        Sets a string value at the specified prefix and key in
        the PCS database.
  --set-pcs-raw=PREFIX,KEY,HEXSTRING
        Sets a raw binary value at the specified prefix and key in
        the PCS database.  The value is specified as a series of
        hex bytes with no 0x or spaces.
        (e.g. --set-pcs-raw="TestSection,TestData,E84C0E" sets 3 bytes)
  --del-pcs-key=PREFIX,KEY
        Deletes the specified prefix and key from the PCS database.

Multiple display adapter options:
  Following options are used for querying and setting up multiple
  display adapters that are installed for multihead or Crossfire
  configurations.
  --lsa, --list-adapters
        Lists all detected and supported display adapters.
        The default adapter (used when --adapter is not specified)
        will be indicated with a "*" next to it.
  --adapter=ADAPTERLIST
        Selects which adapters returned by --list-adapters should
        be affected by other aticonfig options.  ADAPTERLIST contains
        either a comma-seperated sequence of the index numbers of the
        adapters to be affected or else contains the keyword "all" to
        select all the adapters.  If --adapter is missing, only the
        default adapter will be affected.
  --lscc, --list-crossfire-candidates
        Queries the driver to determine the pool of available devices that can
        can be chained together for CrossFire.
  --lsch, --list-crossfire-chains
        Lists the CrossFire chains that are currently defined along with their
        enabled state
  --cfa, --add-crossfire-chain
        Defines a new CrossFire chain.  --adapter should contain the adapter
        chain definition, with the master adapter being the first entry and
        the slave adapters being the subsequent entries in order of priority.
  --cfd, --delete-crossfire-chain
        Delete and existing defined CrossFire chain.  --adapter should list the
        master adapters of the chains to be deleted.  --adapter=all will delete
        all chain definitions.
  --cf, --crossfire={on|off}
        Enables/disables CrossFire support on the currently defined CrossFire
        chains.  --adapter should list the master adapters to be enabled or
        disabled.
  --cfl, --crossfire-logo={on|off}
        Enables/disables the appearance of the CrossFire Logo when rendering
        in CrossFire mode

ATI Overdrive (TM) options:
  The following options are used to get and set current and peak, core
  and memory clock information as well as read the current temperature of
  adapters.  By using the "--adapter=" argument the ATI Overdrive (TM)
  options can be targeted to a particular adapter in a multi-adapter scenario.
  If no adapter is explicitly targeted the commands will be run on the Default
  adapter as indicated by the "--list-adapters" command
  --od-enable
        Unlocks the ability to change core or memory clock values by
        acknowledging that you have read and understood the ATI Overdrive (TM)
        disclaimer and accept responsibility for and recognize the potential
        dangers posed to your hardware by changing the default core or memory
        clocks
  --od-disable
        Disables ATI Overdrive(TM) set related aticonfig options.  Previously
        commited core and memory clock values will remain, but will not be set
        on X Server restart.
  --odgc, --od-getclocks
        Lists various information regarding current core and memory clock
        settings.
        Including: current and peak clocks
                   the theoretical range clocks can be set to
                   the current load on the GPU
  --odsc, --od-setclocks={NewCoreClock|0,NewMemoryClock|0}
        Sets the core and memory clock to the values specified in MHz
        The new clock values must be within the theoretical ranges provided
        by --od-getclocks.  If a 0 is passed as either the NewCoreClock or
        NewMemoryClock it will retain the previous value and not be changed.
        There is no guarantee that the attempted clock values will succeed
        even if they lay inside the theoretical range.  These newly set
        clock values will revert to the default values if they are not
        committed using the "--od-commitclocks" command before X is
        restarted
  --odrd, --od-restoredefaultclocks
        Sets the core and memory clock to the default values.
        Warning X needs to be restarted before these clock changes will take
        effect
  --odcc, --od-commitclocks
        Once the stability of a new set of custom clocks has been proven this
        command will ensure that the Adapter will attempt to run at these new
        values whenever X is restarted
  --odgt, --od-gettemperature
        Returns the temperature reported by any thermal sensors available on
        the adapter.

ACPI Options:
  --acpi-services=on|off
        Enable/disable ACPI services. In the case of BIOS or kernel ACPI issues,
        ACPI services in the driver can be disabled through this option.
        The ACPI services are enabled by default.

X Server Options:
  --xinerama={on|off}
        Enable/disable Xinerama (MultiView) in the X Server configuration file.
        MultiView allows for the merging of independent desktop heads into a
        unified workspace allowing windows to freely cross X Screen boundaries.

Miscellaneous Options:
  -v, --verbose
        Show what aticonfig is doing.
  -q, --quiet
        Disable all information output except for errors.
  --effective={now,startup}
        Choose when the requested changes should take effect.
            now:     Immediately.  This change will affect the running X
                     session if applicable.  Only 'set-powerstate' and
                     'overlay-on' are applicable for now.
            startup: On future X server startups.  This change will modify the
                     X server configuration file if applicable.
        The default is 'now,startup', i.e., do both as applicable.
  --nobackup
        Do not make an automatic backup of the configuration file.
  -i, --input=FILE
        Select a FILE to input as the configuration file. Set FILE to '-' to
        pipe from standard input.  Without this option, aticonfig will search
        /etc/X11 for the default configuration file.
  -o, --output=FILE
        Select a FILE to output the new configuration file to.  Set FILE to '-'
        to print to standard output.  Without this option, aticonfig will
        replace the input file with the newly generated file.
  -h, --help
        Display this help screen.
  -f, --force
        Only valid with 'initial' option.  Force aticonfig to generate default
        Monitor, Device, and Screen sections even if the original configuration
        file has invalid settings in these sections.

Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
  2. Setting up big desktop to horizontal and set overlay on secondary display.
                        aticonfig --dtop=horizontal --overlay-on=1
  3. Setting up modes for primary display.
                        aticonfig --resolution=0,1600x1200,1280x1024,1024x768
  4. Force primary CRT on and TV-out off.
                        aticonfig --force-monitor=crt1,notv
  5. Change tv geometry 
                         aticonfig --tv-geometry=85x90+10-10 
         This will set tv to 85% width (where 100% ==
         overscan) 90% height and shift 10 pixels right of centre
         and 10 pixels down of centre. 
  6. Multiple display adapters.
       List adapters :  aticonfig --list-adapters
       Init 0 and 2  :  aticonfig --adapter=0,2 --initial
       Init all      :  aticonfig --adapter=all --initial
       MultiView     :  aticonfig --xinerama=on
  7. ATI Overdrive (TM).
       List adapters          :  aticonfig --list-adapters
       Get Clocks of 0        :  aticonfig --adapter=0 --od-getclocks
       Set new Clocks for 0   :  aticonfig --adapter=0 --od-setclocks=770,1126
       Test out 3D            :  atiode -P60 -H localhost:0; echo $?
       Check Temperature of 0 :  aticonfig --adapter=0 --od-gettemperature
       Commit changes for 0   :  aticonfig --adapter=0 --od-commitclocks

     ***note***
             atiode is a stress application you start with a required
             parameter -P which specifies the test duration and the optional
             -H parameter to target a specific display to use.  For example
             atiode -P 600 -H localhost:0 would test display 0 for 10 minutes
             the return code from the application is the test result
             0: Test successfully completed.
             1: Invalid command-line parameters.
             2: Test failed because of rendering errors.
             3: Target adapter not found.
             4: Test aborted due to unknown reason

Please report bugs to [http://support.ati.com](http://support.ati.com)
david@david-desktop:~$

---

### Post by zika on 2009-02-05
You've just got aticonfig help. type:```
aticonfig --initial
``` or, with "force" option:```
aticonfig --initial -f
```I'm fresh now, since I was trying some tweaking in Catalyst 9.2 beta (from CES 2009) ... and got myself a little scare because I was unable to get to X for about an hour .. ;) got myself and my computer back to 9.1 ... huh ... ;)
note:I would not recommend 9.2 beta since it's slower than 9.1 and incomplete.

---

### Post by garrydog on 2009-02-05
Hi Zika
This is the readout .


david@david-desktop:~$ aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
david@david-desktop:~$ aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
david@david-desktop:~$ 

Is this what you expected .

---

### Post by zika on 2009-02-05
You have to do it as a super-user, sorry:```
sudo aticonfig --initial
``` or```
sudo aticonfig --initial -f
```

---

### Post by garrydog on 2009-02-05
Thanks this is the readout .


david@david-desktop:~$ sudo aticonfig --initial
[sudo] password for david: 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
david@david-desktop:~$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
david@david-desktop:~$ sudo aticonfig --initial -f

---

### Post by zika on 2009-02-05
are we making any progress now ...?

---

### Post by garrydog on 2009-02-05
Don't know you tell me!myself I am lost .

---

### Post by garrydog on 2009-02-05
Just had a look at the catalist controle center in applications .

Got a pannel up saying ,

No Ati grafics driver is installed,or the driver is not functioning properly .

What's going on .

---

### Post by zika on 2009-02-05
if You are lost and sitting in front of a computer (I hope) how can I be less lost .. ;)
did You reboot? if You did not, reboot. where are You, in a 800x600? if You are, after aticonfig, reboot. I'll be here to wait to see what happens...

---

### Post by garrydog on 2009-02-05
no I did not reboot will do that now ,let you know .

---

### Post by garrydog on 2009-02-05
No same old loop ,rebooted black screen ,rebooted in recovery ,then xfix and boot to get back to the desktop .

---

### Post by garrydog on 2009-02-05
Sorry yes still in 800x600 .

---

### Post by zika on 2009-02-05
ok. it seems that something is messing up the whole process. before You start with the advice I wrote below let us reiterate and see the real situation. Can You boot in a working X? no matter what resolution. if You can disregard a rest of my post and we will try something different. If You do not have working X after boot, than ... You could try what I've come up with. I'm not an expert so You should take with grain of salt any advice of mine.
0. make a backup of Your xorg.conf, even though it doesn't work ...
1. make xorg.conf look like this:```
Section "Device"
    Identifier    "Configured Video Device"
        Driver          "ati"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
EndSection
```or, even,```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```You can do that with a command```
gksudo gedit /etc/X11/xorg.conf
```2. uninstall ATI driver ```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh
```3. clean up /etc/ati:```
cd /etc
sudo rm ati/*
```[COLOR=Red]be careful since **[COLOR=Black]rm[/COLOR]** is dangerous command[/COLOR]
4. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```5. check **again** if /etc/X11/xorg.conf looks like in 1.
6. go in Synaptic and clean any occurrence of fglrx in it ... be careful! 
7. reboot
8. do You have working X? no matter what resolution ...?

Explanation: purpose of this "remedy" is to clean all the remnants of any kind of fglrx driver and to get You back to radeon ... (second offered xorg.conf gets You to vesa).
Be careful because I could get You in a position You could not get out without a "proper" help ... ;)

---

### Post by zika on 2009-02-05
> **garrydog said:**
> Sorry yes still in 800x600 .
OK, You've answered while I was compiling the "remedy". I'm confused in what driver You have now running ...? what ```
fglrxinfo
``` gives?

---

### Post by garrydog on 2009-02-05
So I do't mess things up ,what do you mean by a working x .

---

### Post by zika on 2009-02-05
working X=are You in a graphical environment that's working. I assume You are in metacity (effects=None)

---

### Post by garrydog on 2009-02-05
In system  apperance visual effects, I am in none .But I can only boot in recovery mode .

---

### Post by zika on 2009-02-05
> **garrydog said:**
> In system  apperance visual effects, I am in none .But I can only boot in recovery mode .
proceed with my "remedy" but on Your own risk ... ;)
I'll be intermittently away from computer in the time ahead so You're mostly on Your own ... :)
once You get a hold of good X after boot (not in recovery) You could install ATI driver again.

---

### Post by garrydog on 2009-02-05
> **zika said:**
> OK, You've answered while I was compiling the "remedy". I'm confused in what driver You have now running ...? what ```
fglrxinfo
``` gives?
david@david-desktop:~$ sudo fglrxinfo
[sudo] password for david: 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
david@david-desktop:~$

---

### Post by garrydog on 2009-02-05
I will try my best thanks .

---

### Post by crho85 on 2009-02-05
Right click the package. Under properties (i believe the permissions tab). tell it to run as an executable. then go to applications---> accessories---> terminal

type: Sudo then drag the icon onto the terminal. Worked for me

but i ended up uninstalling as they did not work for my card

---

### Post by garrydog on 2009-02-05
Made the xorg.config look like no 1 .
whet to step no2 uninstall the ati driver , and got this readout is this OK .

david@david-desktop:~$ cd /usr/share/ati
david@david-desktop:/usr/share/ati$ sudo sh fgrx-uninstall.sh
sh: Can't open fgrx-uninstall.sh
david@david-desktop:/usr/share/ati$

---

### Post by zika on 2009-02-05
> **garrydog said:**
> david@david-desktop:~$ sudo fglrxinfo
[sudo] password for david: 
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
david@david-desktop:~$
it seems that Your driver is not installed properly. either it is incompatible with Your card or something went wrong in the process of installation. revert to radeon(hd) (as above) and then You might try again. sorry I did not help You much. at least I hope I did not mess up much ... ;)

---

### Post by garrydog on 2009-02-05
I have just rebooted ,now i can boot normaly but i am still in 800x600 .
The driver do's work I have had it working before on this system ,but I do not know how i made it work .

---

### Post by garrydog on 2009-02-05
OK Zika once again thanks for your help .

---

### Post by zika on 2009-02-05
> **garrydog said:**
> I have just rebooted ,now i can boot normaly but i am still in 800x600 .
The driver do's work I have had it working before on this system ,but I do not know how i made it work .
OK, now just to clear: what driver? ati-restricted (from their site), ati-open_source (radeon(hd)) or vesa ...?
once that is cleared we can scratch our (own) heads and make the resolution-switch possible ... ;)

---

### Post by garrydog on 2009-02-05
ATI Catalyst&#8482; 9.1 Proprietary Linux x86 Display Driver

    * Release Notes
    * Installer Instructions

Download Link 	File Size 	Version 	Date Posted 	Package Includes
ATI Driver Installer 	78.5MB 	9.1 	Jan. 29, 2009 	Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4

Notes:
The above drivers support English only.
The display driver requires POSIX shared memory to be enabled on the system.
Kernel Source package is no longer required if Kerne

This is copied from the ati web site ,and the one that I downloaded .

---

### Post by zika on 2009-02-05
yes, that's the driver I have also. did You follow the site to get right one for Your card? if so, did You enter Catalyst and tried to change resolution there?
Applications->ATI Catalyst Control Center->Display Manager->Desktop area...

---

### Post by garrydog on 2009-02-05
If I do that applications,catalist control center,I get a pannel telling me that no ati driver is installed ,or the ati driver isnt functioning properly .
Yes i did get the correct driver for my card .

---

### Post by zika on 2009-02-06
> **garrydog said:**
> If I do that applications,catalist control center,I get a pannel telling me that no ati driver is installed ,or the ati driver isnt functioning properly .
Yes i did get the correct driver for my card .
that's the reason I've put in my "remedy" removing the driver, removing /etc/ati, removing fglrx from Synaptic. something is intertwined in Your installation ... I remember that You've mentioned the same thing at the very beginning. that is why I've insisted on removing everything thoroughly... so, please read my previous posts ... (step-by-step) they seem to be too comprehensive but the reality proves me right ... ;)

---

### Post by garrydog on 2009-02-06
Hi Zika
I have made the No1 section xorg.config look like the top panel,the ati driver and saved .
No 2 uninstall ati driver,the readout is.
david@david-desktop:~$ cd /usr/share/ati
david@david-desktop:/usr/share/ati$ sudo sh fgrx-uninstall.sh
[sudo] password for david: 
sh: Can't open fgrx-uninstall.sh
david@david-desktop:/usr/share/ati$ 

shall I go to No3 is this OK .

---

### Post by garrydog on 2009-02-06
acording to synaptic none of the fglrx are installed .

---

### Post by garrydog on 2009-02-06
This is the output from No3 .

david@david-desktop:~$ cd /etc
david@david-desktop:/etc$ sudo rm ati/*
[sudo] password for david: 
rm: cannot remove `ati/*': No such file or directory
david@david-desktop:/etc$

---

### Post by zika on 2009-02-06
> **garrydog said:**
> Hi Zika
I have made the No1 section xorg.config look like the top panel,the ati driver and saved .
No 2 uninstall ati driver,the readout is.
david@david-desktop:~$ cd /usr/share/ati
david@david-desktop:/usr/share/ati$ sudo sh fgrx-uninstall.sh
[sudo] password for david: 
sh: Can't open fgrx-uninstall.sh
david@david-desktop:/usr/share/ati$ 
shall I go to No3 is this OK .
sorry, the right name is **fglrx-uninstall.sh **if I did not misspell it again. once that is done, You can go to No.3.

---

### Post by garrydog on 2009-02-06
Readout No4.

david@david-desktop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090206155853
david@david-desktop:~$

---

### Post by zika on 2009-02-06
you have to go back to No.2 and finish it then to No. 3 and then to No.4 (they depend one on another...)

---

### Post by garrydog on 2009-02-06
Re readout No2.

david@david-desktop:~$ cd /usr/share/ati
david@david-desktop:/usr/share/ati$ sudo sh fglrx-uninstall.sh

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run fglrx-uninstall.sh (this is not recommended).

david@david-desktop:/usr/share/ati$

Yes I will start again .please comment on No2 first .

---

### Post by zika on 2009-02-06
[COLOR=Red]**be careful! I make no promises ... ;)**[/COLOR]
that is what I was talking about. try putting these files in that place
```
cd /etc
sudo mkdir ati
cd ati
gksudo gedit inst_path_default
``````
# /etc/ati/inst_path_default
#
# Created Thu Feb  5 15:19:20 CET 2009 with the following configuration:
#
# Driver version: 8.573
# Default policy
# Policy version: default:v2:x86_64:lib32:x740_64a:none:2.6.27-11-generic

# X_VERSION and _ARCH set by check.sh
       X_VERSION=x740_64a
           _ARCH=x86_64

     ATI_XLIB_32=/usr/lib32
     ATI_XLIB_64=/usr/lib64
     ATI_XLIB_EXT_32=/usr/lib32/xorg/modules/extensions
     ATI_XLIB_EXT_64=/usr/lib64/xorg/modules/extensions
   ATI_3D_DRV_32=/usr/lib32/dri
   ATI_3D_DRV_64=/usr/lib64/dri
        ATI_XLIB=/usr/lib64
       ATI_X_BIN=/usr/bin
        ATI_SBIN=/usr/sbin
    ATI_KERN_MOD=/lib/modules/fglrx
      ATI_2D_DRV=/usr/lib64/xorg/modules/drivers
    ATI_X_MODULE=/usr/lib64/xorg/modules
     ATI_DRM_LIB=/usr/lib64/xorg/modules/linux
 ATI_CP_KDE3_LNK=/opt/kde3/share/applnk
  ATI_GL_INCLUDE=/usr/include/GL
  ATI_CP_KDE_LNK=/usr/share/applnk
         ATI_DOC=/usr/share/doc/ati
ATI_CP_GNOME_LNK=/usr/share/gnome/apps
        ATI_ICON=/usr/share/icons
         ATI_MAN=/usr/share/man
         ATI_SRC=/usr/src/ati
 ATI_X11_INCLUDE=/usr/include/X11/extensions
      ATI_CP_BIN=/usr/bin
     ATI_CP_I18N=/usr/share/ati/amdcccle
         ATI_LOG=/usr/share/ati
      ATI_CONFIG=/etc/ati
      ATI_UNINST=/usr/share/ati
``````
gksudo gedit inst_path_override
``````
# /etc/ati/inst_path_override
#
# Created Thu Feb  5 15:19:20 CET 2009 with the following configuration:
#
# Driver version: 8.573
# No override policy used because no distributions matched the current distro
```[COLOR=Blue]if You are afraid to do the above I think it is the right moment to reboot and see if open-source driver is working. if it is, new installation of restricted driver could be OK. now, before doing the above You already cleaned all the active parts of driver and new install would just copy the files and make clean start. (configuration files for restricted driver are gone with the /etc/ati directory) Your choice ... ;)[/COLOR]

---

### Post by garrydog on 2009-02-06
sorry I don't want to mess it up ,do I put these coads in to the terminal one by one,each one in a new terminal.

---

### Post by zika on 2009-02-06
read the [COLOR=Blue]blue[COLOR=Black] text in my previous post [/COLOR][/COLOR]
4 windows are in my post:
1. go to /etc and re-make directory ati in it and open the editor for a first file missing.
2. contents of the first file that should be copy-paste-ed to gedit window that is now open. after paste is finished, close that window with save ...
3. command for a new gedit window for a second file that is missing
4. contents of the second file that should be copy-paste-ed to gedit window that is now open.  after paste is finished, close that window with save ...

---

### Post by garrydog on 2009-02-06
Zika I am not afraid of doing the above,I can allways reinstall .just wanted to know how to do it correctly .

---

### Post by zika on 2009-02-06
OK. that takes a lot off my chest ... ;)

---

### Post by garrydog on 2009-02-06
I am now in the panel inst_path_default(etc/ati-gedit,and have put the first lot of text in ,do I just press the save button at the top .

---

### Post by zika on 2009-02-06
yes

---

### Post by garrydog on 2009-02-06
OK i will move on.

---

### Post by garrydog on 2009-02-06
done all that ,what now .

---

### Post by zika on 2009-02-06
go back to No2, No3, No4, ... :) hopefully No2 will work now ... it starts to look like board-game ... :lol:

---

### Post by garrydog on 2009-02-06
Please forgive my ignorance ,but No1,No2,No3 on what page ,don't want to uninstall it again .

---

### Post by zika on 2009-02-06
do all on the last post and 2,3,4 on "big" previus post where was the typo in fg(l)rx ... ;)

---

### Post by garrydog on 2009-02-06
readout No2.

david@david-desktop:~$ cd /usr/share/ati
david@david-desktop:/usr/share/ati$ sudo sh fglrx-uninstall.sh

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run fglrx-uninstall.sh (this is not recommended).

david@david-desktop:/usr/share/ati$

---

### Post by zika on 2009-02-06
read blue print and use it. :) as I said I made no promises but tried a shot in the dark. even if You've edited those files OK, that was not something I tried before ... ;)

---

### Post by Bablefish on 2009-02-06
I have had some bad experiances with the ATI driver, which in short crashed my OS. Please take that as a warning...

---

### Post by garrydog on 2009-02-06
I have rebooted ,still the same,and downloaded the ATI/AMD proprietery FGLRX driver rebooted .Got the same black sreen,I have even tryed a different monitor just the same .

Well Zika I think that I have taken up to much of you time now,thanks for all your help
I will have to find the artical that sorted it last time ,if I can .

Thanks again David.

---

### Post by zika on 2009-02-06
do You get black screen with "ati" open-source driver?

---

### Post by garrydog on 2009-02-06
Yes I allways have done,it has never worked .

---

### Post by garrydog on 2009-02-06
Zika do you think that I sould change my video card to another type ,if so what would be the one to get for my system.

---

### Post by zika on 2009-02-06
I'm not up-to-date with graphic HW. sorry. I was a long time ago at one point but now I am not in  a position to give advice that I could stand behind ... even on any of my machines these days I did not choose my HW,  I chose the one that was of the right price, I plunged into Ubuntu and ... in my little LAN (4 machines) I have nvidiax2, atix3, intel, (counting both the cards and on-the-board hw) ... perpetual struggle ... ;) on to-do list for next days is in-house file-sharing ... ;)

---

### Post by zika on 2009-02-07
> **garrydog said:**
> Yes I allways have done,it has never worked .
that is probably because the kernel part after installing fglrx driver was not removed. that is why fglrx-uninstall.sh has to be run properly. so, the remedy might be to install driver again and uninstall it properly, then change xorg.conf to call ati and to make that as a good starting point. we've messed just that one step (3 before 2 was finished properly ... ;))

---

### Post by garrydog on 2009-02-07
When I had the driver running before on my system ,on a normal boot the screen would go black with the "cannot disply this video mode" but it was only on the screen for a fraction of a second,then the black screen would disapear ,then the screen would normal with good resolution.

Myself I think that the drivers ,the one downloaded from ATI and the prprietary one ,are installing OK but there is no way of changing the screen resolution because of the black sreen.When I boot the machine in recovery mode are any of the ATI drivers installed? can they be adjusted in recovery mode . I am only a beginer at with this but is there any way that this can be done ,just for a try .
I have an NV25 geforce4 ti 4200 video card ,do yo think that this may be better to work with,if it will fitt in my computer .

---

### Post by garrydog on 2009-02-17
Hi
Iam still trying to sort out my screen resolution,trying to get a better screen resolution than 800x600 .I have loaded the ati driver following the following .                                            [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installation_Guide_for_Ubuntu_Intrepid_.28v_8.10.29](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installation_Guide_for_Ubuntu_Intrepid_.28v_8.10.29) .            
After the bootup I get the following errors,
Ubuntu is running in low graphics mode
(EE)problem parsing the config file
(EE)error parsing the config file.
Below is my config file ,

Section "Device" 
        Identifier       "Configured Video Device" 
	Driver		"fglrx"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
               Deafault Depth 24
EndSection
Can someone please tell me if this is OK ,if it is not will you tell me what it should be .
Thanks.

---

### Post by ibuclaw on 2009-02-17
> **garrydog said:**
> Hi

Below is my config file ,

Section "Device" 
        Identifier       "Configured Video Device" 
	Driver		"fglrx"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
**               Deafault Depth 24**
EndSection
Can someone please tell me if this is OK ,if it is not will you tell me what it should be .
Thanks.

The line in bold is wrong. It should be this
```
        DefaultDepth    24
```

Regards
Iain

---

### Post by zika on 2009-02-17
if what is in Your post is just cut and paste from Your actual xorg.conf than some typos might be the culprit. 
but, better than spell-checking Your xorg.conf I'm giving You the xorg.conf that might work. it is stripped from any advanced options and fancy stuff. I do not have high hope it will but ... it might be a good recipe for You to make Your own. please, backup Your xorg.conf before You start making any changes and be sure You are able to recover it safely.  

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "DRI"
    Mode         0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection
```

good luck!

---

### Post by onecosmos on 2009-05-15
Hi people

I have installed the 9.04 32 bit version. I have an ATI HD 4550 card, managed to install the drivers provided by ATI for my card, compiled for ubuntu 9.04. However i think i have problem running compiz, to check i downloaded a script called compiz-check and runned it, the output is

doft@cosmos:~/wireless/script$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV710 [Radeon HD 4550]
 Driver in use:         fglrx
 [B]Rendering method:      None
[/B]
Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 



I have executed the aticonfig -initial -f command to update the conf files. The contents of my xorg.conf file are

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

The output of lshw -C video is

doft@cosmos:~/wireless/script$ lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RV710 [Radeon HD 4550]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx


I am relatively new to linux and not sure how to start compiz and check if the graphics drivers are properly functioning, i have to say that in the desktop environment i run the effects on extra with no problem, if any one can suggest why i get rendering mode none i would be very thankful.

---

### Post by drdoormouse on 2009-05-28
[SIZE=3]help required got ubuntu 9.04  having ati radeon card x300 machine dell GX 280 tried to install the driver as directed by ati I got the unzipping portion fine but in the end it says sh policy does not support the verion [/SIZE]
root@eshaal:/home/ahmed/Ati#[SIZE=3] sh ./ati-driver-installer-9-3-x86.x86_64.run[/SIZE]
Created directory fglrx-install.SmwLPK
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.SmwLPK

[SIZE=3]please provide help[/SIZE]

---

### Post by zika on 2009-05-28
> **drdoormouse said:**
> [SIZE=3]help required got ubuntu 9.04  having ati radeon card x300 machine dell GX 280 tried to install the driver as directed by ati I got the unzipping portion fine but in the end it says sh policy does not support the verion [/SIZE]
root@eshaal:/home/ahmed/Ati#[SIZE=3] sh ./ati-driver-installer-9-3-x86.x86_64.run[/SIZE]
Created directory fglrx-install.SmwLPK
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.SmwLPK

[SIZE=3]please provide help[/SIZE]
I think You need at least version 9.4 and the latest is 9.5 of ATI driver ... [SIZE=3][SIZE=1]ati-driver-installer-9-[SIZE=2]{4,5}[/SIZE]-x86.x86_64.run ...[/SIZE][/SIZE]

---

### Post by markbuntu on 2009-05-28
x300 card is no longer supported by ati proprietary drivers from 9.4 on and drivers 9.3 and before will not work with the xserver1.0.16 in Jaunty9.04 so don't bother.

All ati gpus before RV600 series (HD3xxx) will no longer be supported by ati proprietary drivers for all operating systems released after February09. This includes both linux and windows.

---

### Post by zika on 2009-05-29
> **markbuntu said:**
> x300 card is no longer supported by ati proprietary drivers from 9.4 on and drivers 9.3 and before will not work with the xserver1.0.16 in Jaunty9.04 so don't bother.

All ati gpus before RV600 series (HD3xxx) will no longer be supported by ati proprietary drivers for all operating systems released after February09. This includes both linux and windows.
Radeon HD 3650 is RV635 and I think it is still supported.
My mistake is that I have not seen that it is X300 we were talking about. Sorry.
update: I've did it again: You sad **before** ... :(

---

### Post by marcin111 on 2009-06-12
onecosmos - what is the output of glxinfo command? Do you get direct rendering "Yes"?

---

### Post by RGPerson on 2009-07-09
> **onecosmos said:**
> Hi people

I have installed the 9.04 32 bit version. I have an ATI HD 4550 card, managed to install the drivers provided by ATI for my card, compiled for ubuntu 9.04. However i think i have problem running compiz, to check i downloaded a script called compiz-check and runned it, the output is....


Aha! This the exact card we have.  I had it working fine under 8.04.  I upgraded that to 8.10 and it wasn't perfect.  Under my normal boot, I had a beautiful background with a cursor.  No menus, no icons, nothing to click.  I was able to boot into a Mythbuntu session and see things.  From there I upgraded to 9.04.  I got a black screen with a white cursor and nothing to click or do. Let's just say it was a disaster from the start and a total utter disaster now.  I'm back to 8.04 upgrading to 8.10. 

I think I'm going to stay there for a bit before I try again, but I would like to get 9.04. I've heard it works great with our Hauppauge card and we really want that to work, too.

While in 9.04, I did try reinstalling the ATI driver and it seemed to go okay until I rebooted. Then, I didn't even have the black screen. I had a completely distorted screen where I could do nothing again.  I couldn't even make out a cursor.  I couldn't even see the login box, where at least I did when I eventually got a black screen.

It's been a very troubling day.  So if someone can tell me how to get 9.04 (and 8.10 while we're at it) working with our ATI Radeon 4550, I'd love the help.

Update: can't get the driver to work with 8.10 because we're stuck in some nether region of my hard drive where the File System thinks it exists.  My "home" is not my "home".  My "home is really on that other spot called "2.25GB".  The "file system" I now boot to doesn't have enough space to expand the ati driver in order to install it.  How fun is that?

So we have a new plan: I have an extra 160GB HD.  It should be returning to me tomorrow (was recovery media for a crashed hard drive I was trying to get recovered).  Once we have it, I'm going to hook it up to the Linux computer and copy my real home directory to it.  Then I'm going to start completely over.  We'll install, in separate partitions, 8.04, 8.10 and 9.04 so we can experiment but still have a backup OS that works so we can watch our shows.

Gabrielle

---

### Post by markbuntu on 2009-07-09
I found that you can have problems with the hidden config files in the /home/user directory when running more than one distro with the same /home directory.  If you are going to be running 8.04 and 8.10 and 9.04 then you will have some different versions of applications and they will try to use the same hidden config files or overwrite them with newer versions that may not work correctly with all versions of the applications.

What I do instead is have a separate partition/directory called /personal where I keep all my personal stuff and mount that in my /home directories.

Another thing you should do is put all grubs in the partitions with the distros and chainload them from the grub on the MBR. The first distro you install should put grub on the MBR. The others in their partitions. Chainloading is very easy. There are a bunch of threads about that around here.

That way you will not have problems with kernel updates.

Other than that, your plan is a good one.

---

### Post by p0cky84 on 2009-07-09
@garrydog, you don't know how to open the terminal or type in your sudo passwd...

Wouldn't it just be easier getting the driver from the repos?

Or from envy?
```
sudo apt-get install envyng-qt envyng-core
```
*your password* (even tho it doesn't appear there)
Voila!~

---

### Post by markbuntu on 2009-07-10
DO NOT USE ENVY to install ati drivers!!!
Envy misinstalls the driver as often as it is successful, does not provide up to date drivers, often does not install the kernel modules properly and will try to install the wrong driver for many cards.

---

### Post by CaptainMark on 2009-07-10
I might be missing something but arent you going the long way round, you said how do you automatically install the driver. Just go to system>admin>hardware drivers,  click enable ati driver. I may have missed something but this is definatley the easiest way, although not always possible.

---

### Post by markbuntu on 2009-07-11
Hardware Drivers does not supply the latest driver and does not support many of the latest cards.

---

### Post by RGPerson on 2009-07-12
> **markbuntu said:**
> I found that you can have problems with the hidden config files in the /home/user directory when running more than one distro with the same /home directory.  If you are going to be running 8.04 and 8.10 and 9.04 then you will have some different versions of applications and they will try to use the same hidden config files or overwrite them with newer versions that may not work correctly with all versions of the applications.

What I do instead is have a separate partition/directory called /personal where I keep all my personal stuff and mount that in my /home directories.

Another thing you should do is put all grubs in the partitions with the distros and chainload them from the grub on the MBR. The first distro you install should put grub on the MBR. The others in their partitions. Chainloading is very easy. There are a bunch of threads about that around here.

That way you will not have problems with kernel updates.

Other than that, your plan is a good one.

Thanks.  I think I'd like to make a personal partition like that. Anyway I can do that from inside 8.10 or 9.04? Those are the only 2 I've installed thus far. They are on separate 70GB partitions and they show up in the GRUB fine for my choosing.

BTW: the video drivers worked fine in both new installs.

Gabrielle

---

