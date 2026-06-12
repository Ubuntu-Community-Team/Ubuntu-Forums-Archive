---
title: "micromax usb modem application not running"
date: 2014-08-12
forum: Networking &amp; Wireless
---

### Post by sachinwadhwa46 on 2014-08-12
hello.. 
i was able to install mmx 353w modem in /usr/local successfully.
but when i type command to run the modem it does not work 
here is a log ..

sachin@N411Z:~$ su
Password: 
root@N411Z:/home/sachin# /usr/local/MMX353W_3G_USB_Manager/USBModem
root@N411Z:/home/sachin# Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/local/MMX353W_3G_USB_Manager/java/jre1.5.0_15/lib/i386/motif21/libmawt.so: libXp.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at sun.security.action.LoadLibraryAction.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Unknown Source)
    at java.awt.Toolkit.<clinit>(Unknown Source)
    at java.awt.Color.<clinit>(Unknown Source)
    at javax.swing.plaf.metal.MetalTheme.<clinit>(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.getCurrentTheme(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(Unknown Source)
    at ch.randelshofer.quaqua.BasicQuaquaLookAndFeel.getDefaults(BasicQuaquaLookAndFeel.java:73)
    at ch.randelshofer.quaqua.LookAndFeelProxy.getDefaults(LookAndFeelProxy.java:195)
    at javax.swing.UIManager.setLookAndFeel(Unknown Source)
    at javax.swing.UIManager.setLookAndFeel(Unknown Source)
    at com.modem.phonepad.gui.ui.USBModem.main(USBModem.java:60)

root@N411Z:/home/sachin# /usr/local/MMX353W_3G_USB_Manager/USBModem.sh
root@N411Z:/home/sachin# Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/local/MMX353W_3G_USB_Manager/java/jre1.5.0_15/lib/i386/motif21/libmawt.so: libXp.so.6: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.loadLibrary0(Unknown Source)
    at java.lang.System.loadLibrary(Unknown Source)
    at sun.security.action.LoadLibraryAction.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Unknown Source)
    at java.awt.Toolkit.<clinit>(Unknown Source)
    at java.awt.Color.<clinit>(Unknown Source)
    at javax.swing.plaf.metal.MetalTheme.<clinit>(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.getCurrentTheme(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(Unknown Source)
    at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(Unknown Source)
    at ch.randelshofer.quaqua.BasicQuaquaLookAndFeel.getDefaults(BasicQuaquaLookAndFeel.java:73)
    at ch.randelshofer.quaqua.LookAndFeelProxy.getDefaults(LookAndFeelProxy.java:195)
    at javax.swing.UIManager.setLookAndFeel(Unknown Source)
    at javax.swing.UIManager.setLookAndFeel(Unknown Source)
    at com.modem.phonepad.gui.ui.USBModem.main(USBModem.java:60)

please help me out ..
or is there any other method to run the modem on ubuntu 14.04?

---

### Post by varunendra on 2014-08-12
Welcome to the forums Sachin!

There are some cautions related with the applications that come with USB Modems. You should be aware of these before trying to install these applications. Please read this post first -
[http://ubuntuforums.org/showpost.php?p=12945156](http://ubuntuforums.org/showpost.php?p=12945156)
and if you no more need to supply your login password while running commands with 'sudo', please fix it immediately as suggested here -
[http://ubuntuforums.org/showpost.php?p=13074564](http://ubuntuforums.org/showpost.php?p=13074564)

Now, to answer this -
> **sachinwadhwa46 said:**
> or is there any other method to run the modem on ubuntu 14.04?
..yes the native Network Manager program can be used to use your usb modem. But first, the system MUST detect it as a modem.

These devices have multiple personalities (storage, cd, modem etc.) and they need to change their 'mode' to modem before the Network Manager can recognize it and use it to create/use a "Mobile Broadband" connection.

To let us see your modem and whether it switched its mode or not, please do the following -

Remove the modem if it is plugged in > wait for about 10 seconds > plug it in > wait another 30 seconds > open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lsusb
dmesg | tail -40
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

