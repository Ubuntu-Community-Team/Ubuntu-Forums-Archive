---
title: "cant install ubuntu"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by Ngo-Baheng on 2009-05-16
Hello guys,

Im trying to install linux in a dual boot with windows, when i change my boot priority to cd windows still starts so i tried installing the program to help boot from cd, i got an error, permission denied error, so im unable to install ubuntu.

Any help would be appreciated, thanks.

It created this log file when i received the error. Note i had to zip it because the txt file was too big.

---

### Post by OldTimeTech on 2009-05-16
Wubi is to be installed in Windows like another program...ie: photoshop, Office, etc.

If you want to install a dual boot of 9.04 you need to download the desktop version of Jaunty and not the Wubi version.

---

### Post by Ngo-Baheng on 2009-05-16
Hi,

Well i even tried installing it in windows and i still get the error when the install is about to complete.

Also i installed it on my laptop with no problems, this is my desktop.

---

### Post by TheNosh on 2009-05-16
how did you burn the CD? if you just put the ISO on the disk as a file rather than burning the disk image it won't work

---

### Post by Ngo-Baheng on 2009-05-16
Sorry, i just edited my post, i wrote:

Also i installed it on my laptop with no problems, this is my desktop.

It worked on my laptop but not on my desktop which is why im confused. My laptop now has dual boot although it is vista and this desktop is xp

---

### Post by LollYouSuckZor on 2009-05-16
> **TheNosh said:**
> how did you burn the CD? if you just put the ISO on the disk as a file rather than burning the disk image it won't work

My ex-girlfriends dad did that once.  I had to try my best not to laugh my a-- off at him.

---

### Post by OldTimeTech on 2009-05-16
All cds/dvds that you burn for unbuntu must be burned at a very slow rate 2x no more than 4x, because for some reason if not burned slowly they lose stuff...could be your problem

Might even be where your downloading it from....

But I guess first, I would re-download either the Wubi or the desktop from a different location and then burn it slowly to cd/dvd and try loading it again.

---

### Post by Ngo-Baheng on 2009-05-16
Nah i didnt just put the file onto the CD, i burnt it using nero :)

---

### Post by Ngo-Baheng on 2009-05-16
But it worked perfectly on my laptop so i dont think the download location or the way i burnt it to the cd is the reason for the error.

---

### Post by OldTimeTech on 2009-05-16
That could mean that the desktop wasn't set up properly. Or you could go to bios and make your cd your first boot there and see if will work better that way!

---

### Post by Ngo-Baheng on 2009-05-16
I made my CD boot to first priority and windows still started lol, i then even disabled the 2nd and 3rd boot priority so the only boot priority was CD and windows still even started!

---

### Post by OldTimeTech on 2009-05-16
hmmmmmm...I'm running out of thoughts...

Just cause I do strange things, I might be real tempted to back up files, wipe drive and reload operating system on this machine and then try making a dual boot with Jaunty.

---

### Post by Ngo-Baheng on 2009-05-16
Oh wow, so go to that extreme lol, i think i'll just have to use linux on my laptop then :( Or i will try jaunty, where can i download it from because i got the wubi from the home page, i didnt even see an option for the jaunty download.

---

### Post by Hairybudda on 2009-05-16
Update the BIOS on your desktop, if it still doesn't work you can either a) Use unetbootin to install from HDD (although installing from a flash drive is much better especially if you only have one hard disc on your system) or you can do the wubi install on your windows partition and then move the install to a dedicated partition of its own. I've did these a couple of times myself mostly because I'm too lazy to go to the shop for CDs

---

### Post by OldTimeTech on 2009-05-16
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

Try this url

---

### Post by Ngo-Baheng on 2009-05-16
Yea i couldnt even install the wubi onto my exsisting windows partition because i got that error message.

I dont know how to update my BIOS and what is unetbootin?

---

### Post by Ngo-Baheng on 2009-05-16
> **OldTimeTech said:**
> [http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

Try this url


Thats the one i downloaded that came with wubi :)

---

### Post by OldTimeTech on 2009-05-16
Here's another URL

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Ngo-Baheng on 2009-05-16
Yea thats the same install lol. Anyway i dont think its that because as i said, it worked on my laptop, i think theres something wrong with my desktop so i dont know what else to do but other then use linux on my laptop only :(

---

### Post by OldTimeTech on 2009-05-16
To change your bios, when your machine is first booting up you should see a screen that says F10 or DEL to get into bios...when you use which ever of those keys it needs it opens your bios up...you will see things like date, time....but up at the top it should say boot setup or just boot...this where you go to make your cd/dvd the first boot choice.

---

### Post by Ngo-Baheng on 2009-05-16
Yea i did that as i said in a previous post, i even made CDROM the ONLY boot priority and windows still started :s

---

### Post by OldTimeTech on 2009-05-16
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

This is where unetbootin is explained and can be downloaded.

---

### Post by Duskao on 2009-05-16
Did you by chance download the 64 bit version? Maybe your desktop doesn't have a 64 bit processor. And to be honest, you probably want to get a new 9.04 download and reburn it to a disc just to be sure, and don't try to install it from within windows. Pop in the disc and boot up the computer. If it doesn't read the disc then you will need to change the BIOS of the computer, but most have read from cd as the default. Then it will walk you through the installation process and it will easily allow you to make a dual boot with both windows and ubuntu. Just make sure you change the slider during the partition phase of the installation so that you don't end up with 100 megs more then what the ubuntu installation requires so you can't install anything on it (accidently did that one time when trying 64 bit ubuntu LOL).

Edit: and make sure you download the Live version, should be the default from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Ngo-Baheng on 2009-05-16
So which one do i download? windows version or linux version (because im on windows now but will be putting linux on it)

---

### Post by Ngo-Baheng on 2009-05-16
Duskao - I installed it perfectly on my laptop (which isnt a 64bit processor) so i dont think there is anything wrong with the download or the way i burnt it to my CD. As i have said, i changed the boot priority and still had no luck, windows takes over all the time :(

---

### Post by OldTimeTech on 2009-05-16
Give specs on Desktop, please

---

### Post by Ngo-Baheng on 2009-05-16
<<< System Summary >>>

  > Mainboard : Gigabyte GA-MA770-UD3

  > Chipset : AMD RD770

  > Processor : AMD Phenom X4 9750 @ 2400 MHz

  > Physical Memory : 4096 MB (2 x 2048 DDR2-SDRAM )

  > Video Card : NVIDIA GeForce 9800 GTX+

  > Hard Disk : Hitachi (500 GB)

  > DVD-Rom Drive : HL-DT-ST DVD-RAM GH22NS30

  > DVD-Rom Drive : IFYT MVKHQ7C5A SCSI CdRom Device

  > Network Card : Realtek Semiconductor RTL8168/8111 PCI-E Gigabit Ethernet NIC

  > Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 3

  > DirectX : Version 9.0c  (July 2008)

---

### Post by Hairybudda on 2009-05-16
When I told you to update your BIOS i meant go to your motherboard manufacturers site and download an up to date bios image and flash it ([http://www.gigabyte.com.tw/Support/Motherboard/BIOS_DownloadFile.aspx?FileType=BIOS&FileID=14507](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_DownloadFile.aspx?FileType=BIOS&FileID=14507)). Once you've done that try booting again, try both drives to boot from too.

---

### Post by Ngo-Baheng on 2009-05-16
What do you mean by flash it? I've downloaded the update and extracted the file, what do i do then?

---

### Post by Hairybudda on 2009-05-16
flashspi.exe in that archive is an application for flashing the BIOS ROM on your motherboard, I'm running Ubuntu right now so I can't check however it will probably be a DOS program, you'll need to figure out how to flash it yourself because I am not familiar with the application.

---

### Post by NHArticleTen on 2009-05-16
> **Ngo-Baheng said:**
> Yea i did that as i said in a previous post, i even made CDROM the ONLY boot priority and windows still started :s

It's great that you feel comfortable working with the BIOS settings just remember to save them(just changing the setting itself won't actually make any changes...until you save)

Also, it should be noted that a poorly burnt CD(usually burnt too fast) may very well work in one CD/DVD...but not in another.

Make no assumptions.

---

### Post by Ngo-Baheng on 2009-05-16
Yea im pretty comfortable with the BIOS and windows, i want to move over to linux slowly but it seems my desktop is stopping me :(

---

