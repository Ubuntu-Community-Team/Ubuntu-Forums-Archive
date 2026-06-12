---
title: "Verifying ISO"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by Happy Hoppy on 2011-03-11
Following the instructions in the user manual, I downloaded and used winMD5Sum to verify the integrity of the ISO file.  Have done this a couple of times.

I am told that I did not need to go to all that trouble, that I should have just looked in the ISO properties for the hash no. and compared it (by eyeballing it) with the relevant hash from the Release page.

Is it really that simple?
Hoppy

---

### Post by coffeecat on 2011-03-11
> **Happy Hoppy said:**
> I am told that I did not need to go to all that trouble, that I should have just looked in the ISO properties for the hash no. and compared it (by eyeballing it) with the relevant hash from the Release page.


I'm not quite sure what you mean by that. ISO properties? Do you mean by right-clicking on the ISO and choosing properties? If you do that in Ubuntu and click on the digests tab you can indeed get the md5sum, but that takes a few seconds and I would guess that it is running the terminal command md5sum in the background - which is the Ubuntu equivalent of winMD5sum.

You can't do that in Windows without winMD5sum - not that I can find - not even in Windows 7. However you do it, you need to scan the downloaded file to calculate the md5sum hash for that particular file to make sure it matches the published hash.

---

### Post by Paqman on 2011-03-11
IIRC the LiveCD also has a menu option to verify its own integrity before booting.

---

### Post by CharlesA on 2011-03-11
> **coffeecat said:**
> 
You can't do that in Windows without winMD5sum - not that I can find - not even in Windows 7. However you do it, you need to scan the downloaded file to calculate the md5sum hash for that particular file to make sure it matches the published hash.

I've used hashcalc to find the md5sum/sha1sum on a windows box.

> **Paqman said:**
> IIRC the LiveCD also has a menu option to verify its own integrity before booting.

Yep. You just have to hit a key to get the menu and then select "verify"

---

### Post by coffeecat on 2011-03-11
> **CharlesA said:**
> I've used hashcalc to find the md5sum/sha1sum on a windows box.

Useful to know. I wasn't clear in what I posted. I meant that one would need a 3rd-party Windows app to do it in Windows. The functionality doesn't seem to be built into Windows - unlike in Ubuntu. :)

---

### Post by Happy Hoppy on 2011-03-11
Thanks for all your responses.  Yes, I do mean right-click on ISO and choose properties - sorry I worded it so clumsily.  

I think I am missing something:  If you need to scan the downloaded file to calculate the md5sum hash for that particular file to make sure it matches the published hash, then just comparing the two just by looking at them will not do it!  Am I right or wrong? 
Hoppy

---

### Post by Rex Bouwense on 2011-03-11
I just re-read this entire thread and you about have me confused.  If you are looking at the two files what would you be looking for?  That will not cut it.  All you have to do is compare the md5sums.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Happy Hoppy on 2011-03-11
sorry to confuse you Rex, I am trying to explain what was told to me because, apparently, I did it wrong (although it worked out for me).  I was working in windows XP.   I followed the instructions and made the ISO, downloaded the small program and dragged the ISO into it which then revealed the ISO md5sum.  I went back to Ubuntu documentation> Community Documentation> Ubuntu Hashes and copied/pasted the appropriate md5 hash into the program, which program then verified the ISO.

When I explained what I had done, I was laughed at and told that I had not needed to go to such lengths, I simply had to look at the string of numbers/letters (one set in ISO properties and the other set on the Ubuntu hash page) to see that they matched.

Did I waste time following the instructions in the manual?

---

### Post by coffeecat on 2011-03-11
> **Happy Hoppy said:**
> When I explained what I had done, I was laughed at and told that I had not needed to go to such lengths, I simply had to look at the string of numbers/letters (one set in ISO properties and the other set on the Ubuntu hash page) to see that they matched.

Did I waste time following the instructions in the manual?

I don't think so. As far as I can see you can only get the md5sum from file properties in Ubuntu, so what you did in Windows seems fine - unless I'm missing something. Although, tbh, I've only been using Linux to check md5sum hashes for years now.

---

### Post by Happy Hoppy on 2011-03-13
> **coffeecat said:**
> I don't think so. As far as I can see you can only get the md5sum from file properties in Ubuntu, so what you did in Windows seems fine - unless I'm missing something. Although, tbh, I've only been using Linux to check md5sum hashes for years now.

Thank you for the confirmation, coffeecat.  I shall continue using the same method as before.

---

