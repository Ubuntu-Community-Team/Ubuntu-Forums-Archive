---
title: "Loading Linux to my flash drive"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-06-04
I want to use unetbootin to download 5.2.5. to my flash drive. lupu-525.iso (5.2.5.) is downloaded  into my archive manager. For unetbooten to download it it needs the address for lupu-525.iso in my archive manager. For the life of me I can't find it. Any Ideas.

---

### Post by HermanAB on 2011-06-04
$ find /home/username -name filename

---

### Post by Jon Anderson on 2011-06-04
I downloaded puppy linux 5.2.5 which is lupu-525.iso ,it is in my archive manager which unzipped it. So it is a unzipped program somewhere in my files, how do I find it. I want to run it through  unetbooten program and that will install it on my flash drive. but to do that I need the address of were the program (puppy linux 5.2.5 or lupu-525.iso .) is, so that unibooten can find it to put it on my flash drive.

---

### Post by ExileAmongYou on 2011-06-04
If you downloaded the .iso file using your web browser, it should be wherever your web browser normally downloads files to, which might be your Downloads folder or your Desktop. How did you download the file? Did you choose to "open" or "save" it?
 You don't need to open the iso file with Archive Manager, or unzip it, you just need to open that iso file in unetbootin

---

### Post by yetiman64 on 2011-06-04
> **Jon Anderson said:**
> I want to use unetbootin to download 5.2.5. to my flash drive. lupu-525.iso (5.2.5.) is downloaded  into my archive manager. For unetbooten to download it it needs the address for lupu-525.iso in my archive manager. For the life of me I can't find it. Any Ideas.

It may not have been saved to the drive if you told it to open with archive manager, though it may exist in the browser cache still.

There is a browser add-on (not available in firefox in Natty apparently) for older versions of firefox called "cacheviewer". If you are in Maverick or earlier and install cacheviewer you may be able to search for the file by name in cache and highlight and save it to disk.

Otherwise you will need to find the iso download again and tell the download manager to save it to disk. This is because Archive Manager is opening the iso directly from the browser cache as you currently describe it.

---

