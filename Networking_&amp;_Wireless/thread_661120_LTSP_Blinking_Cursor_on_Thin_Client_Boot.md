---
title: "LTSP Blinking Cursor on Thin Client Boot"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by dfault312 on 2008-01-07
I'm trying to setup a thin client to boot from my dell, that I'm using as a server. I had it setup before, but I'm trying to redo it. When I boot the thin client, I get as far as the Ubuntu splash screen, with loading bar. But, when the loading bar finishes, I get a flashing cursor, and nothing else happens. Can anyone help?

Update: I disabled the splash screen, and the last message that I get before the blinking cursor is:
> alsa-util.c: device doesn't support 44100 Hz, changed to 44099 Hz. [ok]

Is that something with the sound card? I don't have any clue if that is even what is causing the cursor to blink. I need to have this thin client booting by monday when school starts. Can anyone help me?

---

### Post by vuul on 2008-03-27
I had this same problem. It turned out to be an xserver issue.
I was able to diagnose my client's xserver issue with LTSP by doing the following:

On the LTSP server machine:
```
sudo chroot /opt/ltsp/i386
```

Give your root of your clients a password with:
```
passwd
```

You have to then rebuild the LTSP image with:
```
sudo ltsp-update-image
```

(wait for image to build...)

Then restart your client

Now when you reach the blinking cursor, use CRLT+ALT+F1 to get a terminal login prompt. Then login as root with your new password.

Then navigate to /var/log
```
cd /var/log
```

Then view your xorg logfile:
```
less Xorg.6.log
```

I hope you will find the fault in the last lines of this logfile.

My specific error was because my thin client had a widescreen display and Xorg couldn't find an acceptable resolution.

I switched to a non-widescreen display and the client booted properly.

However, the no-resolution for the widescreen could probably be resolved with some xorg.conf tweaking...

---

### Post by cstuettgen on 2008-04-18
> **dfault312 said:**
> I'm trying to setup a thin client to boot from my dell, that I'm using as a server. I had it setup before, but I'm trying to redo it. When I boot the thin client, I get as far as the Ubuntu splash screen, with loading bar. But, when the loading bar finishes, I get a flashing cursor, and nothing else happens. Can anyone help?

Update: I disabled the splash screen, and the last message that I get before the blinking cursor is:


Is that something with the sound card? I don't have any clue if that is even what is causing the cursor to blink. I need to have this thin client booting by monday when school starts. Can anyone help me?

Just to add my experience with the blinking cursor on boot problem to the shared knowledge base.

I recently successfully built a test LTSP server on 7.10 (gutsy) using an old spare desktop as the server.  A few days later I built the production system on actual server hardware.  (Dual 3.0 GHz processors, 6 GB ram, dual 73GB 15K Scsi hd's  (hardware Raid 1 mirror), dual GB Nics, dedicated GB switch for ltsp traffic).   The first time I tried to boot a client connected to the production server, I got the blinking cursor in the upper left corner.

I scratched my head,:confused: - and Goolged the world for two days, trying to figure out why the same client would boot perfectly when connected to the test server but would get the blinking cursor when connected to the production server. 

I finally tracked the problem down to "user error".  Mine.  You see rather than "recreate the wheel"  I copied the working LTS.CONF file, as root, via a usb key, from the test system to the production server.  

When I finally realized the client was acting like it wasn't seeing the lts.conf file, I checked it's permissions.  Only root could see it!

After smacking my forehead for forgetting the obvious...:redface: -  a quick  CHMOD 0644 on the file and the client booted perfectly.

My attempt to save the 2 minutes it would have taken to create a new lts.conf file on the production server, cost me 16 hours of troubleshooting time.

Moral of the story.  Check the permissions on a file that needs to shared when you copy it.

Hope this helps someone else in the future. - :biggrin: - :biggrin: - :biggrin:

---

### Post by joehill on 2008-05-26
I'm having the same problem.  But I can't even get a login prompt using CTRL-ALT F1 to diagnose.  When I see the blinking cursor and press CTRL-ALT-F1, I see something like this:
> i8042.c: Can't read CTR while initializing i8042
then I get all the network settings info, then everything just stops.

I'm using a little thin client with an AMD Geode and embedded AMD graphics chipset.

---

