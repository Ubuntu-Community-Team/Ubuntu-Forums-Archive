---
title: "[SOLVED] NO FONTS in qtparted"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by SVWander on 2008-12-16
I just started Open Office and found there were no fonts in that program either. This is getting frustrating! I hate to spend another half day reinstalling everyting.

Is it just me are this particular machine . . . my Dell laptop doesn't seem to have this problem. First I installed Wine but when trying to configure it there were no fonts in the configuration. I thought it was a problem with Wine but then I had the same problem with K3B. So I moved my files to the server and reinstalled Ubuntu. I went through a couple of hours to get all the updates and went to Synaptic Package Manager to install Qtparted . . . guess what? No fonts. It is hard to use a program without them. What am I doing wrong? As I said I have no problem with my Dell. I thought it might be the NVIDIA drivers so I disabled them, logged out then back in and opened qtparted. Still no fonts. Do I have to install an older version of Ubuntu? Is this a problem for anyone else? I attached a screen shot.

Thank you, Tim

---

### Post by Shhnap on 2008-12-17
Try (in a terminal): 

sudo apt-get install sun-java6*

and see if that gives you the fonts. :) After all, open office runs off java, so maybe java provides the fonts.

---

### Post by SVWander on 2008-12-17
> **Shhnap said:**
> Try (in a terminal): 

sudo apt-get install sun-java6*

and see if that gives you the fonts. :) After all, open office runs off java, so maybe java provides the fonts.

Thank you but it didn't help. I don't know if it is in my original post but when I started open office in the terminal I got this error:

openoffice
javaldx: Could not find a Java Runtime Environment! 

So I tried installing Java in Synaptic but sadly it didn't help. Sadly because it looks like I am going to have to reinstall and I am not sure that will help. 

Tim

---

### Post by Kellemora on 2008-12-17
Hi SVW

May I ask HOW you Installed Ubuntu?
Was it from a Live CD and if so, which install did you select?
Was it from an Alternative CD?
Or did you load it from an SD card or USB stick?

Also, did you TEST the data to make sure it was all there before installing md5sum?

If from a CD, did you burn the CD as an .iso and NOT as a copied file or just copied an iso image to a CD.  It MUST be burned as an .iso Image File, no other way will work that I know of.

I have a couple of Dells I've installed Ubuntu on.  Was one of my easier installs.  Dell OptiPlex GX270's.

You shouldn't have had to load things separately from the install other than possibly adding msttcore fonts.

You DO have your fonts in the /usr/share/fonts folder don't you?
If you put them in /home/user/.fonts a hidden file, they will not work with any other user or root.

There is also another file /etc/fonts/fonts.conf
and I've found fonts located in /usr/local/share/fonts also, and have no idea why they are there.  They look specific to a later installed program so I left them there.

But it really sounds like you didn't get a complete or proper install!

TTUL
Gary

---

### Post by SVWander on 2008-12-18
> **Kellemora said:**
> Hi SVW

May I ask HOW you Installed Ubuntu?
Was it from a Live CD and if so, which install did you select?
Was it from an Alternative CD?
Or did you load it from an SD card or USB stick?

Also, did you TEST the data to make sure it was all there before installing md5sum?

If from a CD, did you burn the CD as an .iso and NOT as a copied file or just copied an iso image to a CD.  It MUST be burned as an .iso Image File, no other way will work that I know of.

I have a couple of Dells I've installed Ubuntu on.  Was one of my easier installs.  Dell OptiPlex GX270's.

You shouldn't have had to load things separately from the install other than possibly adding msttcore fonts.

You DO have your fonts in the /usr/share/fonts folder don't you?
If you put them in /home/user/.fonts a hidden file, they will not work with any other user or root.

There is also another file /etc/fonts/fonts.conf
and I've found fonts located in /usr/local/share/fonts also, and have no idea why they are there.  They look specific to a later installed program so I left them there.

But it really sounds like you didn't get a complete or proper install!

TTUL
Gary


Hi Gary,

I installed using a CD I downloaded. The desktop system is an "old" Gateway. It has had Ubuntu on it since Edgy . . . maybe before that. I didn't check the CD but will as soon as I finish writing this. It is the same disk that I installed to my Dell laptop without a hitch. I also ordered a CD and it should be here fairly soon. But the problem started with an upgrade to Intrepid. I installed Wine after the upgrade but had no fonts so I did a complete reinstall using the CD. But the problem was even worse! 

I think you are right about an incomplete install and I will do that again soon. Hopefully it will help.

Thanks again, Tim

Just rebooted after checking the disk. The media check found no errors. I hate the thought of reinstalling only to have the same thing happen.

tm

---

### Post by JohnLM_the_Ghost on 2008-12-18
You might also try to force reinstalling **defoma **and any **ttf-*** packages you might (or not) have...
It can all be done through ```
sudo aptitude
```

---

### Post by Kellemora on 2008-12-18
Hi SVW

Is there anything in Intrepid that you need or want?

The stable Hardy 8.04 LTS version will be supported for at least 6 months after Intrepid is dead and buried.

And if you are working with an older machine, Hardy may be the way to go.  It seems with each new release they drop older drivers from the Kernel and even if you can find them, sometimes they aren't compatible with the newer Kernels.

I know from all my years using Windows that once you have a machine stable and everything in it working right.  Don't update it anymore or you'll end up having to update everything else that goes along with it.  I still have an OLDE Doze 95 machine here with a CGA monitor.  Slow as Grandma Moses, but it works and has games the grandkids love.  So it sits in the playroom for when they come over.  When it dies, I have a couple of old 98 machines to stick in their place.

I was using XP and knew it's days were numbered.  90% of the software I use in business would not run on the Ultimate Spyware OS known as Vista, and at 61 years old, I'm NOT plunking down 8 grand to replace all that software.

Along came Ubuntu and all the software I needed, just about, and all for FREE, with a couple of exceptions of course.

It was a simple decision to make for me!
Eight Grand vs FREE with a learning curve and perhaps a couple of headaches.  Aspirin is Cheap, hi hi..........

I converted my entire office over to Ubuntu, except for two XP machines to run hardware not supported in Linux.  And I did this within the first month of being introduced to Ubuntu.  I've only been running Ubuntu now for like 3 months, 2 months REAL TIME!
Best move I ever made!
But, nothing new do you learn overnight, but I will say, what problems I did have were solved almost instantly.  I still have the same problems in XP that I had since day one with no workarounds.
At least in Linux, there ARE workarounds or alternatives.  And the folks here will tell you about each and every one of them too, so you can try them all until you are a happy camper with one of them.

Good Luck on getting your machine up and running!
I have a couple of older machines too that are as cantankerous as an old mother hen.  But with a little tweaking here and there, with help from the guru's here, they are doing just fine now!

TTUL
Gary

---

### Post by SVWander on 2008-12-19
> **Kellemora said:**
> Hi SVW

Is there anything in Intrepid that you need or want?

The stable Hardy 8.04 LTS version will be supported for at least 6 months after Intrepid is dead and buried.

And if you are working with an older machine, Hardy may be the way to go.  It seems with each new release they drop older drivers from the Kernel and even if you can find them, sometimes they aren't compatible with the newer Kernels.

I know from all my years using Windows that once you have a machine stable and everything in it working right.  Don't update it anymore or you'll end up having to update everything else that goes along with it.  I still have an OLDE Doze 95 machine here with a CGA monitor.  Slow as Grandma Moses, but it works and has games the grandkids love.  So it sits in the playroom for when they come over.  When it dies, I have a couple of old 98 machines to stick in their place.

I was using XP and knew it's days were numbered.  90% of the software I use in business would not run on the Ultimate Spyware OS known as Vista, and at 61 years old, I'm NOT plunking down 8 grand to replace all that software.

Along came Ubuntu and all the software I needed, just about, and all for FREE, with a couple of exceptions of course.

It was a simple decision to make for me!
Eight Grand vs FREE with a learning curve and perhaps a couple of headaches.  Aspirin is Cheap, hi hi..........

I converted my entire office over to Ubuntu, except for two XP machines to run hardware not supported in Linux.  And I did this within the first month of being introduced to Ubuntu.  I've only been running Ubuntu now for like 3 months, 2 months REAL TIME!
Best move I ever made!
But, nothing new do you learn overnight, but I will say, what problems I did have were solved almost instantly.  I still have the same problems in XP that I had since day one with no workarounds.
At least in Linux, there ARE workarounds or alternatives.  And the folks here will tell you about each and every one of them too, so you can try them all until you are a happy camper with one of them.

Good Luck on getting your machine up and running!
I have a couple of older machines too that are as cantankerous as an old mother hen.  But with a little tweaking here and there, with help from the guru's here, they are doing just fine now!

TTUL
Gary

Hi Gary,

I got it working by reinstalling the entire system. I simply backed my stuff up to my little file server and reinstalled, but before I did I ran CD-Live and installed qtparted. I wanted to check to see if the fonts were going to be there because I had a fear it was something to do with my hardware. Anyway, by reinstalling the lost fonts were found. Qtparted and Wine were there for me to use.

I agree totally but it is not just a matter of cost. The entire operation including the test with CD-Live took less than three hours and would have taken less had I been near the computer during all that time. Had I tried to reinstall XP, for whatever reason, I would still be at it. And that is just the dumb operating system that can do almost NOTHING. After installing XP I would have to send HOURS loading disks, putting in silly validation codes, updating the software and gone through countless reboots. Ubuntu for most apts is the way to go. The only one I haven't been able to get to work is the GPS for my laptop. So as the kids say . . . or maybe they don't anymore . . . I don't know. Ubuntu  ROCKS.

Tim

---

### Post by SVWander on 2008-12-19
> **Kellemora said:**
> Hi SVW

Is there anything in Intrepid that you need or want?

The stable Hardy 8.04 LTS version will be supported for at least 6 months after Intrepid is dead and buried.

And if you are working with an older machine, Hardy may be the way to go.  It seems with each new release they drop older drivers from the Kernel and even if you can find them, sometimes they aren't compatible with the newer Kernels.

I know from all my years using Windows that once you have a machine stable and everything in it working right.  Don't update it anymore or you'll end up having to update everything else that goes along with it.  I still have an OLDE Doze 95 machine here with a CGA monitor.  Slow as Grandma Moses, but it works and has games the grandkids love.  So it sits in the playroom for when they come over.  When it dies, I have a couple of old 98 machines to stick in their place.

I was using XP and knew it's days were numbered.  90% of the software I use in business would not run on the Ultimate Spyware OS known as Vista, and at 61 years old, I'm NOT plunking down 8 grand to replace all that software.

Along came Ubuntu and all the software I needed, just about, and all for FREE, with a couple of exceptions of course.

It was a simple decision to make for me!
Eight Grand vs FREE with a learning curve and perhaps a couple of headaches.  Aspirin is Cheap, hi hi..........

I converted my entire office over to Ubuntu, except for two XP machines to run hardware not supported in Linux.  And I did this within the first month of being introduced to Ubuntu.  I've only been running Ubuntu now for like 3 months, 2 months REAL TIME!
Best move I ever made!
But, nothing new do you learn overnight, but I will say, what problems I did have were solved almost instantly.  I still have the same problems in XP that I had since day one with no workarounds.
At least in Linux, there ARE workarounds or alternatives.  And the folks here will tell you about each and every one of them too, so you can try them all until you are a happy camper with one of them.

Good Luck on getting your machine up and running!
I have a couple of older machines too that are as cantankerous as an old mother hen.  But with a little tweaking here and there, with help from the guru's here, they are doing just fine now!

TTUL
Gary

Hi Gary,

Tested my CD-Live and it was okay. Then I ran CD-Live and downloaded Wine. It worked without a flaw, so I just reinstalled the operating system and everything is working fine now!

The value of Ubuntu and Linux isn't just the upfront costs. If this had been XP and I had a similar problem I would have sent HOURS just installing the operating system and dwonloading updates, and then spent even more time installing programs. Any Windows product is of almost no use without the programs you purchase. Many require rebooting some require validation codes. It adds up to lots of time and frustration . . . the old where the hell did I put that damn disk, and endless searching online for drivers and such. 

I enjoy Linux. It makes working with computer fun.

Tim

---

### Post by simi182 on 2008-12-25
Hey... I have the same problem.. Have no fonts in wine.. just like in a photo pasted in this theme?? Anyone know how to get them back?? Do i need to install anything? ive reinstalled 8.10 like for 4 times...any when i install wine with apt or package manager.. everything is the same.. no fots in wincfg.. even if i run a windows game install everything is the same..... Please help me :D 
tnx

---

### Post by simi182 on 2008-12-25
Found a Fix in this theme...

[http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+fonts](http://ubuntuforums.org/showthread.php?t=1009930&highlight=wine+fonts)

everything works now
tnx.

---

