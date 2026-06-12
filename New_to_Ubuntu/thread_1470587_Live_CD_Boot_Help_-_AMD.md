---
title: "Live CD Boot Help - AMD"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by eskarthic on 2010-05-03
Hi,

I have AMD turion 64X2 laptop with windows vista. I am trying to run a live CD. I tried the acpi=off and the other bootable options. It just hangs at showing the menu 
"1.Try ubuntu without install
2. Install Ubuntu"
3. Check disk
-....

it hangs even if i enter the check disk option. Not able to run the live CD. what could be the issue? please help.

thanks,
Karthic Subramanian

---

### Post by Bucky Ball on 2010-05-03
Are you using the AMD64 installer? Dumb question, but ...

What version of Ubuntu?

---

### Post by eskarthic on 2010-05-03
yup, I downloaded ubuntu-desktop-amd.iso image.  version 10.04.

---

### Post by WinterRain on 2010-05-03
Other than the check disk option, at what point does it hang?

---

### Post by eskarthic on 2010-05-03
it hangs for any option that I select and hit enter. it doesn't move forward. It keep shows the menu screen. that's it no reaction.

thanks for the response.

thanks,
Karthic

---

### Post by 3rdalbum on 2010-05-03
Check the MD5 sum of the ISO file that you downloaded (there should be some HOWTOs about checking MD5 sums on Windows). The Ubuntu website contains what the result of the sum should be for that particular file. If yours differs, then the download is damaged, and you should redownload the file from a torrent.

If the MD5 sum checks out as correct, then try reburning the file; this time to a good quality CD, at a speed of 8x or as close to that as possible.

---

### Post by jmszr on 2010-05-03
eskarthic,

About 2/3 of the way down this link it will tell you how to do MD5SUM in Windows: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) . You can find the 10.04 MD5SUM Hashes here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) .

---

### Post by eskarthic on 2010-05-03
Thank you 3rdalbum and jmszr. I will have a loot into that.

Thanks for showing me the directions.

regards,
eskarthic

---

### Post by eskarthic on 2010-05-03
I checked the md5Sum I got 3e0f72becd63cad79bf784ac2b34b448. It is the same as given in the website. looks like the iso image is correct. please some one give me the boot option command to start the process. thanks,
eskarthic

---

### Post by itisachilles on 2010-05-04
With a new release of ubuntu LTS the more popular servers are getting slammed with download requests and understandably their can be some mistakes so the solution is try to re-download from a different server the time it takes will not be as pretty but it may fix your problem\\:D/

---

### Post by Bucky Ball on 2010-05-04
The best and most reliable is to torrent the ISO. Use Transmission. Much faster and safer all round. I don't go any other way meself.

---

### Post by eskarthic on 2010-05-04
Thanks to all of you replied to my queries. I will download again and try that.

Please give me the Boot option that I have to select in the (F6) option (I read in some post as try acpi=off or select nomode** remove quite splash -- etc etc) I tried all those. no luck. 

so can you please give me the exact bootable option that I have select?

My system configuration is AMD 64X2 dual core processor, 1GB RAM, nvedia graphics card with windows Vista. 

thanks very much for the help.

regards,
eskarthic

---

### Post by sadaruwan12 on 2010-05-04
I don't think that it's some thing your doing wrong when your liveCD gets stuck does the optical drive busy indicator light keeps on blinking.

I use a same kind of processor but I didn't got hung up like you've and I'm running the 10.04 on that system smoothly.

Try this download link this ISO worked for me [Click Me]("http://141.30.3.84/ubuntu-releases/lucid/ubuntu-10.04-desktop-amd64.iso")

---

### Post by itisachilles on 2010-05-04
If you want to be SURE that it is not the live CD that is the problem try to get your hands on an official boot CD from ubuntu devs themselves if one of these mess up its your system.period.

---

### Post by eskarthic on 2010-05-13
thanks sadaruwan12.

That one worked. 

thanks for the help.

-karthic

---

### Post by Bucky Ball on 2010-05-13
> **itisachilles said:**
> If you want to be SURE that it is not the live CD that is the problem try to get your hands on an official boot CD from ubuntu devs themselves if one of these mess up its your system.period.

Nice guess but they are generally fairly unreliable! The most reliable way is to torrent the ISO. Cheers. :)

---

