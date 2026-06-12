---
title: "Issues with Ubuntu 8.10 desktop 64 bit not wanting to install(i am a n00b)"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by 1cheap_r1 on 2009-02-21
anyways i am a n00b to Ubuntu and to LInux in general for that matter... so i put the install cd in the dvd drive, hit enter to select English, then hit enter to install... I think to myself... nice this is going so smoothly and i walk away

i come back a few minutes later and on the screen it lists a bunch of Device i/o errors... i am a little confused

thank you for your help

here are my system specs(for the office computer)

CPU: Intel Dual Core Celeron e1400 (2.0GHz, basically a c2d w/ less l2)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819116069](http://www.newegg.com/Product/Product.aspx?Item=N82E16819116069)

Motherboard: Biostar G31-M7 TE
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138125](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138125)

RAM: 2GB DDR2 (2 x 1GB)
[http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820146580](http://www.newegg.com/Product/ProductReview.aspx?Item=N82E16820146580)

Hard Drive: Western Digital 1TB sata
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317)

DVD drive: just some random system pull

---

### Post by 1cheap_r1 on 2009-02-21
no one?

---

### Post by Cresho on 2009-02-21
Burn your iso image@ 2x.  I had the same issue when I started using ubuntu years ago.

---

### Post by 1cheap_r1 on 2009-02-21
the slowested i can burn at is 8x

---

### Post by 1cheap_r1 on 2009-02-21
> **Cresho said:**
> Burn your iso image@ 2x.  I had the same issue when I started using ubuntu years ago.

nope that didnt work:(

---

### Post by The Desert Fox on 2009-02-21
can you paste the errors here?
ALso did you verify the md5 checksum before burning the image.

---

### Post by 1cheap_r1 on 2009-02-21
> **The Desert Fox said:**
> can you paste the errors here?
ALso did you verify the md5 checksum before burning the image.

not sure how to verify the checksum... ummm how do i copy the errors?

---

### Post by 1cheap_r1 on 2009-02-21
here is a couple of examples of the error messages.... there is almost a full page of these...

(initramfs) [69.828931] end_request: I/O error, dev sr0, sector 1431624

[69.828977] buffer I/O error on device sr0, logical block 3579906

there are several more, the first number in the "[]" changes but the sector and logical block is always the same

---

### Post by 1cheap_r1 on 2009-02-21
i have tried the x64 version and the i386 version both have the same issues

---

### Post by Mercury_Alpha on 2009-02-21
Those errors are consistent with a CD burner that doesn't handle high-speed burns very well. Unfortunately, this is pretty common -- I'm not trying to cast aspersions or anything ;)

You're going to want to burn the disc at as low a speed as possible. If you're in Windows, [CDBurnerXP]("http://cdburnerxp.se/") is a very common free burner program that will allow you to burn at low speeds, like 4x or even 2x. Once it's burned, you're going to want to [compare the MD5 sums]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by 1cheap_r1 on 2009-02-21
> **Mercury_Alpha said:**
> CDBurnerXP is a very common free burner program that will allow you to burn at low speeds, like 4x or even 2x.

thats what i am using... it wont let me go below 8x

---

### Post by 1cheap_r1 on 2009-02-21
it came up with a check sum of f9cdb7e9ad85263dde17f8fc81a6305b 
 which mathes the checksum found on the ubuntu hashes website

---

### Post by 1cheap_r1 on 2009-02-21
ok i tested the cd on my main computer and it worked perfect

i tried it on the office computer with 1 stick of memory, then with the other stick of memory, then i even tried another dvd drive... it still didnt work

then, just to be for sure i tried to use the 'just try ubuntu without making changes to your computer' with the hard drive disconnected, same result... ideas?

maybe ubuntu doesnt support some stuff on my motherboard natively?  i am confused

---

### Post by Mercury_Alpha on 2009-02-21
Does the office computer have a 64-bit CPU? And what do you mean by "didn't work"?

---

### Post by 1cheap_r1 on 2009-02-21
> **Mercury_Alpha said:**
> Does the office computer have a 64-bit CPU? And what do you mean by "didn't work"?

yes it is a 64 bit cpu... by it didnt work i meant it did the same thing it did b4

---

### Post by Mercury_Alpha on 2009-02-21
Sounds like a faulty optical drive. Can this drive read other CDs?

---

### Post by 1cheap_r1 on 2009-02-21
> **Mercury_Alpha said:**
> Sounds like a faulty optical drive. Can this drive read other CDs?

i have tested it with 2 DVD drives, yes it can i tested Windows XP Pro with it

---

### Post by Cresho on 2009-02-21
It is definetly either a bad iso, bad dvd/cd burn.  Here are some suggestions

1.  ide ribbon needs to be new
2.  dvd/cd burner......Do not use some cheap burner.  I went from emprex to Pioneer.
3.  software....burn @ 2x-4x.
4.  Make sure to use compatible CD/DVD media.  Use Fujifilm, Memorex on Pioneer burners.  TDK on toshibas, etc.  They seem to like certain brands.



This is definetly a problem with your selected burner and media type.  NOthing to do with ubuntu or iso...unless it is a bad download.  You never see this problem in windows xp....because nobody ever seemed to look deep enough.  I notice some of my backed-up cd images with pictures show corrupt jpegs.  So you just need to find what works...that is all.

---

### Post by 1cheap_r1 on 2009-02-21
1.  ide ribbon needs to be new
it is

2.  dvd/cd burner......Do not use some cheap burner.  I went from emprex to Pioneer.
i used a decent burner

3.  software....burn @ 2x-4x.
how does 1x sound?

4.  Make sure to use compatible CD/DVD media.  Use Fujifilm, Memorex on Pioneer burners.  TDK on toshibas, etc.  They seem to like certain brands.
 umm not sure

i have tried several DVD drives for the installation, however the same install disk works fine on another PC i have

---

### Post by buzzmandt on 2009-02-21
Poster said tried on main computer and it worked, means the burn is fine....
office computer is faulty.

The errors you posted happened to me with a bad hard drive.

---

### Post by theozzlives on 2009-02-21
Poster said tried "live" mode with hard drive unplugged.

---

### Post by 1cheap_r1 on 2009-02-21
> **buzzmandt said:**
> Poster said tried on main computer and it worked, means the burn is fine....
office computer is faulty.

The errors you posted happened to me with a bad hard drive.


the hard drive is brand new... how ever i have tried too boot Ubuntu from CD with the hard drive disconnected... same issues

---

### Post by 1cheap_r1 on 2009-02-21
> **theozzlives said:**
> Poster said tried "live" mode with hard drive unplugged.

you beat me to it... lol

---

### Post by 1cheap_r1 on 2009-02-21
i replaced the motherboard as a just incase precaution... but, sadly it still has the same problem...  is there a smiley for 'pulling my hair out'?

---

### Post by Mercury_Alpha on 2009-02-21
I'm pretty sure that the motherboard was not the problem.

It looks like the optical drive in the office computer just has some issues. For one reason or another, Windows is a lot more fault tolerant in this area than Linux. If you have any external drives, you can try installing Ubuntu with those, but you still have an apparently flaky optical drive in the office computer.

---

### Post by ramirabeau on 2009-02-21
Try burning the .iso to a thumb drive, check to make sure your BIOS is set to boot from usb devices, and run the image that way.  It'll eliminate the optical drive for the time being.

---

### Post by 1cheap_r1 on 2009-02-21
> **Mercury_Alpha said:**
> I'm pretty sure that the motherboard was not the problem.

It looks like the optical drive in the office computer just has some issues. For one reason or another, Windows is a lot more fault tolerant in this area than Linux. If you have any external drives, you can try installing Ubuntu with those, but you still have an apparently flaky optical drive in the office computer.

i have tried 2 different optical drives in the office computer... same issue

---

### Post by 1cheap_r1 on 2009-02-21
ok here is something i forgot to mention...  all of the optical drives i have tested so far in the office computer have been IDE drives...

i tossed in a cheap SATA drive and BAM!!! it loaded into Ubuntu perfectly...

now the issue is i need to use my IDE optical drive... is there a work around for this?

so the issue is that Ubuntu does not want to install with an IDE Optical drive

---

### Post by Cresho on 2009-02-22
your dvd/cd drives are bad...we been telling you this.

---

### Post by 1cheap_r1 on 2009-02-22
you are telling me that 3 different DVD drives are bad?

---

### Post by 1cheap_r1 on 2009-02-22
ok i tried the install on my fiance's computer and it installed perfectly, i took her DVD drive out, it was an IDE drive, i put her IDE DVD drive into the office computer, and her computer still couldnt finish the Unbuntu installation

in short i have tried using a DVD drive that i could confirm was working properly

---

### Post by Cresho on 2009-02-22
i have 7 drives.  All work fine but the pioneer worked the best. What I mean is I was able to do regular stuff with it but I had issues burning iso files what worked 100%

---

### Post by 1cheap_r1 on 2009-02-22
> **Cresho said:**
> i have 7 drives.  All work fine but the pioneer worked the best. What I mean is I was able to do regular stuff with it but I had issues burning iso files what worked 100%


the install cd i burned works great on My main computer(SATA optical drive) and my fiance's computer(IDE optical drive) however it does not work on my office computer(IDE optical drive)...

i then took the SATA optical drive out of my main Computer... hooked it up to the office computer and then the office computer loaded Unbuntu with no problems...

i then took the IDE optical drive out of my fiance's computer and install it on the office computer and the office computer would not install Ubuntu 

i also tried 2 more sata optical drives in the office computer and it worked great... then i tried 3 other IDE optical drives in the office computer and Unbuntu would not load

this is why

---

### Post by Mercury_Alpha on 2009-02-22
Sounds like your IDE data cable is faulty. It's the only relevant thing that apparently hasn't changed. You switched the motherboard, which rules out the drive controller. You've tried multiple optical drives, which rules out them out as problems. But you've attached a SATA drive, which doesn't use the IDE data cable.

As I mentioned earlier, sometimes Windows is more fault tolerant with data cables than Linux. Which is why the XP Pro disk you mentioned could work fine, while the Ubuntu disks will not.

I recommend swapping to a brand-new data cable. Thankfully, they're pretty inexpensive.

---

### Post by 1cheap_r1 on 2009-02-22
> **Mercury_Alpha said:**
> Sounds like your IDE data cable is faulty. It's the only relevant thing that apparently hasn't changed. You switched the motherboard, which rules out the drive controller. You've tried multiple optical drives, which rules out them out as problems. But you've attached a SATA drive, which doesn't use the IDE data cable.

As I mentioned earlier, sometimes Windows is more fault tolerant with data cables than Linux. Which is why the XP Pro disk you mentioned could work fine, while the Ubuntu disks will not.

I recommend swapping to a brand-new data cable. Thankfully, they're pretty inexpensive.

i have tried a new caable... the motherboard came with a cable

---

### Post by 1cheap_r1 on 2009-02-24
i gave up an just bought a sata DVD burner

---

