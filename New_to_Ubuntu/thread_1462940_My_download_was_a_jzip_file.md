---
title: "My download was a jzip file?"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by Ignotus Angelus on 2010-04-26
Hello!

I tried to download the ubuntu-9.10-desktop-i386 file to install on my computer. I read on the website that it is an iso file and that I should not try to unzip it or anything before burning it onto a CD.

So burned the file as it came on my CD and tried to boot on it. 

It is telling me that there are no operating systems available on it. :(

I went back to the file saved on the computer and it's saying it is a jZip file. What do I do with that? 

I simply want the iso file of the latest Ubuntu to install on my computer. Can anyone help me?

I have an ACER Aspire 4720Z which is presently running on Windows 7 Ultimate 32 bits (it is a laptop, does that make any difference?)

Thank you in advance for your help!

---

### Post by -Robert- on 2010-04-26
I guess the ISO extension could be assigned to the wrong program?
Download 9.10 here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Don't burn it as a data CD, follow this guide: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Make sure that your PC is able to boot from CD, check your BIOS settings.

---

### Post by Ignotus Angelus on 2010-04-26
This is the exact file which I have on my computer right now  :frown: I already downloaded it from that very link which you wrote!!!!!!

And as to the How to guide, I have already read it, and to put it simply, I don't even begin to understand the instructions.

"Before burning a CD, it is *highly recommended* that you verify  the md5 sum or sha256 sum (hash) of the .iso file.  For instructions,  please see [HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")  and [HowToSHA256SUM]("https://help.ubuntu.com/community/HowToSHA256SUM").   For the current list of Official Ubuntu SHA256 hashes, see the  SHA256SUMS file for the release you're using under [http://releases.ubuntu.com]("http://releases.ubuntu.com/") (and  optionally the [PGP]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto")  signatures in the SHA256SUMS.gpg file); hashes for the older MD5  algorithm are in the same directory. [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")  currently has only md5sums.  Checking the hash ensures that the file was  not damaged during the download process and is 100% intact."

this is absolute chinese to me.

No matter where I go, what I read, I just get more questions, and no straight answer.

---

### Post by oldos2er on 2010-04-26
Did you read [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows) ?

The ISO file needs to be burned as an image. See [http://psychocats.net/ubuntu/burn](http://psychocats.net/ubuntu/burn)

---

### Post by Ignotus Angelus on 2010-04-26
I downloaded the program to check the file, and it says

"MD5 Check Sums are different"

So what do I do now?:confused::confused::confused::confused:

---

### Post by HarrisonNapper on 2010-04-26
It most likely means that the download did not work. Re-download the file and make sure the md5 sums match.

---

### Post by Rex Bouwense on 2010-04-26
> **Ignotus Angelus said:**
> I downloaded the program to check the file, and it says

"MD5 Check Sums are different"

So what do I do now?:confused::confused::confused::confused:

If the md5sums are different, then the ISO that you downloaded did not download correctly.  You need to download it again, check the md5sum again, then if the sum is correct burn it to a cd at the lowest speed possible.

---

### Post by Ignotus Angelus on 2010-04-26
I will redownload it, but I find that particularly annoying. >.< Unlimited bandwith doesn't exist anymore...

So what do I do if after download, the file still says that it is different?

Should I download and download and download uselessly until it is the same?   ](*,)

---

### Post by ibuclaw on 2010-04-26
You could try torrents, that usually is the safest way to ensure all data downloaded is correctly checksummed and valid.

See [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Regards

---

### Post by Rex Bouwense on 2010-04-26
> **Ignotus Angelus said:**
> I will redownload it, but I find that particularly annoying. >.< Unlimited bandwith doesn't exist anymore...

So what do I do if after download, the file still says that it is different?

Should I download and download and download uselessly until it is the same?   ](*,)

Hold on.  Did you copy the file to the cd or did you follow the instructions given to you in the link?

---

### Post by Ignotus Angelus on 2010-04-26
Yes, I did follow the instructions, to the letter

I downloaded Infrarecorder and tried to burn the image, but it said something about the Speed test not having been made as an error, so I chickened out and cancelled.

I'm still waiting for the download to finish, it is about nearly done.

I'll hope that the MD5 check comes out positive this time.

---

### Post by Ignotus Angelus on 2010-04-26
MD5 Check Sums are different. AGAIN

This is getting annoying.

Can I download Ubuntu somewhere that isn't a bleeting ISO image?????

-.- I feel like such a stupid loser.

---

### Post by Rex Bouwense on 2010-04-26
Calm down and get a cup of coffee.  Can you post the result of the md5sum check?  I assume that you have downloaded it to a Windows OS and saved it to some file.  Are you using the 9.10 hash to check it?  It does make a difference.  Did you use Bit Torrent to download it?  Bit Torrent almost guarantees a good download.

---

### Post by HarrisonNapper on 2010-04-26
Also, if you pay for bandwidth, there are lots of places online where you can either for free or for a nominal fee get a CD shipped to you with Ubuntu already on it. Might be the way to go to conserve your network usage.

---

### Post by Ignotus Angelus on 2010-04-26
:s I downloaded the MD5 program from the webpage I was given in a previous post.

I right clicked on the download and chose "Send to" then WinMD5Sum", which prompted a little dialog box.

I clicked "calculate" and waited. it didn't do anything after 10 minutes, so I clicked compare. it said it was different.

I downloaded the file from the ubuntu website. BitTorrent scares me. I was told it is full of viruses.

I wasn't prompted to save anything to a file whatsoever.

---

### Post by HarrisonNapper on 2010-04-26
BitTorrent is full of viruses. Get the torrent file directly from the Ubuntu page, check it with md5, and you should be fine.

---

### Post by Ignotus Angelus on 2010-04-26
:(

Looks like I'm at my wits end

All the instructions are visibly for people who know their way around computers way more than I do.

I have no idea what 9.10 hash is. I downloaded the file ubuntu-9.10-desktop-i386.iso that is a torrent file from the website. I don't know what to do with it.

I tried to download BitTorrent and open the Torrent file with it. It was doing things which I couldn't understand, so I closed that.

I tried to follow the instructions to install from a USB key. They are as chinese to me as the instructions to burn a ISO image on a CD are.

I have no idea what to do anymore.

---

### Post by jrothwell97 on 2010-04-26
OK, ignore the stuff about checksums for now - if there's a major problem, you'll probably find out about it later, and the chance of there being one is relatively small. Follow the instructions in the next part of the howto - download a piece of CD burning software such as InfraRecorder or ISO Recorder and use that to burn your CD.

---

### Post by lisati on 2010-04-26
> **jrothwell97 said:**
> OK, ignore the stuff about checksums for now - if there's a major problem, you'll probably find out about it later, and the chance of there being one is relatively small. Follow the instructions in the next part of the howto - download a piece of CD burning software such as InfraRecorder or ISO Recorder and use that to burn your CD.

+1

And don't forget to burn as "disk image". Whenever you look at the CD there should be many files, not just a copy of the ISO file you downloaded.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Ignotus Angelus on 2010-04-26
It worked!!!! :D
 
This time the ISO image was burned successfully on the disk, and I have installed Ubuntu on my computer!
 
Hurray!!! <3
 
Thank you so much, everyone!!
 
Now, I have just a wee problem :3 Ubuntu apparently doesn't recognise my wireless, so I cannot access internet from my computer...

---

### Post by durand on 2010-04-26
> **Ignotus Angelus said:**
> It worked!!!! :D
 
This time the ISO image was burned successfully on the disk, and I have installed Ubuntu on my computer!
 
Hurray!!! <3
 
Thank you so much, everyone!!
 
Now, I have just a wee problem :3 Ubuntu apparently doesn't recognise my wireless, so I cannot access internet from my computer...

Yup, that will probably be the case. You need to go to System > Administration > Hardware Drivers. Hopefully, your wifi driver is found. You need to have ubuntu installed for this to work. It won't do it on the live cd.

---

### Post by 3rdalbum on 2010-04-26
> **durand said:**
> Yup, that will probably be the case. You need to go to System > Administration > Hardware Drivers. Hopefully, your wifi driver is found. You need to have ubuntu installed for this to work. It won't do it on the live cd.

You need to connect to the internet somehow for this to work (not a paradox - you can plug your computer straight into the router via an Ethernet cable, or use a mobile broadband stick to get your connection).

---

### Post by durand on 2010-04-26
> **3rdalbum said:**
> You need to connect to the internet somehow for this to work (not a paradox - you can plug your computer straight into the router via an Ethernet cable, or use a mobile broadband stick to get your connection).

Oh yeah, forgot about that. Whoops :S It's possible to download the deb (installation file) from another computer and then transfer it over, but it would be *much* easier if you could just plug it in via ethernet first.

---

