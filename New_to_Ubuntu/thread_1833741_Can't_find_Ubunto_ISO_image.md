---
title: "Can't find Ubunto ISO image"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by Maese909 on 2011-08-26
Hey all. I have just downloaded the Ubuntu 11.04 ISO image file from Ubuntu's website and am trying to burn it to my DVD-R. However, I can't find the ISO image that I downloaded. I am using InfraRecorder to burn the image. I was gong to just use Windows disk image burner, but everytime I click burn on that it says The Selected disk image file isn't valid. Basically I need to know where to find that ISO file, because InfraRecorder is asking for the file name but I have no idea what it is. I have checked all over my documents but can't find it. Thanks for the help!

---

### Post by BlinkinCat on 2011-08-26
Normally in Downloads I think -

Did you do a sum check by the way?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Maese909 on 2011-08-26
No I didn't do a sum check. I checked the downloads file and it is blank. On Windows Disk Image Burner, at the top it says Ubuntu-11.04-desktop-i386[1].iso but it says the selected disk image file is invalid. Also when I search for that file, it says no items matched...

---

### Post by e79 on 2011-08-26
If you downloaded the latest ISO (which is Natty - 11.04), you should be able to find it when doing a file search in your windows with the following :

For 64bit:  ubuntu-11.04-desktop-amd64.iso

For 32bit: ubuntu-11.04-desktop-i386.iso

Hope this helps

---

### Post by Maese909 on 2011-08-26
I searched both those files but neither came up... By the way, I'm on a Windows 7 machine. This is the first Linux distribution I am trying out too. Also, I downloaded the Ubuntu 11.04 from Ubuntu's main site.

---

### Post by BlinkinCat on 2011-08-26
Are you sure you "Saved" the file?

---

### Post by Maese909 on 2011-08-26
All I know is I downloaded it last night and went to bed. WHen I woke up, the download was finished and a dialog screen appeared that said "Allow" and Do not Allow. I clicked Allow and then the Windows Disk Image Burner popped up...and the window that said 100% complete or whatever closed automatically

---

### Post by BlinkinCat on 2011-08-26
Sorry I can't help any more. - :(

---

### Post by e79 on 2011-08-26
> **Maese909 said:**
> All I know is I downloaded it last night and went to bed. WHen I woke up, the download was finished and a dialog screen appeared that said "Allow" and Do not Allow. I clicked Allow and then the Windows Disk Image Burner popped up...and the window that said 100% complete or whatever closed automatically

Instead of having any kind of application opening this download, could you simply try to redownload it in any folders on your computer ? I assume it was in your %temp% folder since you did not asked to save it, and then got erased since it was not used.

---

### Post by Maese909 on 2011-08-26
O.k. This is what I just did right now. I am downloading the 685MB file again and instead of pressing run, I pressed save. It is downloading and says it will be about 6 hours.
 
Edit: Not 6 hours, but 17 minutes :). Hopefully this will work!

---

### Post by e79 on 2011-08-26
> **Maese909 said:**
> O.k. This is what I just did right now. I am downloading the 685MB file again and instead of pressing run, I pressed save. It is downloading and says it will be about 6 hours.
 
Edit: Not 6 hours, but 17 minutes :). Hopefully this will work!

It should :D 

On another hand, when you will burn your ISO, make sure to _burn it at lowest possible speed_, to avoid any errors. Give us a feedback on how it goes !

---

### Post by BlinkinCat on 2011-08-26
Should do - :P

---

### Post by Maese909 on 2011-08-26
O.k guys. I have just started the Ubuntu installation from a CD onto my Windows 7 laptop. I am on the screen where it says allocate drive space and all I am trying to do is install it next to Windows so I can use both OS's whenever I want. However, this screen that shows partitions and whatever is confusing me. SHould I just click Install Now?
 
P.S. I had to click Save instead of Run to get the ISO image. :<
 
Edit: Blinkin Cat - thanks a ton for telling me to save the ISO. That fixed the major problem!

---

### Post by BlinkinCat on 2011-08-26
I believe you can go "back" or "cancel" if you are not certain.

This may help -
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Maese909 on 2011-08-26
When I hit back the only options are Replace Windows 7 with Ubuntu and Something Else. I clicked on something else and it shows partitions but am not sure how to do that stuff...
 
Edit: The "Something Else" says You can create or resize partitions yourself, or choose multiple partitions for Ubuntu.

---

### Post by BlinkinCat on 2011-08-26
I thought you could "cancel"

You may need to wait for more learned advice than I can give -

I have Xubuntu as my sole OS which was easy to set up! - :(

---

### Post by Maese909 on 2011-08-26
Just some more information, on the Allocate drive Space window, it shows a long orange bar and at the end of the orange is a short blue bar. The blue bar is 14.6GB.
 
Edit: I clicked install not, and i says "No root file system is defined. Please correct this from the partitioning menu." Any idea on what I have to do?

---

### Post by BlinkinCat on 2011-08-26
Hi -

Maybe it would pay to create another thread with a more fitting title - you could link to this thread if you like -

---

### Post by e79 on 2011-08-26
> **Maese909 said:**
> Just some more information, on the Allocate drive Space window, it shows a long orange bar and at the end of the orange is a short blue bar. The blue bar is 14.6GB.
 
Edit: I clicked install not, and i says "No root file system is defined. Please correct this from the partitioning menu." Any idea on what I have to do?

Do you have the option that say :

'Install Ubuntu alongside with Windows ?' 

If so, it should bring you this 'Allocate drive space' in orange and blue. The orange one (if I remember) is the space taken by your Windows installation and the blue the intended partition to install Ubuntu on it. If you decide you have enough space simply hit Continue/Install. If not, you can always drag that bar (if I still remember) to give more or less space to Ubuntu.

The 'root' file system refers to the root foler, where everything begins. A bit like Windows would have a 'C:' as a beginning, you have  a '/' instead of it.

Hope this helps

---

