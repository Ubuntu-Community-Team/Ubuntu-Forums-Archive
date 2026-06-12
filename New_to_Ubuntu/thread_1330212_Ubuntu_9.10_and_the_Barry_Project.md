---
title: "Ubuntu 9.10 and the Barry Project"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Daughain on 2009-11-18
Another newb, and hopefully someone here has dealt with my current issue. I am having trouble installing Barry for BlackBerry on my 9.10 box, and apparently need a step-by-step how-to to get it running. From my research everything is released for a 'build' in Karmic. I just don't seem to know enough to do this. Any and all help will be appreciated. BTW, what is a 'build' anyway?

---

### Post by kimda on 2009-11-18
This program is allready in the repositories. So you should be able to install it via Ubuntu software center or synaptic or terminal. No need to compile it yourself.


sudo apt-get install barrybackup-gui

---

### Post by AJROKR on 2009-11-18
I had some serious trouble with 9.10 (Dont know 32 or 64) must be 32..

My 9.04(32bit) was working perfectly with my laptop along with XP( I have dual os)

Two days back i updated to 9.10 from 32 bit 9.10 and facing problem since then.

Everything is working perfectly except one...and i.e. i am not able to shutdown the system completely

Then i had to remove ubuntu from my laptop. i dont mind making my laptop to run only ubuntu...please help on this 
My system is Levnovo core 2 duo, 1 GB RAM ,160 GB SATA, DVD RW etc etc. Model no 77579RQ

The message i got was this....during shutdown...

Stopping ClamAV Virus databse update freshclam
Shutting down ALSA
Asking all remaining process terminate
Deconfiguring network interface
Deactivating Swap
1635.324526 Buffer I/O error on device loop0, logical block 2137453

What i have to do to rectify this.....

Looking forward for your reply...


Regards,
Anoop

---

### Post by Daughain on 2009-11-18
kimba: Thanks, sorta. I have already installed all the files like that, yet I still cannot find any way to access the gui. I figured I still needed to compile something, hence my OP. I may slap myself soon...Do I need to reboot after the Barry install for some reason?

AJROKR: Thanks for trying to hijack my thread.

---

### Post by AJROKR on 2009-11-18
i was not trying to......i thought i cant post problems on 9.10 here...sorry anyway..

---

### Post by kimda on 2009-11-18
Odd. It doesnt make a new menu item in gnome. Well...here's the binary. If you run it in the terminal it will run. 

/usr/bin/barrybackup

You can make a new menu item yourself (rightclick mouse on the application text and select edit menu - add new application in appropriate category). Unfortunately I do not have a blackberry to test it for you.

---

### Post by kimda on 2009-11-18
AJROKR make a new thread with your questions. People coming here will be looking for problems with Ubuntu and the Barry project.

---

### Post by Daughain on 2009-11-18
Ok, looks like I still have work ahead of me. That string helps, as now I can at least run the app, now just need to get it to recognize the phone, or find out what my usb error is. Thanks again, kimda

---

### Post by laughlin.bill on 2009-11-19
I've had similar problems with barry and karmic 9.10.  Everything seemed to be working fine on jaunty 9.04;  now, I'm getting all sorts of write errors on the BlackBerry client when trying to sync large amounts of data (I have around 1800 contacts).  Any suggestions?

---

### Post by natrone on 2009-11-19
Is Barry available for 9.04 in the repositories?  Or, do I have to build?  How reliable is Barry for syncing your BB.  There were programs for my Palm, i.e. jPilot, but they were not reliable at all.  FYI, for syncing Calendar and Contacts ONLY on the BB Google offers GoogleSync.  It syncs OTA and is quite reliable.  I love it.  The only thing keeping me tied to windows is my BB and Ipod Touch.  I would love to see the day they release iTunes and Desktop Manager for Linux.

---

### Post by Daughain on 2009-11-20
Palm appears to be natively supported in 9.10, and if I can ever get barry organized under Karmic, I'll let ya know. Yes, 9.04 is still in the repositories, and if I remember correctly, you wont need to build it yourself, just install. No polite comments available for the ipod, though. =)

---

### Post by zappadragon on 2010-01-12
When I try to run barrybackup in the terminal I get an error (-110, No error): Timeout in usb_bulk_read. Anyone got any ideas?

Thanks

---

### Post by zappadragon on 2010-01-12
OK so I got barrybackup to run once but now I can't run it again and I get the same error. So I browsed to /usr/bin and double clicked barrybackup and it worked fine but now it will not work again.

---

### Post by zappadragon on 2010-01-13
> **zappadragon said:**
> OK so I got barrybackup to run once but now I can't run it again and I get the same error. So I browsed to /usr/bin and double clicked barrybackup and it worked fine but now it will not work again.

Man this is killing me I can't get it to backup

---

### Post by chitowner2 on 2010-04-18
> **kimda said:**
> Odd. It doesnt make a new menu item in gnome. Well...here's the binary. If you run it in the terminal it will run. 

/usr/bin/barrybackup

You can make a new menu item yourself (rightclick mouse on the application text and select edit menu - add new application in appropriate category). Unfortunately I do not have a blackberry to test it for you.


VERY IMPORTANT to know this!! I was chasing through all kinds of 'barry' links, trying to figure out why it wouldn't run. It doesn't show up on menu anywhere, so if you use shell or alt+f2, they won't work without the exact right name: barrybackup.

((note to any barry developers who find this: could you please enable the app being listed on applications menu?))

:lolflag:

---

### Post by lavinog on 2010-04-18
> **chitowner2 said:**
> 

((note to any barry developers who find this: could you please enable the app being listed on applications menu?))

:lolflag:

The developers are not likely to read this post.  You can file a bug report for things like this though.

---

### Post by chitowner2 on 2010-04-18
> **zappadragon said:**
> Man this is killing me I can't get it to backup


It's been a while since your post but- "PIN" number (which I think is really a 'serial #) is required.

You must know your PIN and have your BB connected on USB before booting the app. It will either autodetect or open with a prompt for the PIN#, then ask for a device name (whatever you want to cal it). after that, you can go ahead and run the backup. 

NB: Barry only backs up 'device memory', not SIM card or Media card data. I have no idea what can backup SIM data, but Media is seen as a USB device and can be handled accordingly.

Hope that helps.
CT

---

