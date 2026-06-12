---
title: "Worked fine, then suddenly display problems"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by franklin_m on 2009-10-14
Hi,

I'm running Ubuntu Netbook remix (9.04 Jaunty). It's been running great for several weeks using the netbook desktop display.

Last night I was playing around and briefly put it into the standard Ubuntu desktop mode, then I switched it back. All appeared normal.

Tonight when I rebooted, all the information (clock, battery, network, weather, etc.) was missing from the top of the screen. No matter what I tried, I couldn't get it back.

I switched to the standard desktop mode, and all of the above showed up (except weather). When I switched it back to the netbook desktop mode, they all reappeared and worked normally...until I shut down and rebooted...

Then I'm back where I was before.

Any help would be appreciated.

Thanks,
Frank

[email]frank.mellott@earthlink.net[/email]{

---

### Post by franklin_m on 2009-10-14
An update. I logged off with it in the normal desktop display mode, not the netbook mode, and when I logged on again, there's no toolbars, nothing but the background screen. No toolbar, no menus, nothing but the wallpaper is visible. My only option is to shut down via the power button.

I tried boot via the recovery mode, same result.  Help would be really appreciated....

Thanks,
Frank

---

### Post by NE Key on 2009-10-14
Just had the same problem - when I tried the "classic" display of the NBR.
The only solution I could find was to re-install.

However you will be able to log in, in text only/command line mode - so it shout be theoretically possible to edit/delete some file which will throw you back into NBR display - but I don't know which one.

-----------

Got this from another thread;

sudo killall maximus

I re-installed but before switching to classic display I removed maximus from the start up list.

---

### Post by franklin_m on 2009-10-16
All,

Have tried the killall maximus and the sudo killall maximus, neither worked. Any other ideas?

Frank

---

### Post by ugm6hr on 2009-10-16
This might be worth try....

Try deleting all gnome settings:

In home directory, show hidden files.

Backup then delete all .gnome, .gconf and .nautilus directories.

Then reboot.

There is a bug in the netbook switcher which causes problems.

---

### Post by bondokan on 2009-10-21
Please help.
I own an Esus R2H UMPC, I downloaded and wrote the netbook remix .img file to 1Gb USB drive and all went well in live mode except (touchscreen, special keys, wifi, webcam image upside down).
I then went ahead to partion my drive 32Gb formatted and installed Netbbok remix. At first boot all went well except issues noted above. At second boot I get these messages below how do I proceed?
On my own I clicked OK for first message & Run in low-graphics mode for second message.

1. Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself <option> OK.
2. what would you like to do?
Run Ubuntu in low-graphics mode.
Reconfigure graphics.
Troubleshoot the error.
exit to console login.
<options> CANCEL/OK

Then I get this message.
There already appears to be an X server running on display :0.
Should another display number be tried? Answering no will cause GDM to attempt starting the server on :0 again. (you can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7. X servers usually run on console 7 and higher.)

---

