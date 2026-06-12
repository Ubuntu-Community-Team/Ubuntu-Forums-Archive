---
title: "Sierra Wireless 881 USB, modem not found at /dev/ttyUSB0 !!!"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by capsid on 2008-01-12
I found this guide here:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076)

When I do "modinfo sierra" the driver is located, but my problem is that the device doesn't seem to be located at /dev/ttyUSB0, or /dev/usb/ttyUSB0, or /dev/modem...How would I tell where it is located?

AT&T was worthless when it came to answering my questions. They couldn't tell me what my username and password are, though I do know the phone number of the device. I will keep experimenting and let you know what I find out, but if anybody has experience with this particular card and AT&T, I'd love to hear what you did to get it to work!

I saw some other threads about Sierra Wireless cards, so I think I can guess username and password, I just have to figure out how to tell where the modem is located in /dev

Thanks!!!

---

### Post by capsid on 2008-01-12
I found this:
[http://ubuntuforums.org/showthread.php?t=633869](http://ubuntuforums.org/showthread.php?t=633869)

So i thought the modem would show up if I did
dmesg | grep sierra

but no luck.  So I guess the first thing I need to do is get it to show up in there.  It shows up in lsusb.

Maybe I will try recompiling the kernel with the drivers from sierra?  That seems counterintuitive because they imply that you don't to do that if modinfo sierra returns a positive result...

---

### Post by capsid on 2008-01-14
I followed the Master Kernel Thread:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

...to compile a 6.23 kernel which is supposed to support the Sierra Wireless 881U.  After I did that, the modem did show up in dmesg, but there are a host of other problems that I don't feel like dealing with (wireless, nvidia, etc).  Ubuntu strongly reccomends that you do not use a custom kernel unless you have the time and knowledge to keep your system functional as you receive upgrades.  I wonder why you can't get the 6.23 kernel as an apt package?  

At any rate, I would venture to say that this card is not worth using with Ubuntu unless you have plenty of time to tinker.  Can anybody suggest a different modem that works with Ubuntu?  USB is preferred over PCMCIA.

Thanks!

---

### Post by mistadman on 2008-01-28
Here is my small contribution to the open source community! I patched the sierra.c module to included the AT&T 881U 3G Modem. Just untar and make. I also included a basic PPP script. Before you run make make sure you have 'sudo apt-get install build-essential'. If you have any questions, I will do my best to help.


By the way this should work with kernel  2.6.18 or greater. I'm running ''2.6.24-5-generic". Have fun!

---

### Post by OMEGA303 on 2008-01-31
hello mistaman ,

        i have a friend that have this Sierra Wireless 881 we are new to ubuntu, the problem is that he dosent have a internet conection or wires he only have this card can you splain step by step how to install it i have read this treat , [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076card](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=1076card)  but i dont now how to do this or him i can download the packege for him but how to install it in his computer  any help i will I really apriciate need the step by step guide  the problem is that we dont know  how to install sierra.tar once i dowload the pakege how unzip and were to put it  i have try for a couple of days but i have no clue on how to do this thank you have a nice day.

---

### Post by mistadman on 2008-02-02
I'll try. If something goes wrong, or I miss a step someone let me know. Here goes...

1.Make sure you have installed the necessary development files. You will need the :


linux-headers: These are the core Linux Kernel Header Files that are used to to compile kernel modules.
build-essential: This is the command that is used with the "apt-get" command to install core development files

Ubuntu makes it easy by running this command: "apt-get install build-essential linux-headers-`uname -r`-generic" (type everything between the quotes). This will install the necessary file needed compile and install the custom sierra module.


2.Copy the attachment in this post to your hard drive; preferably to you home dir (~/). Expand the tar package by running: "tar -xf sierra.tar" (Or if you prefer you can expand using the Gnome GUI) The contents of the package contain:
    Makefile: Used to help compile the Sierra Module
    sierra.c: The module driver code
    sierra.patch: Contains the code used to patch (modify) the original kernel module code so that the 881U will work. (Provided for information purposes only)
    881u/881uchat: pppd script is used for telling Ubuntu (or more specifically pon) how to make a data connection to your ISP/Cellular provider
    
3.Make sure that serria.c and Makefile are in the same folder and run the command: "make". If you don't get any errors, assume the command was completed successfully. (What we have just done was compile source code (human readable text programing langauge) in to a kernel module (machine language). The file sierra.ko will be created. (The next step will automatically install the file into the correct directory)

4.Next run the command: "sudo make install". At this time you will probably will be presented with a password prompt. Just type your password. (You are prompted for a password because this command copies your complied driver to a directory that is owned by "root")

5.If all goes well, you will simply need to plug in your 3G USB Adapter (881u). You can verify that the driver was loaded successfully by running the command: "dmesg". In the output look for something like this:

```
[   22.976866] usbcore: registered new interface driver usbserial
[   22.976891] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   22.976968] usbcore: registered new interface driver usbserial_generic
[   22.976971] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   23.016740] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[   23.016764] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[   23.016805] sierra 3-2:1.0: Sierra USB modem (3 port) converter detected
[   23.018568] usb 3-2: Sierra USB modem (3 port) converter now attached to ttyUSB0
[   23.018642] usb 3-2: Sierra USB modem (3 port) converter now attached to ttyUSB1
[   23.018712] usb 3-2: Sierra USB modem (3 port) converter now attached to ttyUSB2
[   23.018724] usbcore: registered new interface driver sierra
```

What you should see is that the driver has attached to ttyUSB# (# = any number). In my example it attached to ttyUSB0, ttyUSB1, and ttyUSB2.

In my case ttyUSB0 is the modem device we will be configuring. If for some reason your output doesn't look similar, please restart you computer; it could be that the original unmodified driver module is loaded in memory. (If you are up for typing more command lines, you can type: &#8220;sudo modprobe -r sierra&#8221;. This command tells the Ubuntu to unload the driver if loaded. You can also type: &#8220;lsmod&#8221; to get a list of loaded module drivers. &#8220;lsmod&#8221; can be used to determin if the driver modules is loaded or not. If and once the sierra driver is unloaded, you can now type: &#8220;sudo modprobe sierra&#8221; (without the -r) to load the (hopefully) new sierra driver. Or like I said earlier, you can just restart your computer!)



!***! The next commands involve files (881u and 881uchat) that you will most likely need to be edited so that they will work with your cellular/3G data provider. See: [http://www.google.com/search?hl=en&q=pon+chat+scripts+ppp&btnG=Google+Search](http://www.google.com/search?hl=en&q=pon+chat+scripts+ppp&btnG=Google+Search) for more information (Google is your friend).

6.If all goes well you will now need to copy the file 881u to the &#8220;/etc/ppp/peers&#8221; directory by typing the command: &#8220;sudo cp 881u /etc/ppp/peers/&#8221;. Make sure you are in the directory where the &#8220;881u&#8221; file is located.

7.Next copy the file &#8220;881uchat&#8221; to the &#8220;/etc/chatscripts/&#8221; directory by typing: &#8220;sudo cp 881uchat /etc/chatscripts&#8221;

8.Last but not least type the command &#8220;pon 881u&#8221;. And vola! Your connected!




CAVEATS: All command must be typed in the console. The files: &#8220;881u and 881uchat&#8221; will need to be edited to work with your cellular/3G data provider. This could probably be a whole lot easier with the right software added to your OS/Distribution. For me though, I am running the latest development version of Ubuntu, and as far as I know there is know easier way that I know with the default install of Hardy.

If I can help you further please let me know and I hope you find this information useful. Thanks!

---

### Post by Jalke on 2008-02-07
I've been using a Sierra Wireles 595 AirCard.  I got it working after a bit of reading up and tinkering.  Worked great for a number of months.  However, for some reason it stopped working a couple of days ago.  I just don't know how to get it going again.  

It won't detect the modem for some reason.  When I type "lsusb" I can see it connected to the usb port.  However, using the command "sudo wvdialconf /etc/wvdial.conf" the modem isn't detected.  
There's no /dev/modem or /dev/modem/tty0 anymore (which was the original location).  I think it has to do with this, but I'm not sure, let alone how to fix it.  How can I find out the location of the modem? Or how can I assign one, if that's the problem?  The output of "dmesg" shows no reference to the modem.

Any ideas?  Thanks a lot.

---

### Post by Jalke on 2008-02-07
I figured it out!  I reinstalled the driver.  Something must have gone wrong with it, because now it's working again!  :guitar:  Why didn't I try that straight away instead of wasting two evenings of my life...?

---

### Post by mistadman on 2008-02-07
Jalke, glad to see you have figured it out! Did you have to recompile the driver? If so, just remember that anytime you receive a kernel update you will have to do this.

---

### Post by Jalke on 2008-02-08
Sorry, I'm one of the noobs: I'm not too sure what recompiling is.  I used 'make' and 'make install' on the driver file (module?).  I downloaded a whole bunch of automatic updates, which is probably what mucked things up.  Thanks.

---

### Post by landtodd on 2008-05-28
I haven't worked thru all of this yet, but at the outside, **thank you** for your generosity.  I have the same 881u, and this is the  "last frontier" before making my Cloudbook (now with Ubuntu 8.04!) my primary laptop and indispensible traveling companion!  Thanks again.  Karma!  Points over here!

---

