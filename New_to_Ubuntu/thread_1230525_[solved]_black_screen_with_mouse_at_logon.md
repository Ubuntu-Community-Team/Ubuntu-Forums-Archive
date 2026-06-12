---
title: "[solved] black screen with mouse at logon"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by fonque on 2009-08-03
I am a Linux n00b. I installed Ubuntu for the first time yesterday, after I broke windows (story unto itself). I was only able to use the alternate install for 9.04 since I could never get the desktop version to load. After the alternate install finished, I was able to reach the logon page. However, the logon page was completely black with only the mouse/cursur visible.
I assumed it was a video issue since I have an ati radeon 2600 HD video card installed.

I used the following how-to [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I was able to mount a usb drive from the command line and copy the files to the /desktop folder.

1. "sh ati-driver-installer-9-7-x86.x86_64.run --buildpkg Ubuntu/jaunty"
    first few tries did not work. I missed the first line to install all of the dependencies.

2. "sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb" 
(with full file names using the tab key)

skipped step 5 of the how-to - additional 64-bit instructions 

3. "sudo nano /etc/X11/xorg.conf"
	added the [driver "fglrx"] line

4. "sudo aticonfig --initial -f"
	failed

5. "sudo aticonfig --input=/etc/X11/xorg.conf --tls=1"
	tried this next and it failed.

I then rebooted my machine, which now would not even make it to the login screen.
It would just lock up with a little text "0" in the bottom left corner.

6. reboot and pressed "esc" to access the grub boot menu
   I accessed the terminal as root with networking

7. I tried to remove the driver using "sudo apt-get remove --purge xorg-driver-fglrx"
    that failed, I dont remember all of the errors I received, but one indicated that I needed to run
   "sudo apt-get install -f"    

8. "sudo apt-get install -f"
    received a bunch of text lines for things installing, and the files looked like they related
    to the ati fglrx driver.

9. then re-tried "sudo aticonfig --initial -f" and "sudo aticonfig --input=/etc/X11/xorg.conf --tls=1" and they both worked.

I rebooted again and could see the logon screen. I sucessfully logged in and was able to play around with the desktop for a little before going to bed.


why did I need to run the "sudo apt-get install -f" command if I am running a 32-bit version of Ubuntu?

---

### Post by wojox on 2009-08-03
-f = Fix

---

### Post by fonque on 2009-08-03
what did it "fix"?

---

