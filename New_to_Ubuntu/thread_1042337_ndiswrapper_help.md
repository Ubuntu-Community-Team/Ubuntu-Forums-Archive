---
title: "ndiswrapper help"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by iball8888 on 2009-01-17
When i try going to ndiswrapper id list, the page is blank so i do not know which driver to install.  My wireless usb adapter is the trednet TEW-644UB.  please i need help

---

### Post by anewguy on 2009-01-17
Do you have the Windows (non-Vista) drivers for it?

Dave :)

---

### Post by cariboo on 2009-01-17
Your device should work without having to use ndiswrapper, could you paste the output of:

```
sudo lshw -C network
```

in your next post. The above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

### Post by captian kangaroo on 2009-01-17
> **anewguy said:**
> Do you have the Windows (non-Vista) drivers for it?

Dave :)
are you asking for toshibas driver for win 32

---

### Post by iball8888 on 2009-01-17
> **cariboo907 said:**
> Your device should work without having to use ndiswrapper, could you paste the output of:

```
sudo lshw -C network
```

in your next post. The above command must be run in a Applications-->Accessories-->Terminal.

Jim

*-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:ee:2c:81:c3:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Also the other thing is that ndiswrapper is not installed on this comp.   Btw this Linux comp has no internet access i am using an xp laptop.  So how do i install it?  Al Synaptic is preinstalled...i heard you can use it to install ndiswrapper so i how do i do that?

---

### Post by iball8888 on 2009-01-18
alright so i figured out how to install ndiswrapper and then I took the Adapter's Cd and i took the xp drivers and put it on the computer then i made a new folder, called it "driv", and put the inf file into it.

Then i opened up the terminal and typed

cd ~/driv

sudo ndiswrapper -i rt2870.inf

installing rt2870 ...
couldn't find models section "Ralink" -
installation may be incomplete
couldn't find models section "ASUS" -
installation may be incomplete
couldn't find models section "Sitecom" -
installation may be incomplete
couldn't find models section "Conceptronic" -
installation may be incomplete
couldn't find models section "Planex" -
installation may be incomplete
couldn't find models section "D-Link" -
installation may be incomplete
couldn't find models section "AL" -
installation may be incomplete
couldn't find models section "Airlink" -
installation may be incomplete
couldn't find models section "Corega" -
installation may be incomplete
couldn't find models section "Gigabyte" -
installation may be incomplete
couldn't find models section "Sparklan" -
installation may be incomplete
couldn't find models section "SMC" -
installation may be incomplete
couldn't find models section "Arcadyan" -
installation may be incomplete
couldn't find models section "ZCOM" -
installation may be incomplete
couldn't find models section "ZyXEL" -
installation may be incomplete
couldn't find models section "EnGenius" -
installation may be incomplete
couldn't find models section "Philips" -
installation may be incomplete
couldn't find models section "Draytek" -
installation may be incomplete
couldn't find models section "AzureWave" -
installation may be incomplete
couldn't find models section "Accton" -
installation may be incomplete
couldn't find models section "AMIT" -
installation may be incomplete
couldn't find models section "Hawking" -
installation may be incomplete
couldn't find models section "Siemens" -
installation may be incomplete
couldn't find models section "Edimax" -
installation may be incomplete
couldn't find models section "AboCom" -
installation may be incomplete
couldn't find models section "BUFFALO" -
installation may be incomplete
couldn't find models section "Gemtek" -
installation may be incomplete
anthony@anthony-desktop:~/driv$ sudo ndiswrapper -l
rt2870 : invalid driver!
anthony@anthony-desktop:~/driv$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.




So..what happened?  did i do something wrong?

---

### Post by anewguy on 2009-01-18
Besides the .inf file, you also must have the .sys files in that folder as well.  While I haven't seen that error before, it's possible it is caused by the missing .sys files.

Before you do anything more, you will need to remove the invalid driver so that you can try ndiswrapper again:

sudo ndiswrapper -e  rt2870

Each time you want to try something different with ndiswrapper, be sure to do a list first, then remove any shown drivers via the above syntax.  You want to have ndiswrapper list return nothing before you start again.

Dave :)

---

### Post by iball8888 on 2009-01-18
the sys is in there.  I moved all the files from the whole folder.

---

### Post by iball8888 on 2009-01-18
I did it!!!  I was using the wrong drivers.  I was using the xp64 drivers so i used the 86 and it worked.  Now i am online.:popcorn:

---

### Post by error420 on 2010-03-22
> **iball8888 said:**
> I did it!!!  I was using the wrong drivers.  I was using the xp64 drivers so i used the 86 and it worked.  Now i am online.:popcorn:

Are you getting 802.11 N speeds or 54Mbps?

---

### Post by Vincenso27 on 2011-04-07
Please Help!

I am a total Linux noob.  I have been trying to get my DWA-140 working on Linux for 3 days.  I have tried everything and learned a lot in the process.  I have tried installing Linux drivers, but the "make" command never compiles properly.

I finally was able to get ndiswrapper to say that the rt2870 driver was successfully installed.  However, my DWA-140 still will not work in Linux.  I know that the stick is not broken.  It shows up in the USB device list but Linux will not detect any wireless interfaces.  I feel like the fix for this is simple, I just don't know it due to my noobishness.

Any ideas?

---

### Post by Hippytaff on 2011-04-08
Hi Vicenso27
 
You mightbe better off starting a new thread. If you do (which I recommend) post the wireless-results.txt generated by running the script found in the link below (wireless info script) people will be better able to help you because it will provide all the information needed to trouble shoot rather than ask you to type command after command into a terminal. 
 
when you post it, highlight the text and click the # button to wrap it in code tags to make it easier to read - it will appear like ```
this
```

---

