---
title: "Problems after 10.04 upgrade"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by WiReIs on 2010-05-02
Hi, im quite new to Ubuntu, my first ubuntu OS was 9.10 which i loved and had no problems whatsoever with.. i have recently upgraded to 10.04LTS every thing was fine until i connected up my Fujifilm camera via USB so i could upload pictures onto my laptop, when i connect the USB from the camera in nothing happens, the system is not detecting my camera at all, can anyone shed some light on this for me..

Many thanks, Ross

---

### Post by Funnnny on 2010-05-02
Did you try importing via F-spot or Digikam ?

---

### Post by WiReIs on 2010-05-02
I tried opening using F-Spot

Opened F-spot > Import > Select Folder > Fuji Finepix S6500fd

Error message opens in window saying..

> Error connecting to camera

Received error "could not lock the device" 
while connecting to camera

---

### Post by Funnnny on 2010-05-02
Try open nautilus and unmount (click on eject icon) next to the device

---

### Post by WiReIs on 2010-05-02
how do i open nautilus? sorry ive been brainwashed with windoze all my life.

i tried to open via DigiKam.. same error message

---

### Post by sixthwheel on 2010-05-02
Places/Home Folder

---

### Post by totfit on 2010-05-02
Click on Home folder. Nautilus is just the file manager like Explorer in windows.

---

### Post by WiReIs on 2010-05-02
> **sixthwheel said:**
> Places/Home Folder

Thanks :)

the device is not showing though to eject or unmount.

It worked fine on 9.10 using F-spot

---

### Post by rathmullen on 2010-05-08
Anybody found a solution for connecting Finepix 6500 to 10.04

---

### Post by oldspammer on 2010-05-08
I have a different set of problems.

My Microsoft Serial Mouse with wheel (Intellimouse) seemed to me worked fine, but now, after upgrading from 9.10 to 10.04 often will not operate at all after doing a shutdown -r now command as root a few times.  I am using the rc.local method ( [http://ubuntuforums.org/showthread.php?t=1331499](http://ubuntuforums.org/showthread.php?t=1331499) ) that has the command inputattach --intellimouse /dev/ttyS0 .  It seems that somehow the mouse or its interface is not getting sufficient device re-starting instructions after a warm boot, leaving the device or the software drivers in some kind of hung limbo thinking that the device is not there or not properly responding or whatever.  My question of  [http://ubuntuforums.org/showthread.php?t=1464591](http://ubuntuforums.org/showthread.php?t=1464591) remains unanswered about how the serial mouse functionality configuration gets lost after the mouse is not plugged in during one or two reboots, but was working upon installation and sessions where it had not previously been unplugged...

My screen saver / power saver scheme is set to "power down my hard disk drives" after a fairly short time interval.  When I warm boot the system via root using the shutdown -r now command, the mainboard's BIOS hangs for a very long (perhaps indefinite) time looking at the disk drives that are in power saver mode even though the system BIOS has detected their existence and displayed the make / model number during its scan of the SATA bus.  Upon manually pressing Ctrl-Alt-Del during this BIOS hang looking at the disks, the system will subsequently not hang looking at the SATA disk drives until the next shutdown -r now command execution.  I don't think that this was happening prior to upgrading?  To solve this difficulty, it would be a simple matter to use a no wait version of a wake up command to each connected disk drive to facilitate a flawless reboot through the BIOS boot stages similar to how a cold boot would have woken up the hard disk drive devices.  Most of the Microsoft operating systems that I have used always seemed to have powered back up the hard disk drives that it had powered off during power saving mode kicking into action when a shutdown or a warm boot was initiated by the Administrator user.  Maybe the problem that I have encountered is why "they" do this?

The /etc/network/interfaces file was changed and my system upgrade or the upgraded system decided that my local LAN ip address should be used (192.168.4.x).  The system decided when I first started up FireFox that my computer used a proxy server (that I do sometimes use for blocking certain web sites) instead of using the ip address (24.x.x.x) that goes into my router out to the world through my cable modem.  I reverted back that configuration file, and also changed my FireFox not to use "system proxy settings" and set it instead to be "no proxy."

During the upgrade process, prior to rebooting, the ip configuration was changed live, and so my Samba shares went down sometime during the 6 hour upgrade processing.  I have not checked yet if Samba was broken during the upgrade processing.

During any boot up, my system hung waiting for user intervention instead of making a system log entry of the error / warning that there were disk drives being mounted in /etc/fstab that were no longer connected / powered up and so appeared missing.  The prompt on the boot up GUI screen was something to the effect of press S to skip or 'R' (or some other letter) to retry.  This design change is a bad plan because the entire computer's functionality may be frozen indefinitely waiting for the user to press 'S' on the console.  This would be like during a electric power interruption or unanticipated reboot.  It would be better to presume that the device is not plugged in or is temporarily powered off, and skip it automatically, but logging the event to the system log for later checking, etc.  In this way other computers networked to the Linux box would be able to resume access to its services without "a human being" having to sit in front of the console, watching the screen, then pressing 'S' repeatedly for each disconnected / powered off unmounted disk drive / dasds / DVD drives, etc, mentioned in the /etc/fstab file.  Temporarily, to solve this problem I had to go in as root and edit the /etc/fstab file and use '#' to comment out the errant lines (where the given device was unplugged or powered off).

---

