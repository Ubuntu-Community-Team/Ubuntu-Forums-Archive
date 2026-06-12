---
title: "Virtual box pc suite usb"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-06-27
Hi,
    I have installed latest version of vb from Oracle. Not from repositories.
OS is Lucid. Pc suite is installed and usb set up.

When I check the usb device tab from the guest (xp). It sees the the phone but it is faded and I can't get it to "see" it.
  Phone is Nokia 5310 Xpressmusic.

Any  help would be appreciated. Apparently the drivers are in the pc suite program itself and I have tried manually installing them. the cable is a Ca-101.

---

### Post by Vege 4wd on 2010-06-27
Bump

---

### Post by Vege 4wd on 2010-06-27
Bump. Anyone willing to have a go?

---

### Post by b0b138 on 2010-06-27
Check and make sure you are a member of the vboxusers group. Logoff and back on to take effect if not.

Under the details for the guest, goto the usb section and add the filter for the usb device you want to use.  Yes, it must be plugged in. No the guest can't be running yet.

---

### Post by Vege 4wd on 2010-06-27
I found a link and copied it for future reference.

  	 	 	 	 	 	  [IMG]https://answers.launchpad.net/@@/favourite-yes[/IMG][George Standish]("https://launchpad.net/%7Egeorge-standish") said on 2010-03-07:  
 First open a terminal and type "groups", is "vboxusers" listed there? If NOT, you will need to run "sudo adduser YOUR_USERNAME_HERE vboxusers". Then log out and log back in! Again run "groups" in a terminal - is "vboxusers" listed? If yes, continue -- if no, something went wrong with above step.
 Next still in a terminal run "sudo hald --daemon=no".
 Note when I run the "sudo hald --daemon=no" I get an error:
    Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
   Error binding udev_event socket: Address already in use
 But it works anyways.
 Then start VirtualBox as you normally would, and USB should work now.
 Good luck,
George
 [George Standish]("https://launchpad.net/%7Egeorge-standish") said on 2010-03-07:  
 Oh ya, the "sudo hald --daemon=no" will need to be re-run after every reboot, before USB will work in VBox.
 [jiehanzheng]("https://launchpad.net/%7Ejiehanzheng") said on 2010-03-08:  
 Hello George,
 Thank you so much. The result of `groups` is "jiehan adm dialout cdrom plugdev lpadmin admin sambashare vboxusers", "vboxusers" is listed there.
 I began to run `sudo hald --daemon=no`, then it solved my problem!
 Thanks! And will Ubuntu fix this "problem" in the future, how to make the "hald" startup by itself on system startup?
 [jiehanzheng]("https://launchpad.net/%7Ejiehanzheng") said on 2010-03-08:  
 Oh, I achieved that!
 I just added `hald --daemon=yes` into '/etc/rc.local', and it now run automatically on startup! Other Lucid users may try this way.
 Thank you very much!


Worked for me.:popcorn:

---

### Post by b0b138 on 2010-06-27
all the sudo hald --daemon stuff if not necessary. Those solutions are 3 years. VB is a lot more mature now and doesn't need to be hacked as much as it used to

---

### Post by Vege 4wd on 2010-06-27
If there is anything else I would like to know cause I spent quite some time trying to work it out.

---

