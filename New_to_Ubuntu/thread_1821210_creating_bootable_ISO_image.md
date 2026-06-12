---
title: "creating bootable ISO image"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by hookitup on 2011-08-08
Hello ppl i am here to ask what is a great program to make bootable ISO cd and dvds,,, i know how to make a ubuntu one but it doesn't seem to work for backtrak , mac, windows or any other image for that mater unless its related to ubuntu... i was wondering if you guys could point me in the right direction to which program i would use to make a _**bootable**_ ISO image out of any ISO file wither it be linux mac or windows.


i cant find much info on the web sadly and i wanted to know from all these linux user opinions.

oh and FYI i am using ubuntu 11.04.

---

### Post by XubuRoxMySox on 2011-08-08
Yup! It's called [UNetbootin]("http://en.wikipedia.org/wiki/UNetbootin"), and it's already in Ubuntu's repositories!

-Robin

---

### Post by papibe on 2011-08-08
Once you have Ubuntu ISO file. You have to select the option called 'Burn Image'. Almost any software has it (maybe named slightly different). You want to avoid something like 'Data CD', or similar, because that will create a regular non bootable CD.

I hope it helps.
Regards.

---

### Post by hookitup on 2011-08-10
> **dixiedancer said:**
> Yup! It's called [UNetbootin]("http://en.wikipedia.org/wiki/UNetbootin"), and it's already in Ubuntu's repositories!

-Robin


this does not make ISO bootable CD or DVDs,,, only usb and starting to hardrive. which i don't want, so this will not work ,, any other ideas ? anybody?

---

### Post by amjjawad on 2011-08-10
You didn't post clearly what exactly are you trying to do, hence people will think you are trying to create a LiveCD or LiveUSB.

What exactly are you trying to do so that we can guide you through the right procedure :)

---

### Post by hookitup on 2011-08-11
> **hookitup said:**
>  i was wondering if you guys could point me in the right direction to which program i would use to make a _**bootable**_ cd or dvd ISO image out of any ISO file wither it be linux mac or windows.


??.

---

### Post by amjjawad on 2011-08-11
> **hookitup said:**
> ??.

We can read your post but we CAN NOT read your mind.

I'll assume you want to create a LiveCD which is obviously bootable and there is no need to mention that anyway.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Also from the download page of Ubuntu, there is some instruction of HOWTO Create LiveCD.

After you download an iso for any distro, better to check MD5SUM.
Once it's equal then you can burn the image to a CD.

I assume this is what you want. Otherwise, please explain in details what exactly do you want.

:)

---

### Post by hookitup on 2011-08-12
> **amjjawad said:**
> We can read your post but we CAN NOT read your mind.

I'll assume you want to create a LiveCD which is obviously bootable and there is no need to mention that anyway.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Also from the download page of Ubuntu, there is some instruction of HOWTO Create LiveCD.

After you download an iso for any distro, better to check MD5SUM.
Once it's equal then you can burn the image to a CD.

I assume this is what you want. Otherwise, please explain in details what exactly do you want.

:)

your confuseing me buddy, ok lets say i have a backtrack ISO file, a redhat  ISO file and a mac ISO file,,, i want to be able to test these expecially the 2 linux distros on a computer just to check out all the different kind of distros out there. iv tried about 7 so far and ubuntu is my favourite. i was useing windows to put the ISO files on CD's and it also made them bootable CD's not just data CD's ,,, but scene my windows machine crashed i am trying to use my ubuntu machine to create these bootable CD's .. when i use brasero or anything else pre installed on ubunut i select the file then insert a blank cd and doesnt seem to work.  so i was wondering what is a good program to creat bootable ISO cds.


oh and yes live cd not bootable,, my bad

---

### Post by aeiah on 2011-08-12
cant you just right-click on the .iso and select 'burn image to disc' or whatever its called nowadays?

incidentally, the iso has to be designed as a livecd. that means this method won't work for purely installation media, such as windows or os x disks.

---

### Post by amjjawad on 2011-08-12
> **hookitup said:**
> your confuseing me buddy, ok lets say i have a backtrack ISO file, a redhat  ISO file and a mac ISO file,,, i want to be able to test these expecially the 2 linux distros on a computer just to check out all the different kind of distros out there. iv tried about 7 so far and ubuntu is my favourite. i was useing windows to put the ISO files on CD's and it also made them bootable CD's not just data CD's ,,, but scene my windows machine crashed i am trying to use my ubuntu machine to create these bootable CD's .. when i use brasero or anything else pre installed on ubunut i select the file then insert a blank cd and doesnt seem to work.  so i was wondering what is a good program to creat bootable ISO cds.


oh and yes live cd not bootable,, my bad

I'm not confusing you, you are already confused :D ;)

From Terminal in Ubuntu:

```
sudo apt-get update && sudo apt-get install k3b

```Done!

I have never used Mac OS X or anything from Apple Products so I'm sorry, can't help you with this.

---

### Post by hookitup on 2011-08-12
i tried k3b and all it made was a data cd, wasnt bootable or "live" in this case.

i haven't tried this, you think this process will work [http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html) ????

---

### Post by amjjawad on 2011-08-12
> **hookitup said:**
> i tried k3b and all it made was a data cd, wasnt bootable or "live" in this case.

i haven't tried this, you think this process will work [http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html) ????

Because you didn't burn it as an image, you burned it as a Data CD. Not k3b fault :)

---

### Post by hookitup on 2011-08-12
that would but under the "more actions" tab then "burn image" correct ?

---

### Post by amjjawad on 2011-08-12
> **hookitup said:**
> that would but under the "more actions" tab then "burn image" correct ?

**Burn CD Image**



[IMG]http://www.ghacks.net/wp-content/uploads/2009/01/k3b_main.png[/IMG]

---

### Post by amjjawad on 2011-08-12
By the way, if you'll use k3b, MD5SUM check will be so easy as k3b will already provide the Hash Value for the iso file and you just need to compare it.

K3b is amazing program.

---

### Post by hookitup on 2011-08-12
mine looks like this


when i click on more actions i get a bunch of options and the only logical one is "burn image"

---

### Post by amjjawad on 2011-08-12
> **hookitup said:**
> mine looks like this

I'm on Lubuntu now and I don't have k3b, that screenshot I found on google.

What will happen when you click on "More Actions"?

I think Right-Click on the file (iso) is helpful but I just don't remember what exactly you'll get ... maybe Open with?

I'm sorry, don't have K3b here and I have to log off now.

---

### Post by cmcanulty on 2011-08-12
Brasero Disk Burner just click Burn Image

---

### Post by Johnb0y on 2011-08-12
> **cmcanulty said:**
> Brasero Disk Burner just click Burn Image

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

check "ubuntu" section...works for me... ;)

---

### Post by PCaddicted on 2011-08-14
Use the Brasero Disk Burner(default in Ubuntu), that's the best solution. :P
In its GUI, press the button "Burn Image to Disk" and then "Click here to select a disk image". In the window that appears, make sure that only iso image files are displayed and select the desired one, then click Open and finally Burn.

---

### Post by hookitup on 2011-08-16
it might be a hardware issue if all these programs work cause i tried all of them and no luck. i will try them on another computer and see the outcome.

---

### Post by anewguy on 2011-08-17
> **hookitup said:**
> i tried k3b and all it made was a data cd, wasnt bootable or "live" in this case.

i haven't tried this, you think this process will work [http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html) ????

Yes, you want to follow that link, but don't put an ISO image in the disk to be burned, instead put all the files contained in the ISO to the disk to be burned.  Then when you select burn you can select that you want to burn an ISO to a file.

I tested this using the following:

- the download dos boot floppy image it says to use
- all of the files from a non-bootable Windows 98SE disk

Burned to disk, restarted, in brought up DOS off the CD and I could have installed Windows 98SE if I had wanted to.

So:

- add the boot image as specified in that link
- add all the files you want on that disk
- burn, selecting ISO image file as the output (unless you just want a CD)

That worked for me.

When the CD is used at boot, it boots using the boot floppy image, then goes to the DOS prompt.

Dave ;)

---

