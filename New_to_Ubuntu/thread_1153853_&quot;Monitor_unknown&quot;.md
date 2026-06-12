---
title: "&quot;Monitor unknown&quot;"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by RobinScott93 on 2009-05-09
Hi,

I'm completely new to Ubuntu and any Linux operating system.  Today I decided to install Ubuntu and run it in VirtualBox.  The install went fine and now I am able to run Ubuntu.

However, I noticed that Ubuntu was running at a low resolution - it was just a small box in the middle of my windows desktop.  I maximises VirtualBox but Ubuntu was still small.  So I went into the Display settings in Ubuntu and tried to change the resolution.  However it says "Monitor unknown" and I am unable to change any settings.  The resolution is stuck at 800x600.

I have an nVidia GeForce 7900 GS graphics card and a Samsung monitor capable of displaying resolutions of up to 1680x1050.  Do I need to install a seperate nVidia driver inside Ubuntu?  I'm sorry if this is a completely stupid question but I really don't know where to start.  When I go to Hardware drivers in Ubuntu there are none installed.

Any help would be greatly appreciated.  Also remember I am new so please don't reply with a load of command line code without telling me what to do first.

Thanks.

---

### Post by Panzor on 2009-05-09
Hello, glad to see new blood hee hee heeee *cough* I mean. I think I can help :P.

I use VMware which offers a thing called "vmware tools" that you can install and it takes care of this sort of thing. Soooo I can't help you in the VirtualBox regard (though since VMware takes care of setting up the virtual "hardware," I'd guess that VirtualBox has a similar thing to take care of the resolution issue. 

You can *try* going to "Add/Remove" under Applications menu at the top left (its default location) of the screen, selecting "all available applications" from the dropdown box, and searching for "nvidia." You'll find some nVidia drivers for yourself, though I'm not sure if VirtualBox wants you to use nVidia drivers or VirtualBox drivers, if you catch what I mean.

All in all, you won't have this problem if you installed on a partition - and of course I recommend that :P - but that's one way I could see it fixed. Actually two if you count looking around for something akin to VMware's software you can install on the boxes, in VirtualBox. Good luck to ya, and I hope you enjoy Ubuntu :).

EDIT: forgot to turn off smilies...they bug me >_>.

---

### Post by Bölvaður on 2009-05-09
Please ignore the post above me. (glad to see new blood such as Panzor hee hee heeee)
Man Im funny -.-


Well to get to business you can stop thinking about installing drivers on a virtual machine as the hardware the virtualmachine isn't the one in your computer, but is like... virtual... -.-
Your other operating system is using the hardware and therefore is inaccessible to the virtualmachine, if you catch my drift.


To change the screen resolution:

[http://ubuntuforums.org/showthread.php?t=1153437](http://ubuntuforums.org/showthread.php?t=1153437)


note that to open the terminal you go to
Applications &#8594; Accessories &#8594; Terminal

---

### Post by carml on 2009-05-09
@ RobinScott93 
If you want to see the Ubuntu installation under Virtualbox at full screen size,you need to install the Guest Additions,so:
Start the virtual machine;
Log into the system;
Go to the terminal and type:sudo apt-get install build-essential.
Go to the second menù in the window of Virtualbox,the one called devices;
Choose the "Mount a image" option;
At this point you should notice a CD-Rom icon on the desktop of the virtualized Ubuntu.
Open it,there's something called VBoxLinuxAdditions-x86.run ,go to Applications->Accessories->Terminal and type there:
cd media/cdrom0.
So you changed to the cdrom,then type: sudo ./VBoxLinuxAdditions-x86.run;after a while you'll be prompted to reboot your virtualized system;
at the reboot you should be able to get a full screen window by pressing Ctrl+F. :)

---

### Post by Weebeegee on 2012-01-31
This is a problem I have been wrestling with for several days. All of the recommendations relative to xorg.conf, various updates and so on were to no avail. But one of the postings mentioned the difficulty that may arise from connecting the monitor via VGA. I have a Samsung S23A350H monitor that was working flawlessly and then would not support anything above 1024x768. Display said the monitor was unknown.

Then I remembered that I had reordered things on my desk including disconnecting my Belden switch. I connected the monitor directly to the computer and suddenly Ubuntu knew exactly what was connected. 

At that point I took each connection apart and put it back together carefully and full functionality was restored. 

This, of course, may not be the solution in all cases, but clearly, solid connections are needed for autodetection to work correctly.

---

### Post by oldos2er on 2012-01-31
Closed, necromancy.

---

