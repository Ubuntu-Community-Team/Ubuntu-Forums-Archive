---
title: "problems with ATI video card"
date: 2011-03-26
forum: New to Ubuntu
---

### Post by taptap on 2011-03-26
I'm a total newb.  I don't know how to get my ATI Rage Mobility M3 AGP 2x to do anything other than VGA compatible mode.  Also, I can't get the video to output to through the VGA port once the desktop loads.

Using Ubuntu 10.10 Maverick Meerkat with GNOME desktop.

---

### Post by mörgæs on 2011-03-26
Hi, welcome to the fora.

This might help you:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by taptap on 2011-03-27
Thanks morgaes for the tip.  I followed the procedure at: 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") 
to remove and install the opensource ATI driver.  I am curious.  How do I confirm what driver ubuntu is using for video?

These are the commands I used:

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*   
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon    
sudo apt-get install xserver-xorg-video-ati   
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core   
sudo dpkg-reconfigure xserver-xorg

After doing this and rebooting it appears that the video performance is significantly better.  Screen paints are snappy.  I still do not know how to get video to my VGA connected LCD monitor.  I saw a bunch of posts on this, but I do not know how to make heads or tails of it.  Any more tips would be greatly appreciated.

Thanks.

---

### Post by rajeev1204 on 2011-03-27
Is this an old card? If yes then fglrx wont work for it ,by default ubuntu installs the open source driver for your card and for any ati card new or old.

Empty the xorg.conf file at /etc/X11/xorg.conf and then reboot.

See if you have proper output now.

---

### Post by taptap on 2011-03-27
Alright.  I am a little confused here.  I did an lshw to find the ATI video driver and this is what I got:

id:display
                   description: VGA compatible controller                 
product: Rage Mobility M3 AGP 2x                 
vendor: ATI Technologies Inc                 physical id: 0
                 bus info: pci@0000:01:00.0
                 version: 02                 width: 32 bits                 clock: 66MHz                 capabilities: agp agp-2.0 pm vga_controller bus_master cap_list                  
configuration: latency=32 mingnt=8                 
resources: memory:f8000000-fbffffff ioport:ec00(size=256) memory:fdffc000-fdffffff memory:fd000000-fd01ffff

No mention of driver (usually under configuration?).  What gives?

---

### Post by rajeev1204 on 2011-03-27
Yes that will list the hardware.

For driver you can try  glxinfo | grep render

install mesa-utils package if glxinfo command is not found.

---

### Post by taptap on 2011-03-28
results of grep render

direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 

I did not see a driver listed here.  I am confused.

---

### Post by taptap on 2011-03-28
Found this log file: .xsession-errors

contents:
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-DWj6uO
GNOME_KEYRING_CONTROL=/tmp/keyring-DWj6uO
GNOME_KEYRING_CONTROL=/tmp/keyring-DWj6uO
SSH_AUTH_SOCK=/tmp/keyring-DWj6uO/ssh

(polkit-gnome-authentication-agent-1:1288): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1288): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:1296): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1296): DEBUG: old state indicates that this was not a disconnect 0
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0
Initializing nautilus-gdu extension

(nautilus:1293): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
** (nm-applet:1296): DEBUG: foo_client_state_changed_cb
** (nm-applet:1296): DEBUG: foo_client_state_changed_cb
/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py:35: GtkWarning: Ignoring the separator setting
  self.builder.add_from_file(path)
** (update-notifier:1516): DEBUG: --security-updates-unattended: 0

** (update-notifier:1516): DEBUG: aptdaemon on bus: 0
** (update-notifier:1516): DEBUG: Skipping reboot required
WARNING:root:timeout reached, exiting

---

