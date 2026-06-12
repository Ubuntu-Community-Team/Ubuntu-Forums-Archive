---
title: "silly girl stuck in grub4dos ^_^;"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by toni_gielow on 2009-01-07
hey ^_^;
i recently decided to try out ubuntu and i LOVE IT!!!!!!!!!!!!! :popcorn:

i used wubi to install it and i managed to get everything working. found out how to install programs, figured out wine, listened to music and looked up everything else i could do. its so AWESOME!!! :D and now im even more curious on how to do even greater things with ubuntu.

perhaps i installed something that brings my ubuntu directly to grub4dos/grub2dos(i forget ^_^;;;) whenever i select ubuntu on boot. before this happened however, my wine kept crashing. because i was opening a program called ZSNES for windows with wine because i couldnt figure out how to get the linux one working correctly, but im still learning!

but anyway, my wine crashed and i was forced to shut down the computer by the tower. i got into ubuntu just fine, but i was messing around with wine again and wine crashed. i was unable to do anything so i shut it down again telling myself to be more careful with wine! but now whenever i select ubuntu, it goes to a grub4dos/2dos kind of screen. it says tab gives me options, and i tried everything in my power to get back to ubuntu. when i go to the "main menu" all it says is 4 listing options that just say theyre not found, command line, reboot, and halt. i think i saw some error around there as well.

i looked up this program and tried creating my own service cd and printed out what i had to do, but i think its a different problem! i did a scandisk to my c drive letting it finish(it took hours...) and it still doesnt work!

is there any way to save it? or do i have to reinstall it?
thanks !!!!!! :D

p.s sorry if this is supposed to be in the wubi forum, im not sure if its a simple mistake, i installed something i probably should not had, or what!!!!???

---

### Post by skern03 on 2009-01-07
> **toni_gielow said:**
> hey ^_^;
i recently decided to try out ubuntu and i LOVE IT!!!!!!!!!!!!! :popcorn:

i used wubi to install it and i managed to get everything working. 

but now whenever i select ubuntu, it goes to a grub4dos/2dos kind of screen. it says tab gives me options, and i tried everything in my power to get back to ubuntu. when i go to the "main menu" all it says is 4 listing options that just say theyre not found, command line, reboot, and halt. i think i saw some error around there as well.



I tried Wubi on one machine, and had no end of problems with it. I'm sure it can be made to work, though. Just to be sure, you are speaking of an install under Windows, where it's installed like an app, and can be removed via the Add/Remove Programs Control Panel Applet, right?

If you like Ubuntu as much as I do, then you might consider dual-booting with Windows. Or eliminating Windows altogether.

You may be able to fix the problems with your boot menu by sticking the Windows CD in the drive, then restarting. Make sure your BIOS is set to boot from CD. When the windows CD loads, you'll eventually get an option screen. Select Repair. 

You'll then get an MS-DOS like window where you select your windows installation (it's usually something like "1: C:\Windows"). Then you can run commands (help will produce the list available). I think the one you want is 
> fixboot

That MAY restore your boot menu options.

Apologies if I misunderstood your problem.

---

### Post by toni_gielow on 2009-01-07
> **skern03 said:**
> I tried Wubi on one machine, and had no end of problems with it. I'm sure it can be made to work, though. Just to be sure, you are speaking of an install under Windows, where it's installed like an app, and can be removed via the Add/Remove Programs Control Panel Applet, right?

If you like Ubuntu as much as I do, then you might consider dual-booting with Windows. Or eliminating Windows altogether.

You may be able to fix the problems with your boot menu by sticking the Windows CD in the drive, then restarting. Make sure your BIOS is set to boot from CD. When the windows CD loads, you'll eventually get an option screen. Select Repair. 

You'll then get an MS-DOS like window where you select your windows installation (it's usually something like "1: C:\Windows"). Then you can run commands (help will produce the list available). I think the one you want is 


That MAY restore your boot menu options.

Apologies if I misunderstood your problem.

awwww thank you (b^-')b
but yes, right now i am dual-booting ubuntu under windows. once i figure out ubuntu better, maybe one day ill make the full switch! i just need to know how the heck to get out of GRUB4DOS and back to ubuntu :P

---

### Post by caljohnsmith on 2009-01-07
Do you have a Ubuntu Live CD (the install CD) that you can boot and use for troubleshooting your problem? If not, I think it might be difficult to get your Ubuntu working again. But if you have a Live CD, how about booting it, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Ubuntu problem might be.

---

