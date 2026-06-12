---
title: "Wont go to menu to chose from Ubuntu or Windows"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by bocephus5781 on 2010-01-26
Hi, This is my first time using Ubuntu and all I want to do is experiment with it to see if I like it better than windows.  I just reformated my hard drive and installed windows xp media center edition.  At the moment im trying to set it up to where I can chose if I want to go into Ubuntu or Windows from startup which is the same thing wubi does but i used the CD i made from the iso file instead.  Ubuntu seamed to have installed properly as far as i know. I just cant startup Ubuntu because the option to start it never comes up. any ideas?

---

### Post by drzoo2 on 2010-01-27
> **bocephus5781 said:**
> Hi, This is my first time using Ubuntu and all I want to do is experiment with it to see if I like it better than windows.  I just reformated my hard drive and installed windows xp media center edition.  At the moment im trying to set it up to where I can chose if I want to go into Ubuntu or Windows from startup which is the same thing wubi does but i used the CD i made from the iso file instead.  Ubuntu seamed to have installed properly as far as i know. I just cant startup Ubuntu because the option to start it never comes up. any ideas?

After you reformatted did you install Ubuntu first or Windows first? 
Did you partition for more than 1 partition? Would have needed 2 or when installing Ubunutu you would have had to resize the existing. 

If you installed Ubunut first, it installed grub to your master boot record. (Grub is the boot manager) Then when you installed Windows, it rewrote the Master Boot record with it's own boot manager. Windows won't see an OS that isn't another windows install so it won't give you a boot menu. 

OR 

You had one partition. Installed Ubuntu, Then installed Windows over it.

The easiest way to install Linux with Windows is to install Windows first on one partition, Then Linux on another. Grub plays nice with other OS's and will give options for both.
z

---

### Post by bocephus5781 on 2010-01-27
I didnt partition at all... I installed windows first then I poped the ubuntu cd in it had the option to install ubuntu alongside windows i selected that and installed it... from what I understood it did the same thing wubi does... which btw did the same exact thing its doing now... but at the moment it has ubuntu in my add/remove programs list file size 20.7gbs (i chose 20gb). That being there I would say its the same way wubi does it... btw i tried partitioning my hard drive and it froze midway then I tried fully installing ubuntu and it froze midway as well. Then i reformatted again and installed windows xp again ran the installer but it still will not bring up that menu on startup.

---

### Post by 3rdalbum on 2010-01-27
Wubi uses a different method for installing than the live CD. If you have already got a Wubi installation, you should remove it from Windows' Add/Remove Programs, and then edit your Windows bootloader to no longer pop up. (Google should be able to help you there).

When you install Ubuntu on the live CD, it will override the Windows bootloader with its own GRUB bootloader. GRUB will give you the option to boot into Ubuntu, or into Windows.

---

### Post by drzoo2 on 2010-01-27
> **bocephus5781 said:**
> I didnt partition at all... I installed windows first then I poped the ubuntu cd in it had the option to install ubuntu alongside windows i selected that and installed it... from what I understood it did the same thing wubi does... which btw did the same exact thing its doing now... but at the moment it has ubuntu in my add/remove programs list file size 20.7gbs (i chose 20gb). That being there I would say its the same way wubi does it... btw i tried partitioning my hard drive and it froze midway then I tried fully installing ubuntu and it froze midway as well. Then i reformatted again and installed windows xp again ran the installer but it still will not bring up that menu on startup.

Did you try installing Ubunutu from Windows or did you boot from the Ubunut live CD?

Easy method since your starting from scratch. 
You will need two partitions.
Install Windows first. When you get to partition and formatting section on the Windows install, Create two partitions. Leave about 20GB atleast for Linux. Just format the first partition for Windows. Leave the other alone. 
Finish Installing windows. 

You should have a Windows install on one and an empty partition for Linux. IF you go into the Windows drive manager you should see an empty partition.

Stick the Linux live CD in and boot from that. Select install Ubunutu.
When you get to the format and partition section do not select use entire disk. Use the guided selection. This should see the Windows install and use the empty partition. Once this finishes installing a reboot will show the grub menu that you can use to select which OS you want to boot.

The Grub menu is displayed before ANY OS is booted. This is a boot manager.

z

---

### Post by garvinrick4 on 2010-01-27
So you think you are installing Wubi but you told it to reside along side XP. Now did you just pop in the CD and tell it to install or did you put the CD in the tray and reboot so you
booted off the CD? It is important so think about it.

---

### Post by bocephus5781 on 2010-01-27
I put the cd in and installed while i was in windows.... i did not install wubi im just saying it seamed like it installed like wubi.

---

### Post by J V on 2010-01-27
it did... If the menus gone its not buntus fault, its windows fault, get a real install and it will work...

---

### Post by Bartender on 2010-01-27
> **bocephus5781 said:**
> I put the cd in and installed while i was in windows.... i did not install wubi im just saying it seamed like it installed like wubi.

See, this indicates you need to do a little more research.  If you installed Ubuntu with Windows already up and running then you DID install wubi.  wubi runs within Windows, or inside of Windows, or underneath Windows, whatever...

I agree with JV.  I don't like wubi, and won't waste my time with it.  Do a "traditional" dual-boot and you should be good to go.

---

### Post by PhoHammer on 2010-01-27
> **Bartender said:**
> I don't like wubi, and won't waste my time with it. 

May I ask why? I usually do traditional dual-boots, but I am using a MacBook now, 
dual-booting Mac OS X 10.6 and Win7. I figured I might save some trouble by just 
"wubi-ing" some ubuntu on there under Win7, but you seem like you know something I 
don't about wubi.

---

### Post by J V on 2010-01-27
Unlike bartender, I don't hate wubi... lack of hibernation isn't that big of a deal, the biggest problem is getting a file setup in windows big enough for a swap or extra drive etc...

---

