---
title: "Intruder in my computer"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by jamiehendrich on 2011-01-28
Someone has gotten into my computer as follows:  They added a password file that now says passwd- in my file system area and instead of shadow it's gshadow~ with a paddlock,  and it said something about a shell and to ignore other passwords.  They put a padlock on my gconfd. file....whatever that is.  I'm a newbie and I know  none of this stuff.  

Can anyone tell me how to get them out of my computer?  This is unconscionable.

Jamie

```
#
# /etc/login.defs - Configuration control definitions for the login package.
#
# Three items must be defined:  MAIL_DIR, ENV_SUPATH, and ENV_PATH.
# If unspecified, some arbitrary (and possibly incorrect) value will
# be assumed.  All other items are optional - if not specified then
# the described action or option will be inhibited.
#
# Comment lines (lines beginning with "#") and blank lines are ignored.
#
# Modified for Linux.  --marekm

# REQUIRED for useradd/userdel/usermod
#   Directory where mailboxes reside, _or_ name of file, relative to the
#   home directory.  If you _do_ define MAIL_DIR and MAIL_FILE,
#   MAIL_DIR takes precedence.
#
#   Essentially:
#      - MAIL_DIR defines the location of users mail spool files
#        (for mbox use) by appending the username to MAIL_DIR as defined
#        below.
#      - MAIL_FILE defines the location of the users mail spool files as the
#        fully-qualified filename obtained by prepending the user home
#        directory before $MAIL_FILE
#
# NOTE: This is no more used for setting up users MAIL environment variable
#       which is, starting from shadow 4.0.12-1 in Debian, entirely the
#       job of the pam_mail PAM modules
#       See default PAM configuration files provided for
#       login, su, etc.
#
# This is a temporary situation: setting these variables will soon
# move to /etc/default/useradd and the variables will then be
# no more supported
MAIL_DIR        /var/mail
#MAIL_FILE      .mail

#
# Enable logging and display of /var/log/faillog login failure info.
# This option conflicts with the pam_tally PAM module.
#
FAILLOG_ENAB		yes

#
# Enable display of unknown usernames when login failures are recorded.
#
# WARNING: Unknown usernames may become world readable. 
# See #290803 and #298773 for details about how this could become a security
# concern
LOG_UNKFAIL_ENAB	no

#
# Enable logging of successful logins
#
LOG_OK_LOGINS		no

#
# Enable "syslog" logging of su activity - in addition to sulog file logging.
# SYSLOG_SG_ENAB does the same for newgrp and sg.
#
SYSLOG_SU_ENAB		yes
SYSLOG_SG_ENAB		yes

#
# If defined, all su activity is logged to this file.
#
#SULOG_FILE	/var/log/sulog

#
# If defined, file which maps tty line to TERM environment parameter.
# Each line of the file is in a format something like "vt100  tty01".
#
#TTYTYPE_FILE	/etc/ttytype

#
# If defined, login failures will be logged here in a utmp format
# last, when invoked as lastb, will read /var/log/btmp, so...
#
FTMP_FILE	/var/log/btmp

#
# If defined, the command name to display when running "su -".  For
# example, if this is defined as "su" then a "ps" will display the
# command is "-su".  If not defined, then "ps" would display the
# name of the shell actually being run, e.g. something like "-sh".
#
SU_NAME		su

#
# If defined, file which inhibits all the usual chatter during the login
# sequence.  If a full pathname, then hushed mode will be enabled if the
# user's name or shell are found in the file.  If not a full pathname, then
# hushed mode will be enabled if the file exists in the user's home directory.
#
HUSHLOGIN_FILE	.hushlogin
HUSHLOGIN_FILE	/etc/hushlogins

#
# *REQUIRED*  The default PATH settings, for superuser and normal users.
#
# (they are minimal, add the rest in the shell startup files)
ENV_SUPATH	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11
ENV_PATH	PATH=/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games

#
# Terminal permissions
#
#	TTYGROUP	Login tty will be assigned this group ownership.
#	TTYPERM		Login tty will be set to this permission.
#
# If you have a "write" program which is "setgid" to a special group
# which owns the terminals, define TTYGROUP to the group number and
# TTYPERM to 0620.  Otherwise leave TTYGROUP commented out and assign
# TTYPERM to either 622 or 600.
#
# In Debian /usr/bin/bsd-write or similar programs are setgid tty
# However, the default and recommended value for TTYPERM is still 0600
# to not allow anyone to write to anyone else console or terminal

# Users can still allow other people to write them by issuing 
# the "mesg y" command.

TTYGROUP	tty
TTYPERM		0600

#
# Login configuration initializations:
#
#	ERASECHAR	Terminal ERASE character ('\010' = backspace).
#	KILLCHAR	Terminal KILL character ('\025' = CTRL/U).
#	UMASK		Default "umask" value.
#
# The ERASECHAR and KILLCHAR are used only on System V machines.
# 
# UMASK usage is discouraged because it catches only some classes of user
# entries to system, in fact only those made through login(1), while setting
# umask in shell rc file will catch also logins through su, cron, ssh etc.
#
# At the same time, using shell rc to set umask won't catch entries which use
# non-shell executables in place of login shell, like /usr/sbin/pppd for "ppp"
# user and alike.
#
# Therefore the use of pam_umask is recommended (Debian package libpam-umask)
# as the solution which catches all these cases on PAM-enabled systems.
# 
# This avoids the confusion created by having the umask set
# in two different places -- in login.defs and shell rc files (i.e.
# /etc/profile).
#
# For discussion, see #314539 and #248150 as well as the thread starting at
# [http://lists.debian.org/debian-devel/2005/06/msg01598.html](http://lists.debian.org/debian-devel/2005/06/msg01598.html)
#
# Prefix these values with "0" to get octal, "0x" to get hexadecimal.
#
ERASECHAR	0177
KILLCHAR	025
# 022 is the "historical" value in Debian for UMASK when it was used
# 027, or even 077, could be considered better for privacy
# There is no One True Answer here : each sysadmin must make up his/her
# mind.
#UMASK		022

#
# Password aging controls:
#
#	PASS_MAX_DAYS	Maximum number of days a password may be used.
#	PASS_MIN_DAYS	Minimum number of days allowed between password changes.
#	PASS_WARN_AGE	Number of days warning given before a password expires.
#
PASS_MAX_DAYS	99999
PASS_MIN_DAYS	0
PASS_WARN_AGE	7

#
# Min/max values for automatic uid selection in useradd
#
UID_MIN 1000
UID_MAX 60000

#
# Min/max values for automatic gid selection in groupadd
#
GID_MIN			  100
GID_MAX			60000

#
# Max number of login retries if password is bad. This will most likely be
# overriden by PAM, since the default pam_unix module has it's own built
# in of 3 retries. However, this is a safe fallback in case you are using
# an authentication module that does not enforce PAM_MAXTRIES.
#
LOGIN_RETRIES		5

#
# Max time in seconds for login
#
LOGIN_TIMEOUT		60

#
# Which fields may be changed by regular users using chfn - use
# any combination of letters "frwh" (full name, room number, work
# phone, home phone).  If not defined, no changes are allowed.
# For backward compatibility, "yes" = "rwh" and "no" = "frwh".
# 
CHFN_RESTRICT		rwh

#
# Should login be allowed if we can't cd to the home directory?
# Default in no.
#
DEFAULT_HOME	yes

#
# If defined, this command is run when removing a user.
# It should remove any at/cron/print jobs etc. owned by
# the user to be removed (passed as the first argument).
#
#USERDEL_CMD	/usr/sbin/userdel_local

#
# When prompting for password without echo, getpass() can optionally
# display a random number (in the range 1 to GETPASS_ASTERISKS) of '*'
# characters for each character typed.  This feature is designed to
# confuse people looking over your shoulder when you enter a password :-).
# Also, the new getpass() accepts both Backspace (8) and Delete (127)
# keys to delete previous character (to cope with different terminal
# types), Control-U to delete all characters, and beeps when there are
# no more characters to delete, or too many characters entered.
#
# Setting GETPASS_ASTERISKS to 1 results in more traditional behaviour -
# exactly one '*' displayed for each character typed.
#
# Setting GETPASS_ASTERISKS to 0 disables the '*' characters (Backspace,
# Delete, Control-U and beep continue to work as described above).
#
# Setting GETPASS_ASTERISKS to -1 reverts to the traditional getpass()
# without any new features.  This is the default.
#
#GETPASS_ASTERISKS 1

#
# This enables userdel to remove user groups if no members exist.
#
# Other former uses of this variable such as setting the umask when
# user==primary group are not used in PAM environments, thus in Debian
#
USERGROUPS_ENAB yes

#
# Instead of the real user shell, the program specified by this parameter
# will be launched, although its visible name (argv[0]) will be the shell's.
# The program may do whatever it wants (logging, additional authentification,
# banner, ...) before running the actual shell.
#
# FAKE_SHELL /bin/fakeshell

#
# If defined, either full pathname of a file containing device names or
# a ":" delimited list of device names.  Root logins will be allowed only
# upon these devices.
#
# This variable is used by login and su.
#
#CONSOLE	/etc/consoles
#CONSOLE	console:tty01:tty02:tty03:tty04

#
# List of groups to add to the user's supplementary group set
# when logging in on the console (as determined by the CONSOLE
# setting).  Default is none.
#
# Use with caution - it is possible for users to gain permanent
# access to these groups, even when not logged in on the console.
# How to do it is left as an exercise for the reader...
#
# This variable is used by login and su.
#
#CONSOLE_GROUPS		floppy:audio:cdrom

#
# Only works if compiled with MD5_CRYPT defined:
# If set to "yes", new passwords will be encrypted using the MD5-based
# algorithm compatible with the one used by recent releases of FreeBSD.
# It supports passwords of unlimited length and longer salt strings.
# Set to "no" if you need to copy encrypted passwords to other systems
# which don't understand the new algorithm.  Default is "no".
#
# This variable is used by chpasswd, gpasswd and newusers.
#
#MD5_CRYPT_ENAB	no

################# OBSOLETED BY PAM ##############
#						#
# These options are now handled by PAM. Please	#
# edit the appropriate file in /etc/pam.d/ to	#
# enable the equivelants of them.
#
###############

#MOTD_FILE
#DIALUPS_CHECK_ENAB
#LASTLOG_ENAB
#MAIL_CHECK_ENAB
#OBSCURE_CHECKS_ENAB
#PORTTIME_CHECKS_ENAB
#SU_WHEEL_ONLY
#CRACKLIB_DICTPATH
#PASS_CHANGE_TRIES
#PASS_ALWAYS_WARN
#ENVIRON_FILE
#NOLOGINS_FILE
#ISSUE_FILE
#PASS_MIN_LEN
#PASS_MAX_LEN
#ULIMIT
#ENV_HZ
#CHFN_AUTH
#CHSH_AUTH
#FAIL_DELAY

################# OBSOLETED #######################
#						  #
# These options are no more handled by shadow.    #
#                                                 #
# Shadow utilities will display a warning if they #
# still appear.                                   #
#                                                 #
###################################################

# CLOSE_SESSIONS
# LOGIN_STRING
# NO_PASSWORD_CONSOLE
# QMAIL_DIR
```

---

### Post by jamiehendrich on 2011-01-28
Who would do this?  

This file changed as well:

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0



And also here's a screenshot of another file that changed.  I didn't change them.

---

### Post by jamiehendrich on 2011-01-28
here's the other screenshot.

---

### Post by bodhi.zazen on 2011-01-28
I do not see anything abnormal in anything you posted so far.

Many applications, nano and gedit, make a backup flle ending in ~ or possibly -

padlock simply means you do not have permission to alter the file, probably because it is owned by root.

Please do not post long lines of output as in the first post, either post the relevant lines or attach it as text.

---

### Post by lisati on 2011-01-28
> **bodhi.zazen said:**
> Many applications, nano and gedit, make a backup flle ending in ~ or possibly -
That was my thought too. This is roughly equivalent to MS-DOS/Windows making a backup file with a .BAK extension. This is a normal part of using Ubuntu, and doesn't necessarily mean that there is intruder.

> **bodhi.zazen said:**
> Please do not post long lines of output as in the first post, either post the relevant lines or attach it as text.
Agreed. Another way that some people find useful for listings is to put [noparse]```
[/noparse] at the start and [noparse]
```[/noparse] at the end, which creates a window within your post that can be scrolled independently.

---

### Post by jamiehendrich on 2011-01-28
RESPONSE BY NEWBIE:

It isn't abnormal for "someone" to enter the following on MY computer:

Instead of the real user shell, the program specified by this parameter
# will be launched, although its visible name (argv[0]) will be the shell's.
# The program may do whatever it wants (logging, additional authentification,
# banner, ...) before running the actual shell.
#
# FAKE_SHELL /bin/fakeshell

Gosh, is the above output?  I'm a complete novice.  Someone can type in the above text and make changes to my computer and all of it appeared on my computer without me doing it and there is nothing abnormal about that?   You are kidding, right?  I didn't insert any of the text.  My computer did this on "its own."  I have a single computer.

---

### Post by bodhi.zazen on 2011-01-28
Nothing wrong with that at all.

You are looking at a configuration file.

# = comments

So if you wanted to configure "FAKE_SHELL" you would uncomment that line.

Like this```
FAKE_SHELL /bin/fakeshell
```

and save the changes.

The lines above describe briefly what "FAKE_SHELL".

---

### Post by Joe of loath on 2011-01-28
> **jamiehendrich said:**
> RESPONSE BY NEWBIE:

It isn't abnormal for "someone" to enter the following on MY computer:

Instead of the real user shell, the program specified by this parameter
# will be launched, although its visible name (argv[0]) will be the shell's.
# The program may do whatever it wants (logging, additional authentification,
# banner, ...) before running the actual shell.
#
# FAKE_SHELL /bin/fakeshell

Gosh, is the above output?  I'm a complete novice.  Someone can type in the above text and make changes to my computer and all of it appeared on my computer without me doing it and there is nothing abnormal about that?   You are kidding, right?  I didn't insert any of the text.  My computer did this on "its own."  I have a single computer.

I suggest you do some reading up and research on Linux in general. Everything you have described is absolutely normal, and either a part of the system, or part of its normal running.

---

### Post by rg4w on 2011-01-28
> **Joe of loath said:**
> I suggest you do some reading up and research on Linux in general. Everything you have described is absolutely normal, and either a part of the system, or part of its normal running.
These forums really help me appreciate Ubuntu:  in the last several months I've seen maybe a dozen or more posts from people even greener to this OS than myself who believe that their system was compromised, only to find out that it wasn't.

Man, if I'd been using Windows long enough I might suspect everything I didn't understand was a security breach too, because on Windows it so often is. ;)

---

### Post by Rasa1111 on 2011-01-28
jamie...

You should listen to Bodhi,  if no one else.
He knows his stuff. 

nothing here indicates you've been compromised.

---

### Post by jamiehendrich on 2011-01-28
thank you for the input.    You have no idea what my computer has been doing lately.

And of course I should read up on it.  I'm clueless and I'[ll admit it.  I know nothing about computers.  I just know when it's different and it's different.

Please just disregard my paranoia.

Jamie

PS  And is it normal that I cannot put a password on my ethernet connection?

---

### Post by ikt on 2011-01-28
> **jamiehendrich said:**
> PS  And is it normal that I cannot put a password on my ethernet connection?

how would you put a password on an ethernet connection in windows?

I've never heard of putting a password on an ethernet connection before and I've been around for a while :/

---

### Post by robsoles on 2011-01-28
> **jamiehendrich said:**
> ...    You have no idea what my computer has been doing lately.

...

You've shared a few things that others have responded to tell you are normal things to find in an Ubuntu installation


Have any of ***your*** files (that you created, not that installers and configurators create or modify) been altered?

Have you suddenly been locked out of an application you could access before, with a statement regarding permissions, **without** statements regarding errors?

Is your computer too busy for you, under **exactly** same circumstances, where it was very available shortly after first installing and completing all the updates?

If the answer to those three questions is no and you find a funny looking line in, or perhaps just, a funny looking file somewhere in your system an easy enough thing to do, before stressing at all, is to pop them into Google with your OS version, check this out:

[www.google.com/search?q=ubuntu+10.04+etc%2Flogin.defs]("http://www.google.com/search?q=ubuntu+10.04+etc%2Flogin.defs")

Look through Google's responses and see if you can find firm clues: Is it part of your OS? Is it part of some software package? Are there more people trying to make it work than asking how to remove it? Is the majority saying it is evil?

"why is the folder showing a padlock in ubuntu" into Google should get you some great stuff too.


As you learn more about Ubuntu, computers and OSes in general you will first understand ***how*** the file has a padlock and how you can easily get around that and at some point or another you will understand ***why*** the file has a padlock and why you should be fairly well-read and very careful if you choose to operate around that padlock ;)



*Note: The worst malicious things make no visible sign and do their best not  to slow your connection down either, you are very likely to know which file  you set the execution bit on if you ever figure out this is happening  in your Linux box.

---

### Post by srs5694 on 2011-01-29
Some more comments:


[list]
[*]The [chkrootkit](http://www.chkrootkit.org/) utility can check for suspicious signs on a Linux installation. If you suspect a break-in, you might consider running it. Unfortunately, it doesn't seem to be in the Ubuntu repositories, so you'll have to download it from its Web site.
[*]The Tripwire program (which *is* in the Ubuntu repositories) can monitor your system for changes to critical configuration files. Unfortunately, it's a bit hairy to set up properly, but if you're really concerned about intrusion, it's worth the effort.
[*]Posting fragments of configuration files (or whole files) that you find suspicious without identifying what those files are is unhelpful. If you don't understand something in a configuration file, by all means post it and ask for advice, but you *must* identify the file if you expect a helpful response. Although I could clearly identify what some of the files you posted were, I had to track down others myself. It would have been easier for me to not bother.
[*]Likewise, you must say what you find suspicious about the file or quoted fragment thereof. It's unclear why you found some of the things you quoted suspicious.
[*]You claimed a number of files had been changed, but you didn't say why you thought they'd been changed. (Your screen shot shows file modification times of "today," so I'm guessing you used that to identify at least some of them.)
[*]A large number of ordinary manual and automatic system activities alter files in /etc and elsewhere on a Linux system. These can include routine package updates, users changing their passwords, filesystems being mounted or unmounted, and any number of manual system configuration changes.
[*]If you suspect your system has been compromised, *remove it from the Internet at once!* Compromised computers are often used to attack other computers, so you don't want to leave such a system connected for a second longer than necessary. If you need Internet access to research the problem, use another computer, or at least reboot the computer into another OS. (An Ubuntu disc's live CD mode should work fine for this purpose.)
[/list]


Like others, I found nothing suspicious in the files and file fragments you posted.

---

### Post by jd2012 on 2011-01-29
> **srs5694 said:**
> Some more comments:


[LIST]
[*]The [chkrootkit]("http://www.chkrootkit.org/") utility can check for suspicious signs on a Linux installation. If you suspect a break-in, you might consider running it. Unfortunately, it doesn't seem to be in the Ubuntu repositories, so you'll have to download it from its Web site.
[/LIST]
 


I obtained chkrootkit via:

```

sudo apt-get install chkrootkit

```


Any insight on how that happened? :lolflag:
Extra packages/updates ect.?

---

### Post by robsoles on 2011-01-29
> **srs5694 said:**
> Some more comments:


[LIST]
[*]The [chkrootkit]("http://www.chkrootkit.org/") utility can check for suspicious signs on a Linux installation. If you suspect a break-in, you might consider running it. Unfortunately, it doesn't seem to be in the Ubuntu repositories, so you'll have to download it from its Web site.
[/LIST]

  ...

I have partner sources 'checked' in my sources, maybe that is the difference, I opened "Ubuntu Software Centre" in 10.04 here and pumped 'rootkit' into the search box - three entries and the middle one is chkrootkit.

---

### Post by supererki on 2011-01-29
Monitor your network traffic. 
Set up firewall.

---

### Post by srs5694 on 2011-01-29
> **jd2012 said:**
> I obtained chkrootkit via:

```

sudo apt-get install chkrootkit

```
Any insight on how that happened? :lolflag:
Extra packages/updates ect.?

I must have mistyped when I did my initial search; I tried again and it showed up on my system. Sorry about the confusion!

---

### Post by jamiehendrich on 2011-01-29
Thank you.

---

### Post by jamiehendrich on 2011-01-29
PS  I clicked on "file system," then on "date modified" and all kinds of files came up that had been modified on a day when I wasn't at that particular computer for two days.  I didn't know that a computer would change its file system when I didn't touch it.

Thus, the paranoia.  Guess I was completely wrong.

---

### Post by JKyleOKC on 2011-01-29
> **jamiehendrich said:**
> I didn't know that a computer would change its file system when I didn't touch it.

Thus, the paranoia.  Guess I was completely wrong.A little paranoia is a good thing to have, these days, when dealing with the Internet and its high percentage of baddies!

That said, you need to be aware of the system program called "cron." This runs at regular intervals whenever the computer is powered up, whether anyone is logged in or not. It can have any number of tasks to perform, and their timing can be set individually for each task. For instance, this machine runs a cron task at 17 minutes past the hour, every hour of the day, and that task can itself have a number of sub-tasks.

Those files that roused your suspicions were probably created or modified by cron tasks. Still, it's always worthwhile to ask about anything that you don't recognize. For example, my home office LAN got invaded last summer (though a series of stupid mistakes on my part that left it wide open to the intruder) so I had to reformat and reinstall ALL of the machines. Being a bit paranoid myself at that point, I kept close track on the system logs for a few days -- and found entries referring to a process named "rtkit" that I had never heard of before!

I immediately disconnected all machines that had been infected from the Internet and used my laptop, which had been powered down through the whole episode, to search for such a process. It turns out that "rtkit" is not a root kit, but a real time kit that is part of the new sound system "pulseaudio." Thus it's completely normal for it to be there.

As you gain more experience with the system, you'll be better able to spot suspicious happenings. Welcome to the world of Linux!

---

### Post by jamiehendrich on 2011-01-29
thank you very much, Mr. Kyle!  Really appreciate the warning/advice.

jamie

---

### Post by Rasa1111 on 2011-01-30
jamie~

 DO you have your firewall on?

It's really not even needed if youre not running a server..
 But since I am a newb myself (using Ubuntu for 1 year)
I still feel safer with my firewall on. lol
Although Im quite sure no one will be getting into my system, regardless. lol
, but hey... you never know. 

 If you don't have your firewall on, and would like it on..
You can install a simple way to configure your firewall, turn it on/off. 

In Ubuntu software center.. 
Type into the search box, "UFW"

something will pop up in the list called "firewall configuration".  

 Install it. 

Once installed,
 Navigate to "System menu> Administration> and click on "firewall configuration". 

 Once its open, just click on the "enable" box. 

 Your firewall is now on, and you can close it out and forget about it. 

SOrry if you already knew this.

---

### Post by jamiehendrich on 2011-01-30
In the software center?  You mean synaptic?  I see nothing called "software center."

---

### Post by jamiehendrich on 2011-01-30
I just went into synaptic.  It's already in green and is there.  It must be disabled.  I noticed when my screen comes on and all that stuff comes up in black and white, it says the firewall is off.

And I have nothing re "firewell" in neither "preferences" nor "administration.  Is that maybe the issue?

---

### Post by philinux on 2011-01-30
Please dont keep posting the same item. Wait at least 24 hours before Bumping your thread. Or wait for a reply.

---

### Post by jamiehendrich on 2011-01-30
Inadvertent.  Sorry.

---

### Post by Paqman on 2011-01-30
> **jamiehendrich said:**
> In the software center?  You mean synaptic?  I see nothing called "software center."

Ubuntu Software centre is an alternative to Synaptic. You can find it under Applications > Ubuntu Software Centre.

If you want to enable your firewall, install the package "gufw". That will give you a tool (under Admin I presume?) that will allow you to turn the firewall on. However, doing so isn't going to make you any safer, since Ubuntu's default configuration is just as secure.

---

### Post by oldos2er on 2011-01-30
To enable the firewall, run ```
sudo ufw enable
```
I suggest the OP read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by jamiehendrich on 2011-01-30
thanks.  I'll try it.

---

### Post by jamiehendrich on 2011-01-30
It says it's active and available on startup, yet when that black and white lingo comes up when all of the stuff is loading when I turn on my computer, it says it's disabled.

I'm going to turn off and try it again.

---

### Post by Rasa1111 on 2011-01-30
every noob should know about the software center. 

It's basically "synaptic for noobs". lol

as has already been said..
it is under **Applications**> **Ubuntu Software Center**.

 good luck.

---

### Post by jamiehendrich on 2011-01-30
Rasa, I don't have "Ubuntu Software Center."  I have only "Synaptic Package Manager" under "Administration."

So....

Is that what you're talking about?  There's also something called "Software Sources."  There's nothing in "Software Sources" dealing with a firewall. 

I have now done the "enabling firewall" step in a terminal as suggested by 
"Phyllis Diller."  Thank you again.

---

### Post by jamiehendrich on 2011-01-30
PS  Rasa, it's not under "Applications" either.  Hmmmmm.  Why do you have it and I do not?

---

### Post by mikewhatever on 2011-01-30
Why on earth do you want a firewall? Is it to have more logs and config files to freak out about? Leave it be, breath deeply, there is no intruder.

---

### Post by jamiehendrich on 2011-01-30
:lolflag:

out, O-U-T-, out.  

You would be LIVID if someone were in your computer......"Mike."  You would probably go to the ends of the earth to put a stop to it.  So.....

However, I have the firewall on "supposedly" and am going to move on with life.

Jamie

PS  You should be more sympathetic.........IMO.

---

### Post by coffeecat on 2011-01-30
> **jamiehendrich said:**
> I don't have "Ubuntu Software Center."  I have only "Synaptic Package Manager" under "Administration."

Which version of Ubuntu are you running? If it's Lucid/10.04 or Maverick/10.10 you do have Software Centre. It's at the bottom of the Applications menu, not in Administration.

---

### Post by jamiehendrich on 2011-01-30
jaunty

---

### Post by davidmohammed on 2011-01-30
software center is not available in jaunty...

jaunty was released on 23rd April 2009 - support for jaunty ended back in October last year.

I would strongly recommend you start thinking of upgrading to lucid (through karmic) as soon as possible.

---

### Post by QLee on 2011-01-30
[QUOTE=jamiehendrich]...
out, O-U-T-, out.  [/QUOTE]

If you mark this thread as solved (edit first post title to include solved) most people will stop posting. Otherwise it appears to be an open question.



[QUOTE=jamiehendrich]You would be LIVID if someone were in your computer......
...

PS  You should be more sympathetic.........IMO.[/QUOTE]

Sure, anyone would be bothered by intruders. Keep in mind, we (at least most of us) know there isn't much chance of intruder in your computer and people would surely have been appropriately serious in helping you if any data you gave looked dangerous. It's always a good idea to breathe and calm down when troubleshooting, impatience is not your friend.

---

### Post by jamiehendrich on 2011-01-30
I know, David.  If I would upgrade, I'll ruin it or cause issues.
So I'll have to remain where I am for now.  

But I will think about it............sometime.

---

### Post by coffeecat on 2011-01-30
> **jamiehendrich said:**
> But I will think about it............sometime.

Another thing to think about considering your concerns about security. With Jaunty now end of life and no more updates, this means no more security patches for firefox and the kernel. That's an important consideration.

Good luck! :)

---

### Post by JKyleOKC on 2011-01-30
> **jamiehendrich said:**
> I know, David.  If I would upgrade, I'll ruin it or cause issues.
So I'll have to remain where I am for now.  

But I will think about it............sometime.Just keep in mind that ever since Jaunty went EndOfLife back in October, it has had absolutely NO security updates -- and in that nearly three months, the current versions have gotten almost a dozen.

Staying on a version that gets no updates is much riskier than running without a firewall.

---

### Post by jamiehendrich on 2011-01-30
thank you very much.

---

### Post by Paqman on 2011-02-02
> **JKyleOKC said:**
> 
Staying on a version that gets no updates is much riskier than running without a firewall.

+1 to this. Enabling a firewall on Ubuntu won't improve your security at all, but missing out on security updates is a massive security issue. You've got two options to get your security back up to scratch:
[LIST=1]
[*]Upgrade or reinstall a supported version. I would suggest 10.04 since it's an LTS release, and will be supported for another two years.
[*]OR disconnect the machine from the internet
[/LIST]

---

### Post by overdrank on 2011-02-02
Some post have been removed. Please keep the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") in mind when posting. :)

---

### Post by srs5694 on 2011-02-02
> **Paqman said:**
> +1 to this. Enabling a firewall on Ubuntu won't improve your security at all, but missing out on security updates is a massive security issue.

This sort of comment makes me nervous, for a couple of reasons. First, security is best applied in layers so that an error in configuring one layer can be corrected by another layer. This is relevant to the comment about firewalls not improving security because, although a default Ubuntu installation runs few or no servers and therefore is at low risk of intruders breaking in remotely, it's easy to accidentally install a server in Ubuntu (or any Linux distribution). If you do that, then a firewall might well be very useful in preventing abuse. Firewalls can also be useful in preventing abuse that could be triggered remotely through some other means. For instance and hypothetically, a security problem in a Web browser's Java implementation could enable an intruder to set up a server that could then be used to break into your computer. A firewall could block access to this server, and therefore be useful.

Second, many security updates affect either flaws in servers (which are irrelevant if none are being run) or flaws that are accessible only to local users (which for most Ubuntu users means the person who owns the computer). There's a great deal of overlap between what patching these flaws protects against and what a firewall protects against. That is, patching flaws in servers is important only if you run them, but of course if they're run accidentally but blocked by a firewall, the flaws become irrelevant; and flaws in local programs that might be abused by bad guys will often (although not always) be important only if the attacker can open a port, which a firewall will protect against.

Please note that I'm not saying that system upgrades are unimportant; they are important. There are means of attack, and types of abuse, that can be prevented by keeping your software up to date but not by running a firewall. (Say, a hypothetical Web browser/Java flaw that makes your computer contact another system for spam that's then relayed through your outgoing mail configuration.) What I *am* saying is that a firewall can be equally important. Fortunately, many (perhaps most) home and small business users today have firewall-like protection in the form of a broadband router. Unfortunately, Wi-Fi broadband routers provide another weakness, particularly if they're configured to use the useless WEP encryption rather than WPA2, so you've got to be extra careful when configuring Wi-Fi setups, but that's another matter....

Remember: Apply security in layers. Do not rely on a single method of protection, since no single form of protection is completely effective. In terms of system updates specifically, there may be a window of opportunity between a flaw being discovered (and used by miscreants) and fixed on your system.

---

### Post by Paqman on 2011-02-04
> **srs5694 said:**
> it's easy to accidentally install a server in Ubuntu (or any Linux distribution). If you do that, then a firewall might well be very useful in preventing abuse.

Of course, there's also the problem that not all users will be aware what "server software" includes. I think everybody would understand that Apache is a server, but some might not realise that setting up ssh for use within their own network is.

Having said that, within the context of Absolute Beginners one of the problems we encounter continually is new users bringing their Windows security assumptions over to Linux. Standard assumptions on Windows are that you must install two 3rd party applicaitons to be safe:
[LIST=1]
[*]An antivirus suite
[*]A software firewall
[/LIST]

Once they've done that, they think they've taken care of security. That's clearly not the case on either Windows or Linux, so it's a good misconception to clear up.

You'll note that despite downplaying the criticality of enabling your firewall on Ubuntu, I did instruct the OP how to do so. At the very least, enabling ufw does no harm.

---

