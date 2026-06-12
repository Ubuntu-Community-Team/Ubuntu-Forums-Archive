---
title: "turnnig on the computer"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by duthieamber on 2009-12-18
I am currently using Ubuntu 9.10. When i turn on my computer instead of going into my login screen im getting this message: There already appears to be an X server running on display :0. Should another display number be tried? Answering no will cause GDM to attempt starting the server on :0 again. (you can change consoles by pressing Ctrl-Alt plus a function key, such as ctrl-alt-F7 to go to consoles 7. X servers usually run on consoles 7 and higher.) and then it has yes or no .
If I hit yes i get another message saying: The specified display number was busy so this server was started on display :1 and then i hit ok and my login screen comes up, but there have been times when i hit ok i will get another message telling me that it is crashing and to hit ok to try another server. And that message will keep coming up no matter how many times i hit ok.

I am having to go through this every time i turn my computer on and will have to just keep holding down the power key to turn it off and turn it back on hoping it will go to my login screen. This can get old very quickly so i am just leaving my laptop open at all times so i dont have to go through this. If anybody knows what i can do to fix this problem please let me know as soon as you can. I have a 2 yr. old and leaving my laptop open is just screaming at her " PLEASE COME PLAY WITH ME" which i do not allow. PLEASE HELP !!   thanks in advance!
                                                                          Amber

---

### Post by northern lights on 2009-12-18
When asked whether another display number should be tried, select neither Yes or No. Hit "Ctrl+Alt+F2".

Run```
sudo /etc/init.d/gdm stop
```

Login via the CLI and run```
startx
```

In the panel, navigate to  *System > Administration > Services* and untick '*Graphical Login manager (gdm)*'

On the next boot, login from the CLI and again run```
startx
```

---

### Post by duthieamber on 2009-12-18
will i have to do that every time i turn on my lap top or will this stop the problem for good?

---

### Post by northern lights on 2009-12-18
Well what ought to be done after is check your gdm configuration. Can you please post the output of```
cat /etc/gdm/gdm.conf
```Thank you.

---

### Post by duthieamber on 2009-12-18
sure thing i have to feed my baby and i will do it. I will just message you afterwards is that ok?

---

### Post by xifer on 2009-12-18
a look at the end of the file /var/log/Xorg.0.log might give a clue.


or check contents of /etc/X11/xorg.conf

---

### Post by audiomick on 2009-12-18
> **xifer said:**
> 
or check contents of /etc/X11/xorg.conf

May not be there in 9.10. Don't panic if it isn't, it is normal. just means your computer is happy with default settings.

---

### Post by duthieamber on 2009-12-18
Can anybody please tell me what " login via the CLI and run startx" means??
Also when i go to Sytem-Administration-services there is no services to click on.

And sometimes im also getting the error saying that the greeter application is crashing and that it is attempting to use another one.

I am very new to ubuntu and need step by step directions to solve this problem.

I went to ctrl-alt-F2 and typed sudo /etc/init.d/gdm stop 
it said Gdm was stopped im not sure what to do after doing this.

---

### Post by audiomick on 2009-12-18
> **duthieamber said:**
> Can anybody please tell me what " login via the CLI and run startx" means??


go to appplications> accessories>terminal
an almost empty white window will open. That is your CLI, which means Command Line Interface. If you ever used DOS, or text commands in windows, it is a little like that. (but only a little...)

in the window, type
```
startx
```
that is a command that starts the x sever, which is what is behind your graphical user interface.

Can't help with the rest, sorry..:(

---

### Post by northern lights on 2009-12-18
Mkey.

We might not even have to work from Console 2.

Let's a) follow the error message and try to switch to Console 7 (Ubuntu should by default boot into that) by hitting '*Ctrl+Alt+F7*' after the error message occurs. Apparently it's booting into another Console.

The X Windows System provides you with a graphical interface and interprets keyboard and mouse input. It appears as if on another Console (likely 7) X is started already. And now the attempt to start it on another Console directing output to the same monitor is causing a conflict.

I have no idea how the default Console could have gotten altered without you doing so, but it happened, apparently.

What does trying to switch to Console 7 result in?

Please also post the output of ```
cat /etc/gdm/gdm.conf
```

---

### Post by xifer on 2009-12-18
> **duthieamber said:**
> Can anybody please tell me what " login via the CLI and run startx" means??
Also when i go to Sytem-Administration-services there is no services to click on.

And sometimes im also getting the error saying that the greeter application is crashing and that it is attempting to use another one.

I am very new to ubuntu and need step by step directions to solve this problem.

I went to ctrl-alt-F2 and typed sudo /etc/init.d/gdm stop 
it said Gdm was stopped im not sure what to do after doing this.

Well I didn't know there might not be an xorg.conf - you live and learn.

Anyway, running CLI (command line interpreter ) just means in a terminal window.  Or at the console - CTRL-ALT-F1
login as root (or if you don't have that set login as administrator or whatever you normally use) and type the command startx. or maybe sudo startx


but I'm thinking you need to look at the log file mentioned earlier.

I can sympathise with you - running ubuntu for the first time on odd monitors and swapping graphics cards I've been there a painful number of times!  Even though have been a unix admin for yearS!

---

### Post by duthieamber on 2009-12-18
Do you want me to just run that code in a terminal???

---

### Post by northern lights on 2009-12-18
> **duthieamber said:**
> Do you want me to just run that code in a terminal???
The *cat /etc/gdm/gdm.conf*'? Yes. And thereupon copy/paste the output here.

What did rebooting and trying to switch to Console 7 result in?

---

### Post by xifer on 2009-12-18
yes - the suggestion is you let us know the contents the gnome configuration file which is /etc/gdm/gdm.conf
(which by the way curiously doesn't exist on my system whereas xorg.conf does.  I do have /etc/gdm/custom.conf)

cat means concatenate the file contents to the screen output - so it gets written in our terminal window.  Than you copy that text in this thread so we can see the problem.

hope I'm not being too simplistic?


Do the same with the log file - have a look for lines with an E (for error) at the beginning rather than an I (for information) or W (for warning)  and let us know if anything is there.

---

### Post by duthieamber on 2009-12-18
when i type that code in i get :
# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10
and a bunch of stuff do you want that as well?

---

### Post by northern lights on 2009-12-18
> **duthieamber said:**
> ...
and a bunch of stuff do you want that as well?
Yup.

You are aware that you can copy/paste from the terminal, hopefully?! As in, don't retype that info.

Further, for the sake of readability, please enclose the output in code tags (pound/hash/# button).

---

### Post by duthieamber on 2009-12-18
```
# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10

[security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
# Allow login as root via XDMCP.  This value will be overridden and set to
# false if the /etc/default/login file exists and contains
# "CONSOLE=/dev/login", and set to true if the /etc/default/login file exists
# and contains any other value or no value for CONSOLE.
AllowRemoteRoot=false
# This will allow remote timed login.
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions.
RelaxPermissions=1
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# If your HOME is managed by automounter, set to true
SupportAutomount=false
# Number of seconds to wait after a failed login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly attached sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS by
# detecting "root-squashing".  It seems bad practice to place cookies on things
# that go over the network by default and thus we do not do it by default.
# Sometimes you can however use safe remote filesystems where this is OK and
# you may want to have the cookie in your home directory.
#NeverPlaceCookiesOnNFS=true
# Will cause PAM_DISALLOW_NULL_AUTHTOK to be passed as a flag to
# pam_authenticate and pam_acct_mgmt, disallowing NULL password.  This setting
# will only take effect if PAM is being used by GDM.  This value will be
# overridden with the value from /etc/default/login if it contains
# "PASSREQ=[YES|NO]"
#PasswordRequired=false
# Specifies the PAM Stack to use, "gdm" by default.
PamStack=gdm
# GDM allows configuration of how ut_line is set when it does utmp/wtmp and
# audit processing.  If VT is being used, then ut_line will be set to the
# device associated with the VT.  If the console is attached and has a device
# name specified in the [servers] section, then this value will be used.
# Otherwise the value is defaulted to the value specified in UtmpLineAttached
# for attached displays and UtmpLineRemote for remote displays.  The value
# can be left empty which means that ut_line will be set to an empty value
# (if not VT and no value specified in the [servers] section.  The values
# can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.  The values for both keys  must begin with
# "/dev/".
UtmpLineAttached=/dev/console
UtmpLineRemote=
# If true and the specified UtmpLineAttached or UtmpLineRemote does not exist,
# then create a pseudo-device filename that will be touched when the utmp
# record is updated.  Creating such a psuedo-device ensures that programs
# that stat the utmp device associated with ut_line such as finger, last,
# etc. work in a reasonable way.  
UtmpPseudoDevice=false

# XDMCP is the protocol that allows remote login.  If you want to log into GDM
# remotely (I'd never turn this on on open network, use ssh for such remote
# usage).  You can then run X with -query <thishost> to log in, or
# -indirect <thishost> to run a chooser.  Look for the 'Terminal' server type
# at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
#AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
#GtkThemesToAllow=all

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=true
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=nobody
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
Logo=/usr/share/pixmaps/gdmDebianLogo.xpm
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#000000
GraphicalThemedColor=#000000
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=bijou/:blueswirl/:circles/:debblue-list/:debblue/:ayo/:debian-dawn/:debian-greeter/:debian/:glassfoot/:hantzley/:happygnome/:industrial/:crystal/:linsta
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
#SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
PreFetchProgram=/usr/lib/gdm/gdmprefetch @/etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

# Attached DISPLAY Configuration
#
[servers]
# This section defines which attached DISPLAYS should be started by GDM by
# default.  You can add as many DISPLAYS as desired and they will always be
# started.  The key for each entry must be a unique number that cooresponds to
# the DISPLAY number to start the X server.  For a typical single-display
# machine, there will only be one entry "0" for DISPLAY ":0".  The first word
# in the value corresponds to an X server definition in the "X Server
# Definitions" section of the configuration file.  For example, the entry:
#
# 0=Standard
#
# Means that DISPLAY ":0" will start an X server as defined in the 
# [server-Standard] section.
#
# The optional device argument is used to specify the device that is associated
# with the DISPLAY.  When using Virtual Terminals (VT), this value is ignored
# and GDM will use the correct device name associated with the VT.  If not
# using VT, then GDM will use the value specified by this optional argument.
# If the device argument is not defined, then GDM will use the default setting
# for attached displays defined in the UtmpLineAttached configuration option.
# For the main display (typically DISPLAY ":0"), "/dev/console" is a reasonable
# value.  For other displays it is probably best to not include this argument
# unless you know the specific device associated with the DISPLAY.  The device
# value can contain "%d" which is translated to the DISPLAY value or %h which
# is translated to the hostname.
#
0=Standard device=/dev/console

# Example of how to set up DISPLAY :1 to also use Standard.
#1=Standard

# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

# X Server Definitions
#
# Note: Is your X server not listening to TCP requests?  Refer to the 
# security/DisallowTCP setting!

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/X11R6/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Do not handle this X server for attached displays.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/X11R6/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

[customcommand]
# This section allows you specify up to 10 custom commands. Each of the
# commands can be defined by the seven parameters listed below. In each of the
# descriptions of the parameters N can take on any values between 0 and 9,
# i.e. CustomCommand0=,CustomCommand1=,...,CustomCommand9=.  The  numbers
# can have gaps as long as they fit within predefined set of 10, and their
# placement order within this section and with respect to each other is
# not important.
#
# CustomCommandN, CustomCommandTextN, CustomCommandLabelN, 
# CustomCommandLRLabelN, CustomCommandTooltipN, CustomCommandIsPersistentN
# and CustomCommandNoRestartN should all be defined for a given integer N, 
# where N can be a number from 0-9 (if not the default values will be 
# assigned except CustomCommandN for which no default exists).

# Custom command to run.  Multiple commands may be specified separated by 
# semicolons.  GDM will use the first valid command.  Examples:
# /sbin/bootwindoze;/usr/bin/bootwindoze, or
# /sbin/runupdate;/usr/local/sbin/runupdate
#
#CustomCommandN=

# Custom command dialog message that will appear on all warning dialogs.
# This will vary depending on what you want to do. Examples:
# Are you sure you want to restart system into Windoze?, or
# Are you sure you want do do this?
#CustomCommandTextN=

# Custom command label that will appear as stock label on buttons/menu items.
# This option can't contain any semicolon characters (i.e. ";").
# Examples:
# _Windoze, or
# _Update Me
#CustomCommandLabelN=

# Custom command label that will appear as stock label on radio buttons/list
# items.  The underscore indicates the mnemonic used with this item.  Examples:
#   Restart into _Windoze
#   Perform system _Update
#CustomCommandLRLabelN=

# Custom command tooltip. Examples
# Restarts the computer into Windoze
# Updates the computer software to the most recent version(s)
#CustomCommandTooltipN=

# Custom command persistence option. Setting it to true will allow this
# command to appear outside the login manager, e.g. on the desktop through 
# Log Out/Shut Down dialogs. The default value is false.
#CustomCommandIsPersistentN=

# Custom command gdm/system restart option. Setting it to true will not
# restart gdm after command execution.  The default commands (reboot, shut
# down) all reboot the system by default which is why the default setting
# is true.
# In addition when corresponding CustomCommandIsPersistentN option is set to
# true, setting CustomCommandNoRestartN to false will place CustomCommandN
# in the Shut Down dialog set of actions, setting it to true will place
# CustomCommandN in the Log Out dialog set of actions.
#CustomCommandNoRestartN=
#
# Example layout for more than one command:
#CustomCommand0=
#CustomCommandText0=
#CustomCommandLabel0=
#CustomCommandLRLabel0=
#CustomCommandTooltip0=
#CustomCommandIsPersistent0=
#CustomCommandNoRestart0=
#
#CustomCommand1=
#CustomCommandText1=
#CustomCommandLabel1=
#CustomCommandLRLabel1=
#CustomCommandTooltip1=
#CustomCommandIsPersistent1=
#CustomCommandNoRestart1=
#
# and so on
amber@amber-laptop:~$
```

---

### Post by duthieamber on 2009-12-19
I have replied back as asked and posted everything i got. I have yet to hear anything else about it so maybe y'all just forgot about me I dont know, but the past couple of time i have turned on my computer i haven't gotten the error message any more. So im not sure if maybe the problem worked it self out or what .

If anybody could please give me an answer on how to solve this issue and let me know i would greatly appreciate it so when i do get that error i will know what to do!! 

                               Thanks to everyone who helped,
                                                         Amber

---

### Post by mechaxl on 2009-12-21
So I've got the same problem, and I've got a workaround for it, but not a solution.

What you're going to want to do is when you're at that screen, hit ctrl-alt-f7. This will bring you to what's hogging up display :0. It will probably be a notice saying that Ubuntu is running in low graphics mode. Just hit cancel (I think, try hitting the other one if that doesn't work), and then select go to console from the next menu. Once it goes to a console, hit ctrl-alt-f9 (for me, at least), and then hit no. GDM should now start up just fine.

Did you by chance try downgrading to gdm 2.20? That's when I encountered the problem.

If anyone else knows what the problem might be, or where I could start to look for a solution, I'd appreciate it.

---

### Post by xifer on 2009-12-21
> **mechaxl said:**
> So I've got the same problem, and I've got a workaround for it, but not a solution.

What you're going to want to do is when you're at that screen, hit ctrl-alt-f7. This will bring you to what's hogging up display :0. It will probably be a notice saying that Ubuntu is running in low graphics mode. Just hit cancel (I think, try hitting the other one if that doesn't work), and then select go to console from the next menu. Once it goes to a console, hit ctrl-alt-f9 (for me, at least), and then hit no. GDM should now start up just fine.

Did you by chance try downgrading to gdm 2.20? That's when I encountered the problem.

If anyone else knows what the problem might be, or where I could start to look for a solution, I'd appreciate it.

I use kdm not gdm and sometimes got this when gnome checked and found gdm wasn't running and tried to restart it.  Doesn't happen anymore with newest updates.

If you are using gdm/gnome then something else may be stopping/delaying a clean startup.  I didn't see anything odd in your gdm.config file but others may.  If it happens again see if any errors are in the log files.

---

