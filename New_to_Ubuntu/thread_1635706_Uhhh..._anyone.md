---
title: "Uhhh... anyone?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by zipteye on 2010-12-02
Welp...
I resized (shrunk) my C: drive through Windows 7 to make more room for ubuntu.
Installed ubuntu on what i thought was the right partition.
Clicked restart when it finished installing.
Now, it has never worked when I just click on restart, so I took the disc out and powered down the computer.
Booted it back up, and it showed a normall looking boot menu,
I chose the first windows one because I wanted to check if I had over written the Win 7 backup partition.

The I got this:

```

Windows failed to start. A recent software change might be the cause.
To fix the problem:
1. Insert your windows installation disc and restart
2. Choose language setting then click next.
3. Click repair your computer

Status:  0xC0000225

Info: The boot selection failed because a required device is inaccessible


```

Well, I dont have a windows 7 install disc.
I do have a windows repair disc.
Which hasnt helped. bootrec /fixmbr ... no dice
bootrec /rebuildbcd  ... no dice
Shows no image (No C:) through the repair disc.

Through the Ubuntu Live cd I can see all of my windows OS folders.
Ubuntu has already been installed, but no boot menu comes up, just that black screen with the windows error.

The partition tool from ubuntu fails with an error when running it from the Live disc.

Maybe no partition is marked as active... I dunno.

Help?

---

### Post by Quackers on 2010-12-02
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by zipteye on 2010-12-02
Well, when I got up today I threw in the ubuntu live disc and just used the basic disk partiton app.
The deledted the Ext4 partition.
Rebooted and windows came right up.
But... somehow my windows disc is all Dynamic Disk now instead of Basic.
 
?

---

### Post by Mark Phelps on 2010-12-03
> **zipteye said:**
> But... somehow my windows disc is all Dynamic Disk now instead of Basic.

It's been know to do that conversion if it thinks there are "too many" partitions on the drive.

Run the script that Quackers told you about -- so we don't have to GUESS what's on your drive.

---

### Post by Spike-57 on 2010-12-03
i had this problem a few times and ended up just starting again, ill keep my eye out and on this thread to see how it goes ;)

closest i came to a fix was to trash the linux partition then use the windows cd to re write the bppt files, its under the repair menu on disk, id go with the above tho less crude.

---

### Post by pricetech on 2010-12-03
A Windows PE disk would come it handy as well.  The tools are free from Microsoft.

---

### Post by madjr on 2010-12-03
windows is way too sensitive...

you scream at it a bit and it breaks sometimes :p

---

