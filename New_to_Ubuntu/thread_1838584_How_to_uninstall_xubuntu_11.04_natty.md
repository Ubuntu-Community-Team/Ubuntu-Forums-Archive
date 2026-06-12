---
title: "How to uninstall xubuntu 11.04 natty?"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by WubiAR on 2011-09-03
Hi,
I have one computer that I wish to leave with just Windows 7 as its operating system and remove Xubuntu 11.04 natty (Please don't defame me; I like Ubuntu, but I want to have at least one machine with just Windows). How would I go about with doing this? I used OS-Uninstaller through Xubuntu to uninstall some other leftover Ubuntu copy, but I want to delete Xubuntu now. When I try to use it, it says something about a "live-CD", and closes.

---

### Post by cariboo on 2011-09-04
Just delete the Xubuntu partition, and use your Windows 7 install disk to remove grub2.

---

### Post by PatrickD-52761 on 2011-09-04
> **cariboo907 said:**
> Just delete the Xubuntu partition, and use your Windows 7 install disk to remove grub2.

To be more specific, you'll want to google something like "Troubleshooting Windows 7 startup" or "Repairing Windows 7 Startup". You don't need to use the entire install disc, per se. Just repair your startup.  

And, you can do the Reparing Windows 7 portion first. It won't recognize the Linux partitions at all, so it will automatically boot you into Windows. Then you can wipe the other partitions out.

Also, if you used Wubi to install Xubuntu, then you simply need to boot into Windows, and uninstall it via Add/Remove programs. That should take care of the bootloader also.  If not, then repairing your startup will fix that as well.

Hope this helps, and have a great weekend:)
Patrick.

---

### Post by PatrickD-52761 on 2011-09-04
> **WubiAR said:**
> Hi,
I have one computer that I wish to leave with just Windows 7 as its operating system and remove Xubuntu 11.04 natty (Please don't defame me; I like Ubuntu, but I want to have at least one machine with just Windows). How would I go about with doing this? I used OS-Uninstaller through Xubuntu to uninstall some other leftover Ubuntu copy, but I want to delete Xubuntu now. When I try to use it, it says something about a "live-CD", and closes.

One more piece of information might be needed. Exactly what does it say when you try to uninstall Xubuntu? You mentioned that it says something about a "Live CD", but without knowing exactly what that message is, we really can't advise you properly.

Assuming that your name is reflective of how you installed Xubuntu, you'll need to take care of it in Add/Remove Programs from Windows (or via the Live CD, if that's the message it's giving you).  Trying to delete the partition and running the Windows repair may break more than it fixes.

Have a great weekend:)
Patrick.

---

### Post by BKbroila on 2011-09-07
Sorry to somewhat hijack this thread, but I'm also in the same situation as OP.

So to get it straight, should I uninstall Xubuntu from within Xubuntu first, and then go into Windows and delete/reformat the partition that Xubuntu was on?

I'm just worried that I may screw things up and Grub (or Burg since I have that installed) will still be on my computer and screw with the startup

---

### Post by bcbc on 2011-09-07
You need to:
1) reinstall the windows bootloader
2) ensure that it boots straight into windows
3) delete the ubuntu partition

If you do 3) before 1) you get a grub rescue prompt.

For 1), from a windows repair prompt:
On XP run:  fixmbr
On Vista/7 run: bootrec /fixmbr

Or use lilo - you can do this from your Ubuntu install.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
(ignore warning screen when installing lilo - not an issue for this usage. Check that your drive is /dev/sda)

---

### Post by nipunshakya on 2011-09-07
> **WubiAR said:**
> Hi,
I have one computer that I wish to leave with just Windows 7 as its operating system and remove Xubuntu 11.04 natty (Please don't defame me; I like Ubuntu, but I want to have at least one machine with just Windows). How would I go about with doing this? I used OS-Uninstaller through Xubuntu to uninstall some other leftover Ubuntu copy, but I want to delete Xubuntu now. When I try to use it, it says something about a "live-CD", and closes.

Few weeks back, my friend too wanted to uninstall ubuntu and get have only windows 7 on his pc...and so i suggested him the following:
1. Boot the LiveCD of the same version of ubuntu.
2. Format the whole partition related to ubuntu using Gparted.
3. Restart the machine.
3. **Insert the windows 7 installation disk**..[B]and boot from it.
[/B]4. Run the startup repair tool from the installation disk...
5. Restart the machine.
6. Done.

The above process worked fine for my friend using ubuntu...don't have any idea regarding Xubuntu but i guess that should work similarly....goodluck

Regards,Winux User

---

### Post by macmike on 2011-09-07
I have installed, or attempted to, install Ubuntu 11.04 on an eMachines D620 laptop. I try to start the machine it comes up with the big E screen sets then recycles and back again. I assume something about the loader isn't right. I have tried reinstalling Ubuntu hoping to repair the loader. I don't have a Windows 7 disk to repair the windows loader. How do I get Ubuntu off and repair Windows so it will run?

---

### Post by nipunshakya on 2011-09-08
> **macmike said:**
> I have installed, or attempted to, install Ubuntu 11.04 on an eMachines D620 laptop. I try to start the machine it comes up with the big E screen sets then recycles and back again. I assume something about the loader isn't right. I have tried reinstalling Ubuntu hoping to repair the loader. I don't have a Windows 7 disk to repair the windows loader. How do I get Ubuntu off and repair Windows so it will run?

It seems your MBR has been disturbed...if you are using windows 7, i would suggest you to boot through that disk and just format the partitions reserved for ubuntu.

Alternatively, the link below might help you..
[http://www.howtogeek.com/howto/31804/the-10-cleverest-ways-to-use-linux-to-fix-your-windows-pc/](http://www.howtogeek.com/howto/31804/the-10-cleverest-ways-to-use-linux-to-fix-your-windows-pc/)
Goodluck
Regards,WunixUser

---

### Post by macmike on 2011-09-08
All well and good on starting through Windows 7 but I don't have a Windows 7 CD to start.  Should I be able to see the Ubuntu partition through Windows Explorer?

---

### Post by nipunshakya on 2011-09-08
> **macmike said:**
> All well and good on starting through Windows 7 but I don't have a Windows 7 CD to start.  Should I be able to see the Ubuntu partition through Windows Explorer?

Not at all, your ubuntu if your ubuntu isn't installed on a NTFS partition i guess...
you probably have ext3 or sth lyk that for your ubuntu installations isn't it?
However, There is a thing called Disk Management Utility inside windows 7. You should be able to see your Ubuntu partitioned drive as a **Primary partition** ,  but i suggest you not to work from there because Windows Disk Management  gets confused when the Linux  partitions are logical ones. It then calls them primary with the hazardous result that it can report more than 4 "primary" partitions on a  hard drive.
 
So its better if you start from the win 7 dvd installer and format everything and begin from scratch.........

OR you might surely want some help suggestions from others if you get confused doing that..

---

