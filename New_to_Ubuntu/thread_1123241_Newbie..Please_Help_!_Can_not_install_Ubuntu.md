---
title: "Newbie..Please Help ! Can not install Ubuntu"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by drdave69 on 2009-04-12
I tried posting this in the installation thread with no replies. lets try here :)

I have tried several times, with no success, to install Ubuntu to dual boot with my windows xp installation. I have downloaded the iso many times & burned it (slow & fast), but when I verify the cd integrity before installing it says there are 28 errors. Then freezes during installation. (as expected)
I have had some success with installing using Wubi. But I am under the understanding that installing using this method has limitations and some security issues.
I am in love with the Ubuntu interface and would really like to experiment with it some more to see if it is a viable option to replace xp with.
I have attached my system specs, per pcpitstop.com, to show what I am working with, in hopes that someone can tell me which version or method of installation is right for my computer.
I want to keep my xp installation, and dual boot Ubuntu.
As you can see I have many drives, and space available to put the Ubuntu installation on.
I am open to any option for installation, but will require step by step instructions, as I am a nube to linux and Ubuntu.
Thank you in advance for any and all help / suggestions,
Dave

---

### Post by the.phantom on 2009-04-12
i'm not a expert
but can you have a friend download and burn the cd on their computer?
and was it 32 bit or 64 version and 8.10 or what?
\
and what type of install? dual boot ?

---

### Post by Andavane on 2009-04-12
> **drdave69 said:**
> I tried posting this in the installation thread with no replies. lets try here :)

 I have downloaded the iso many times & burned it (slow & fast), but when I verify the cd integrity before installing it says there are 28 errors. nube to linux and Ubuntu.
Thank you in advance for any and all help / suggestions,
Dave

Well the first step would be to find out why you're getting these errors. I wonder if it was a good download, or if you tried downloading from another mirror?

---

### Post by RaiCoss on 2009-04-12
Did you try the Ubuntu Jaunty Beta??

[http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso](http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso)

It's pretty sweet and may well work where previous version's didn't.

Also what disc burning software are you using on Windows??

---

### Post by Andavane on 2009-04-12
> **RaiCoss said:**
> Did you try the Ubuntu Jaunty Beta??

[http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso](http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso)

It's pretty sweet and may well work where previous version's didn't.

Also what disc burning software are you using on Windows??

I take it that HAS to be burned as a DVD & won't burn as a CD?

---

### Post by lamalex on 2009-04-12
Does anyone else find the .doc attachment a little bit ironic?

What speed are you burning the isos at? You should burn them as slow as possible and also make sure the iso you got was not corrupted somehow, I have no idea how do to anything except open firefox on windows, but there should be a way to check the sha1sum of your iso, and then compare it against the checksums [here]("https://help.ubuntu.com/community/UbuntuHashes"). Here is whole page about making sure your iso file is ok. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by RaiCoss on 2009-04-12
MY BAD!! I didn't know they switched to DVD image's.

---

### Post by drdave69 on 2009-04-12
> **the.phantom said:**
> i'm not a expert
but can you have a friend download and burn the cd on their computer?
and was it 32 bit or 64 version and 8.10 or what?
\
and what type of install? dual boot ?
32 bit 8.10
Tried the download on multiple computers, same result :(

---

### Post by RaiCoss on 2009-04-12
Heres the correct Jaunty Beta CD image:

[http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso](http://releases.ubuntu.com/releases/9.04/ubuntu-9.04-beta-desktop-i386.iso)

Also try this and see if it makes any difference when burning:

[http://download.softpedia.com/dl/b0a6263359c815974505ef560abb5c5b/49e16e82/100027810/software/cd_dvd_tools/SetupImgBurn_2.4.4.0.exe](http://download.softpedia.com/dl/b0a6263359c815974505ef560abb5c5b/49e16e82/100027810/software/cd_dvd_tools/SetupImgBurn_2.4.4.0.exe)

---

### Post by drdave69 on 2009-04-12
> **RaiCoss said:**
> Did you try the Ubuntu Jaunty Beta??

[http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso](http://cdimage.ubuntu.com/releases/9.04/beta/ubuntu-9.04-beta-dvd-i386.iso)

It's pretty sweet and may well work where previous version's didn't.

Also what disc burning software are you using on Windows??
Looking into this option now. Thanks

---

### Post by Andavane on 2009-04-12
> **drdave69 said:**
> 32 bit 8.10
Tried the download on multiple computers, same result :(
Have you been to the link given by lamalex and tested the iso in Windows?
Testing the iso is the next step.

---

### Post by drdave69 on 2009-04-12
> **Iamalex said:**
> Does anyone else find the .doc attachment a little bit ironic?

What speed are you burning the isos at? You should burn them as slow as possible and also make sure the iso you got was not corrupted somehow, I have no idea how do to anything except open firefox on windows, but there should be a way to check the sha1sum of your iso, and then compare it against the checksums [here]("https://help.ubuntu.com/community/UbuntuHashes"). Here is whole page about making sure your iso file is ok. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thank you, will check image using link provided when it is finished downloading.

---

### Post by drdave69 on 2009-04-12
OK, I downloaded 'ubuntu-9.04-beta-desktop-i386', Installed 'winMd5Sum', went here to get hash: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) But there are no hashes for this version. Does anyone know where I can find them at?

---

### Post by Jazzy_Jeff on 2009-04-12
Are you burning to new media each time or are you using a rewritable disk?

You may also want to try [unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=222386") if you have a pen drive. You can boot right from the pen drive.

---

### Post by overdrank on 2009-04-12
> **drdave69 said:**
> OK, I downloaded 'ubuntu-9.04-beta-desktop-i386', Installed 'winMd5Sum', went here to get hash: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) But there are no hashes for this version. Does anyone know where I can find them at?

I do not recommend a new user using a beta release as it is apt to break the hashes are 
```
671917146e569cc0fb05d29703d79753 *ubuntu-9.04-beta-alternate-amd64.iso
84d3bdac6a38237cec9bf27d49e90714 *ubuntu-9.04-beta-alternate-i386.iso
4a9d522d06f118fa72dbd613a02ca43e *ubuntu-9.04-beta-desktop-amd64.iso
03b63dada5e5fce0119a52d822e406a1 *ubuntu-9.04-beta-desktop-i386.iso
7f2d68febda3d67c9dbae8b6d3011281 *ubuntu-9.04-beta-server-amd64.iso
1cca6e7e29d0e25c857e76144c4b799f *ubuntu-9.04-beta-server-i386.iso

```
Found [here]("http://releases.ubuntu.com/releases/9.04/")

---

### Post by drdave69 on 2009-04-12
> **Jazzy_Jeff said:**
> Are you burning to new media each time or are you using a rewritable disk?

You may also want to try [unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=222386") if you have a pen drive. You can boot right from the pen drive.
New media each time.

---

### Post by drdave69 on 2009-04-12
UPDATE: 
I have downloaded ubuntu-8.10-desktop-i386, verified the hash with winmd5sum, burned the iso with imgburn, verified the disk was ok with imgburn and by booting with disk and selecting the verify option there. 
I now have a good copy of Ubuntu to install with !!!! :)
I want to dual boot with my windows xp, what are the next steps to installing Ubuntu to do this?
REMEMBER, I am a newbie so be specific.
Thank you in advance for your assistance,
Dave

---

### Post by Sef on 2009-04-12
>  I want to dual boot with my windows xp, what are the next steps to installing Ubuntu to do this?

Read [Psychocats]("http://psychocats.net/ubuntu").

---

### Post by irfan9727 on 2009-04-12
Have a look at this: [http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-10-97417.shtml)

---

### Post by Ticketoride on 2009-04-12
> **drdave69 said:**
> I tried posting this in the installation thread with no replies. lets try here :)I verify the cd integrity before installing it says there are 28 errors. Then freezes during installation. (as expected)
That&#347; a mis-burn.

Update your Burner&#347; Firmware and do not use Cheap CD-R/DVD-Rs.

You cannot accidentally burn CD-R ISO Images to DVD-R, your CD-Writing Prog will recognize what Type of ISO it is by reading its Header. Some Windows Programs such as Nero & UltraISO have Checkboxes that prompt you to convert if you want to burn a CD-R Image to DVD-R. Any Software that burns an ISO to the other Medium and then the Disk won´t boot/read, that Software is pure Trash. Junk it.

Most Optical Unit Firmwares deal with Burning Speed Related Issues. Cut back to 8x or 16x for CD-Rs, no more more 4x for DVD-R.

Lately we have been seeing many top Brand Names slashing Prices such as Sony, Maxell & Verbatim buying junk Media from ´Moser Baer´ in India.

Even if your CD Writer is on the Edge, try to locate some ¨Taiyo Yuden¨ Media in your Town made in Japan. They don´t cost more, and is the very best Media Money can buy.

When you have Errors on a burned Disk, you should´nt be installing anything from it.

> **drdave69 said:**
> I want to keep my xp installation, and dual boot Ubuntu.
As you can see I have many drives, and space available to put the Ubuntu installation on.
I am open to any option for installation, but will require step by step instructions, as I am a nube to linux and Ubuntu.
I recommend installing Ubuntu to another Hard Drive, not only another Partition, so won´t have Boot Manager Headaches later. Been there, done that.

In this Way both OSs are independant from each other, and you are free to upgrade/re-install either one, without interfering with the other. Should you decide to upgrade your WinXP to Win 7, your Linux won´t boot and you´ll have to futz with Grub and what not.

If you prefer this route over a Boot Loader which manages both Windows & Linux ...

1. You need 2 HDDs.
2. BIOS has to be able to change the Boot Order of Drives.
3. You have to disconnect the Windows Drive while installing Linux, and vice versa.

You´ll never futz with Lilo or Grub again ...

---

### Post by drowner on 2009-04-12
> **drdave69 said:**
> UPDATE: 
I have downloaded ubuntu-8.10-desktop-i386, verified the hash with winmd5sum, burned the iso with imgburn, verified the disk was ok with imgburn and by booting with disk and selecting the verify option there. 
I now have a good copy of Ubuntu to install with !!!! :)
I want to dual boot with my windows xp, what are the next steps to installing Ubuntu to do this?
REMEMBER, I am a newbie so be specific.
Thank you in advance for your assistance,
Dave

This is excellent news. Read the psychocats tutorial posted for you, and let us know if you have any questions.

And, I disagree with whoever gave the advice to install the Beta Jaunty. The OP did not have a problem with a particular release, did not ask for beta software, he or she needed help with burning, and now, dual booting. Please try and keep your advice relevant and appropriate.
/rant

---

### Post by Andavane on 2009-04-12
> **Ticketoride said:**
> That&#347; a mis-burn.

.....Checkboxes that prompt you to convert if you want to burn a CD-R Image to DVD-R. Any Software that burns an ISO to the other Medium and then the Disk won´t boot/read, that Software is pure Trash. Junk it.

..........
May I interject at a tangent here, as you seem to know something about this?
(I take the point about a CD with errors not being used for installing anything_):
I made a bootable usb stick (for Eeebuntu 2.0) used "Create a USB startup" in Intrepid. Before installing I used the "Test CD integrity" option on the USB stick, and it returned 99 errors.  My question is "Does the test Cds facility work just the same?" Or perhaps the USB stick, not being a CD, can't be subjected to the same tests?

Perhaps I should make it again with     enetbootin.

---

### Post by drdave69 on 2009-04-12
I am posting this using my new Ubuntu os :)
I installed it its own drive, had to take all other drives out of computer during install to get this to work. To get it to boot I go into my bios & shut off the drive with windows on it, this seems to work pretty good, if I want to boot windows I just turn the drive back on in bios & it boots.
Thank you all for the support, ideas & guidance, as I took bits & pieces of all input and came up with this solution.
Thanks again,
Dave

---

### Post by RaiCoss on 2009-04-12
> **Ticketoride said:**
> That&#347; a mis-burn.

Update your Burner&#347; Firmware and do not use Cheap CD-R/DVD-Rs.

You cannot accidentally burn CD-R ISO Images to DVD-R, your CD-Writing Prog will recognize what Type of ISO it is by reading its Header. Some Windows Programs such as Nero & UltraISO have Checkboxes that prompt you to convert if you want to burn a CD-R Image to DVD-R. Any Software that burns an ISO to the other Medium and then the Disk won´t boot/read, that Software is pure Trash. Junk it.

Most Optical Unit Firmwares deal with Burning Speed Related Issues. Cut back to 8x or 16x for CD-Rs, no more more 4x for DVD-R.

Lately we have been seeing many top Brand Names slashing Prices such as Sony, Maxell & Verbatim buying junk Media from ´Moser Baer´ in India.

Even if your CD Writer is on the Edge, try to locate some ¨Taiyo Yuden¨ Media in your Town made in Japan. They don´t cost more, and is the very best Media Money can buy.

When you have Errors on a burned Disk, you should´nt be installing anything from it.


I recommend installing Ubuntu to another Hard Drive, not only another Partition, so won´t have Boot Manager Headaches later. Been there, done that.

In this Way both OSs are independant from each other, and you are free to upgrade/re-install either one, without interfering with the other. Should you decide to upgrade your WinXP to Win 7, your Linux won´t boot and you´ll have to futz with Grub and what not.

If you prefer this route over a Boot Loader which manages both Windows & Linux ...

1. You need 2 HDDs.
2. BIOS has to be able to change the Boot Order of Drives.
3. You have to disconnect the Windows Drive while installing Linux, and vice versa.

You´ll never futz with Lilo or Grub again ...

Yeah you can. I burned a Jaunty Alpha with Brasero to A DVD with a CD iso by mistake. And it worked :P

---

### Post by r1ch on 2009-04-12
Just to chuck in my own experiences to the mix...

... I've had much the same problem with mutliplt ISO burns to a variety of branded and unbranded (new and old) media failing the integrity tests, and failing to either boot to live CD or to install. This was with 8.10 a few months ago.

Getting around this I finally used a free CD give away with a magazine, and had a friend burn a spare disc for me.

My conclusion seemed to be that either the drive was the most likely culprit as the download passed the md5 test and the discs were all new.

Trial and error really... and quite hit and miss. Pain in the *** all around!

---

### Post by t0p on 2009-04-12
Nothing to see here, move along...

---

### Post by Andavane on 2009-04-12
> **drdave69 said:**
> I am posting this using my new Ubuntu os :)
I installed it its own drive, had to take all other drives out of computer during install to get this to work. To get it to boot I go into my bios & shut off the drive with windows on it, this seems to work pretty good, if I want to boot windows I just turn the drive back on in bios & it boots.
Thank you all for the support, ideas & guidance, as I took bits & pieces of all input and came up with this solution.
Thanks again,
Dave
Oh I do love that just-installed-ubuntu-for-the-first-time look!
It's a great feeling, isn't it? --- and you crafted your own way of doing it based on helps. We find so many ways of doing Ubuntu things

Welcome :guitar:

---

