---
title: "GRUB bootloader problem"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by thatsloankid on 2010-07-30
Hi,
My friend installed ubuntu netbook 10.04 on his asus eee pc using wubi installer. It all installed fine and worked for about an hour or so until he restarted his computer. When his computer started back up it booted straight to this:
error: no such device: 5f82c49c-f3c4-4270-8241-cde1927c4061
grub-rescue>
but the strange thing every command he types in doesnt work we have been trying to find a solution for several hours but we have no luck.It would be helpful if anyone could post anything that might help or advance us in finding a solution.
Thanks

---

### Post by bcbc on 2010-07-30
> **thatsloankid said:**
> Hi,
My friend installed ubuntu netbook 10.04 on his asus eee pc using wubi installer. It all installed fine and worked for about an hour or so until he restarted his computer. When his computer started back up it booted straight to this:
error: no such device: 5f82c49c-f3c4-4270-8241-cde1927c4061
grub-rescue>
but the strange thing every command he types in doesnt work we have been trying to find a solution for several hours but we have no luck.It would be helpful if anyone could post anything that might help or advance us in finding a solution.
Thanks

You have the grub bootloader in your harddrive MBR (master boot record). With wubi dual boots, you need the windows bootloader. You can either repair it with a windows repair disc or you can install an equivalent bootloader from an ubuntu 'live cd/usb':
1.Boot from an Ubuntu cd/usb and select 'Try without installing'
2.Then click on 'Applications, Accessories, Terminal' 
3.Run
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

When you install lilo a screen will popup with some info. Hit Enter. The warnings you see refer to a different use of lilo.

---

### Post by ellabee on 2010-08-02
i used a windows vista recovery and followed the directions in this post 

[http://ubuntuforums.org/showthread.p...ghlight=device]("http://ubuntuforums.org/showthread.php?t=1542770&highlight=device")


worked like a charm and now all of my OS's are available for boot and no grub recovery.:p

---

### Post by thatsloankid on 2010-08-03
Thanks it worked like a charm!

---

### Post by Robert A. Morin on 2010-08-04
Right, I did the LILO thing, and it did work, however, it gives me a warning that there was "No Active Partition."  However, it does refer me to the Windows Bootloader, which is most likely better, so no harm no foul.

---

### Post by bcbc on 2010-08-04
> **Robert A. Morin said:**
> Right, I did the LILO thing, and it did work, however, it gives me a warning that there was "No Active Partition."  However, it does refer me to the Windows Bootloader, which is most likely better, so no harm no foul.

You need to set the boot flag on the windows partition for this type of bootloader to work. You must have some other issue if the boot flag is not set correctly, but this is fixable. Why don't you post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by another_sam on 2010-12-31
On yesterday, a regular update of an Ubuntu 10.04 installed from Wubi left me with a nice grub rescue console and some nice homicidal feelings.

FYI, the console was preceded by 
error: no such device: 8bbc4f70-.....

At
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Grub%202%20gives%20%22error:%20no%20such%20device:%20xxxxx.xxxxx.xxxxx.xxxx%22](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Grub%202%20gives%20%22error:%20no%20such%20device:%20xxxxx.xxxxx.xxxxx.xxxx%22)
I found
sudo update-grub2
but it did not work.

By contrast,
> **bcbc said:**
> 
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

did work.

The world is now a better place to live in thanks to bcbc.

---

