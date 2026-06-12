---
title: "Ubuntu loads into grub"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by thinhman on 2009-08-17
Hi all I'm very new to Ubuntu; linux for that matter.  I've installed Ubuntu from my windows OS and thus have no CD.  Now it appears that my menu.lst has disappeared or something...everytime I turn on the laptop it goes into the grub commandline.

It shows me the
[Minimal BASH-like line editing is supported...etc.]

if I press esc, it shows me 8 things.  

find /ubuntu/disks/boot/grub/menu.lst 
find /ubuntu/install/boot/grub/menu.lst  
find /menu.lst 
find /boot/grub/menu.lst 
 find /grub/menu.lst  
commandline 
 reboot  
halt

Any help on this guys? I'd really appreciate it; thanks!


EDIT: I just tried searching for my stage1 file so I can reinstall grub and it says that the file does not exist.  I don't know if this helps or not.

---

### Post by trilobite on 2009-08-17
> **thinhman said:**
> Hi all I'm very new to Ubuntu; linux for that matter.  I've installed Ubuntu from my windows OS and thus have no CD.  Now it appears that my menu.lst has disappeared or something...everytime I turn on the laptop it goes into the grub commandline.

It shows me the
[Minimal BASH-like line editing is supported...etc.]

if I press esc, it shows me 8 things.  

find /ubuntu/disks/boot/grub/menu.lst 
find /ubuntu/install/boot/grub/menu.lst  
find /menu.lst find /boot/grub/menu.lst 
 find /grub/menu.lst  
commandline 
 reboot  
halt

Any help on this guys? I'd really appreciate it; thanks!


EDIT: I just tried searching for my stage1 file so I can reinstall grub and it says that the file does not exist.  I don't know if this helps or not.

Hi thinhman - 

 Hmm, doesn't sound like you've been having much fun... :) It's always much easier to install Linux using a CD (rather than from Windows), but let's see what we can do. 

From the above options, select commandline. That should take you to a command-prompt that will look like either a "$" or a "#". 

Assuming that you do get one of the above command-prompts, type "pwd" (without the quotes). That means "present working directory", and will tell you which directory you're in.  

Next, tyoe this command (without the quotes)-
"cat /boot/grub/menu.lst"  -This will tell you what the menu.lst file looks like. We'll need to know this in order to change it so that you can choose to boot into either Windows or Linux when you boot the PC. (By the way, which version of Windows are you using? XP? Vista?)

That will do for a start. In the next post, let me know what the menu.lst file looks like, and it should be possible to proceed from there. 
 Good luck - hope this helps!  
- trilobite

---

### Post by thinhman on 2009-08-17
Hello trilobite; first of all thank you for responding.
I am running windows XP and my ubuntu is 9.04.  I have been using it fine for the first few weeks.

I have tried typing in pwd and it comes up with "unrecognized command"
I have tried typing in cat /boot/grub/menu.lst and it came up file not found.

I went back into winXp and looked for the menu.lst myself and it was in my hd0,0 under /ubuntu/winboot/
I don't know if it's possible to see the ubuntu files from XP but it appears as if I do not have any directories under the name of /boot or /grub.  

I've been googling and searching the forums for answers and everyone seems to be able to find their kernel or stage1,2 but I am lacking both of those.  

I can tell you what my menu.lst says in a notepad form while in winXP if that helps any bit?

Once again thank you for all your help.

UPDATE: Once again I do not know if this helps but from windowsXP my menu.lst says 
              "debug off[]hiddenmenu[]default 0[]timeout 0[]
fallback 1[][]title find /ubuntu/disks/grub/menu.lst[]       find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst[]       configfile /ubuntu/disks/boot/grub/menu.lst[][]title find /ubuntu/install/boot/grub/menu.lst[]            
fallback 2[]    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst     configfile /ubuntu/install/boot/grub/menu.lst[][]title find /menu.lst[]              
fallback 3[]    find --set-root --ignore-floppies /menu.lst      configfile /menu.lst[][]title find /boot/grub/menu.lst[]
fallback 4[]    find --set-root --ignore-floppies /boot/grub/menu.lst[][]title find /grub/menu.lst[]
fallback 5[]    find --set-root --ignore-floppies /grub/menu.lst       configfile /grub/menu.lst[][]title commandline[]       commandline[][]title reboot[]        reboot[][]title halt[]       halt[]




Then the really weird thing is that...once I try to go to /ubuntu/disks  it says that it is not accessible.  The file or directory is corrupted and unreadable!!!!!!!  :confused::confused::confused:
Does this mean I basically have to reinstall ubuntu?  If I remember correctly I tried installing the extra gimmick programs that ubuntu offers last night.

---

### Post by trilobite on 2009-08-17
> **thinhman said:**
> Hello trilobite; first of all thank you for responding.
 

Ok, you're welcome.... 

[QUOTE=thinhman]
I am running windows XP and my ubuntu is 9.04.  I have been using it fine for the first few weeks.

I have tried typing in pwd and it comes up with "unrecognized command"
I have tried typing in cat /boot/grub/menu.lst and it came up file not found.

I went back into winXp and looked for the menu.lst myself and it was in my hd0,0 under /ubuntu/winboot/
[/quote] 
Hmm... ok.... That gives enough information for me.  
(snip) 

I think that the best and simplest solution would be to remove the Ubuntu installation and do a conventional re-install using a CD (from outside Windows). It sounds like you may have used "Wubi" to install Ubuntu. 

While I haven't heard any negative comments about Wubi, it will be much simpler in the long run if your Ubuntu install is done the usual way, from a CD. 

One **very important** thing to keep in mind - if you do go ahead and install using a CD, you will see an option in the course of the install which says "Use entire disk for install" (or something similar). Do **NOT** choose that option. If you do, your Windows install will be erased. 

 I'm in New Zealand, and since it is getting late here, I may be off to bed soon. Anyway, I will try to drop in here tomorrow to see how you're going. 

 Bye for now - 
- trilobite

---

### Post by thinhman on 2009-08-17
Okay then thanks for the info!
I'll just burn myself a copy of ubuntu and reinstall.  Is there anything I can do to prevent this in the future though?

---

### Post by blindape on 2009-08-24
Hi I am having a very similar problem to thinhman.  I installed intrepid Ibix back in Feb and it has been working fine since, but when I came out this morning and started to boot up my computer I came up with the same grub prompt.  I didn't do anything out of the ordinary yesterday before shutting down the computer so I'm not sure what is happening.

Ubuntu is installed in Windows with a wubi install, but on D drive not C drive.
My win version is Vista.

Regards,

John Curwood

---

