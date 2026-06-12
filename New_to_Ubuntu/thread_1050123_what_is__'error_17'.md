---
title: "what is  'error 17'"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by kaykav on 2009-01-25
good morning,
              A slight boot loader problem; My first status was
 Windows (vista premium), ubuntu 8.04 & linuxmint 6. I upgraded vista (clean install).  My next status was Windows (vista ultimate)
only. Evedently I lost grub. I then put linuxmint (live cd) in and installed  grub. I got linuxmint ,but not ubuntu. The boot menu showed all three systems (windows,linuxmint,ubuntu). I got 'error 17' when trying to boot into ubuntu.It stated 'could not mount ubuntu'. I searched all forums for a solution for an understandable solution, to no avail. I then reinstalled ubuntu using ,my 'alternative disc,(not a live cd). It installed great,even saved my profiles. What went wrong? how did the reinstall correct the problem  (mounting ubuntu)? Any thoughts on this would be enlightening.   Thank you..Rich

---

### Post by caljohnsmith on 2009-01-25
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by ubername on 2009-01-25
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

Provides a useful ubuntu related search facility using google.

Although you indicate that the problem has gone away, I have used the 'trial and error' method of editing the grub command lines when the computer is booting. At the grub menu select the option which is giving you problems and push 'e'. This will show the commands that the option will execute. Then mess about with anything that says e.g. (hd0,0) and change it to e.g. (hd1,0) The numbers represent the hard drive and partition that the boot will look for . In my case I have my BIOS set to boot from a USB drive first so (hd0,0) is the first partition on my USB drive which has Ubuntu on it. I also have a hard drive (no surprise there) so this is referred to as (hd1,0) for the windows install and (hd1,1) for the Ubuntu install on that drive.

---

### Post by oldos2er on 2009-01-25
When you [FONT=Arial]upgrade[/FONT]d Vista, no doubt it overwrote your MBR, no more grub. And for some reason when you reinstalled grub from Mint it failed to accurately recognize your Ubuntu partition.

 When Win* (or whatever) destroys the MBR, you can use Super Grub Disk ([www.**supergrubdisk**]("http://www.%3Cb%3Esupergrubdisk%3C/b%3E").org) to reactivate it; there's no need to reinstall an entire OS.

---

### Post by kaykav on 2009-01-26
I went to super grub web site. I found it very difficult to download the iso application. Maybe I got annoyed too fast. I'll try again. Also I downloaded that 'info script' (very nice app),
 I will send it to 'caljohn' asap.  Thank you all ...Rich

---

