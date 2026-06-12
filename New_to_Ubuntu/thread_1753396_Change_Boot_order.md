---
title: "Change Boot order"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2011-05-08
So, I absolutely love Ubuntu and I want my system to automatically boot into it when I start my computer. So I need to know how to change the order that appears right now. 

I have read the [Grub How To]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") However when /boot/grub/menu.lst is pulled up it is blank and I cannot rearrange anything, owing to the fact that there is nothing there.

I think this may be caused by the fact that I installed it using wubi inside windows. Any help anyone could provide would be very gratefully received.

Best,
Jeff

---

### Post by drs305 on 2011-05-08
You are now using Grub 2, which has a completely different file structure.

You can take a look at various links in my signature line. 'Basics' will probably be too much information, but if you have a question it might have the answer. 

'Tasks' will probably explain how to do what you want.

And 'Customizer' will tell you how to install and run a good GUI app that can make the changes without you needing to get into manual editing of the configuration files.

---

### Post by Jeff.Smith on 2011-05-08
> **drs305 said:**
> 
And 'Customizer' will tell you how to install and run a good GUI app that can make the changes without you needing to get into manual editing of the configuration files.

I will take the customizer option good sir, less work the better.

---

### Post by frank604 on 2011-05-08
I am not on my ubuntu partition so this is just from my head, so excuse me if the information is incorrect.

Edit the grub config:
sudo nano /etc/default/grub

change the # in  'GRUB_DEFAULT=0' to the partition you want (0 is the first boot selection, 1 is the 2nd boot selection)

If your boot menu is, 

Windows
ubuntu
ubuntu fallback

Then windows = 0, ubuntu = 1, ubuntu fallback = 2, etc.

Next step is to change grub_timeout=# to the number of seconds you want.  Change it to 1 or 2 seconds so it automatically loads ubuntu but also gives you that second or two to boot into another OS if you need to.  Or not. Up to you.

Save it by pressing Control + X, hit Y for yes, then enter

Now you have to update your grub, type:

sudo update-grub

And reboot to test:

sudo reboot

---

### Post by Jeff.Smith on 2011-05-08
Thanks for the reply but I think the GUI fix is best for a noob like me. Also, I think I run into the same problem with the nano. I run the command 

```
sudo nano /etc/default/grub
```

in the terminal and there is nothing to edit.

I do have a question about the GUI Grub Customizer though. If I completely hide the Windows boot option it wont completely wreck my computer or anything will it? I don't know why it would but I've messed around with this stuff enough to know it is better to ask first.

best,
Jeff

---

### Post by frank604 on 2011-05-08
I actually walked to my laptop to look at the grub file in ubuntu 11.04, it is indeed there as /etc/default/grub

strange...  you are on 11.04 with grub 2 yes?

---

### Post by Jeff.Smith on 2011-05-08
> **frank604 said:**
> I actually walked to my laptop to look at the grub file in ubuntu 11.04, it is indeed there as /etc/default/grub

strange...  you are on 11.04 with grub 2 yes?

Whoops, I was using 
```
/boot/grub/menu.lst
```
My mistake.

---

### Post by frank604 on 2011-05-08
So does the changes work for you?

---

### Post by Jeff.Smith on 2011-05-09
Here is a screenshot of what comes up for me when I execute your commands. I didn't see anything for windows that I could move around. All I see is linux stuff.

Also the grub customizer did not hide my windows bootup option, so on the whole, no, I'm still having problems.

---

### Post by frank604 on 2011-05-09
The grub_timeout="10" means that when you reboot your computer, it should display a boot menu for 10 seconds showing you boot selections.

The grub_default="0" means that it is selecting the first boot selection from the menu shown at boot.

You will have to modify these values to the ones you want.

---

### Post by Jeff.Smith on 2011-05-09
> 
The grub_default="0" means that it is selecting the first boot selection from the menu shown at boot.


So changing the grub_default to "grub_default="1"" would change it to boot into ubuntu by default? How do I know that Ubuntu is listed as 1? I hate messing around in grub...

---

### Post by frank604 on 2011-05-09
The easiest way to find out what the number value is to reboot, look at the grub boot menu at startup.  It should list something like:

Ubuntu
Ubuntu Fallback
Memtest
Windows 7

The values for grub_default start at 0, so ubuntu =0, ubuntu fallback= 1, memtest=2, windows 7=3

I am unsure which value is your Ubuntu.  Just reboot and see.  Then change your grub configuration.

---

### Post by shuttleworthwannabe on 2011-05-09
alternatively install Startupmanager from synaptic; fire it up after installation (just search for it in applications) use this GUI tool to select the OS you want to boot on system boot up. Hope this helps,

SWB

---

### Post by Jeff.Smith on 2011-05-09
Thanks guys I think this is /completed.

---

### Post by frank604 on 2011-05-09
awesome and congrats

---

### Post by drs305 on 2011-05-09
> **Jeff.Smith said:**
> Also the grub customizer did not hide my windows bootup option, so on the whole, no, I'm still having problems.

Did you untick the Windows menu entry in Grub Customizer and then press Save?

Another way is to turn off the os-prober, which will prevent Grub from looking for operating systems on other partitions. If you only want to see your main Ubuntu options, you have several ways of doing it:
[LIST]
[*]Unticking os-prober in Grub Customizer (all the entries within that category will not be displayed).
[*]Turning off the executable bit of the 30_os-prober file in /etc/grub.d
[*]Adding a line to disable os-prober in /etc/default/grub
[/LIST]

There is another way where you can have a blank line represent Windows so it's available but not visible. It's a bit sneaky but it's easy to do.

If you want to do any of those options I can tell you how.

---

### Post by Jeff.Smith on 2011-05-09
Well I'm pretty sure it's all on the same partition since I used Wubi to install it. Isn't that the whole idea of wubi? to keep you from having to partition your hard drive?

> Did you untick the Windows menu entry in Grub Customizer and then press Save?

Another way is to turn off the os-prober, which will prevent Grub from looking for operating systems on other partitions. If you only want to see your main Ubuntu options, you have several ways of doing it:
Unticking os-prober in Grub Customizer (all the entries within that category will not be displayed).
Turning off the executable bit of the 30_os-prober file in /etc/grub.d
Adding a line to disable os-prober in /etc/default/grub

Yeah I unticked the os-prober option, as well as every option underneath it. Windows still shows up and it is still on top of ubuntu (despite the fact that I moved it down to be below ubuntu).

> There is another way where you can have a blank line represent Windows so it's available but not visible. It's a bit sneaky but it's easy to do.

That would be really great actually.

---

### Post by drs305 on 2011-05-09
> **Jeff.Smith said:**
> Well I'm pretty sure it's all on the same partition since I used Wubi to install it. Isn't that the whole idea of wubi? to keep you from having to partition your hard drive?

I either didn't know or forgot you were using WUBI. Since WUBI is a file within Windows, you would have to go through that OS to get to WUBI. 

That doesn't mean you have to *see* a Windows entry. Depending on your version of Windows, you can edit the boot.ini file or use BCDedit to modify the Windows bootloader. I'm not a Windows guy so that is about all the info I can provide.

If you really want to bypass Windows completely, install Ubuntu on it's own partition.

---

