---
title: "Cant Install 10.04"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Cmac90 on 2010-05-07
I have created the ubuntu boot cd but when i restart it will not recognize that the disc is in my system. i have changed the boot order for the boot to come off of my disc drive first but still it goes straight to my hard drive and boots up like normal. what am i doing wrong?

---

### Post by warfacegod on 2010-05-07
Are you using an external CD-ROM?

---

### Post by spydeyrch on 2010-05-07
> **Cmac90 said:**
> I have created the ubuntu boot cd but when i restart it will not recognize that the disc is in my system. i have changed the boot order for the boot to come off of my disc drive first but still it goes straight to my hard drive and boots up like normal. what am i doing wrong?

Try this:

During POST, most systems display a message, such as press DEL to enter BIOS (the button might change depending on the bios maker, and it might not say bios but perhaps setup)

There is usually, at least in the systems of 5 years and newer, also a message during POST that says something to the effect of "Press XX to select boot device". For example, mine says:

Press DEL to enter Setup
Press F8 to enter boot device menu

When I press F8, it then gives me a list of my connected, bootable devices. I select the one that I want and away I go. ;)

See if you can do the same.

-Spydey :lolflag:

---

### Post by dannyboy79 on 2010-05-07
did you verify the MD5 sum of you downlaoded iso? did you burn it as contents versus a data cd? i always start with the basics and dont make any assumptions

---

### Post by albert s on 2010-05-07
the first CD I burnt of 10.04 wasnt recognised either, it bypassed my cd-rom and went straight to HD.
I downloaded another direct from the site(the first was a torrent), and it booted up straight off.
try another download.

---

### Post by Cmac90 on 2010-05-07
My system gives me the option to press F9 to select the order in which it boots, my internal CD/DVD rom drive is selected to be the first thing. I downloaded the file straight from ubuntu's website and burned a data file to a 700MB CD. The file has verified that all 699.2MB have been transfered to the disc. should i still try a new download? Is my disc possibly bad?

---

### Post by warfacegod on 2010-05-07
> **Cmac90 said:**
> My system gives me the option to press F9 to select the order in which it boots, my internal CD/DVD rom drive is selected to be the first thing. I downloaded the file straight from ubuntu's website and burned a data file to a 700MB CD. The file has verified that all 699.2MB have been transfered to the disc. should i still try a new download? Is my disc possibly bad?

There's your problem. You made a data CD instead of burning as an iso. Make a new disc.

---

### Post by Rex Bouwense on 2010-05-07
You need to check the md5sum first and then burn it as an ISO not a data disc.
The War guy beat me to it.  That's because I type with two fingers and I think a lot slower.

---

### Post by waynefoutz on 2010-05-07
If you are using Windows, use this program to burn the disk:
Imgburn [http://www.imgburn.com/]("http://www.imgburn.com/")

After you install it, launch it and hit the button that says "burn image file to disk" 

You can't just copy the file over to a data cd. The iso file is an image, or snapshot, of a bootable install disk.

---

### Post by Cmac90 on 2010-05-07
thanks guys thats what i needed. works just fine now

---

