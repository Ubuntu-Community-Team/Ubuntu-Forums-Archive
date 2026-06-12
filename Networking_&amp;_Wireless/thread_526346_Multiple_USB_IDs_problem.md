---
title: "Multiple USB IDs problem"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Sean_0 on 2007-08-15
Hello everyone,

I haven't seen this question posted in either the documentation or the forums and I was hoping maybe someone had run into this problem before.

I've been trying to my USB wireless adapter (Trendnet TEW-504UB) to work with my ubuntu system.  I've gone through a number of the forums and it seems I need ndiswrapper.  It's all installed and I've gotten the proper windows drivers.  My problem is that when I plug the adapter in it will sometimes show up as one of three (usb) IDs:
lsusb
   ID: 157e:3602
   ID: 157e:3600
   ID: 157e:3502
each of these IDs starts up different drivers, but only ...:3502 works properly as a wireless adapter should, but most of the time when plugging in the adapter it shows up as 3602 (it's happened only one where 3502 popped up, that's how I know it works).

My question, in two parts, is: How can I get the USB to identify the adapter as the 3502 version? and how can I set it up to do it automatically everytime I boot up, so at if I unplug the adapter, the net time I plug it in it goes directly to the correct driver ID?

thanks in advance
Sean_0

---

### Post by noob12 on 2007-08-16
It sounds like you're using ndiswrapper and the Windows driver, so you can try this method.

The basic idea is to find the .inf file and edit it to include the other USB IDs.
You may be able to do this directly in the installed /etc/ndiswrapper windows driver subdir,
or you may have to reinstall the windows driver into ndiswrapper with the modified .inf.

Bluefightingcat over on this thread [http://ubuntuforums.org/showthread.php?p=3199270](http://ubuntuforums.org/showthread.php?p=3199270)  used a similar approach, though not in the multi-id case but on an id mis-match case (using an alternate driver recommended for the device).  Any closet Windows experts out there might have more to pitch in.

Attach the .inf file for concrete edit suggestions from me and others.

**Note:** For people using a linux native driver, the mapping files are in /lib/modules/*yourkernelversion*/.  I'm not sure if there's a way to augment these by adding files elsewhere in /etc.  Tips from linux experts for that case invited.

---

### Post by Sean_0 on 2007-08-18
Thanks for the reply.
I tried what you mentioned. Added an entry in the .inf file. Sadly it didn't work.
I also tried ndiswrapper -a DevId driver, which is meant to link an installed driver to a different device, that didn't seem to work either.

I installed ndisgtk yesterday and it had the wifi adapter working right from the get go.  Although it didn't list the driver in the 'installed driver' box when I added it.  Everything worked up until I rebooted and the adapter switched back to using the 157e:3206 ID.
It seems that for whatever reason it randomly chooses 157e:3205 ID for whatever reason, once that happens it works perfectly.

I'm going to try one more thing.  When I used ndiswrapper -a command it created a soft-link to a different ID, but one that uses the same driver.  I'm going to try to create a soft-link to the 3205 ID.  If that doesn't work I was wondering if someone knows how to 'force' the adapter to use a specific ID or when the ID appears have the computer interpret it as another ID?

thanks again
Sean

---

### Post by noob12 on 2007-08-18
This seems to be a bug/limitation.  USB devices can have multiple ids and "personalities".  It seems like what happens is that the kernel isn't enumerating the whole list but taking just one.  Which one you get seems to be somewhat arbitrary.  

I'm a bit surprised that the .INF editing didn't work for you though since some other users have reported it to work, though not in exactly the same situation, admittedly.

When you install the driver into ndiswrapper with the edited inf, you should get .conf files in the directory /etc/ndiswrapper/*drivername* (where *drivername* is the name of the windows driver); I think you should see one prefixed with each vendor id for each of the vendor ids appearing in the .inf.  Do you see this?

---

### Post by Sean_0 on 2007-08-18
update:
Tried changing the soft-link to point to the proper ID that works with the wireless adapter.   It didn't work.

Noob12:
yes I do see the files for each vendor ID.  I'm going to try going through the .INF file again and make sure I didn't miss anything.

---

### Post by Sean_0 on 2007-08-18
Don't know what to say.  It's still not working.
Tried changing around the .inf file with no success.

my output for 'ndiswrapper -l' is: (the net5523 is the new driver with the new device ID added)
net5523_new : driver installed
                       device (157E:3206) present

device 157E:3206 is the device it is detecting and present, but isn't working.
net5523 is the driver that does work when the ID is 157E:3205

I've added the net5523 if anyone wants to have a look.  I've commented out the change I made to get it to read the 3206 USB device.
```
[Atheros]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; Atheros
%ATHER.DeviceDesc.5523%  = ATHER_DEV_5523.ndi,    USB\VID_157E&PID_3205
;%TEW-504UB%                    = ATHER_DEV_5523.ndi,      USB\VID157E&PID_3206
%ATHER.DeviceDesc.5523g% = ATHER_DEV_5523.ndi,    USB\VID_157E&PID_3006
```
I'm stuck, it says that it accepts the new device ID with the driver, but it doesn't 'use' the device.  I'm still thinking the answer might involve having to 'force it to use it's other ID if that's even possible.

thanks,
Sean

---

### Post by noob12 on 2007-08-19
You said
> 
I've commented out the change I made to get it to read the 3206 USB device.
...
;%TEW-504UB%                    = ATHER_DEV_5523.ndi,      USB\VID157E&PID_3205
...


I notice that your commented line has the wrong product id value 3205.  The last column should be
USB\VID157E&PID_3206 to match the device id you indicated 157E:3206.  Maybe this is just a typo in the posting and wasn't in your file before you had it commented out.  If it was, then fix it and try again.  I would use the same reference %ATHER.DeviceDesc.5523% in the first column as well.
Basically you want a copy of the line with just the one digit changed in the device id column.

I'll be gone from the forum for the next week, so I won't be able to respond during that time. Good luck.

---

### Post by Sean_0 on 2007-08-19
Noob12: Thanks for all your help so far.
It was just a typo, I was using my windows computer to type the message.  I think I may have also given an unedited version of the file when I uploaded.

When I originally told you it didn't work had copy and pasted the line with the one digit difference.  The reason it's been changed to %TEW-504UB.....etc% is I found BlueFightingCat's HOW-TO with an example of his hacked .inf file.   I was trying to edit mine to resemble his but all his does is add the same settings under new headings which really shouldn't matter if they all access the same data. (And it didn't work).  Going to see what I can find about USB device IDs.

---

