---
title: "cant change vnc Passwd from ssh."
date: 2011-03-19
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-03-19
So I mistakenly wiped out my vnc configurations....

I use a headless sever that i ssh into and sometimes vnc

I was testing out vnc servers too, so i have all of them.

here is my error

```

luke@media:~$ [COLOR="Red"]x11vnc -storepasswd[/COLOR]
Enter VNC password:

Verify password:

Write password to /home/luke/.vnc/passwd?  [y]/n y
Password written to: /home/luke/.vnc/passwd
luke@media:~$ sudo x11vnc -storepasswd
[sudo] password for luke:
Enter VNC password:

Verify password:

Write password to /home/luke/.vnc/passwd?  [y]/n y
Password written to: /home/luke/.vnc/passwd
luke@media:~$ cat /home/luke/.vnc/passwd
&#9618;&#9618;&#9618;luke@media:~$ cat /home/luke/.vnc/passwd
&#9618;&#9618;&#9618;luke@media:~$ sudo cat /home/luke/.vnc/passwd
&#9618;&#9618;&#9618;luke@media:x11vnc :1
19/03/2011 00:05:44 passing arg to libvncserver: :1
###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        [COLOR="Red"]YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!![/COLOR]        @#
#@                                                           @#
#@  This means anyone with network access to this computer   @#
#@  may be able to view and control your desktop.            @#
#@                                                           @#
#@ >>> If you did not mean to do this Press CTRL-C now!! <<< @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  You can create an x11vnc password file by running:       @#
#@                                                           @#
#@       x11vnc -storepasswd password /path/to/passfile      @#
#@  or   x11vnc -storepasswd /path/to/passfile               @#
#@  or   x11vnc -storepasswd                                 @#
#@                                                           @#
#@  (the last one will use ~/.vnc/passwd)                    @#
#@                                                           @#
#@  and then starting x11vnc via:                            @#
#@                                                           @#
#@      x11vnc -rfbauth /path/to/passfile                    @#
#@                                                           @#
#@  an existing ~/.vnc/passwd file from another VNC          @#
#@  application will work fine too.                          @#
#@                                                           @#
#@  You can also use the -passwdfile or -passwd options.     @#
#@  (note -passwd is unsafe if local users are not trusted)  @#
#@                                                           @#
#@  Make sure any -rfbauth and -passwdfile password files    @#
#@  cannot be read by untrusted users.                       @#
#@                                                           @#
#@  Use x11vnc -usepw to automatically use your              @#
#@  ~/.vnc/passwd or ~/.vnc/passwdfile password files.       @#
#@  (and prompt you to create ~/.vnc/passwd if neither       @#
#@  file exists.)  Under -usepw, x11vnc will exit if it      @#
#@  cannot find a password to use.                           @#
#@                                                           @#
#@                                                           @#
#@  Even with a password, the subsequent VNC traffic is      @#
#@  sent in the clear.  Consider tunnelling via ssh(1):      @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/faq.html#faq-passwd](http://www.karlrunge.com/x11vnc/faq.html#faq-passwd)    @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  the setting in your ~/.x11vncrc file.                    @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
19/03/2011 00:05:45 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 6140
19/03/2011 00:05:45 XOpenDisplay("") failed.
19/03/2011 00:05:45 Trying again with XAUTHLOCALHOSTNAME=localhost ...
19/03/2011 00:05:45
19/03/2011 00:05:45 *** XOpenDisplay failed. No -display or DISPLAY.
19/03/2011 00:05:45 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
19/03/2011 00:05:45 *** 1 2 3 4
19/03/2011 00:05:49

19/03/2011 00:05:49 ***************************************
19/03/2011 00:05:49 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).

** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

** Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

See also: [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)
luke@media:~$


```

Furthermore when i run vncviewer from windows lappy i get a "failed to connect to server"

---

### Post by ralph.ronnquist on 2011-03-19
Mayeb it works with the following?
[PHP]x11vnc -rfbauth /home/luke/.vnc/passwd :1[/PHP]

---

### Post by wlraider70 on 2011-03-19
that did get me some progress, it appears that since X is not running, due to the server booting to command line vnc cannot start it.

however i cannot start X due to not having a screen attached. 
I'll work on starting X first.

that seems to have done, along with getting x running (i think)

---

