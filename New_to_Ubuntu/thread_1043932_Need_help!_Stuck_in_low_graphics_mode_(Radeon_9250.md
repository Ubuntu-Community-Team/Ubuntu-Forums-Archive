---
title: "Need help! Stuck in low graphics mode (Radeon 9250)"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Famicommander on 2009-01-19
I got a new video card today, and I also got a new copy of XP. So I figured it would be simpler to do a fresh install of Ubuntu, since I didn't have anything worth backing up in the first place.

I installed XP without a hitch, then installed Intrepid Ibex via Wubi. Everything went great, and it looked fine. I updated everything, installed my multimedia, and then rebooted. When it did, it came up in low graphics mode. Before the reboot, I was running 1280x1024@75hz. It was all good. Now it's all ugly.

I looked in the restricted drivers manager, and there is nothing to install. I looked in the ATI Catalyst Control Center, and it says that there is no ATI Driver installed, or that it is not functioning properly. It told me to type aticonfig, and I did. Here is the output of that command:
```
jason@ubuntu:~$ aticonfig
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
        hardware overlay can be used for either OpenGL, video or pseudo-color
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

Please report bugs to http://support.ati.com
jason@ubuntu:~$ 

```

I have no idea what any of that means, or where to go from here. And help would be great.

---

### Post by eatberrys on 2009-01-19
Have u tryed insatlling the driver from the ATI site ?
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

### Post by Famicommander on 2009-01-19
> **eatberrys said:**
> Have u tryed insatlling the driver from the ATI site ?
[http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

How do I install that?

---

### Post by Famicommander on 2009-01-19
Tried this:
```
jason@ubuntu:~$ aticonfig --initial
Segmentation fault
jason@ubuntu:~$ 

```

What does that mean?

---

### Post by Famicommander on 2009-01-19
Those ATI Drivers you linked me to say they were posted in 2006. Is that really going to be relevant to Intrepid Ibex?

---

### Post by DOS4dinner on 2009-01-19
Check/post your xorg.conf and xorg.0.log.

I'm assuming 8.10 still has those.

---

### Post by Famicommander on 2009-01-19
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

That's what I've got. Maybe I should just cut my losses and revert back to vesa? I don't know.

---

### Post by DOS4dinner on 2009-01-19
> **Famicommander said:**
> ```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver 		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

That's what I've got. Maybe I should just cut my losses and revert back to vesa? I don't know.

You shouldn't have to go that far back. You should be able to use the open source driver if nothing else (and on that card, it will probably work fine)

You can find a guide [here.]("https://help.ubuntu.com/community/RadeonDriver")

I think it still works in 8.10 (It worked for me, anyway)

---

### Post by LeeHB on 2009-01-19
I had the same problem last week with a non-wubi install...I had to redo the install completely, chosing F4 and 'Safe Graphics Mode'; I don't remember if Wubi has the same video option...but when the system came up, I did have alternate screen resolution choices....check Wubi for an option similar to this...might help.

LeeHB

---

### Post by Maheriano on 2009-01-19
I have the same video card with the same problem. I did some research on the ATI website and read the FAQ, somewhere in there I saw that the 9250 isn't supported by their Linux drivers so it just won't work. I ended up buying a nVidia and not looking back.

---

