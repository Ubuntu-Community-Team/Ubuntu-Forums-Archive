---
title: "Corrupted MBR"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Corrupt3d on 2009-02-06
Hello, I have a laptop on which I was happily dual booting Ubuntu & XP. However I decided to give the computer to my sister and decided to remove Ubuntu and just leave XP. I probably should of looked up the correct method or removing Ubuntu, but I didn't...

Anyway, I booted from an USB stick and ran G-parted, and proceeded to delete the Ubuntu & Swap Partitions. Upon restarting my computer, GRUB was corrupted and gave me "error 22" :(, I tried looking up solutions and all told me to fix the master boot record (MBR) by popping in a windows install disc and typing "fixmbr" in recovery mode. 

The restore disc that came w/ my computer doesn't give me that option, instead it just reinstalls the entire system. I tried doing just that, and like 3 hrs later when it was done I rebooted and got "NTLDR is missing". Is there any way to fix this from an Ubuntu Live Cd, or any other solutions?

Edit: If all fails? Would buying Windows Vista (It's like $30 at my Univ.) & reinstalling that, fix it?

---

### Post by 2hot6ft2 on 2009-02-06
You might try downloading and using the free vista recovery cd here.
[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)
it should work for repairing the mbr on xp too just get the 32 bit one.

---

### Post by hansdown on 2009-02-06
Hi Corrupt3d.

$30 for a vista install disk is $200 cheaper than my buddy just paid.

It will re-install no problem, unless you need drivers first.

---

### Post by caljohnsmith on 2009-02-06
Actually you don't even need a Windows Install CD to reinstall a Windows MBR to your HDD. You can do it from your Ubuntu Live CD by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Let me know how that goes or if you run into problems.

---

### Post by Corrupt3d on 2009-02-06
Thanks for all the help, but I'm not having any luck. 

I tried the link 2hot6ft2 gave me, I went there, downloaded and burned the .iso, but when I finally got to a command line it gave me "fixmbr is not recognized as a internal or external command...", I also tried fdisk /mbr. 

The second thing I tried was Super Grub, ([http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)). I followed all the steps and it told me it had succeded but didn't work at reboot. 

Lastly, I tried what caljohnsmith suggested. But still get "NTLDR is missing, Press Ctrl + Alt + Del to restarts". If I boot from an USB, all the files and partitions seem to be correct.

I saw another suggestion here : [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/), which also uses an ubuntu live cd along w/ ms-sys but haven't tried it yet.

---

### Post by sandyd on 2009-02-06
maybe this?
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by mpl34 on 2009-02-07
for vista it uses a tool called bootrec.exe therefore you may need to use the command 
```
bootrec.exe/ fixmbr
bootrec.exe/ fixboot
```
(from memory)

---

### Post by linuxuser21 on 2009-02-07
Do you have the Ubuntu Live CD?

---

### Post by evilempire on 2009-02-07
Boot back up off of that Windows cd, start the console, and run fixmbr. That should do the trick.

---

### Post by caljohnsmith on 2009-02-07
Corrupt3d, it sounds to me like you have more of an issue than just reinstalling a Windows MBR in order to boot into Windows again. It would help to get a clearer picture of your setup, so how about booting your Ubuntu Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Corrupt3d on 2009-02-07
Thanks for all the suggestions, I finally fixed it.

I ended up borrowing a proper install disc from my friend, and then used my own serial to reinstall the OS. The recovery discs that come w/ most computers are hopeless, they take forever to 'restore' the computer and don't even work right half the time. Still I learned my lesson and I'll double check what I'm doing before I start messing w/ partitions in the future. Now I can finally give my comp to my sis and I can go back to Ubuntu :)

Edit: I can't seem to find "solved" under Thread Tools.

---

