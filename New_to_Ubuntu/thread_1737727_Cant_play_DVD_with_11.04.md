---
title: "Cant play DVD with 11.04"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-04-23
I put in the Fast and Furious and wanted to watch the movie on natty. I cant play the movie becuase it says ```
Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.
```

I have installed Ubuntu restricted extras and also libdvdread4 and still doesnt work.  Any suggesstions?

---

### Post by uRock on 2011-04-23
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by hunter99507 on 2011-04-23
Has this changed since Maverick? I also have Maverick installed on another partition and it can read dvd's.

---

### Post by ClientAlive on 2011-04-23
> **uRock said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```


+1  I haven't had to do it yet myself but I've done some reading on it and I have that repo installed in synaptic (for future use).
---------------------------

By the way - I think it may be libdvdcss2 (sometimes called libdvdcss) that you need. Check me on that someone please.

Thx

---

### Post by K_45 on 2011-04-23
Just a note, you'll also need this even if you install VLC, which out of the box doesn't support encrypted DVD's.

---

### Post by yetiman64 on 2011-04-23
> **ClientAlive said:**
> +1  I haven't had to do it yet myself but I've done some reading on it and I have that repo installed in synaptic (for future use).
---------------------------

By the way - I think it may be libdvdcss2 (sometimes called libdvdcss) that you need. **Check me on that someone please**.

Thx
libdvdcss2 is what is required and is what uRock's command installs. You are right. 

Even having libdvdread4 installed doesn't automatically install libdvdcss2 (though it does provide a script in /usr/share/doc/libdvdread4 called install-css.sh which will do the job of installing for you, if used). I believe this may be for legal reasons with regard to what the distro itself can distribute.

---

### Post by cantormath on 2011-04-23
You should always use the medibuntu repo for codecs.

---

### Post by alphaG33k on 2011-04-28
I did the suggested install above.
I also installed the Restricted Extras. 

I still cannot play DVDs and still get the message that the DVD Decryption Library is not installed

I verified that libdvdcss2 installed.

---

### Post by tabinin on 2011-04-30
Thank you!  This worked! I was able to play DVDs before I upgraded but was getting the error message listed in the first post.

---

### Post by markyblue on 2011-05-10
Thanks Urock! This worked very quickly and easily. I just switched from Windows XP yesterday and was a little worried about command line, but this was no problem. Now I can watch my movies! :popcorn:

---

### Post by mdekoning on 2011-06-28
Thanks! Had the same problem, it works flawlessly now.

---

### Post by bduvall3 on 2011-06-29
Thanks!

---

### Post by zathras1974 on 2011-07-25
I've done everything above, and am still getting the same error. 11.04 64-bit. Install is less than 24 hours old, so I'm not sure how much I could have screwed up in so short a time. ;)

Edit: NVM. It was a problem with my region setting. Set that and it worked. :)

---

### Post by uRock on 2011-07-25
> **zathras1974 said:**
> i've done everything above, and am still getting the same error. 11.04 64-bit. Install is less than 24 hours old, so i'm not sure how much i could have screwed up in so short a time. ;)> **urock said:**
> [https://help.ubuntu.com/community/medibuntu](https://help.ubuntu.com/community/medibuntu) you need to install packages for decrypting the movies.

64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

You even installed the medibuntu package for 64bit?

---

### Post by zathras1974 on 2011-07-25
Correct. I've installed libdvdcss2 and libdvdcss4, I've added the medibuntu repository to my software manager, I've rebooted, stood on my head. Next stop I believe is the sacrificing of the chicken. ;)

Every time I try to play through Movie Player I get a "Could not read DVD. This may be because the DVD is encrypted..." error. I've also tried playing through VLC, which gives me no feedback whatsoever. =/

Edit: I'm also running in gnome classic. I don't think that would change anything, but I'm not ruling anything out at this point.

Edit #2: Working now. I followed ubuntu-freak's how-to ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)). Everything was still broken until I got to the region set. Set it to region 1, threw in a DVD to test, and it fired right up. Doh! Hopefully another user will run across this thread and save themselves some trouble. :)

---

### Post by travlemon on 2011-08-01
> **uRock said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

This worked perfectly for me in Kubuntu 11.04.  Thanks so much!

---

### Post by EricFX on 2011-08-04
[[COLOR=#D40000]**@uRock   : **[/COLOR]]("http://ubuntuforums.org/member.php?u=1018339")
no seriously u rock ! :D

Thx it works :popcorn:
[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=1018339")

---

### Post by CarlosFerreira on 2011-08-10
Seems to have worked. Thanks!

---

### Post by Norabunny on 2011-08-11
flawless, thankyou!

---

### Post by indian_gamer2003 on 2011-09-28
You rock uRock!

---

### Post by joneberger on 2011-10-02
Worked.  Thanks!

---

### Post by Bearw08 on 2011-10-26
> **uRock said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

Thank you so much! I had that trouble for a long time, now with your post help, it's gone :guitar:

---

### Post by dbeuscher on 2011-10-30
It worked for me too, newbie to Ubuntu that I am! Thank you!

---

### Post by zandman on 2011-10-31
And that fixed it for me too. Thanks

---

### Post by Lebow on 2011-11-05
Thanks, URock!

---

### Post by madeinwales on 2011-11-12
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb) 
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

worked for me too:D
and for those muppets like me, its two separate commands, c&p line 1 then
line two.
simples
thanks again

---

### Post by anewguy on 2011-11-12
And a little background for those who may be wondering....

No, this isn't included in a normal install.  Many would like it to be so we wouldn't have to do these steps, but it's a matter of legalities.  So, it's not included, but the information is readily available to install libdvdcssxxxx and run the install if needed.

So, it may seem like an extra step but it has to be.

---

### Post by clint1010 on 2011-11-20
Thank you

:D

---

### Post by al-iksir on 2011-12-20
Unfortunately did not work for me. Still getting the same error message (yes, I c&ped the 2 lines separately). 

This is what happens when I enter the second command:

```
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 47822 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 47823 package 'virtualbox-3.1':
 error in Config-Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 50615 package 'virtualbox-3.1':
 error in Version string '3.1.4-57640_Ubuntu_karmic': invalid character in revision number
(Reading database ... 351811 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using libdvdcss2_1.2.9-2medibuntu4_i386.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.9-2medibuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```NB: newbie. ;)

---

### Post by bnleez on 2011-12-20
This worked for me, thanks!!

---

### Post by cignonero on 2011-12-26
Hello everybody,
Just want to say Thank You, it worked for me too with Ubuntu 11.10. 

I've just downloaded this package (32bit) and installed with ubuntu software center.

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)

---

### Post by TokyoYank on 2011-12-28
> **cignonero said:**
> Hello everybody,
Just want to say Thank You, it worked for me too with Ubuntu 11.10. 

I've just downloaded this package (32bit) and installed with ubuntu software center.

[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Me too, 11.10 :KS

Humble request to update thread title to "11.04, 11.10"

---

### Post by goodbye-windows(tm) on 2012-01-07
I used the info in this thread to enable dvd player in my own xubuntu system, my daughter's ubuntu/unity system and Grandma's new Dell 620 running ubuntu/unity. All systems play dvd's without any issues.

TY to all who contributed to this thread.

Art

---

### Post by cheapodonuts on 2012-01-15
Solved for me too. Thanks guys. I'm running 11.04 and although I went through the [Comprehensive Multimedia & Video How To]("http://ubuntuforums.org/showthread.php?t=766683") I still couldn't watch DVDs and found that libdvdcss2 was not enabled. That done and I was watching my DVD immediately! :popcorn::popcorn::popcorn:

---

### Post by djpemberton on 2012-01-30
> **zathras1974 said:**
> 
Edit #2: Working now. I followed ubuntu-freak's how-to ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)). Everything was still broken until I got to the region set. Set it to region 1, threw in a DVD to test, and it fired right up. Doh! Hopefully another user will run across this thread and save themselves some trouble. :)

That worked! I had tried EVERY OTHER prominent suggestion. Only this worked. That was frustrating! Thank You!

---

### Post by whosane21 on 2012-02-11
> **uRock said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```

64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

This did the trick perfectly on 64bit 11.10.  Thanks, urock!

---

### Post by Gone fishing on 2012-02-11
Just a thought on regionset

DVD drives often have the  region set in the firmware of the drive - you can change this using regionset, but you can only make 5 changes before the drive locks itself (in the firmware of the drive).

If you travel around the world as I do this is a problem - it is often possible to flash the firmware of the drive to overcome this problem and region free the drive. I always check before I buy a DVD drive that this is possible - I've found liteon drives to be easy to do this with.

---

### Post by rchaplin on 2012-03-10
> **uRock said:**
> [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) You need to install packages for decrypting the movies.

32bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```64bit```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

This worked great for me on 11.10 Thanks!

---

### Post by portal443 on 2012-05-27
Want to confirm that this works in Ubuntu 12.04 LTS (precise) 64 bit for VLC. No configuration required beyond the two command line entries. Thanks for the great post, now I'll get on with my movie. :)

---

### Post by gombocarti on 2012-08-05
Hello everyone, I found a way which require no third-party repos:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs/)

Update: Sorry, I was wrong, the solution above does the same thing.

---

### Post by makdaddy8888 on 2012-08-08
I installed 11.04 and then the system upgraded to 12.04 LTS

i tried to load a dvd and eventually found this forum.

I ran both commands in the terminal now i get this error message

[B]Required Plugin could not be found
POython (v2.7) requires to install plugins to play media files of the following type:
DVD subpicture decoder[/B]

I think this is why Ubuntu is still not main stream. Just my opinion

---

