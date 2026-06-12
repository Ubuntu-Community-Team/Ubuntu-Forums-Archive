---
title: "Newbie wishes to install wireless usb drivers"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by anotherposter on 2009-10-29
Hi

I have an edimax ew-771UTn usb adapter.  I have a PC that dual boots.  I got wireless working without much bother in XP.  But I prefer using Ubuntu for web browsing because it seems to run much faster than XP on this somewhat outdated machine (XP is like swimming through treacle).

But while the usb adapter has linux drivers ('for the 2.6 Kernel) I'm a complete newbie and can't understand the instructions for installing it.

Would it be possible to get Ubuntu to download and install the drivers automatically and hence avoid all this, if I were to put it on-line in wired mode and tell it to look for hardware drivers?

Instructions are appended below 

I think I've managed step 1

Presumably in step 2 I have to change the kernel number to whatever is correct for 9.04?

In step 3 what are gcc and ld and compiler flags?

what is all that about wpasupplicant?  No idea what that is.

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
    ** Build for being controlled by WpaSupplicant with Ralink Custom Event
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make                                    # compile driver source code

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta

---

### Post by Talon2 on 2009-10-29
What version of Ubuntu are you using?

Have you tried plugging the adapter in? (Based on what you said I'd bet that this device is already supported in Ubuntu 9.04 and 9.10.  It should autodetect and you shouldn't have to do anything).

---

### Post by anotherposter on 2009-10-30
Using 9.04.  Tried plugging device in, nothing happens, hardware manager says no proprietary drivers on system, doesn't seem to be any other obvious way to install a driver.  Tried again with wired internet back on, still nothing seems to happen.  Perhaps will upgrade to 9,10, though not sure I want to spend all that time right now.

---

### Post by anotherposter on 2009-10-31
Hmm, OK, having installed the application called something like 'wireless radar', I find that application does show the local networks, including mine.  So the device is actually working under Ubuntu, which is good.  But I guess my issue then is not knowing how to proceed from there.  This app seems to want me to tell it where to find the 'WPA driver'.  What does that mean exactly?  I need to set it to use WPA2-PSK.

---

### Post by ugm6hr on 2009-10-31
These Edimax RT usb devices should "just work" on Ubuntu 9.04.

There will not be any drivers listed in "Hardware Drivers" since they are open source (i.e. not proprietary).

I am uncertain re: WPA2 support though.

With Network Manager, you should be able to see your network access points too - do you know how Network Manager works?

---

### Post by bubbles99 on 2009-10-31
i think its all under the same driver for WPA (??????)

---

### Post by anotherposter on 2009-11-02
OK, this is a bit tricky because I have to quit Ubuntu and reboot in windows in order to access the web to post here, and then go back to Ubuntu to try things.

Network Manager seems to report it as something like 'unknown device ra01'.

I searched this forum and found a post saying to try something like wext(? - I forget now) in the box where it asks for a driver.  But a further problem is it (wireless radar or whatever its called) won't let me type enough characters to enter the password.  Does this mean it wants the hex form rather than the passphrase I use in windows?  Not sure I know how to get the hex form.

---

### Post by ugm6hr on 2009-11-03
Given 9.10 is out now, why not just try that?  The latest kernel drivers may have solved your problem (although I have no idea if that is the case or not).

If it doesn't work, post the output from:
```
lsusb
lshw -class network
```

You can cut and paste the output into a text file to upload from XP.

---

### Post by anotherposter on 2009-11-04
Hmmm, having switched back to a wired connection to install 9.10 I now find the wired connection no longer works (that is, before even installing 9.10, am still on 9.04), Ubuntu just tells me its 'disconnected' network manager isn't running and I can find no way to get it going again.  It can 'see' the ethernet port, but refuses to use it.  Lan light on modem doesn't light.  Switched back to XP and it works fine.   No idea what to do now.

---

### Post by ugm6hr on 2009-11-06
Why not just start from scratch?

Use the 9.10 Live CD to just install it.  Then connect the wired LAN and reboot and see if it works.

If you dual-boot and LAN doesn't work, it may be becasue XP is set to disable networking at logoff.  See the Wifi help link below - point number 9.

---

