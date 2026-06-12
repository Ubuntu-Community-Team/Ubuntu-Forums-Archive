---
title: "Setting up x windows remotely"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by seattle vic on 2009-10-05
I've been successful in setting up an SSH link and then using vncviewer to link into my home machine from work.  However on the rare occasions that I have to reboot the machine remotely (like today when I upgraded to 9.10, I can't get it to work.  When I run X11vnc on the remote machine via the shell, it will not work.  I get the message:
***************************************************************

login as: vic
[email]vic@victorycat.com[/email]'s password:
Linux vic-desktop 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:55:55 UTC 2009 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

272 packages can be updated.
0 updates are security updates.

Last login: Mon Oct  5 13:39:32 2009 from ip-130-76-32-100.boeing.com
vic@vic-desktop:~$ a
alias a='alias'
alias ap='apropos'
alias backupbudget='rsync -e '\''ssh -ax -p 1372'\'' -avz /home/vic/budget 192.168.2.101:/home/vic'
alias backupfinance='rsync -e '\''ssh -ax -p 1372'\'' -avz /home/vic/finance 192.168.2.101:/home/vic'
alias backupwriting='rsync -e '\''ssh -ax -p 1372'\'' -avz /home/vic/writing 192.168.2.101:/home/vic'
alias boeinglaptop=' rdesktop 192.168.2.105 -u hardyv -p Okydokey98 -g 1600x1000'
alias conservative='sudo cpufreq-selector -c 0 -g conservative; sudo cpufreq-selector -c 1 -g conservative'
alias earth='cd ~/google-earth;sudo ./googleearth &'
alias h='history'
alias l='ls -CF'
alias ll='ls -al'
alias lll='ls -al | less'
alias localbackupbudget='rsync  -avz /home/vic/budget /media/disk/home/vic'
alias localbackupfinance='rsync  -avz /home/vic/finance /media/disk/home/vic'
alias localbackupwriting='rsync -avz /home/vic/writing /media/disk/home/vic'
alias ls='ls --color=auto'
alias mountwindowspartition='sudo mount /dev/sda2 /media/windows/ -t ntfs -o iocharset=utf8,umask=000'
alias nwrestart='sudo /etc/init.d/NetworkManager restart'
alias ondemand='sudo cpufreq-selector -c 0 -g ondemand; sudo cpufreq-selector -c 1 -g ondemand'
alias performance='sudo cpufreq-selector -c 0 -g performance; sudo cpufreq-selector -c 1 -g performance'
alias powersave='sudo cpufreq-selector  -c 0 -g powersave; sudo cpufreq-selector -c 1 -g powersave'
alias startvnc='cd //home/vic/bin; source ./vnc'
vic@vic-desktop:~$ startvnc
vic@vic-desktop://home/vic/bin$ 05/10/2009 16:12:44 -usepw: found /home/vic/.vnc/passwd
05/10/2009 16:12:44 x11vnc version: 0.9.3 lastmod: 2007-09-30
No protocol specified

05/10/2009 16:12:44 ***************************************
05/10/2009 16:12:44 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: [http://www.karlrunge.com/x11vnc/#faq](http://www.karlrunge.com/x11vnc/#faq)

************************************************************

I've tried to figure this out before, but have been frustrated.  Can anybody help?

Thanks in advance...

---

### Post by krunge on 2009-10-05
No user is logged into an X session yet, right?   Only the GDM login greeter is running?  If so and it is GDM you will need to run something like this:
```
x11vnc -auth /var/gdm/:0.Xauth -display :0 ...
```
or if the auth file is in a different location (e.g. KDM location), point to that file instead.

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

BTW the auth file will only be readable by root so you will need to run x11vnc as root or via sudo.

---

### Post by lavinog on 2009-10-06
what os are you using at work?
if linux, you can enable x11forwarding on your server and run the gui programs via ssh

if windows you can look at this thread: [thread]225898[/thread]

---

