---
title: "Installing 9.10 from Live CD"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by cdo on 2010-10-29
Trying to install Ubuntu 9.10 from a live cd . Can get to desktop but when i click on the install Ubuntu 9.10 icon and the process gets to step 4 "prepare partitions" message is "no root file system installed , please correct this from the partitioning menu" . I don't even know where the partitioning menu is .  :-)

Note: Our autistic son managed to crash this computer but don't know exactly how . The hard drive had/has both Windows and Ubuntu equally split on it . I want to install Linux and use the entire hard drive removing the Windows . Took me 2 hrs just to get the live cd to work so maybe problem in bios ?

Advice appreciated..

---

### Post by beew on 2010-10-29
What did you do in step 3?

Just out of curiosity, why didn't you install 10.04 or 10.10?

---

### Post by Jetso on 2010-10-29
Did you make a / partition and a swap partition? I think thats the message it gives you when you don't.

---

### Post by nmyrick on 2010-10-29
Have you been able to read anything off of the hard drive?

---

### Post by cdo on 2010-10-29
Step 3 was just setting the keyboard layout . Keep in mind this is install from the live cd desktop icon and not the normal install procedure that i have done in the past as i could not get that to boot as usual from the first screen . Hope that makes sense .

Using a 9.10 cd only because i don't have a newer version .

---

### Post by Jetso on 2010-10-29
Okay, step four should say: 
1.) Install along side other Operating Systems
2.) Install as only OS
3.) Manually define Partition

Which are you choosing? That should help *us* help *you.*

---

### Post by beew on 2010-10-29
You can download 10.04 or 10.10 from here.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Sorry, that was a typo, I meant to say what did you do in step 4, meaning which install option  you chose.

---

### Post by nmyrick on 2010-10-29
In step 4, which you should be able to back up to, you need to make a / partition (/ is the boot partition) and format it as either ext3 or ext4. Then you need to make a linux-swap partition.  I would just use the default settings for size, which is generally about 2 1/2 times the size of your RAM.  Then you should be able to format the drives.  

However, you need to _**make sure that you backup everything on the drive before you do this**_! Formatting will destroy everything on the drive! You should be able to recover all of your files by using the live desktop of the 9.10 cd and going into your system drive, and back them up to a USB hard drive before you re-format.

---

### Post by cdo on 2010-10-29
Ray

That's not what i am seeing . Step 4 shows a screen that says "setting up partitions" then switches to a screen that says "Install" at the top and "prepare partitions" next but the screen is blank . Listed below are these identities - Device , Type , Mount Point , Format ? , Size , Used . None of these titles are active if moused . If i forward i get the "no root file system is defined" message which i assume is because the step 4 process is not live/active ?

---

### Post by cdo on 2010-10-29
Maybe that's what has happened . Maybe there is nothing on the hard drive to be read ?

---

### Post by beew on 2010-10-29
Ok. check out the screenshots here.

[http://www.pronetworks.org/forums/ubuntu-9-04-installation-screenshots-t108880.html](http://www.pronetworks.org/forums/ubuntu-9-04-installation-screenshots-t108880.html)

Does step 4 look like what you are seeing?

---

### Post by cdo on 2010-10-30
Yes , same process except for 9.10 instead of 9.4 . Problem is step 4 is not active . The actual partitioning process never engages /starts .

---

### Post by beew on 2010-10-30
What do you mean by step 4 is not active? Can you choose the install option? It shouldn't start preparing partition without you checking a box first.

---

### Post by cdo on 2010-10-30
No box appears to check from step 3 to step 4 . Only option is to forward and next screen pops up . I can take a screenshot but don't know how to get it to you .

---

### Post by beew on 2010-10-30
When you boot from the CD, there should be two options: Try Ubuntu or Install Ubuntu. If you pick "Try" it will boot you into the Ubuntu desktop, from which you can also install by clicking the "Install Ubuntu" icon (something like that, can't remember the exact words) 

If you install inside the Ubuntu desktop you should be able to take screen shots and access the internet. I don't know the lay out of 9.10 but in 10.10 and 10.04 you can take screen shots from Applications > Accessaries > Take Screen Shots or just use the function key in your keyboard.

---

### Post by georgetom on 2010-10-30
I think if you do not have another OS installation to take care of AND know which drive you want the installation to be in, why don't you try the 'Specify partitions Manually'option. Here you tell him where root (/) and swap should be and then then click next.

BUT BE SURE ABOUT THE PARTITIONS YOU PROVIDE IF YOU HAVE DATA IN SOME OF THEM.

---

### Post by cdo on 2010-10-30
I did boot from the cd and did click Install Ubuntu but for some reason the boot went to the Ubuntu desktop . I am having the step 4 issue when clicking the Install ubuntu icon . 

I have a screens hot sitting on my desktop and obviously have an internet connection . What do i need to do so that you can see the screen shot ?

---

### Post by cdo on 2010-10-30
> **georgetom said:**
> I think if you do not have another OS installation to take care of AND know which drive you want the installation to be in, why don't you try the 'Specify partitions Manually'option. Here you tell him where root (/) and swap should be and then then click next.

BUT BE SURE ABOUT THE PARTITIONS YOU PROVIDE IF YOU HAVE DATA IN SOME OF THEM.


I am not being given a 'specify partitions manually option" .

---

### Post by beew on 2010-10-30
There may be better ways to do it, but you can click "Quick Reply" and then Under the reply box click "Go dvanced" you should see a more elaborate reply box where there is an option to upload attachment.

---

### Post by cdo on 2010-10-30
I did upload the screen shot so let me know if it got there /here .   :-)

---

### Post by beew on 2010-10-30
No. :)

---

### Post by cdo on 2010-10-30
Ok , well it said it uploaded so i have no idea .  I am going to reboot and see if i just missed something along the way which might mean i get back on line and might not .

 I appreciate all the suggestions and you efforts very much . That's the best thing about Linux , the people who use it and their willingness to help out us old guys that grew up on punch cards .  :-)

Be in touch if able ..

thanks Again ... everyone

---

### Post by nmyrick on 2010-10-30
When you are in the desktop portion of the live CD, you should be able to read the hard drive under Places>computer>file system.  If you haven't already re-formatted the drive and you and can't read anything on the hard drive or if the file system drive doesn't show up, then the hard drive is probably shot.  

Also, you say that your son crashed the computer.  Are you sure that he just didn't compress the entire drive in Windows?  I've seen this before, and it will compress the entire drive, including the boot sector, and will cause Windows to not boot.  I don't know what effect it would have on a dual-booted system.

What you need to do, in this case, is to remove the hard drive and install it in another Windows machine or connect it to a Windows laptop with a USB connector and de-compress the drive.

To do this, once the drive is connected to the other computer, double click on 'My Computer', right click on the affected drive, then select 'Properties,' then un-check the box next to 'Compress drive to save disk space' then select OK.  Yes, unfortunately in Windows, the default user has admin privileges and is actually allowed to screw up the entire drive by selecting this option!

---

### Post by cdo on 2010-10-30
> **nmyrick said:**
> When you are in the desktop portion of the live CD, you should be able to read the hard drive under Places>computer>file system.  If you haven't already re-formatted the drive and you and can't read anything on the hard drive or if the file system drive doesn't show up, then the hard drive is probably shot.  

Also, you say that your son crashed the computer.  Are you sure that he just didn't compress the entire drive in Windows?  I've seen this before, and it will compress the entire drive, including the boot sector, and will cause Windows to not boot.  I don't know what effect it would have on a dual-booted system.

What you need to do, in this case, is to remove the hard drive and install it in another Windows machine or connect it to a Windows laptop with a USB connector and de-compress the drive.

To do this, once the drive is connected to the other computer, double click on 'My Computer', right click on the affected drive, then select 'Properties,' then un-check the box next to 'Compress drive to save disk space' then select OK.  Yes, unfortunately in Windows, the default user has admin privileges and is actually allowed to screw up the entire drive by selecting this option!


I am thinking you may be on to something regarding Windows as our son prefers it for gaming . I can see the files in places> computer> file system . I tried to get into the Windows part of the dual boot a couple of days ago and it would not boot to Windows .

My wife was actually on her Ubuntu desktop yesterday when the system froze up . Rebooting just pulled up a blank screen . Now , i tried monkeying with the bios and  made have made things worse as now the bios don't recognize a hard drive . 

If i reboot the computer with the Ubuntu live cd it will not install and in fact tries to install with the ubuntu desktop live cd process .  :-) the only way i could get back on-line was by booting to the "try live cd" function . But , still have the same issues with partitioning .

---

### Post by Jetso on 2010-10-30
Why don't you just go to Ubuntu.com and download the 10.10 .iso. Burn the image to the disc, load it up, then take a screen shot and upload it to us. I *Think* more people are familiar with 10.10 than 9.10, as that was about a year ago.

---

### Post by nmyrick on 2010-10-30
You need to fix the BIOS first.  Nothing will be able access the hard drive if the BIOS can't see it.  Not even the live CD.

---

