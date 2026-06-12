---
title: "USB stick: memory &quot;gone&quot;"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by OllieGab on 2009-04-14
I use Ubuntu 8.10 and put an .iso file on a memory stick to install on a different machine. The memory stick **should **be 4GB but after deleting everything on it, I've only got about 1.3 GB.
I tried to format it, using Ubuntu **and **Windows, but there still only seems to be 1.3G available.
Are there any hidden files anywhere, perhaps?

Curious!

Ollie:confused:

---

### Post by halitech on 2009-04-14
in Nautilus, go to View - show hidden files or press CTRL + H to show the hidden folders. then look for a folder called .trash and the files are probably in there

---

### Post by gali98 on 2009-04-14
When formating it, you may need to reset the disk label. 
!!!Make sure you know for sure what device you are applying it to!!!
Just use gparted. Then you can reformat it and any space lost should be reclaimed.
When you say you put the iso on it, did you just copy it, or did you use the program to actually install it on the drive?
Kory

---

### Post by halitech on 2009-04-14
> **gali98 said:**
> When formating it, you may need to reset the disk label. 
!!!Make sure you know for sure what device you are applying it to!!!
Just use gparted. Then you can reformat it and any space lost should be reclaimed.
When you say you put the iso on it, did you just copy it, or did you use the program to actually install it on the drive?
Kory

why format the drive when he can look in the .trash folder and remove the files from there? seems over kill with a big chance of making a mistake and killing the wrong partition.

---

### Post by OllieGab on 2009-04-14
I used the inbuilt function to create the iso image.

---

### Post by Jakey_TheSnake on 2009-04-14
```
sudo apt-get install gparted
``` 

from terminal. 

Then

```
sudo gparted
```

In the top right where you can select device, choose "/dev/sdb". Likely you have another partition on it, I ended up with one after doing the same. Delete the other, and expand the first, or delete both and then create a new FAT32 partition. It should be fairly intuitive, if it's not then post a screenshot here :)

---

### Post by Jakey_TheSnake on 2009-04-14
> **halitech said:**
> why format the drive when he can look in the .trash folder and remove the files from there? seems over kill with a big chance of making a mistake and killing the wrong partition.

Trash should be emptied on unmount, I believe (like in my case) sometimes the USB drive can be partitioned - possibly when leaving space on the drive for the LiveUSB to download files to? The "Creating Persistence File" part of the USB creation.

---

### Post by halitech on 2009-04-14
> **Jakey_TheSnake said:**
> Trash should be emptied on unmount, I believe (like in my case) sometimes the USB drive can be partitioned - possibly when leaving space on the drive for the LiveUSB to download files to? The "Creating Persistence File" part of the USB creation.

I agree it should be but I still think looking for the hidden files first would be easier then partitioning the drive.

---

### Post by OllieGab on 2009-04-14
Using gparted worked fine...well, I got 3.75 GB "back".
Looking for hidden files didn't help as all information that was returned was that there just weren't any files on the stick.

Using gparted showed me that there were 1.3 GB used and the rest just  "not allocated".

Is this what to be expected when using a memory stick? Or is it just some sort of "bug" that you jut can't delete the contents and get all the space back?

Ollie

---

### Post by Jakey_TheSnake on 2009-04-14
It's pretty stupid, but I'm not sure that it's a bug *shrugs* 

See halitech ;) 

NB - do you know much about surround sound in ubuntu?

---

### Post by halitech on 2009-04-14
> **OllieGab said:**
> Using gparted worked fine...well, I got 3.75 GB "back".
Looking for hidden files didn't help as all information that was returned was that there just weren't any files on the stick.

Using gparted showed me that there were 1.3 GB used and the rest just  "not allocated".

Is this what to be expected when using a memory stick? Or is it just some sort of "bug" that you jut can't delete the contents and get all the space back?

Ollie

actually, I guess thats where I missed something, didn't think about the USB creator making a smaller partition on the stick and basically leaving the rest unpartitioned so it created a 1.3gig partition and left the rest blank. IN that case, yes you would need to repartition with gparted to get your space back. If it had been normal files, when you unmouinted it or emptied the trash folder, you would have gotten your space back.

It's not a bug because you got the space back in the partitioned part of the drive, problem was that it had been partitioned into 2 smaller parts and left 1 blank.

> **Jakey_TheSnake said:**
> It's pretty stupid, but I'm not sure that it's a bug *shrugs* 

See halitech ;) 

NB - do you know much about surround sound in ubuntu?

yeah yeah yeah, so I don't know it all but never claimed I did and my fault for reading too fast and not thinking about all what he said. :)

---

### Post by Jakey_TheSnake on 2009-04-14
The surround sound question was directed at you, too by the way >_> :)

---

### Post by cyberphrog on 2009-04-14
I've had the same with one of my USB sticks.  Thanks for the info, I'll now recover my unallocated space...

---

### Post by halitech on 2009-04-14
> **Jakey_TheSnake said:**
> The surround sound question was directed at you, too by the way >_> :)

I know it works fine on my girlfriends stereo with 5 speakers :shock:

---

### Post by Jakey_TheSnake on 2009-04-14
> **halitech said:**
> I know it works fine on my girlfriends stereo with 5 speakers :shock:

Hummm. Care to take some screenshots of her volume control panel settings, with all the options on display? 

I have 5 speakers and a subwoofer, I'm only getting 2 channels output :(

---

### Post by halitech on 2009-04-14
> **Jakey_TheSnake said:**
> Hummm. Care to take some screenshots of her volume control panel settings, with all the options on display? 

I have 5 speakers and a subwoofer, I'm only getting 2 channels output :(

how about a picture of the front of the EQ of her stereo ;)

honestly I have no idea, I have 5 speakers here but an el cheapo sound card and the only thing I use sound for is amsn to tell me when I have a message and for checking dvd iso's for sound before I burn them so I don't waste a dvd.

are the plugs into the correct jacks on the sound card?

---

### Post by Jakey_TheSnake on 2009-04-14
> **halitech said:**
> how about a picture of the front of the EQ of her stereo ;)

honestly I have no idea, I have 5 speakers here but an el cheapo sound card and the only thing I use sound for is amsn to tell me when I have a message and for checking dvd iso's for sound before I burn them so I don't waste a dvd.

are the plugs into the correct jacks on the sound card?

I get it, it's a stereo system #-o 

There are 3 jacks and they each go into the correct port on the back of my machine *shrugs*

---

### Post by halitech on 2009-04-14
and it worked in windows and you haven't changed the wires so it should work now. sound has never been my strong point so no idea where to go from here. Hopefully someone else will have an  idea for you.

---

