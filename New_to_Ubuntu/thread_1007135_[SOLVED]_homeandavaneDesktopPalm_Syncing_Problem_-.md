---
title: "[SOLVED] /home/andavane/Desktop/Palm Syncing Problem - Gnome Configuration Tool.odt"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Andavane on 2008-12-10
Hello
I have a Palm Handheld model Treo 680, and am pleased to see that there are many Palm options in the system I am using – Hardy Heron, running on a Sony Vaio VGN-S3HP.

On running the gnome-pilot, I’ve selected USB button on the 4 options at the top, then  followed the wizard following the instructions up to
“please put PDA in cradle and press hotsync button”.
I’ve stepped through this procedure using:
“/dev/pilot” as well as “dev/ttyUSB0” (and USB1)
“/dev/ttyS0” (and ttyS1) as well as “/dev/pilot”.

On each occasion I am getting the message (screenshot below).

At this point I have read the advice, but do not fully understand, I actually feel rather lost here.

I’ve love to get this to work.

I’m currently in the Indian countryside, and I make visits to a internet shop, from where this is posted; there’s a huge festival in swing at the moment, so there may be some delay in reverting to the forum.

Regards

John

---

### Post by DieB on 2008-12-10
seems like this post might be a help:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

hope it is a help

---

### Post by Andavane on 2008-12-12
Thank you - I'm working on it and will revert with results,
cheers!
John

---

### Post by Andavane on 2008-12-15
> **DieB said:**
> seems like this post might be a help:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

hope it is a help
Yes, thank you, I believe I am making some progress following the link to the above guide.
Before I was getting nothing, now (after going through steps 1--4)I am getting the name of the computer (vaayubuntu-0) on my screen (on the Palm).

However, nothing happens when I press the Hotsync button.
In the link you mentioned I read what I do should next:
> 5. For Ubuntu 7.04 (Feisty Fawn), 7.10 (Gutsy Gibbon) and 8.04 (Hardy Heron) when still not working (and for me it didn't) add the visor module to etc/modules.

    *  gksudo gedit /etc/modules

     * Add after last line
    *  visor

      and save the file. Restart your computer.
The problem is (a bit shamefaced here) I don't know how to get back into the rule file which I made, in order to add the line suggested in the guide.

Looking forward to a reply!

Regards

John

---

### Post by DieB on 2008-12-15
u mean the rule file from step 2? it would be:
gksudo gedit /etc/udev/rules.d/10-custom.rules
or open a terminal and push the up-cursor until u get to the command, but here in step 5 they want u to add a kernel module and that is done via
gksudo gedit /etc/modules
as mentioned in the text. gedit is the gnome editor, console-based editors would be nano or vi - just replace gedit with that to see ( getting comfortable with nano or vi could be helpful, e.g. if X is not running (due to bad xorg-config-file or missing drivers or .... 

hope that is the answer u looked for

---

### Post by Andavane on 2008-12-23
> **DieB said:**
> u mean the rule file from step 2? it would be:
gksudo gedit /etc/udev/rules.d/10-custom.rules
or open a terminal and push the up-cursor until u get to the command, but here in step 5 they want u to add a kernel module and that is done via
gksudo gedit /etc/modules
as mentioned in the text. gedit is the gnome editor, console-based editors would be nano or vi - just replace gedit with that to see ( getting comfortable with nano or vi could be helpful, e.g. if X is not running (due to bad xorg-config-file or missing drivers or .... 

hope that is the answer u looked for

Indeed, DieB: Things seem to be getting warmer;
again  progress is made - but not quite there yet.

When I pressed the HotSync button on the Palm, something flashes on the Ubuntu screen, disappears and then the Pal gives the "Unable to initiate Hotsync operation because the port is in  use by another application" which I guess must be a bug, because I checked and as far as I know, nothing else was running

This is when I selected "USB" at the beginning of the new user sequence for Pal devices.
When I seected "serial" and pressed Hotsync I had: "Device error on Cradle (/dev/pilot) Caught unhandled port error, but it's toldme that it is configured.

The up-arrow key is most useful for seeing previous commands. I'm glad I now know that.

Kind regards

John

PS: Delay in responding is due to days'absence from the net.

---

### Post by Andavane on 2009-01-03
Hello -
Eventually I found that I'd clicked the USB option; when I switched it to "cradle", everything went fine, and my Palm is now syncing correctly with Evolution.
Many thanks to all who helped me to get this working...
Very happy ;)
Problem solved
Kind regards
John

---

### Post by silvagroup on 2009-02-12
For the last three weeks since upgrading to Intrepid my ability to sync with my Centro was gone, after following this post I have at least been able to re-establish a useful sync via usb cable. Yeah!!! my Centro finally now up to date.
However bluetooth sync which worked great in Hardy still will not work.
I can send files from PC via bluetooth but every time I try the bluetooth sync I get a "Unable to initiate Hotsync operation because the port is in use by another application"

Any help with this would be greatly appreciated.

---

### Post by Andavane on 2009-02-12
> **silvagroup said:**
> For the last three weeks since upgrading to Intrepid my ability to sync with my Centro was gone, after following this post I have at least been able to re-establish a useful sync via usb cable. Yeah!!! my Centro finally now up to date.
However bluetooth sync which worked great in Hardy still will not work.
I can send files from PC via bluetooth but every time I try the bluetooth sync I get a "Unable to initiate Hotsync operation because the port is in use by another application"

Any help with this would be greatly appreciated.

Hi...
I was sorry to see your plight, and also sorry to say that having got it all working, it began playing up again. Ugh!...

My intention was to remove "solved" from this thread, but I can now not find how to "unsolve" it ( or to "solve" a thread for that matter #-o ).

Anyway for the time being, I'm intrigued that you have had bluetooth hotsync wrking on Hardy!  
How did you do that? I gave up on it when I tried to do it.

Can you write the steps you went through?

I have a laptop on  Hardy, and the main machine is now on intrepid.
I'd love to be able to sync on Hardy with Bluetooth.

Kind regards

John

---

### Post by silvagroup on 2009-02-12
WOW, Andavane that was so long ago,but I believe I used these [http://howto.pilot-link.org/bluesync/]("http://howto.pilot-link.org/bluesync/") and [http://www.newt.com/debian/treo650.html]("http://www.newt.com/debian/treo650.html")then some tweaking after following these process was the way I set up Bluetooth in Hary. 
If I recall I didn't install Bluez, because the Bluetooth stack is already available in Hardy and it worked. If you don't have bluetooth installed do it with apt-get or package manager.

I am going to run through the same process from scratch again tomorrow again with this Intrepid install to see if that helps any.

Unfortunately this is a weak link in the Linux chain. It's one of those things that should just work !!!!! :(

As for removing the solved just go back to your first post and edit the title.

---

### Post by silvagroup on 2009-02-13
OK well not waiting until tomorrow I did, followed the links, actually just the first one, and now my bluetooth connection is once again working, but now in Intrepid.

---

### Post by Andavane on 2009-02-13
Hi there... silvagroup...

> **silvagroup said:**
> WOW, Andavane that was so long ago,but I believe I used these [http://howto.pilot-link.org/bluesync/]("http://howto.pilot-link.org/bluesync/") and [http://www.newt.com/debian/treo650.html]("http://www.newt.com/debian/treo650.html")then some tweaking after following these process was the way I set up Bluetooth in Hary...
I know the feeling!

> I am going to run through the same process from scratch again tomorrow again with this Intrepid install to see if that helps any.

Please tell me how you get on... my intrepid on on a main IBM machine with no bluetooth, but I have a belkin bluetooth dongle, and who knows it may be one of those days for things to work ;)

The big question is finding the time to do it, isn't it? 	:?

> Unfortunately this is a weak link in the Linux chain. It's one of those things that should just work !!!!! :( 

Indeed! But I guess that the wonderful team, being under the same time restraints, just haven't quite got round to it... Still With all those Palm Settings in the Preferences... We can live in hope...

> As for removing the solved just go back to your first post and edit the title.
thanks for the tip... We live and learna little every day... 

Kind regards

John

PS: If it no longer says "Solved".... it worked...

---

### Post by Andavane on 2009-02-13
> **silvagroup said:**
> OK well not waiting until tomorrow I did, followed the links, actually just the first one, and now my bluetooth connection is once again working, but now in Intrepid.
Really?   WOW!...
Well my laptop is on Hardy, so when I'm on that, hopefully sooner rather than later... I'll get a similar result...
Only things is I have a Treo 680, not 650... so will live in hope.

Am glad to have a machine with intrepid on as well.

That's the 'mucking about' machine, so I can't (hopefully) screw up much on it  ;)

---

### Post by Andavane on 2009-02-13
Oh NO!

I edited "Solved" out of the title of the first post, but it appears in others as well...

---

