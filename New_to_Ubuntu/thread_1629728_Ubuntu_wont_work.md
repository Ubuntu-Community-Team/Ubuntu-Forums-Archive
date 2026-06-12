---
title: "Ubuntu wont work"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by shiftman on 2010-11-24
Hi All,

I installed Ubuntu last night, all went well, so I thought. The hard drive is now split with 300gb Vista and 200gb Ubuntu, now when I turn computer on I get the Grub menu and select Ubuntu but all the computer does is hang and I have to hold in power button to shut it down.
I have started Ubuntu in recovery mode and selected repair installed package and now I have the Ubuntu selections duplicated on the Grub menu and it still does exactly the same, comp just hangs.
I have started the comp with the Iso disc in but it just wants to install Ubuntu again splitting the other Ubuntu partition.
Should I uninstall Ubuntu (how do I do this) and start again, will this put hard drive back to 500gb with Vista and I start over or is there anyway to get it to run properly.

Thanks folks

Paul

---

### Post by Peter09 on 2010-11-24
You need to post the specification for you computer (especially the graphics card).
 
As a start when you hold the shift key and get to the boot line, try using the 'e' key (for edit) on the first line of the boot menu. Add the command 'nomodeset' to the end of the boot line. (do not use the quotes). Then hit enter and see if it boots.

---

### Post by mastablasta on 2010-11-24
how did you install ubuntu? (procedure)
 
since you didn't provide any system specs have a ,ok at this thread and post your specs:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
if you can't access Ubuntu in any way then find and use Everest home edition to get the informaiton from your windows boot.

---

### Post by shiftman on 2010-11-24
Ok I have Intel Core 2 quad 2.4ghz processor, 3Gb ram, 500gb Hdd, ATI Radeon HD 4300/4500 series graphics card, what else do you need to know

I copied the spec for graphics card below, 

Primary Adapter        
Graphics Card Manufacturer    Powered by ATI    
Graphics Chipset    ATI Radeon HD 4300/4500 Series        
Device ID    954F    
Vendor    1002    
    
Subsystem ID    1619    
Subsystem Vendor ID    1462    
    
Graphics Bus Capability    PCI Express 2.0    
Maximum Bus Setting    PCI Express 2.0 x16    
    
BIOS Version    011.022.004.000    
BIOS Part Number    xxx-xxxxxxxx-xxx    
BIOS Date    2009/06/09    
    
Memory Size    1024 MB    
Memory Type    HyperMemory    
    
Core Clock in MHz    600 MHz    
Memory Clock in MHz    400 MHz    


I downloaded Ubuntu from  [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) burned the i386.ISO  file to CD-R disc using the iso recorder V3 as it stated, started computer with disc in and followed the install as it showed from the link above.
I did get a message about the graphics card saying something about the driver and just followed the driver update (sorry I can give you more details about that as I cant remember what it said exactly) this is the web address for my card [http://eu.msi.com/index.php?func=proddesc&maincat_no=130&prod_no=1869](http://eu.msi.com/index.php?func=proddesc&maincat_no=130&prod_no=1869)
I have had a look for linux driver but none are on the driver list, but to be honest I could remove the card as I dont need it for gaming etc...

Anyway I continued with the install and everytrhing went ok untill right at the end it said it had finished install and I selected restart comp, the screen went black and then I got a screen full of lines of god knows what to be honest, the comp just hung and I had to power it off.

Paul :D

---

### Post by Peter09 on 2010-11-24
When you go to recovery mode, have you selected the reconfigure graphics option on the menu, does it attempt do reconfigure?

---

### Post by mastablasta on 2010-11-24
> **shiftman said:**
> ATI Radeon HD 4300/4500 

 
This card has proprietary linux drivers available:
[http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.38&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20](http://support.amd.com/us/psearch/Pages/psearch.aspx?type=2.4.1&product=2.4.1.3.38&contentType=GPU+Download+Detail&ostype=Linux+x86&keywords=&items=20)
 
 
> 
I downloaded Ubuntu from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) burned the i386.ISO file to CD-R disc using the iso recorder V3 as it stated, started computer with disc in and followed the install as it showed from the link above.

Did you check the md5sum of the iso to see if the burn is ok? but let's assume everyhting is ok.
 
> 
I did get a message about the graphics card saying something about the driver and just followed the driver update (sorry I can give you more details about that as I cant remember what it said exactly). 

 
the message might have been important as to me it seems like something is wrong with your graphics drivers that were "updated". you could try to install it without them first. you will use open source radeon drivers (which might be a good fit or not, but since you can run live CD, they should be ok). after install is finished you can go to System->Administration->Hardware drivers and then enable your proprietary hardware driver there. this will download them from ATi and install i believe.
 
EDIT: on a related topic have a look at this:
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)
 
To sum up 4200 and 4250 works better with opensource drivers according to some users. so install without enabling ATI drivers (fglrx) then see if oyu actually need them.

---

### Post by shiftman on 2010-11-24
OK, its working OK now I think, I turned comp on, selected recovery mode then "run in failsafe graphic mode"  then got a message saying Ubuntu is running in low graphics mode, your screen, graphics card and input device settings could not be detected correctly you will need to configure these yourself. 
I restarted the comp and it booted up OK, Ubuntu loaded fine then I got message about the ATI graphics drivers and activated it and all seems to be ok now. Is there anything else I should do.

Also how do I get rid of the duplicated Ubuntu selections on the Grub screen.

Another question I have is do I need to install any Internet security software with Ubuntu, does it come with a firewall, is there a dedicated firewall programme suitable for Linux or can I use my AVG internet security suite with it.

Once again many thanks for all your help

Paul :D

[IMG]http://i15.photobucket.com/albums/a395/prlowry/CIMG0192.jpg[/IMG]

[IMG]http://i15.photobucket.com/albums/a395/prlowry/CIMG0190.jpg[/IMG]

[IMG]http://i15.photobucket.com/albums/a395/prlowry/CIMG0189.jpg[/IMG]

[IMG]http://i15.photobucket.com/albums/a395/prlowry/CIMG0188.jpg[/IMG]

---

