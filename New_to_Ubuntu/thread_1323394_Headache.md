---
title: "Headache"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by Mag1cN1nja on 2009-11-11
I been working on this for about 6 hours now, prolly 8 hours. Went through 3 boot discs and 1 usb drive. Im currently running a live session from the fourth disc. But whenever i try to install it it wont let me adn it gives me errors everytime. Does ne one know how i could fix this problem. The hard drive im trying to install ubuntu on is a 80 gig western digital. It has some files on it from a previous attempt to install ubuntu on it. If someone has an aim and can assist me that way it would help alot. But i cant sleep until i have ubuntu correctly installed on this drive. (before installing ubuntu it was a clean harddrive that i recently formatted.)

---

### Post by 73ckn797 on 2009-11-11
Did you burn the CD's at the slowest speed? Did you check the "md5sums" on the downloaded file before burning to disk? 

md5's:
                          ```
 

 836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe
```Go to Applications/Accessories/Terminal and open Terminal.

Enter the following command:

```
md5sum ubuntu.iso
```The "ubuntu.iso" will be the name of the downloaded iso, such as "ubuntu-9.10-desktop-i386.iso". You should preface the file name with the correct folder where the file is at. Example: /home/yourname/desktop or where ever it is at.

---

### Post by Mag1cN1nja on 2009-11-11
> **73ckn797 said:**
> Did you burn the CD's at the slowest speed? Did you check the "md5sums" on the downloaded file before burning to disk? 

md5's:
                          ```
 

 836440698456aa2936a4347b5485fdd6 *ubuntu-9.10-alternate-amd64.iso
3faa345d298deec3854e0e02410973dc *ubuntu-9.10-alternate-i386.iso
dc51c1d7e3e173dcab4e0b9ad2be2bbf *ubuntu-9.10-desktop-amd64.iso
d91659de6e945dbb96eb8970b2b4590a *ubuntu-9.10-desktop-armel+dove.img
297875d2a7531824a0fb08f241d33e85 *ubuntu-9.10-desktop-armel+imx51.img
8790491bfa9d00f283ed9dd2d77b3906 *ubuntu-9.10-desktop-i386.iso
ed6e77587b87fe0d92a2f21855869f00 *ubuntu-9.10-netbook-remix-i386.iso
14707e8847b9c9ba2dd1869fb5086e4f *ubuntu-9.10-server-amd64.iso
55618ad5f180692f9dac20cbff352634 *ubuntu-9.10-server-i386.iso
37a04db193b1a342f961f59aea2fada8 *wubi.exe
```Go to Applications/Accessories/Terminal and open Terminal.

Enter the following command:

```
md5sum ubuntu.iso
```The "ubuntu.iso" will be the name of the downloaded iso, such as "ubuntu-9.10-desktop-i386.iso". You should preface the file name with the correct folder where the file is at. Example: /home/yourname/desktop or where ever it is at.

im running the live session on the cd right now, i dont have the hard drive plugged in with the iso on it. Im running my other hard drive right now. Should i switch over right quick so u can walk me through this. And im out of blank cds, so maybe u can walk me through how to do it from jump drive. (i read all the tutorials and followed instructions) But now my computer wont let me format my jump drive

---

### Post by waspbr on 2009-11-11
if you are out of blank cds then you might want to use [unetbootin]("http://unetbootin.sourceforge.net/"). I installed ubuntu in a machine yesterday through it. 

I won't be able to talk you through it since it is late here, but hopefully someone will

---

### Post by 73ckn797 on 2009-11-11
> **Mag1cN1nja said:**
> im running the live session on the cd right now, i dont have the hard drive plugged in with the iso on it. Im running my other hard drive right now. Should i switch over right quick so u can walk me through this. And im out of blank cds, so maybe u can walk me through how to do it from jump drive. (i read all the tutorials and followed instructions) But now my computer wont let me format my jump drive


I have never tried the jump drive stuff so would be of very little help.

---

### Post by Mag1cN1nja on 2009-11-11
well i need some kind of help, i can get into ubuntu from a live session disc, but cant install from a disk, ne ideas of what to do from there once im in ubuntu

---

### Post by wojox on 2009-11-11
What are the errors it's giving you?

---

### Post by Mag1cN1nja on 2009-11-11
> **wojox said:**
> What are the errors it's giving you?

its different every time. I just reformatted my jump drive. Can u link me to a ubuntu download that is compatible with the usb install method .

---

### Post by waspbr on 2009-11-11
just a regular iso from the ubuntu website
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by wojox on 2009-11-11
[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by bodhi.zazen on 2009-11-11
> **Mag1cN1nja said:**
> its different every time. I just reformatted my jump drive. Can u link me to a ubuntu download that is compatible with the usb install method .

Any of the desktop disks can be put on a USB (via unetbootin or other method).

When you first boot the disk, run the option to check the integrity of the media.

If you are getting a different error message each time my guess would be that you have a bad quality burn.

---

### Post by Mag1cN1nja on 2009-11-11
> **bodhi.zazen said:**
> Any of the desktop disks can be put on a USB (via unetbootin or other method).

When you first boot the disk, run the option to check the integrity of the media.

If you are getting a different error message each time my guess would be that you have a bad quality burn.

well im reburning the img to the jump drive, my only jump drive is an 8 gig so it takes a bit longer and will get back to you after i try it

---

### Post by waspbr on 2009-11-11
unetbootin is definately the easiest method, I normally download the iso myself from the ubuntu website and run unetbootin in windows. 

Since you have formated the usb-drive, all you need to do is select the disk image option and browse to the iso that you have downloaded.

below select the letter corresponding to you usb-drive, just make sure is the right one, and press ok, everything is then going to go automatically. 

when it is done it will ask you to reboot, do so. If your computer does not detect the usb-drive on boot, then you will have to go to your bios and change the boot sequence. 

Once that is sorted everything will load just as it would load in a livecd


You can also check out the installation instructions in the unetbooting website main page, there are screenshots there to aid you.

gl, off to bed now

---

### Post by Mag1cN1nja on 2009-11-11
> **waspbr said:**
> unetbootin is definately the easiest method, I normally download the iso myself from the ubuntu website and run unetbootin in windows. 

Since you have formated the usb-drive, all you need to do is select the disk image option and browse to the iso that you have downloaded.

below select the letter corresponding to you usb-drive, just make sure is the right one, and press ok, everything is then going to go automatically. 

when it is done it will ask you to reboot, do so. If your computer does not detect the usb-drive on boot, then you will have to go to your bios and change the boot sequence. 

Once that is sorted everything will load just as it would load in a livecd


You can also check out the installation instructions in the unetbooting website main page, there are screenshots there to aid you.

gl, off to bed now

im getting grub error, grub rescue and >

---

### Post by Mag1cN1nja on 2009-11-11
bump

---

### Post by Mag1cN1nja on 2009-11-11
ne one wanna help

---

### Post by bodhi.zazen on 2009-11-11
You have not given us sufficient information in any of your posts.

1. Start by checking the md5 sum of your iso.

[HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM") 

2. I forget the default options you get after using unetbootin, try another boot option =)

3. If all else fails, re-format the USB to FAT and re-run unetbootin.

---

### Post by Mag1cN1nja on 2009-11-11
> **bodhi.zazen said:**
> You have not given us sufficient information in any of your posts.

1. Start by checking the md5 sum of your iso.

[HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM") 

2. I forget the default options you get after using unetbootin, try another boot option =)

3. If all else fails, re-format the USB to FAT and re-run unetbootin.

usb is fat32 right now,

8790491bfa9d00f283ed9dd2d77b3906

if that matters, i use diskimage and load the iso from my downloads

---

### Post by bodhi.zazen on 2009-11-11
Check the md5sum against the published md5sums ...

[http://noncdn.releases.ubuntu.com/9.10/MD5SUMS](http://noncdn.releases.ubuntu.com/9.10/MD5SUMS)

---

### Post by mickcalcara on 2009-11-11
I had the same issue. It turned out my cd rom drive was getting very hot. I noticed the install would get further, before errors, if cd rom drive was off for period of time. I am about 90% sure over heating was causing read errors. I finally, after going through many cds, put a cold pack on my cd rom drive to keep the temperature low. Install completed.

---

### Post by Mag1cN1nja on 2009-11-11
well come back from another failed attempt to install ubuntu. Errno(no typo, thats what it said) 5 at 27% completion after install. I did the check disc for errors before i started the install and it found nothing. I can still boot the os from the disc. And i still get the grub error, grub rescue error when i try to boot with nothing but hardrive and boot from jump drive. So idk whats going on

---

### Post by Mag1cN1nja on 2009-11-11
ne on here?

---

### Post by bodhi.zazen on 2009-11-11
So, you can boot , but ubiquity (the graphical installer) fails ?

I suggest you try the alternate CD as the installer is more robust on the alternate CD. The final installed OS is the same.

---

### Post by Mag1cN1nja on 2009-11-11
> **bodhi.zazen said:**
> So, you can boot , but ubiquity (the graphical installer) fails ?

I suggest you try the alternate CD as the installer is more robust on the alternate CD. The final installed OS is the same.

can u link me to the alternate download please, and im out of blank cds so will this work booting from jumpdrive even though im getting grub error every time i try to boot from it. Also my hardrive i used to try to install linux on wont show up anymore when i try to use it as a slave drive.

---

### Post by bodhi.zazen on 2009-11-12
I do not think you can boot the alternate CD from a USB drive.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by Mag1cN1nja on 2009-11-12
is there any way to run the live session from disc and install from there even though the disc wont let me n can someone explain the grub error to me

---

### Post by Mag1cN1nja on 2009-11-12
bump

---

### Post by bodhi.zazen on 2009-11-12
can you please provide more information on what is happening ?

with one post you state you are getting a grub error ? with another the installer fails at 27 % ???

those are very different problems.

In addition you are booting from USB or CDROM ? 

Did you test the integrity (md5sum) of your CDROM ?
Did you test the integrity (md5sum) of your iso ?

Are you using the Desktop CD or the Alternate CD?

---

