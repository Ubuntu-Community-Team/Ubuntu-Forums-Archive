---
title: "Problem with initializing OpenGL for Wine apps"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by yashpathak on 2009-05-23
Hi
I have recently moved to Linux - Ubuntu 8.10 and am having problems in running all 3 softwares i installed using wine. i.e. Google sketchup, AutoCAD 2004, PorgeCAD2008

The message i receive when launching sketchup is:
"
Sketchup was unable to initialize Open GL!
Please make sure you have installed the correct drivers for your graphics card.
Error: ChoosePixelFormat failed
"
Autocad starts but closes down as soon as i open a file. same with Porgecad.

Can you please guide how i can check if the correct driver is installed for the graphics card; and then how to install the correct one.

...and please suggest if there is a Linux app which works with the *.dwg format of the Autocad.

thanks[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by yashpathak on 2009-05-23
Hi
I have recently moved to Linux - Ubuntu 8.10 and am having problems in running all 3 softwares i installed using wine. i.e. Google sketchup, AutoCAD 2004, PorgeCAD2008

The message i receive when launching sketchup is:
"
Sketchup was unable to initialize Open GL!
Please make sure you have installed the correct drivers for your graphics card.
Error: ChoosePixelFormat failed
"
Autocad starts but closes down as soon as i open a file. same with Porgecad.

Can you please guide how i can check if the correct driver is installed for the graphics card; and then how to install the correct one.

...and please suggest if there is a Linux app which works with the *.dwg format of the Autocad.

thanks[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

### Post by overdrank on 2009-05-23
Please do not create multiple threads on the same issue. threads merged

---

### Post by loell on 2009-05-25
google sketchup  do almost run smoothly with wine versions after ubuntu 9.04, expect that it will run and be usable on the up comming ubuntu 9.10 or later.

if you need it now, update your wine to later versions.

---

### Post by supersonicdarky on 2009-05-25
Can you run any opengl apps? Do you have the proper drivers installed and activated?

Also you need to upload screenshots somewhere, not just link them to yourself (unless you are running a webserver, in which case it would be http:// not file://)

---

### Post by yashpathak on 2009-05-30
sorry guys, my system was down so couldnt come back to the forum earlier.
Back to the original context:

i have now upgraded to ubuntu 9.04 and have installed all updates including wine.
Sketchup has made some progress, but is still not usable. here is the event sequence:

first the sketchup said that 'HTML rendering is disabled; and wine requested to download 'Gecko for Mozilla'. Before installing it the screenshot was like the attached 'screenshot-1.png'

after installing gecko, wine doesnt give an error but the sketchup tutorials etc. still do not show correctly- the images are missing (see 'screenshot-2')

apart from the tutorials, the workspace of sketchup is just a black space (see 'screenshot-3'). so the sketchup still doesnt work.

m not sure whether openGL is working at all!! there is surely something wrong with the display...even the minimizing/ maximizing of the general windows is not smooth (even though nothing else is running)

i looked up in the 'hardware drivers' but it says no propreitory drivers installed (see screenshot-4). please advise how can i check whether openGL is working or not?

---

### Post by loell on 2009-05-30
one thing that isn't mentioned here is you need a decent graphics card in order to run these apps (sketchup specifically).

attached: sketchup window, running on top of **wine-1.1.22** with working nvidia graphics card.

appart from the white stripes button, with some quirky 3d model display, it's working and usable.

---

### Post by Mark Phelps on 2009-05-30
If you're going to run Wine apps, you need to take the time to familiarize yourself with the CodeWeavers app compatibility database -- which indicates testing results of various apps and versions.

The link below shows clearly that AutoCad 2004 is "known not to work":

[=ASC;curPos=350"]http://www.codeweavers.com/compatibility/browse/name/?letter=a;showall=1;sort[app_name]=ASC;curPos=350]("http://www.codeweavers.com/compatibility/browse/name/?letter=a;showall=1;sort[app_name)

---

### Post by anewguy on 2009-05-30
As an add-on to what Mark Phelps posted above, for anyone trying to figure out their wine applications, what this user has posted as the first screen image has been fairly typical in my experience when the app won't run in wine.  Missing boxes, colors not right, etc..  Some applications can be made to run with the addition of .dll files to wine and other tweaks, but that is normally beyond what is covered in this forum.  Please do as Mark Phelps suggested and check the compatibility lists first, the proceed at your own "risk".  I haven't seen a wine app "hurt" Ubuntu, just many that either act screwy, give bad screens, or once it a great while just cause my Linux to freeze.

Dave :)

---

### Post by tx-uturn on 2009-06-15
I too am having the same problem of the black field and unable to draw.  I am running 8.10 with wine 1.1.23 and Sketchup7.

*-display
                description: VGA compatible controller
                product: M22 [Mobility Radeon X300]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx


Any help would be much appreciated.  Also, keep in mind I am about a 6 month Linux user.  Please, if you tell me to try something, you need to tell me how.

Thanks

---

### Post by Mark Phelps on 2009-06-17
Sketchup has a "bronze" rating at the CodeWeavers site, which means at best, only SOME of the functionality will work.  So, you may be in luck and the particular thing you want to do can be made to work eventually with enough tweaking, but more likely, you'll just have to live with the limitations.

---

### Post by clive littlewood on 2009-06-17
Hi

Why not run XP or Vista in virtualbox and run the programs as they are supposed to run ?

Clive

---

### Post by loell on 2009-06-17
> **Mark Phelps said:**
> Sketchup has a "bronze" rating at the CodeWeavers site, which means at best, only SOME of the functionality will work.  So, you may be in luck and the particular thing you want to do can be made to work eventually with enough tweaking, but more likely, you'll just have to live with the limitations.

you might like to run it yourself than rely on user's rating.  the only thing that didn't work are some shortcut keys that are conflicting with default DE keys.

---

