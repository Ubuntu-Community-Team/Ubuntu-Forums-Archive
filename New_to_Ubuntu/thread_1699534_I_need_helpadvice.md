---
title: "I need help/advice"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Glendža on 2011-03-03
I am currently using Windows 7, and I find it too sparkly, fancy and  useless for my needs. Saw Linux today, and I really liked it, and want  to install it, but first I need to know some very important details, so  if anyone could help me... :KS  I also need Linux for C programming... I will install it anyway, I am  deciding if I should install it on a partition or replace the win7 with  it :)

First, this is my computer, got it for a far much bigger  price than I should, it is warm as hell itself, you can fry pancakes on  the lower side of it, so it is very useless for games because it  overheats and the lags begin... MSI CR610...

Ok, these are my needs:

1) Will I be able to find all the drivers needed, the integrated camera and microphone are very important ones;
2) Is there a good Nero replacement for burning CD's and DVD's?
3) Will I be able to watch all usual movie formats?
4) Is there any image editor that is at least close to photoshop?
5) Will I be able to open microsoft office documents? 
6) Will I be able to connect via my wireless modem?

Hope somebody can help me :)

---

### Post by migrate from windows on 2011-03-03
Yes to all...... sometimes finding drivers may be a trouble..please post a list of the harware you have so that people with similar hardware can share their experience.

---

### Post by NCLI on 2011-03-03
> **Glend&#382 said:**
> Ok, these are my needs:

1) Will I be able to find all the drivers needed, the integrated camera and microphone are very important ones;
When you boot from the install cd for the first time, you can choose to just try Ubuntu without installing it. This is great for checking whether the necessary drivers for your devices exist. In Linux, all drivers are included in the kernel, which means that either it works out of the box, or it doesn't work at all. There are a few drivers you have to install separately, due to licensing issues, but they are all listed in System->Administration->Additional Drivers.
> 2) Is there a good Nero replacement for burning CD's and DVD's?
Plenty. I recommend K3B, which is easily installable from the Software Center. Brasero is the default CD/DVD writing app, and it does fine for simple tasks.
> 3) Will I be able to watch all usual movie formats?
Yes, just make sure to install Ubuntu Restricted Extras from the Software Center, or tick the box asking you whether you want Ubuntu to install the usual codecs during the installation.
> 4) Is there any image editor that is at least close to photoshop?
Yes, GIMP, which is also easily installable from the Software Center(Beginning to notice a pattern here? ;))
> 5) Will I be able to open microsoft office documents? 
Yes, OpenOffice is included, and handles all document formats just fine.
> 6) Will I be able to connect via my wireless modem?
Are we talking 3G or WiFi?

Both should "just work", but 3G can be problematic, depending on the model.

---

### Post by Glendža on 2011-03-03
> **migrate from windows said:**
> Yes to all...... sometimes finding drivers may be a trouble..please post a list of the harware you have so that people with similar hardware can share their experience.

Here you go:

AMD Athlon II Dual-Core M320 2.10 GHz
3.00 G  of ram
ATI Mobility Radeon HD 4200
some integrated camera and mic
That's all I know :(

[http://www.testfreaks.co.uk/laptops/msi-cr610/](http://www.testfreaks.co.uk/laptops/msi-cr610/)

---

### Post by wojox on 2011-03-03
Dual boot until you get use to it. :P

---

### Post by Glendža on 2011-03-03
> **NCLI said:**
> Are we talking 3G or WiFi?

Both should "just work", but 3G can be problematic, depending on the model.

It is WiFi... So no problems with all? :D GIMP is great...

And camera and mic? My uncle had some problems with camera, he cannot use it at all, that's why I'm asking:/

---

### Post by NCLI on 2011-03-03
> **Glend&#382 said:**
> Here you go:

AMD Athlon II Dual-Core M320 2.10 GHz
3.00 G  of ram
ATI Mobility Radeon HD 4200
some integrated camera and mic
That's all I know :(

[http://www.testfreaks.co.uk/laptops/msi-cr610/](http://www.testfreaks.co.uk/laptops/msi-cr610/)

Just pop the installation CD in the drive, select "Try Ubuntu", then see whether it works :)

You can always come back here if you encounter any problems.

---

### Post by NCLI on 2011-03-03
> **Glend&#382 said:**
> It is WiFi... So no problems with all? :D GIMP is great...

And camera and mic? My uncle had some problems with camera, he cannot use it at all, that's why I'm asking:/

If it's WiFi, it should work out of the box nowadays. If it doesn't, connect to the wired network, and check System->Administration->Additional Drivers. There are still a few WiFi drivers which can't be included in the kernel, but it's quite rare now.

When it comes to the camera and mic, most of them work perfectly well, but there are a few bad apples. Just use the live cd to make sure, you can even use Firefox to post here while running Ubuntu from the CD, so we'll be able to help you immediately :)

---

### Post by Glendža on 2011-03-03
Thanks for help! :) I'm impressed :) Going for a test drive now :)

---

### Post by NCLI on 2011-03-03
> **Glend&#382 said:**
> Thanks for help! :) I'm impressed :) Going for a test drive now :)

I'll be keeping an eye on this thread for a few hours, so just post any issues/questions you encounter.

---

### Post by houseworkshy on 2011-03-03
Well you can collect some knowlage to have by your elbow first.

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

Are both excellent introductions and the pdf downloads are free.  Highly  recomended.  I learned and at the same time set up my system using one  of them.

Next which version of Ubuntu?  I'd go for the long terms support one,  10.04.1 lts at the moment, but that is just my preferance.  

The easy way to answer some of your questions is to burn an iso and boot  up with it, then select "try Ubuntu without changeing your system" or  something like that.  It will run more slowly than from the hd.  Then  try it out.  Whilst in there go to System>Administration>Hardware  drivers, that will go online and search for your graphic card drivers.   If found you're ook to go, but don't yet, just back out.  Installing  them requires a reboot so is pointless but at least you'll know.
If all is good then go for it.

1/ I think that you will probably be ok with drivers most are with many  built in anyway.  Canon printers are very badly supported.

2/Yes and actually much better, in default install with several  alternatives if you wish.  Nero is dreadful compaired to most linux  burning software, on applications I think linux is king, less so for  games but good and getting better.  Certainly cheaper too as in mostly  free.

3/Yes, though you will have to do some simple installing for propritrey  ones. There is a windows one with a double barrel extension which I  haven't got to work yet ( but I haven't tried really as it is rare )

4/The gimp, superb in my opinion.  Once you get used to a very differant  interphase with "floating windows".  With the addition of gimp gap it  can also animate.  I love it

5/Yes you can AND you can save in their format too if you wish, can also  export files as pdf's.  Open office is the one and most of it will be  there on your default install.

6/Should be automatic.  When doing the live cd test open firefox and see if you can browse.   

Duel boot or all Ubuntu?  Well I'd go with duel boot to start with just  in case something essential is win only and you can't find an  equivelent.  That's what I did, lasted about a month then I just  couldn't be bothered mending vista when it went wrong and got rid of ms  for good.  oddly I was getting only 500 on the win side and at least 800  download speed on the linux side from the same machine when going  online, no idea why or even if that was normal or strange.  i also found  that when I tested rendering similar animations in gimp, for which  there is a windows version ( made a fractal, made it tileable, turned it  into a little gif of a spining ball ), same size the rendering in linux  was way faster.

You mention games, try "+Ubuntu +games" in youtube and take a look.  Open source develops very fast and well see for yourself.  

On apps just brilliant, scribus, open office, cinelerra, blender,  stunningly good.  Any media task you want to accomplish.  For sound,  which you mention, check out rose garden once you've got a hard drive  installation set up. 

Hope you enjoy it.

---

### Post by NCLI on 2011-03-03
@houseworkshy: I wouldn't recommend 10.04 in this specific case. His WiFi card reportedly has issues with anything earlier than 10.10.

---

### Post by houseworkshy on 2011-03-03
Thanks Cinnamon, I didn't know that.  Maybe that is why he hasn't posted back from a live cd session. I hope he saw that, drat..I'll feel guilty if he doesn't.

---

### Post by Glendža on 2011-03-03
Hey, one more question: Is there any Disk Management program available? To format partitions, merge, create them etc?

---

### Post by Jerry N on 2011-03-03
> **Glendža said:**
> 

2) Is there a good Nero replacement for burning CD's and DVD's?
3) Will I be able to watch all usual movie formats?
4) Is there any image editor that is at least close to photoshop?
5) Will I be able to open microsoft office documents? 


2.  K3b works OK but I prefer Nero for Linux.  It costs about $40
3.  Probably
4.  Depends on what you are doing with Photoshop.  If you are working with RAW files, GIMP does not do 16 bit color depth at all.  Version 2.8 will allegedly fix that, if it ever gets released.  Otherwise, GIMP works well with JPG files.  Try GIMP for Windows if you want to see how it works. 
5.  Open the files, yes.  But Openoffice is likely to screw up any fancy formatting you have in Word and it won't use your Excel macros, if any. It might mess up Excel graphs too. If you are using Access, you are out of luck.  Try Openoffice.org (or Libreoffice) for Windows to see if it works OK with your Office files.

Jerry

---

### Post by NCLI on 2011-03-03
> **Glend&#382 said:**
> Hey, one more question: Is there any Disk Management program available? To format partitions, merge, create them etc?

Yes, Gparted is installed on the LiveCD, and available from the Software Center once you've installed.

I fell asleep in my chair, so it's bed time now. I'll check back here in ~7 hours, to make sure everything went OK. :)

---

### Post by Glendža on 2011-03-03
I burned the image, but I cannot boot it :( It starts windows all over again, or if I try to change the boot device it shows some errors :/

---

### Post by NCLI on 2011-03-04
> **Glendža said:**
> I burned the image, but I cannot boot it :( It starts windows all over again, or if I try to change the boot device it shows some errors :/

Try downloading the iso again, your download may have been corrupted. If it still doesn't work, try to boot from a USB drive instead.

---

### Post by Glendža on 2011-03-04
I chose to install it as normal windows application on a separate partition I made, now it works just fine :) I like it for now :) Only I wish if it wouldn't ask me for password every time i try to do something :P

---

### Post by NCLI on 2011-03-04
> **Glendža said:**
> I chose to install it as normal windows application on a separate partition I made, now it works just fine :) I like it for now :) Only I wish if it wouldn't ask me for password every time i try to do something :P

That's just the way Linux works. In return, it's completely safe :)

---

### Post by Glendža on 2011-03-04
So there is no way to stop that from prompting? 

My mic and camera are not working on skype :/

---

### Post by Paddy Landau on 2011-03-04
> **Glendža said:**
> I chose to install it as normal windows application on a separate partition I made
Do you mean WUBI? If so, please be aware that WUBI is lovely for experimenting, but it is not reliable especially when it comes time to upgrade.

> **Glendža said:**
> Only I wish if it wouldn't ask me for password every time i try to do something
It only does that when you are about to do something that affects your system. That's a big reason that (so far) Linux has no viruses. Once your system is properly set up, you won't be getting that prompt all the time.

When you are ready to run Ubuntu for real, dual-boot with Windows so that you have the best of both worlds.

---

### Post by Paddy Landau on 2011-03-04
> **Glendža said:**
> My mic and camera are not working on skype :/
Go to the Skype options and experiment with the Sound Devices and the Video Devices. Skype can be a little problematic at first, but once you have it working, it works fine.

---

### Post by Glendža on 2011-03-04
Camera works now, but mic is not working yet :P 

Now I have a situation here, I have Win 7 on partition C and Ubuntu on partition D. If I format C with disk manager, will I get booting problems? I used the "install as normal windows application" option when installed Ubuntu on D, and I'm on dual boot now.

---

### Post by Paddy Landau on 2011-03-04
> **Glendža said:**
> Camera works now, but mic is not working yet
Search the forum for your Skype problem, because other people have had your problem. If you don't find a solution, start a new thread so that someone with more knowledge than me can help you.

> **Glendža said:**
> I have Win 7 on partition C and Ubuntu on partition D.
We have to be careful about names. Partitions do not have the names C or D. They have names like sda1, sda2, sda3 and so on.

Windows gives these partitions names. Probably, it calls sda1 C and sda2 D. So, I'm guessing that you installed Ubuntu on sda2.

In order to find out, please *either*:

[LIST]
[*]Go to System > Administration > GParted; then make a screenshot (press Alt-PrintScreen); and post your screenshot here.
[/LIST]
*or:*

[LIST]
[*]Open a terminal (Accessories > Terminal); type:
```
sudo parted --list
```Post the results.
[/LIST]

When you want to install Ubuntu properly, you need to *first* uninstall WUBI to clear your bootup choices. Warning: When you uninstall WUBI, you will *lose all data* in your WUBI Ubuntu (but your Windows will still be safe). I'm guessing you don't have any data in your WUBI, though, as you have been experimenting.

---

### Post by Glendža on 2011-03-04
Here's what I think you ask :P

[http://img140.imageshack.us/i/screenshotjvr.png/](http://img140.imageshack.us/i/screenshotjvr.png/)

---

### Post by NCLI on 2011-03-04
> **Glend&#382 said:**
> Here's what I think you ask :P

[http://img140.imageshack.us/i/screenshotjvr.png/](http://img140.imageshack.us/i/screenshotjvr.png/)

You've installed using WUBI, so yes, you will not be able to boot Ubuntu after erasing Windows. You have to do an ordinary install to get rid of Windows.

I'd recommend installing from a USB drive, since you had trouble using the CD. Here's [the official guide]("http://www.ubuntu.com/desktop/get-ubuntu/download") for doing just that.

---

### Post by Glendža on 2011-03-04
> **NCLI said:**
> You've installed using WUBI, so yes, you will not be able to boot Ubuntu after erasing Windows. You have to do an ordinary install to get rid of Windows.

I'd recommend installing from a USB drive, since you had trouble using the CD. Here's [the official guide]("http://www.ubuntu.com/desktop/get-ubuntu/download") for doing just that.

Blah hope all this work is worth it :) 

Only, my bios cannot boot from USB... And I wasn't able to boot from ubuntu CD yesterday neither...

---

### Post by NCLI on 2011-03-04
> **Glend&#382 said:**
> Blah hope all this work is worth it :) 

Only, my bios cannot boot from USB... And I wasn't able to boot from ubuntu CD yesterday neither...

Well that's problematic. What happened when you tried the cd?

Also, are you absolutely sure you can't boot from USB? The computer must be very old if it can't do that.

---

### Post by Paddy Landau on 2011-03-04
Thanks for the screenshot.

You have the following partitions on your drive:

[LIST]
[*]sda1 (primary): NTFS (a Windows partition, probably C)
[*]sda2 (primary): NTFS (a Windows partition, probably D)
[*]sda3 (extended): an extended partition, which contains sda5
[*]sda5 (logical): NTFS (a Windows partition, probably E)
[*]sda4 (primary): NTFS (a Windows partition, probably F)
[/LIST]
(By the way, in case you don't know, a drive can hold at most four partitions. These are usually "primary" partitions. However, an "extended" partition can contain extra "logical" partitions, allowing you to have more than four partitions. Linux does not care whether a partition is primary or logical.)

I agree with NCLI ([post 27]("http://ubuntuforums.org/showthread.php?p=10521423#post10521423")).

To make efficient use of your drive, I would recommend:

[LIST]
[*]Delete partitions sda4, sda5 and sda3 -- but **be careful** in case you have data on them! *Back up everything, first.* This will leave you with sda1 and sda2, with the rest of your drive blank.
[*]Create a new *extended* partition to fill the blank part of your drive. This will be called sda3.
[*]Create three logical partitions *inside* sda3, called sda4, sda5 and sda6.
[LIST]
[*]I would make sda4 10Gb; this will hold your Ubuntu operating system.
[*]I would make sda5 the size of double your RAM (e.g. if you have 4Gb RAM, make it 8Gb). This will be your swap area.
[*]Make sda6 fill the remainder of your drive. This will be your home partition.
[/LIST]
 
[/LIST]

After you have uninstalled WUBI, you can manage the partitions from the Live CD (once you have it working) from the menu System > Administration > GParted. Be careful! Ask if you get stuck!

Then, when you install 10.04, choose the manual partitioning method. Set sda4 to your root ("/") partition, sda5 to the swap, and sda6 to your home ("/home").

This seems complicated when reading it here, but it's really quite easy. Doing it this way will make it easier for you in the long run.

---

### Post by Toafan on 2011-03-04
Glendža, it sounds like you might be having BIOS trouble.  Try this:
[LIST=1]
[*]Make sure your boot media (CD or USB) is connected
[*]Restart your computer (no, not right away - you need to read the rest of this first! :P)
You're going to need to watch closely as it boots, so don't go away.
[*]Right after it turns on, the BIOS load screen will come up.  It'll put up some messages.  One of them should say something like "press DEL to enter setup" or "press F12 to enter BIOS".  On some of the modern Dell systems I've used, it says "Press F12 for boot options" in the top right corner - if you see something like that, hit it.  Otherwise, just pick one.
[*]The boot list, if you have it, should give you a simple list of options, and one of them should be your CD (or USB).   Otherwise, you'll have to look in the BIOS for a boot order option (try looking for "boot order").  Your Hard Disk is should be at the top - that's why you can't boot from anything else.  Move your CD (or USB) to the top of the list, then exit the BIOS (it has an exit option) - make sure to save your settings! - and let it reboot.  DON'T change anything else in the BIOS unless you know what you're doing - it could really muck up your system, and the only way to fix it would be to go back in the BIOS and set it back.
[*]After you reboot, you should now find yourself at the ubuntu 'loading' screen and can continue.

When you're done, just remove your CD or USB from your computer before it turns back on - when it boots, your laptop will look for it, realize that it can't find it, and boot from the Hard Drive.  Easy.
[/LIST]
+1 for a /home partition, by the way - at the very least, they make upgrading much easier since you don't have to copy your user files back onto your computer.

---

