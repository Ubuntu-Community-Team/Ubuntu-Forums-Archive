---
title: "Newish Netbook, Security Compromised. Uninstall Windows and wipe, add Ubuntu. How?"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by falldownstumble on 2011-04-23
Hello,
I'm not sure I can figure out this process on my own, so I'd like someone who knows more than me to advise me if they can!

I bought an HP netbook when I was traveling in Bangkok.  The guys in the Electronics market there installed Windows 7 on it for me.  The purchase was maybe not the greatest decision in retrospect.  Anyway, at some point in my travels, somehow unknown to me but possibly through unsecured wireless, somebody got into my Gmail account and changed the password and did embarrassing things with it.  I started a new email account, and a couple weeks later the same thing happened.  I downloaded and ran all kinds of virus killers, keylogger-searchers, registry cleaners, etc, but didn't find a "culprit."  I stopped using the netbook entirely because I just can't trust it.

But alas, my trusty old laptop is on its last legs, and I want to get the netbook up and running to replace it.  So my idea to be sure every potential threat is gone from it, (and that I avoid them in the future), is to wipe it completely, including Windows 7 obviously, and install Ubuntu and start a new way of life!

Since I don't trust that computer in its current state to be connected to the Internet, I'm downloading Ubuntu to this old laptop and putting it on a USB stick.  From there, though, I'm not confident about how to get it onto the netbook.  After I wipe it and remove Windows, what happens?  Also, all the Googling I'm doing for "how to wipe a computer" etc keeps pointing me to articles that want me to use my Windows recovery disks.  No thank you!  DNW!  But I can't find how to just straight up wipe everything including Windows.

I'd appreciate a little guidance! Thanks very much!

---

### Post by mapes12 on 2011-04-23
Hi

To completely erase disks I use [http://www.killdisk.com/](http://www.killdisk.com/)

If you can get it onto a USB stick then boot from it then it will do the job. You can then boot from the USB stick where you have the UBU install and you should be good to go.

---

### Post by fballem on 2011-04-23
You will probably want to zero the drive (set all bits on the drive to zero) on the new laptop before you install ubuntu. 

[http://www.cmich.edu/Financial_Services/Financial_Information_Systems/FIS_Tech_Sheet/GW_Scan_Hard_Drive_Tool.htm](http://www.cmich.edu/Financial_Services/Financial_Information_Systems/FIS_Tech_Sheet/GW_Scan_Hard_Drive_Tool.htm)

The link points to a place where you can download a utility that has several options, including one to zero the drive.

You may have a hidden partition on the drive that contains the restore facility for the laptop. This should also be removed if you are CERTAIN that you do not want to go back to windows.

Once you have downloaded ubuntu onto the USB stick, you will need to change your bios to boot from the USB stick. Not sure how you enter bios settings on your laptop (it varies from machine to machine). Pressing the key during the boot process will normally allow you to enter your bios. You are looking for a setting called Boot Order or Boot Priority. Make sure that the USB is set to boot before the hard disk.

Hope this helps,

---

### Post by mikewhatever on 2011-04-23
Once you put Ubuntu on the USB stick, just boot from it. I hope that computer can boot from USB. There is no need to wipe the computer separately, as the Ubuntu installer can do it in the process.

---

### Post by yetiman64 on 2011-04-23
You have the tools to zero a drive on the live cd / usb, they are the shred or dd commands used in terminal.

 [[COLOR=Blue]See this link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1731099").  

In the link the person may have wanted to erase a partition only, you want to do the whole drive so use /dev/sda. 
I also mention the steps required to put back a partition table when wiping the whole drive, take note of them. Gparted is also available on the live cd image. No need for 3rd party tools off the internet.

Edit: I agree with mikewhatever's post, just use the installer to overwrite the whole drive.

---

### Post by Locke_99GS on 2011-04-23
Ubuntu itself is *relatively* secure out-of-box compared to Windows. After you install it, I'd also recommend you use Firefox 4 (it has Strict Transport Security methods built in) and, when possible, try to stick to WPA wireless networks. If you have to use an open, public, wifi network, avoid going to any sites that require login credentials - even if you don't have to re-enter them. WEP is better than open, but is easily breakable.

---

### Post by falldownstumble on 2011-04-23
Wonderful.  I will try just overwriting everything with the installer.

Thanks for everyone's responses! :)

---

