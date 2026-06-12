---
title: "Could not find kernel image: linux error? booting back to XP Pro"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by Bobmark8 on 2009-02-08
[FONT=Trebuchet MS][COLOR=Blue]I am one day into Linux and I will try to keep my issue brief. My wife's Dell 8400 which runs XP Pro is sick. :(
First problem (nothing to do with Linux);[COLOR=Red] [/COLOR][/COLOR][/FONT][FONT=Trebuchet MS][B][COLOR=Red]
Windows could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM[/COLOR][/B][/FONT][FONT=Trebuchet MS][COLOR=Blue] [/COLOR][/FONT][FONT=Trebuchet MS][COLOR=Blue]Soooo... I created a "bootable" from download and burn the [Ubuntu Live CD]("http://www.ubuntu.com/getubuntu/download") Ubuntu 8.10 [/COLOR][/FONT][FONT=Trebuchet MS][COLOR=Blue]to run Linux to backup files before trying to restore anything. I was very successful in copying all the data files I need (just in case of a recovery glich ;)). Ubuntu has a fantastic GUI!!!
Now here is the rub. I have removed the [Ubuntu Live CD]("http://www.ubuntu.com/getubuntu/download") and have the MS WIn XP Pro CD in my CD drive to do recovery procedures per the MSs postings I have reviewed AND I now get the unexpected message;[/COLOR][/FONT]](*,)
[FONT=Trebuchet MS][B][COLOR=Red]could not find kernel image: linux
boot: (blinking curser)[/COLOR][/B]
[/FONT][FONT=Trebuchet MS][COLOR=Blue]Google had only 10 posts with this subject and all related to trying to get Linux running. Thats not my long term goal. My goal is to get MS Win XP Pro running again. And then I found this forum.
[SIZE=3]**[COLOR=Green]ANY HELP ON THIS WOULD BE MET WITH GREAT REJOICE.[/COLOR]**[/SIZE][/COLOR][/FONT]

[FONT=Trebuchet MS][SIZE=4][COLOR=Blue]Thanks, Bob[/COLOR][/SIZE][/FONT]

---

### Post by pbotros1234 on 2009-02-08
Put in the Windows Install CD

Go to a Recovery Console (not sure about the actual way to get that, but I'm sure it's fairly straightforward)

type "fixmbr" without the quotes
--- if that does not work, try "fix /mbr" (again, without the quotes)

That should make it so the windows bootloader is back to normal.

---

### Post by Bobmark8 on 2009-02-13
Thanks for the idea; tried it with no success. Recap of status.

I am really struggling with my wife's Dell 8400 which runs XP Pro

Started with the error:
Windows could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM

So, I created a "bootable" CD with KNOPPIX_V6.0-ADRIANE_V1.1CD-2009-01-27-DE.iso to run Linux. I didn’t like the GUI:
Soooo... I created a "bootable" CD with ubuntu-8.10-desktop-i386.iso to run Linux. This worked great. With this I am able to see and copy files; however I have discovered there is no valid restore points available in the System Volume Information folder. 

I re-confirmed this by placing the “bad” HD from the Dell 8400 into my Dell Inspiron 530 and it also confirms no valid restore points are available in the System Volume Information folder.

I have tried to replace the 5 hives in the operating system /WINDOWS/SYSTEM32/CONFIG/folder; however this has not been successful and I have also managed to lose the ability to log in as an administrator in the To repair a Windows XP installation using Recovery Console, press R. (know I screwed that up because this is a machine with an OEM XP install, so you can please skip telling me how I screwed that up)

So I finally decided to do the MS install repair, i.e.
When you see the "Welcome To Setup" screen, you will see the options below   
This portion of the Setup program prepares Microsoft Windows XP to run on your computer:
1.	To setup Windows XP now, press ENTER. (Did this)
2.	Accept the License Agreement and Windows will search for existing Windows installations. (Did this)
3.	Select the XP installation you want to repair from the list and press R. (Did this)

Now here is STILL the rub. I have removed all CDs and put the Boot order back the way is should be AND I STILL get this unexpected message on a black (DOS like) screen; 

Syslinux 3.71 Debian – 2008-09-06 EBIOS Copyright © 1994-2008 H. Peter Anvin
could not find kernel image: linux
boot: (blinking curser)

Any and help would be appreciated very much. I have been at this for DAZE (DAYS)&#61516;!!! :confused:

Thanks, Bob

---

### Post by Kain000 on 2009-02-13
I know that this isnt what you would want to hear but I think at this point with a corrupt system config file(s) you may just be causing yourself more pain by trying to "revive the patient".   

My advice would be to just make sure you have a copy of all your mission critical work somewhere safe, and just run a session of DBAN 
[http://www.dban.org/]("http://www.dban.org/")
to wipe what ever nasties (if any) out and just reinstall ubuntu......(jk install windows if you REALLY need it... lol)

---

### Post by Bobmark8 on 2009-02-13
Kain000,

Thanks for the advice and you are right, it is not what I wanted to hear. Before I go wiping my HD clean as a whistle, I think I would prefer to try the DELL recovery which I understand is ebedded on the Drive somewhere to provide factory settings. If I do a wipe I lose this ability. 
_Remenber my goal is to restore to Windows XP Pro and not ubuntu. _
So I am back to the question in my last post on how to kill off this Linux boot message. I can't understand how Linux put something on my machine when my understanding was that it was to be a "bootable" CD to help troubleshoot Windows XP  

What I believe I need to do is find and nuk the command (not the whole drive) that is looking for "kernel image: linux"

If you agree do you have any ideas on how to do this? Or what would you do next besides throwing the machine out the window (not XP but HOUSE)

Cheers, Bob :(

---

### Post by Kain000 on 2009-02-13
> **Bobmark8 said:**
> Kain000,

Thanks for the advice and you are right, it is not what I wanted to hear. Before I go wiping my HD clean as a whistle, I think I would prefer to try the DELL recovery which I understand is ebedded on the Drive somewhere to provide factory settings. If I do a wipe I lose this ability. 
_Remenber my goal is to restore to Windows XP Pro and not ubuntu. _
So I am back to the question in my last post on how to kill off this Linux boot message. I can't understand how Linux put something on my machine when my understanding was that it was to be a "bootable" CD to help troubleshoot Windows XP  

What I believe I need to do is find and nuk the command (not the whole drive) that is looking for "kernel image: linux"

If you agree do you have any ideas on how to do this? Or what would you do next besides throwing the machine out the window (not XP but HOUSE)

Cheers, Bob :(


right right, if all else fails you can try GRC's spinrite to recover your disk.      I dont know about the boot message tho.

---

