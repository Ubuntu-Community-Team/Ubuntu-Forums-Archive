---
title: "need help quick!"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by benjaminlee on 2010-12-07
I installed ubuntu netbook edition on my toshiba laptop but i kept getting the kernel_thread_help error...
 
right now i installed it and it said that i needed to restart my computer... i clicked the restart button and now im at a page that says "please remove installation media and close the tray if any then press ENTER"
 
The first time i just took the USB stick out of the laptop and pressed enter and ended up at the kernel_thread_help error again... 
 
anyone know how to get around this??
 
i really need help... i have no idea what close tray means

---

### Post by albert s on 2010-12-07
I think you may need to press enter then while the computer is in shutdown for a brief period remove the stick.
BUT,
please wait for someone more knowledgeable in these things to confirm.

EDIT,
the OS doesnt know you are using USB rather than a normal CD drive.

---

### Post by benjaminlee on 2010-12-07
what i did was i left the stick in there and pressed enter and i still get the kernel thread help thingy..
 
i honestly just want to go back to windows 7 at this point... there's no ubuntu support available on the phone and that's what i really need right now.. :( im so frustrated i've been working on this problem for over 12hours

---

### Post by albert s on 2010-12-07
did you check the MD5sum before you installed.?
and did it run OK live.?
you need to either remove the boot device or change the boot order between booting and re-booting.

---

### Post by Quackers on 2010-12-07
What happens if you remove the usb stick and then reboot?

---

### Post by benjaminlee on 2010-12-07
> **Quackers said:**
> What happens if you remove the usb stick and then reboot?
 
i still get the kernel_threaD_help

---

### Post by benjaminlee on 2010-12-07
> **albert s said:**
> did you check the MD5sum before you installed.?
and did it run OK live.?
you need to either remove the boot device or change the boot order between booting and re-booting.
 
I did change the boot order from USB to HDD and it still didnt work.. i get the kernel thread error every single time. 
 
well there's an option for me to select which one i wanna do "recovery mode" etc.. but i still get the kernel_thread_help no matter what...
 
i've been up way too long trying to fix this... going to get some food please help me fix this... i REALLY dont want to go back to windows... i've read books on ubuntu and so far there is no way to fix this problem

---

### Post by Quackers on 2010-12-07
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by benjaminlee on 2010-12-07
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```
 
This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
I cant open up terminal from the applications folder... I am able to get an active internet connection and able to download stuff but i cant open up terminal.. i have no idea where to even type that sudo bash ~/ thingy...
 
but i see terminal in the applications folder but when i click to open it nothing opens

---

### Post by zipteye on 2010-12-07
Power the computer down by holding down the power button.
Wait till the hard Drive spools down. (15 seconds or so)
Power the computer on.
Does it show a boot menu?
If so, choose Memtest.
 
There's a possibility that the culprit is bad RAM.

---

### Post by Quackers on 2010-12-07
Does pressing ctrl+alt+t open a terminal? Check behind the firefox screen :-)

---

### Post by benjaminlee on 2010-12-07
okay im able to get terminal working but there's a problem...
 
when i go to the top right corner and i try to put in my password it says its wrong...
 
someone tried helping me with it, and whenver i put in sudo bash etc it wouldnt work.
 
I did manage to shutdown via the sudo bash shutdown now code or whatever and it did work but when it restarts it automatically goes back to the kernel_thread_help thingy

---

