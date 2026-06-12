---
title: "login frame disappear, I can't login"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by lamier on 2011-05-05
[COLOR=Blue]I installed ARM develop environment from packages that come from internet. When I restart my PC the next day, everything changed. :(
After the dram sound, the screen(with Ubuntu 10.04 default background) and the mouse are shown, but where is the login frame. :confused:
I use Ctrl+Alt+F1 come to console, login my account, and then Alt+F7, but the screen is still like as much. 
I am begging good man's help. please.
this is my[COLOR=Red] .xsession-errors [/COLOR]file[/COLOR]
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=zh_CN.
Start IM through /etc/X11/xinit/xinput.d/zh_CN linked to /etc/X11/xinit/xinput.d/ibus.
GNOME_KEYRING_CONTROL=/tmp/keyring-8WrdWq
GNOME_KEYRING_CONTROL=/tmp/keyring-8WrdWq
SSH_AUTH_SOCK=/tmp/keyring-8WrdWq/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-8WrdWq

(polkit-gnome-authentication-agent-1:3812): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3812): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:3816): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x8d44ce8'
Unable to find a synaptics device.
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/joe/.compiz/session/1038e7dea6f976aa10130408331813597500000037260030"
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
evolution-alarm-notify-Message: Setting timeout for 38250 1304121600 1304083350
evolution-alarm-notify-Message:  Sat Apr 30 08:00:00 2011

evolution-alarm-notify-Message:  Fri Apr 29 21:22:30 2011

** (update-notifier:3976): DEBUG: Skipping reboot required
/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /home/joe/%E4%B8%8B%E8%BD%BD: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Discarding: 1 over 2
Discarding: 1 over 2
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

Error: May not be a PDF file (continuing anyway)
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
Error loading document: File type ????? (text/plain) is not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /media/01F5-01F5__/%E6%88%91%E7%9A%84%E6%96%87%E6%A1%A3/S04/The.Big.Bang.Theory.S04E08.WEB-DL.720p.DD5.1.H.264-jhonny2: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;

(totem:16173): GLib-GObject-WARNING **: value "10752000" of type `guint' is invalid or out of range for property `connection-speed' of type `guint'
&#36825;&#26159;&#36816;&#34892;&#22312; Linux &#19978;&#30340; SMPlayer v. 0.6.8 (SVN r3213) 

(totem:16207): GLib-GObject-WARNING **: value "10752000" of type `guint' is invalid or out of range for property `connection-speed' of type `guint'
/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /home/joe/%E4%B8%8B%E8%BD%BD/GTK+3.0/gtk+-3.0.0: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

&#36825;&#26159;&#36816;&#34892;&#22312; Linux &#19978;&#30340; SMPlayer v. 0.6.8 (SVN r3213) 
/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /home/joe/%E4%B8%8B%E8%BD%BD/GTK+3.0/pango-1.28.4: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Another synaptic is running. Trying to bring it to the foreground

(<unknown>:4047): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4047): Gdk-WARNING **: XID collision, trouble ahead

(<unknown>:4047): Gdk-WARNING **: XID collision, trouble ahead
/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /home/joe/%E4%B8%8B%E8%BD%BD/GTK+3.0/atk-1.30.0: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

/home/joe/.gnome2/nautilus-scripts/&#25171;&#24320;&#32456;&#31471;: &#31532; 36 &#34892;: cd: /home/joe/%E4%B8%8B%E8%BD%BD/GTK+3.0/atk-1.30.0: &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Nautilus-Share-Message: Called "net usershare info" but it failed: “net usershare”&#36820;&#22238;&#38169;&#35823; 255&#65306;net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#27809;&#26377;&#37027;&#20010;&#25991;&#20214;&#25110;&#30446;&#24405;
Please ask your system administrator to enable user sharing.

gnome-settings-daemon: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
evolution-alarm-notify: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
nautilus: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
gnome-panel: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 2095396 requests (2095380 known processed) with 125 events remaining.
gtk-window-decorator: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
fusion-icon: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
 * Detected Session: gnome
 * Searching for installed applications...
 * NVIDIA on Xorg detected, exporting: __GL_YIELD=NOTHING
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding
WARNING: pipe error (3): &#36830;&#25509;&#34987;&#23545;&#31471;&#37325;&#32622;: file ./src/chrome/common/ipc_channel_posix.cc, line 404

(gnome-panel:3809): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed

(gnome-panel:3809): GLib-GObject-CRITICAL **: g_object_run_dispose: assertion `G_IS_OBJECT (object)' failed
gnome-session: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
<unknown>: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
nm-applet: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.
update-notifier: Fatal IO error 11 (&#36164;&#28304;&#26242;&#26102;&#19981;&#21487;&#29992;) on X server :0.0.

```

---

### Post by lamier on 2011-05-05
can somebody give some advices?

---

### Post by leviathan8 on 2011-05-05
If you managed to get into a tty (CTRL + ALT + F1), simply login with your user and type the following:

```
sudo service gdm stop
```

and then:

```
startx
```

This should drop you into the desktop. If you've succeeded, you should disable the Login screen for a while, to see if the problem persists.
You can do this by accessing "Login screen" from the Administration menu, and clicking unlock, in order to be able to make changes, and then simply choose "Login as *username* automatically. Do not put any timeout.
Have a nice day.

---

### Post by lamier on 2011-05-05
> **leviathan8 said:**
> If you managed to get into a tty (CTRL + ALT + F1), simply login with your user and type the following:

```
sudo service gdm stop
```and then:

```
startx
```This should drop you into the desktop. If you've succeeded, you should disable the Login screen for a while, to see if the problem persists.
You can do this by accessing "Login screen" from the Administration menu, and clicking unlock, in order to be able to make changes, and then simply choose "Login as *username* automatically. Do not put any timeout.
Have a nice day.

Thank you for replying. I tried it, and the screen become gray,and stay in that status. I use Ctrl+Alt+F1 come into a tty again. this message fill all the screen.
```
No protocol specified
..
No protocol specified
..
No protocol specified
..
No protocol specified
..

```




could any one tell me what can I do next?

---

### Post by lamier on 2011-05-10
Please! Thank you very much!

---

