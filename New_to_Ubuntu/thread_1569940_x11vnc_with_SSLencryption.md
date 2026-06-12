---
title: "x11vnc with SSL/encryption"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by B34ST1Y on 2010-09-07
Hi all,


I am trying to get x11vnc to run on my Ubuntu machine, but am getting stopped with a large wall of text/errors. I have used tightvncserver in the past.

```

vncuser@Mybox:~$ x11vnc -ssl -stunnel -display :1
###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!!        @#
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
#@    http://www.karlrunge.com/x11vnc/#tunnelling            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    http://www.karlrunge.com/x11vnc/faq.html#faq-passwd    @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  the setting in your ~/.x11vncrc file.                    @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
07/09/2010 11:38:29 Setting -localhost in -stunnel mode.
07/09/2010 11:38:29 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 22249
07/09/2010 11:38:29 XOpenDisplay(":1") failed.
07/09/2010 11:38:29 Trying again with XAUTHLOCALHOSTNAME=localhost ...

07/09/2010 11:38:29 ***************************************
07/09/2010 11:38:29 *** XOpenDisplay failed (:1)

*** x11vnc was unable to open the X DISPLAY: ":1", it cannot continue.
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

See also: http://www.karlrunge.com/x11vnc/faq.html

```

---

### Post by bodhi.zazen on 2010-09-07
x11vnc shares an X session, so you need to log in as the same user who is logged into the physical machine.

What happens if you we :0 rather then :1 ?

If you want a separate X session, use another vnc server (tightvnc, FreeNX).

You can tunnel tightvnc over ssh and FreeNX has encryption built in (ssh I think).

---

### Post by CharlesA on 2010-09-07
+1 to FreeNX. I've only used it recently, but it blows VNC out of the water.

It goes over SSH as well, so it's encrypted.

---

### Post by B34ST1Y on 2010-09-07
The reason I chose x11vnc is because I need to meet PCI/DSS compliance & do not want to activate 11+ ssh servers for each machine that this needs to roll out on :) 

Is there a way that I can use x11vnc on a different xsession other than the one started on the physical display?

---

### Post by B34ST1Y on 2010-09-07
> **bodhi.zazen said:**
> x11vnc shares an X session, so you need to log in as the same user who is logged into the physical machine.

What happens if you we :0 rather then :1 ?

If you want a separate X session, use another vnc server (tightvnc, FreeNX).

You can tunnel tightvnc over ssh and FreeNX has encryption built in (ssh I think).

any variation of :0 :1 etc etc yields the same output

---

### Post by CharlesA on 2010-09-07
Did you already try to set a password with the commands in the error?

```
x11vnc -storepasswd password /path/to/passfile
x11vnc -storepasswd /path/to/passfile
x11vnc -storepasswd
```

---

### Post by B34ST1Y on 2010-09-07
Ok, I set up a password in the default location using 

```
sudo x11vnc -storepasswd
``` and entering it in.


The new output that it spits out:

```
vncuser@Mybox:~$ sudo x11vnc -ssl -stunnel -display :0 -rfbauth /home/vncuser/.vnc/passwd
07/09/2010 12:57:41 passing arg to libvncserver: -rfbauth
07/09/2010 12:57:41 passing arg to libvncserver: /home/vncuser/.vnc/passwd
07/09/2010 12:57:41 Setting -localhost in -stunnel mode.
07/09/2010 12:57:41 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 22281
07/09/2010 12:57:41 Using X display :0
07/09/2010 12:57:41 rootwin: 0xf2 reswin: 0x1400001 dpy: 0x99093a8
07/09/2010 12:57:41
07/09/2010 12:57:41 ------------------ USEFUL INFORMATION ------------------
07/09/2010 12:57:41 X DAMAGE available on display, using it for polling hints.
07/09/2010 12:57:41   To disable this behavior use: '-noxdamage'
07/09/2010 12:57:41
07/09/2010 12:57:41   Most compositing window managers like 'compiz' or 'beryl'
07/09/2010 12:57:41   cause X DAMAGE to fail, and so you may not see any screen
07/09/2010 12:57:41   updates via VNC.  Either disable 'compiz' (recommended) or
07/09/2010 12:57:41   supply the x11vnc '-noxdamage' command line option.
07/09/2010 12:57:41
07/09/2010 12:57:41 Wireframing: -wireframe mode is in effect for window moves.
07/09/2010 12:57:41   If this yields undesired behavior (poor response, painting
07/09/2010 12:57:41   errors, etc) it may be disabled:
07/09/2010 12:57:41    - use '-nowf' to disable wireframing completely.
07/09/2010 12:57:41    - use '-nowcr' to disable the Copy Rectangle after the
07/09/2010 12:57:41      moved window is released in the new position.
07/09/2010 12:57:41   Also see the -help entry for tuning parameters.
07/09/2010 12:57:41   You can press 3 Alt_L's (Left "Alt" key) in a row to
07/09/2010 12:57:41   repaint the screen, also see the -fixscreen option for
07/09/2010 12:57:41   periodic repaints.
07/09/2010 12:57:41
07/09/2010 12:57:41 XFIXES available on display, resetting cursor mode
07/09/2010 12:57:41   to: '-cursor most'.
07/09/2010 12:57:41   to disable this behavior use: '-cursor arrow'
07/09/2010 12:57:41   or '-noxfixes'.
07/09/2010 12:57:41 using XFIXES for cursor drawing.
07/09/2010 12:57:41 GrabServer control via XTEST.
07/09/2010 12:57:41
07/09/2010 12:57:41 Scroll Detection: -scrollcopyrect mode is in effect to
07/09/2010 12:57:41   use RECORD extension to try to detect scrolling windows
07/09/2010 12:57:41   (induced by either user keystroke or mouse input).
07/09/2010 12:57:41   If this yields undesired behavior (poor response, painting
07/09/2010 12:57:41   errors, etc) it may be disabled via: '-noscr'
07/09/2010 12:57:41   Also see the -help entry for tuning parameters.
07/09/2010 12:57:41   You can press 3 Alt_L's (Left "Alt" key) in a row to
07/09/2010 12:57:41   repaint the screen, also see the -fixscreen option for
07/09/2010 12:57:41   periodic repaints.
07/09/2010 12:57:41
07/09/2010 12:57:41 XKEYBOARD: all 28 "must have" keysyms accounted for.
07/09/2010 12:57:41   Not automatically switching to -xkb mode.
07/09/2010 12:57:41   If some keys still cannot be typed, try using -xkb.
07/09/2010 12:57:41   Also, remember "-remap DEAD" for accenting characters.
07/09/2010 12:57:41 X FBPM extension not supported.
07/09/2010 12:57:41 X display is capable of DPMS.
07/09/2010 12:57:41 --------------------------------------------------------
07/09/2010 12:57:41
07/09/2010 12:57:41 Default visual ID: 0x21
07/09/2010 12:57:41 Read initial data from X display into framebuffer.
07/09/2010 12:57:41 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
07/09/2010 12:57:41 failed to start stunnel.

```


And it seems that it still didn't start

---

### Post by B34ST1Y on 2010-09-07
Ok, dumb question. How do I make a cert for stunnel?

---

### Post by krunge on 2010-09-07
> **B34ST1Y said:**
> 
```
vncuser@Mybox:~$ sudo x11vnc -ssl -stunnel -display :0 -rfbauth /home/vncuser/.vnc/passwd

```


Get rid of the "-stunnel"

BTW, what are you planning to use for an SSL enabled VNC viewer? (most aren't)

---

### Post by asmoore82 on 2010-09-07
You might want to check out the Howto in my signature.

---

### Post by CharlesA on 2010-09-07
> **asmoore82 said:**
> You might want to check out the Howto in my signature.

I still think that tunneling VNC over SSH would be the best option. +1

Or better yet, just use FreeNX.

As long as you secure the SSH server, you are fine from problems.

Not to mention to securing it is as easy as modifying the conf file and then copying it to the other machines.

---

### Post by B34ST1Y on 2010-09-08
> **krunge said:**
> Get rid of the "-stunnel"

BTW, what are you planning to use for an SSL enabled VNC viewer? (most aren't)

As posted above, the VNC connection needs to meet PCI/DSS compliance & sending passwords in clear text isn't an option. This will roll out to 10+ servers, so I really can't justify running the SSH service on all of those machines for the sole reason of tunneling VNC.

---

### Post by CharlesA on 2010-09-08
Stupid question, but why are you running VNC on a server? Is there something that you cannot accomplish by forwarding X over SSH, or just by using straight SSH?

---

### Post by krunge on 2010-09-08
> **B34ST1Y said:**
> As posted above, the VNC connection needs to meet PCI/DSS compliance & sending passwords in clear text isn't an option. This will roll out to 10+ servers, so I really can't justify running the SSH service on all of those machines for the sole reason of tunneling VNC.
Why did you write this reply to my post?  I think you meant this for someone else's post in this thread advocating SSH.

Anyway, remove "-stunnel" from your x11vnc cmdline, but keep the "-ssl" option. Then use SSVNC or vinagre as your VNC viewer and you will get an SSL encrypted VNC connection.

---

### Post by B34ST1Y on 2010-09-08
It appears that removing the "-stunnel" option worked like a charm. Thanks so much for the help! :)   [SOLVED]

---

### Post by krunge on 2010-09-09
> **B34ST1Y said:**
> It appears that removing the "-stunnel" option worked like a charm. Thanks so much for the help! :)   [SOLVED]
Glad it is working.  Which SSL VNC viewer(s) did you decide to use for this?

---

