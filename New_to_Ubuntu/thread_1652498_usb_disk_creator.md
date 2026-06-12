---
title: "usb disk creator"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by hollowtd on 2010-12-25
I am trying to make a startup disk using ubuntu 10.10 iso. When I click on "other" and try to choose the .iso saved on my desktop, it will not show up in the field. I can find my usb device but the iso image does not show up above that. What am I doing wrong? 

Thanks

Terry

---

### Post by garvinrick4 on 2010-12-25
If it is a usable .iso file and you are selecting desktop then select the .iso it should show up in startup disk creator.

---

### Post by owise1 on 2010-12-25
I have had some problems with USB startup disk creator - not running to completion in my case.  Found that running as root worked for me.  Done a number of upgrades on this machine and assume that it is due to some screwed up permisions along the way

sudo usb-creator-gtk

---

### Post by hollowtd on 2010-12-25
I'm running 10.04 LTS and it just doesn't show up in the creator. How would I go about running as root? Cheers (I'm using the ubuntu one, should I use gtk?)

---

### Post by owise1 on 2010-12-25
open a terminal window and run

sudo usb-creator-gtk

---

### Post by hollowtd on 2010-12-25
I will try it and let you know. Should by usb (a cruzer) be formatted in any way?

---

### Post by owise1 on 2010-12-25
the tool will allow you to remove the content on the USB driver.  I regularly re-use them to try various distros

---

### Post by amjjawad on 2010-12-25
Not a direct answer of course but I do prefer this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by philipballew on 2010-12-25
i was under the notion that the default usb startup disk maker was not working in 10.10 and the new version of unetbootin was how to make one as a work around

---

### Post by C.S.Cameron on 2010-12-25
Startup Disk Creator in 10.10 has worked for me.
Format it FAT32.
But if you prefer UNetbootin, it can be made persistent.

---

### Post by IndyGunFreak on 2010-12-25
USB Disk Creator, has not worked for me for a while (even running it as root)... I thought it was my USB drive at first, but I tried unetbootin, and it works perfectly.  So thats what I use.

---

### Post by hollowtd on 2010-12-25
I'll try unetbootin and see. It seems a bit more complicated and I don't want to screw up my already made mac/ubuntu parition on my HD.

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> I'll try unetbootin and see. It seems a bit more complicated and I don't want to screw up my already made mac/ubuntu parition on my HD.

It's very easy and you will not screw anything ;)

---

### Post by Plumtreed on 2010-12-25
Startup disk Creator works for me going Ubuntu to Ubuntu. I recently put ubuntu Netbook on a USB drive.

When you select 'other' you have the opportunity to search and find the iso. The iso doesn't necessarily appear.

.....I always 'format' the USB drive in Windows to fat32 ( or if 2GB or under fat16)

---

### Post by hollowtd on 2010-12-25
Im  still not finding the iso showing up in the field. I think I must need to format the usb drive?

---

### Post by hollowtd on 2010-12-25
I do select other and select the iso and it still does not show up. It's very strange indeed.

---

### Post by hollowtd on 2010-12-25
So I've got the 4 gig cruzer formatted to fat32. I put it in the usb port and it and a cd image shows up labeled U3. Then, I open up either startup disk creator or unetbootin and select "other." When I do, I can find the iso files, but after I select them, they do not appear in the text field. The iso files are hardy heron and 10.10 (powerpc.iso for my g3 ibook). I'm at a loss of why when I select either one of the iso files that they do not appear in either startup disk creator. ???

---

### Post by Plumtreed on 2010-12-25
I take it you find the ISO in Desktop or Downloads and Open it but then are unable to find it in the 'Creator' box, you might have to move the selector at the side to have the selected ISO appear in order to highlight it.

---

### Post by amjjawad on 2010-12-25
What tools are you using now? UNetbootin or Startup desk creator?
Are you sure you're looking at the correct folder?

---

### Post by hollowtd on 2010-12-25
I will try this, let me look. thanks

---

### Post by hollowtd on 2010-12-25
I'm trying to use one or the other. I'm trying both to see if I can select the iso and have it appear but it doesn't in either.

---

### Post by hollowtd on 2010-12-25
I can't get it to show up in the creator box. You are correct. I am even trying to drag and drop but it doesn't show up. It's very weird. I'm not sure why it's not recognizing it. Might it be that it is iso of 10.10 and 8.04.1 for powerpc? (apple ibook g3 version)

---

### Post by Plumtreed on 2010-12-25
I'm running 10.10 and when I follow those steps it works the way it should....I can't help any further because I don't know what else to suggest.

I have used hardy heron's USB creator to create itself as a 'live' CD

---

### Post by hollowtd on 2010-12-25
When I use unetbootin I can't find the iso file at all even to select it. When I use startup disk creator, I can find the file when I selct other but then it doesn't appear in the creator box feild.

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> I can't get it to show up in the creator box. You are correct. I am even trying to drag and drop but it doesn't show up. It's very weird. I'm not sure why it's not recognizing it. Might it be that it is iso of 10.10 and 8.04.1 for powerpc? (apple ibook g3 version)

What is/are the name(s) of the iso you're looking at now?

---

### Post by amjjawad on 2010-12-25
[http://unetbootin.sourceforge.net/#install](http://unetbootin.sourceforge.net/#install)

As you can see on that link, you need to select "Disk Image" and try then to locate your iso. Store the iso file in some place you can easily access.

---

### Post by hollowtd on 2010-12-25
Here is a screenshot. You can see both iso files to the left. You can see that for some reason I have two usb drives in the second field. You can see after I select other, and select the iso file, that it does not appear in the creator text field. (I can't get the picture to appear for some reason but I'm trying to make a startup disk using either: ubuntu10-10powerpc.iso or ubuntu-8.04.1-desktop-powerpc.iso

---

### Post by hollowtd on 2010-12-25
I've read your link and have made both the iso files executable. Still it doesn't show up in when I select it. Weird.

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> I'm trying to make a startup disk using either: **ubuntu10-10powerpc.iso or ubuntu-8.04.1-desktop-powerpc.iso**


From where did you get these?
I'm trying to access [www.ubuntu.com]("http://www.ubuntu.com") but the page doesn't show up. My connection is so slow.

---

### Post by amjjawad on 2010-12-25
> **amjjawad said:**
> From where did you get these?
I'm trying to access [www.ubuntu.com]("http://www.ubuntu.com") but the page doesn't show up. My connection is so slow.

Okay, now I understand.
[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)

I'm not sure whether you can create LiveUSB from these images. I guess you could do that while you're in Mac. Let me do some search.

---

### Post by hollowtd on 2010-12-25
I got them from here. I changed the name trying to see if that helped after I saved them to my desktop. 

[http://cdimage.ubuntu.com/ports/releases/10.10/release/](http://cdimage.ubuntu.com/ports/releases/10.10/release/)
This is the one for g3 etc Macs. 

and [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) 
This one is for g3 too. Community supported I believe.

---

### Post by hollowtd on 2010-12-25
Oh, that might make some sense. Is there a usb startup disk creator for mac? What if I use the alternate versions? Might that help?

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> Oh, that might make some sense. Is there a usb startup disk creator for mac? What if I use the alternate versions? Might that help?

Never had Mac so I'm trying to figure that out. I'm trying to do some search.

Try to do the same.
Don't you have any Live USB Creator under Mac?

---

### Post by hollowtd on 2010-12-25
All i really want to do is make a live disk using a USB. I just want to test it out first on my g3. I have to use a usb device because cds only hold 700 and this ISO is 710 (plus I'm out of cds).

---

### Post by hollowtd on 2010-12-25
I will look on my mac. I think one has to use terminal in mac but maybe there is one? I'll look into that too.

---

### Post by amjjawad on 2010-12-25
[http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html](http://www.webupd8.org/2009/04/4-ways-to-create-bootable-live-usb.html)

---

### Post by hollowtd on 2010-12-25
Trying image writer now.

---

### Post by hollowtd on 2010-12-25
Well, I think I got it written. I plugged the usb into the g3 and hold down the option key and I can select which HD to boot from. I selec the one with the usb penguin on it and it acts like it's gonna boot and then goes back to the same screen. Hmm Seems like it almost wants to work.

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> Well, I think I got it written. I plugged the usb into the g3 and hold down the option key and I can select which HD to boot from. I selec the one with the usb penguin on it and it acts like it's gonna boot and then goes back to the same screen. Hmm Seems like it almost wants to work.

Keep trying, you almost there :)

---

### Post by hollowtd on 2010-12-25
I know so close. I'm not sure where to go from here. I know the usb must be correct since a little penguin shows up on it.

---

### Post by amjjawad on 2010-12-25
> **hollowtd said:**
> I know so close. I'm not sure where to go from here. I know the usb must be correct since a little penguin shows up on it.

Did you check MD5SUM for your downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Mac%20OS%20X](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Mac%20OS%20X)

[http://cdimage.ubuntu.com/ports/releases/10.10/release/MD5SUMS](http://cdimage.ubuntu.com/ports/releases/10.10/release/MD5SUMS)

---

### Post by hollowtd on 2010-12-25
Well I can get the two HD to show up when I start the G3. When I select the one with the little penguin, though, it doesn't do much but pretend to boot and then go back to the startup screen. I'm not sure if the image writer does the same thing to the usb stick as the unetbootin or startup disk creator. Seemed to work but won't boot into ubuntu. Strange

---

### Post by amjjawad on 2010-12-26
> **hollowtd said:**
> Well I can get the two HD to show up when I start the G3. When I select the one with the little penguin, though, it doesn't do much but pretend to boot and then go back to the startup screen. I'm not sure if the image writer does the same thing to the usb stick as the unetbootin or startup disk creator. Seemed to work but won't boot into ubuntu. Strange

Sorry, was sleeping when you posted.

Did you check my previous post? you did not answer my Q yet :)

Try to check MD5SUM and try to create a LiveUSB again.
I'm not a Mac User but I'm sure there are tons of guides online :)

---

