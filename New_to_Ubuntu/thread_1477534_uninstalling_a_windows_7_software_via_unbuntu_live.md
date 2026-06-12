---
title: "uninstalling a windows 7 software via unbuntu live cd"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by dustoff2010 on 2010-05-08
I have a program in windows7 that prevents me from logging into windows, so I am using ubuntu cd to log in.I would like to uninstall this program called ayrecovery but i don't see how to from ubuntu.

If it's not possible to uninstall it would it work to rename it just to log into windows then deal with the program?

I tried all avenues like system restore point. i said this software would be removed,but it's still there. I tried everything except disk wipe and reinstall, which i would prefer not to do.
Thanks for any input.

---

### Post by paul88 on 2010-05-08
Under the places menu, click computer and see if you can get to the windows side that way.
On mine my windows drive is called acer, I then click the users folder and go from there.

might not work with the live cd.

---

### Post by Ocxic on 2010-05-08
try manually deleting the program from C:\Program Files\  that should allow you to login.

---

### Post by dustoff2010 on 2010-05-09
I guess I should have included this in the original msg, but I can see the software and really didn't know if it would make matters worse by just deleting it instead of the  the traditional option to uninstall.

up date

I delete the folder with the program, then did a search and deleting everything with that name which was only 2 folders.

But when I tried to log to windows it came up again. I guess i need to check registry, which i am not too fond of doing.

Can I get some input please.

---

### Post by UnknownFear on 2010-05-09
If you can't login to Windows, or delete it from the LiveCD, your best bet would to uninstall Windows and re-install it if needs be.

---

### Post by dustoff2010 on 2010-05-09
I have another question. I have decided to install ubuntu 10.04 and I have two hds in my comp. windows 7 the main and winxp as extra hd space. Unbuntu has chosen the winxp drive to install to. Would that create a problem logging in or is that okay?

Thanks

---

### Post by Ocxic on 2010-05-10
You should be fine, just remember that you will format/delete everything on that drive!!!!!

---

### Post by Mark Phelps on 2010-05-10
Word of advice.  Next time you see a product liked this advertised, carefully look over the material for bad grammer and misspellings.  I looked at the page for ayrecovery and was horrified by how bad it was.  What, for example, are "senconds"?

REAL software companies employ folks know as copy editors to make sure this kind of awful stuff doesn't creep into their advertising.

The presence of this stuff is a clear indication of some scam artists that are simply trying to take your money in return for junk that doesn't work.

Also, the person in England who (they say) endorsed their product was William "Jafferson" Clinton -- changing the name to "Jafferson" to "Jefferson" should have been another clue that this is a scam.

---

### Post by lightstream on 2010-05-10
> **Ocxic said:**
> You should be fine, just remember that you will format/delete everything on that drive!!!!!

errr... no you won't, by default Ubuntu will create itself a new partition from the free space on the install disk and install itself there.

---

### Post by Paddy Landau on 2010-05-10
> **Mark Phelps said:**
> Word of advice...
In addition, I'd advise that you use Firefox and install the add-on called [WOT]("https://addons.mozilla.org/firefox/addon/3456") (Web Of Trust). It would have alerted you to the fact that people have reported the website as untrustworthy.

---

### Post by alphacrucis2 on 2010-05-10
Can you login if you boot Windows in safe mode? If so, boot into safe mode with the networking option. Download and install a copy of Malwarebytes and see if that will get rid of this thing. If not you may have to use ubuntu to back up all the files you need from the Windows ntfs partition and then reinstall Windows.

---

### Post by dustoff2010 on 2010-05-10
It basically took over my comp. can't log to safe mode or anything. when I click home button on keyboard to go to the home page of this software it wants me to register by a keyword which requires buying the product.

At this point I have installed ubuntu,but i get"ubuntu running in low graphics (ee) cypress wireless usb failed to initialize for relative axes"

when it does get past that ,I am in the log in screen i log in and get"bash: cannot create temp file for here-document: no space left on device".
 I am trying to figure that out atm.
any suggestions would be appreciated.

---

### Post by Paddy Landau on 2010-05-10
It sounds as though that software package has really messed you up.

My recommendation (what I would do in your situation) is:

[LIST=1]
[*]Boot with the Ubuntu Live CD to back up all your data (and double-check that you have backed up **all** your data). Do that onto another device, e.g. a USB stick or external hard drive.
[*]Reinstall Windows (warning: It will delete **everything** on your hard drive).
[*]Reinstall Ubuntu if you want it.
[/LIST]
 Of course, you could try to get hold of the software's technical support, but bearing in mind WOT's rating, I wouldn't hold my breath.

---

### Post by dustoff2010 on 2010-05-11
At this point I have backed up my win7 files to dvd and installed ubuntu and wins side by side, however when I  try to boot it goes to the option screen for windows/ubuntu I see gnu grub version 1.98-1ubuntuu5. It lists the options(ubuntu ,with linux etc. I see a windows vista loader,but no ubuntu boot loader.

I let it continue and 
i get a  line flash across the screen which I cannot read(I think it's something like nouvou, but not sure)then a message I think,"graphics did not load, run in low graphics, you need to configure". I click to configure and msg"stand by while the display restarts", it never restarts so i click ok and all i see is a very tiny dot in the upper left corner of screen which is flashing.

any comments or solutions would be appreciated.
Thanks

---

### Post by Paddy Landau on 2010-05-11
Did you completely reinstall Windows 7 and then Ubuntu?

Did you manage to boot successfully into Windows 7 *before* installing Ubuntu?

If 'yes' to both questions, then I think you need to start a new thread, as this is a new problem.

Otherwise, please ensure that you can boot your Windows 7 *before* installing Ubuntu.

---

### Post by dustoff2010 on 2010-05-11
No, I did not reinstall wins7 at this point.I would like to get ubuntu working in order to continue with my online business and then later on deal with the wind7 problem, if that's doable.

---

### Post by mbzn on 2010-05-11
You could try an off-line registry editor (i use the one on ultimate boot cd, [www.ultimatebootcd.com](www.ultimatebootcd.com)) and delete all entries to that program(this should remove it from the startup applications) and then try to log in again. 

This works about 70% of the time

---

### Post by Don1500 on 2010-05-11
> **dustoff2010 said:**
> No, I did not reinstall wins7 at this point.I would like to get ubuntu working in order to continue with my online business and then later on deal with the wind7 problem, if that's doable.

Even if you get Ubuntu working  when you reinstall windows you will have to reinstall ubuntu. Ubuntu takes no time to reinstall (compaired to Windows) and it must be installed After Windows, so just bite the bullet and do it. (You have backed up all your important data, right?)

---

### Post by oldfred on 2010-05-11
I have not tried any of these but the idea of a liveCD virus check sounds like it may help. I would double check that the sites are valid.

[http://www.avg.com/us-en/avg-rescue-cd](http://www.avg.com/us-en/avg-rescue-cd)
[http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/](http://www.askvg.com/download-free-bootable-rescue-cds-from-kaspersky-bitdefender-avira-f-secure-and-others/)

---

### Post by dustoff2010 on 2010-05-11
well, after an hour downloading the ultimate boot cd and burning it twice to be sure, the comp will not boot from this cd. bios does not have an option for it. My guess is it's automatic when you put a disc in,but this one will not boot. I checked the website for solutions also.

Anymore suggestions?

---

### Post by GSF1200S on 2010-05-11
> **dustoff2010 said:**
> well, after an hour downloading the ultimate boot cd and burning it twice to be sure, the comp will not boot from this cd. bios does not have an option for it. My guess is it's automatic when you put a disc in,but this one will not boot. I checked the website for solutions also.

Anymore suggestions?

Im assuming you are using Ubuntu 10.04. What kind of video card do you have? Try going to System>Administration>Hardware Drivers and see if you can enable a video driver- should download them and configure them for you automatically. If nothing is there, open a terminal and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then (your desktop will restart, so please save anything open):
```
sudo /etc/init.d/gdm restart
```
and see if it complains about low graphics mode. Once again, it would help us to know what video card you have. This should get Ubuntu working at least.

And no, you do not have to install Ubuntu after you install Windows, its just more convenient that way. The reason is that Windows overwrites the MBR with its own bootloader, not taking in account any other operating systems on your computer. At this point, when you turn on the computer, it would boot straight to windows. You can however run an Ubuntu liveCD and reinstall grub 2 to the MBR- you can also chroot into your Ubuntu install and do the same.

---

### Post by dustoff2010 on 2010-05-11
Well, i took the plunge and restored windows. And restored my backed up files. I no longer have that distructive program "AYRECOVERY" Now I am going to do some catch up work online and in a few days start setting ubuntu up again.

Thanks for all the help.

---

