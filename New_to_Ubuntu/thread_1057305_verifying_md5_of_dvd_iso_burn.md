---
title: "verifying md5 of dvd iso burn"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by minsf on 2009-02-01
_EDIT2:_ this thread comes down to the following question: **why do k3b/brasero/nero spit extra 24KiB of zero bytes after burning an iso image on a DVD?** (and thereby breaking md5sum checks against original iso). this seems to be fine for iso burns on CDs.

_ORIGINAL POST:_
_short story:_ i had an iso image file. i brunt a dvd from it. to verify the burn, i extract iso image from the dvd. i compare it to the original iso. it should be the same, but it is not. why?

_more details:_ 
1. i tried this with brasero, k3b and nero. none of them complain about the burn process. 
2. i chose 4x, but it's actually an external dvd drive, so my slow usb limits the speed to about 0.6x).
3. i wanted to verify that the burn is good. so i extracted the iso from the burnt dvd using brasero and also using "dd if=/dev/scd1 of=/home/minsf/test.iso" (side question: how does one extract iso image using k3b?)
4. i got a file that is exactly 24KiB (24*1024) larger than the original iso (so there is no point in verifying the md5. of course it is not the same). 
5. tried it with a different iso image. this time iso of LinuxMint, to exclude the possibility that the problem is due to some write-protected/hidden sectors in propriety software. i got the same problem (but maybe different sizes than those mentioned above- i cant remember now).
6. i run ubuntu 8.10, but the nero burn was done on a windows box, so it is not seem to be related to the OS or the box. the drive was the same, though.
7. (EDIT: ) i tried to verify the integrity in Brasero (ctrl+f) with the md5 file produced by md5sum of the original iso file. the test FAILS.

any solution to this mystery will be greatly appreciated!

---

### Post by spcwingo on 2009-02-01
You can verify the burn directly in Brasero.  Just open Brasero and go to tools>check integrity.  After that follow the on-screen instructions.  Ever since switching to Ubuntu this has been the way I've checked the md5 of burned discs.

---

### Post by minsf on 2009-02-01
> **spcwingo said:**
> You can verify the burn directly in Brasero.  Just open Brasero and go to tools>check integrity.  After that follow the on-screen instructions.  Ever since switching to Ubuntu this has been the way I've checked the md5 of burned discs.
i know. i forgot to mention i tried this too and the test FAILS according to brasero. i'll edit my original post and add it as #7. doesnt work but thanks.

---

### Post by minsf on 2009-02-02
i had some progress:
i used xxd to view the bytes of the two images and it seems that the second image is the same as the previous plus 24KiB of zero bytes. lets call the original file iso1, and the image extracted from the dvd iso2. then iso1 has many zero bytes at its end, and iso2 has the same zero bytes at the end plus 24KiB of additional zero bytes.
so i used the count argument of dd to cut iso2 to the size of iso1- let's call this iso3. then iso1 and iso3 have the same md5!
cool. so i guess my question comes down to:
**QUESTION: why do brasero, k3b and nero all burn extra 24KiB of zeros on the DVD after they finish burning the iso image?**

---

### Post by cjv8888 on 2009-02-02
I can second that.  I use k3b to burn iso of image onto CDRs. Every time I asked for verification of the burn and every time it turned out to be different to the original.  The CDs still booted ok and installed ok.  This happens even if I set the burning speed to 4x or 8x.

---

### Post by egalvan on 2009-02-02
**verifying md5 of dvd iso burn**

Here's what I do:

Step 1) download ISO and it's md5sum.
I use bit-torrent to reduce download errors
 (bit-torrent uses checks-sums to verify individial blocks of the file it's downloading, automatically re-trying if there is an error).

Step 2) use the utility "md5sum" to check the md5sum against the download.
If this check passes, continue to Step 3.
If not, download file again (since I started using bit-torrent, I have not had this problem).

Step 3) burn media, then boot and run the "check integrity" option.
This step checks the burn process results.
It uses md5sums that exist on the disc to verify the files.



I don't know how the burning programs do their integrity test.
I don't know how much of the media is included in this test.

Does the md5sum for the ISO file itself have any relation to the final burned media?

Maybe that md5sum is only valid for the ISO file itself?

Anyone have enough knowledge on how the ISO file is laid out on the media?
Are there any headers or footers that are added to the burned media?

Lots of questions that I have no answers to.

ErnestG

---

### Post by minsf on 2009-02-03
bump. anyone knows why brasero/k3b/nero all spit extra 24KiB of additional zero bytes at the end of an iso image burn on a _DVD_? this behaviour seems to break md5sum checks. (this behaviour does not happen when bruning iso image on a CD).

---

### Post by HavocXphere on 2009-02-03
Not sure, but a couple of thoughts on the issue:
[LIST]
[*]It's unlikely that nero and k3b contain the the same bug...they use completely different engines and the whole underlying structure/OS is different.
[*]The dump straight off the device should rather be .bin file, not an .iso i.e. binary dump versus an iso9660 filesystem.
[*]If you convert a .bin to a .iso the filesize sometimes differs by quite a bit.
[*]Kinda also sounds like the last block isn't filled completely so it is paded with zeros.
[*]Not entirely sure about the exact design of the iso standard, but I suppose its also possible that one could get space slack that eats up a few bytes. A raw dump will not realize that this is slack. If the source disk is a DVD, then its naturally aligned already then there won't be any slack, but if its a "compiled" iso like the nix isos, then it won't.
[/LIST]

---

### Post by avtolle on 2009-02-03
It is my understanding that "padding" is added to the CD or DVD once burned, which changes the md5sum of the disc relative to the iso.

---

### Post by minsf on 2009-02-05
> **HavocXphere said:**
> Not sure, but a couple of thoughts on the issue:
[LIST]
[*]It's unlikely that nero and k3b contain the the same bug...they use completely different engines and the whole underlying structure/OS is different.
[*]The dump straight off the device should rather be .bin file, not an .iso i.e. binary dump versus an iso9660 filesystem.
[*]If you convert a .bin to a .iso the filesize sometimes differs by quite a bit.
[*]Kinda also sounds like the last block isn't filled completely so it is paded with zeros.
[*]Not entirely sure about the exact design of the iso standard, but I suppose its also possible that one could get space slack that eats up a few bytes. A raw dump will not realize that this is slack. If the source disk is a DVD, then its naturally aligned already then there won't be any slack, but if its a "compiled" iso like the nix isos, then it won't.
[/LIST]

this makes sense... i'll look into it. 
thanks!

---

### Post by cocoa117 on 2009-09-05
I had exact same problem, after I burn the dvd, i always use 
md5sum /dev/cdrom
to verify the image, and it never the same. What's the solution here?

---

### Post by rio2000 on 2009-10-27
i have same problem :(

so what the solution? :-k

---

### Post by HappyFeet on 2009-10-27
> **rio2000 said:**
> i have same problem :(

so what the solution? :-k

What app are you using to burn?

---

### Post by rio2000 on 2009-10-28
> What app are you using to burn? 

i am using k3b (and also brasero)

i have no problem when verify CD iso, but i always fail verify dvd iso :cry:

---

### Post by r_avital on 2010-04-11
FWIW...


[LIST=1]
[*]Downloaded Karmic amd-64 iso (bittorent/Azureus).
[*]Launched k3b, allowed it to generate md5sum.  Result matches the md5sum posted on the Ubuntu releases web site.  So far so good.
[*]Burned on fresh, blank, DVD-R media, after checking the "verify" option.  Successful.
[*]Verification comes back with an error.
[*]In terminal, entered: ```
md5sum /dev/dvdrw3

```  The generated md5sum was: a4e4558cf95928b20e1ca1ec7e9d9229
[*]This does not match the DVD Hash posted on [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) , which is: ```
dc51c1d7e3e173dcab4e0b9ad2be2bbf ubuntu-9.10-desktop-amd64.iso
```  Could this be because we're comparing a **burned** dvd with a compressed ISO?  This seems to be what everyone else on this thread is reporting.
[/LIST]

**However:**
I entered the following in a terminal (in the /media/Ubuntu 9.10 amd64 directory, which is where the burned DVD is mounted):
```
md5sum -c md5sum.txt | grep -v "OK$"
```

This generates an md5sum hash of each and every file on the DVD and compares them to the hash values in the file named md5sum.txt on the same DVD, and **will output all the *non-matching* file names.**  No output was generated, so I must conclude that the burning was successful and accurate.

Am I incorrect in any of the above?

If I'm correct that all the files on the CD/DVD are ok, then the instructions posted in the "Check the CD" section at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) are incorrect, as they lead you to check your **burned CD/DVD, meaning a decompressed/un-archived collection of files against an ISO archive.**

---

