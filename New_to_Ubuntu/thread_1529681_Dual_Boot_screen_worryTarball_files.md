---
title: "Dual Boot screen worry/Tarball files"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Nephyron on 2010-07-12
Hey :D

I'm a new user to Linux, and installed Ubuntu 10.04 a few days ago, dual-booted with vista. I have a minor worry, that on the dual boot screen on startup, there are TWO linux and linux [recovery] choices? in addition, to get into windows i must select windows RECOVERY environment? is this normal? it works fine, im just a bit paranoid that something has gone wrong :P

Also, instead of clogging up the forum with two topics, how are .tar.gz files installed? i found a link on here to a (monkeyblog?) page but it came up with a list of google ads, so i presume that it is an old link. If possible an explanation (or link to one) in layman's terms would be great!

I have heard lovely things about the ubuntu community, so please help, and maybe this OS will cease to confuse me :P

thanks a lot,
Nephyron

---

### Post by Mr. Hibba on 2010-07-12
Hmm, sorry, I don't know about the first question. 

As for the second question, could you be a little more specific, please? What file did you download?


Welcome to the Ubuntu forums! :-). 

Mr. Hibba.

---

### Post by SlidingHorn on 2010-07-12
Regarding your first question, I think your Windows installation should be accesible without booting into recovery mode.  I'm not very experienced with GRUB (the os menu that opens on boot), so I can't really help when it comes to fixing that.  I can point you to this article, however, which may be helpful: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

When it comes to .tar.gz files - you don't actually install them, per se.  .tar.* files are actually archives (akin to .zip files in Windows) and need to be extracted.  See here for more details: [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

If you're looking to install an application that comes within an archive, you will usually find a README file within that will explain how to proceed with the actual installation after extraction (usually by navigating to the directory in your terminal and using the following commands)

```
./configure
```

```
sudo make
```

```
sudo make install
```

Hope this is helpful :)

---

### Post by oldfred on 2010-07-12
As you update system it will install new kernels. You list will continue to grow. We recommend you keep at least two kernels so if the new one has issues you can choose to boot a known working one. You can go into synaptic  and uninstall old kernels if you want to houseclean.

We have found the the osprober or windows mis-identify partitions. If you want the correct description for now you have to customize menu. 

If at all possible and espeically for a new user you should install applications from synaptic or the Ubuntu Software Center. Those applications are tested and will work. Just about anything you want is already availabe. If you have to install from other downloads you should use a .deb as that is configured for DEBian which Ubuntu is based on.

---

### Post by Nephyron on 2010-07-12
thanks guys, all helped - oldfred, by customize menu do you just mean rename the boot option or actually re-identify the partition? sorry for probably basic question!

thanks again :)

---

### Post by audiomick on 2010-07-12
> **Nephyron said:**
> thanks guys, all helped - oldfred, [COLOR=Red]by customize menu do you just mean rename the boot option[/COLOR] or actually re-identify the partition? sorry for probably basic question!

thanks again :)
I am pretty sure it is just a matter of changing the name. If booting from that entry gets you into your normal windows, then that is what it will be.

---

### Post by Nephyron on 2010-07-12
oh good - set my mind at ease! but erm... how do i do that? i pressed 'e' while over the windows option in GRUB, but it came up with some stuff i don't recognise, so i left it alone! what do i use to rename it?

---

### Post by Paqman on 2010-07-12
> **Nephyron said:**
> how are .tar.gz files installed?

In general: they aren't.

Tar.gz is just a compressed archive, it could contain anything, including software. On a system with a built in package manager (like Ubuntu) you want to get your software from Ubuntu's repositories. Open up Ubuntu Software Centre and have a look. There's also Synaptic, which shows a lot more in depth than Software Centre.

For anything that's not available in the repos, you want to install using a .deb file, which is a bit like a Windows .exe. Another option is Personal Package Archives (PPAs) which are basically private repos.

Installing software from .tar.gz is a pain to do, is a security risk because the app doesn't receive security updates, and can cause your system to become unstable if you use it to replace software that is available in a repo.

---

### Post by Nephyron on 2010-07-12
A quick google told me that to rename a boot entry, i need to edit the menu.lst file... however, i don't seem to have one in the boot/grub folder? should i be looking for a different file?

---

### Post by oldfred on 2010-07-12
This was how I customized my system to only show two entries and let me totaly customize windows & my other entries.

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php...54&postcount=1](http://ubuntuforums.org/showpost.php...54&postcount=1)

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true

When all done run:
sudo update-grub

---

### Post by Nephyron on 2010-07-12
I found grub.cfg, and inside was:

menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod ntfs
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set 284a1e244a1def76
	drivemap -s (hd0) ${root}
	chainloader +1

do I copy all of that into the 40_custom thing, after where is says 'insert after comment' - all seems common sense but you link sent me nowhere and i didnt want to end up with just a duplicate entry ;)

---

### Post by oldfred on 2010-07-12
Yes you want to copy the entire thing where it says & it will be a duplicate entry unless you also turn off the osprober. If you install new systems you can turn the osprober on for an update and reedit 40_custom.

If you want to see it as a duplicate entry and test that it works, run the update grub before turning off the osprober. You will have both entries and can test that the new one works.

Once copied into 40_custom you can change the title to anything you like.

---

### Post by Nephyron on 2010-07-13
I copied that stuff into custom 40, changed nothing but the title, saved but it still doesn't come up! i did the sudo update thing, and turned os prober off and on again (;) ) but nothing - the old entry is still there :(

---

### Post by oldfred on 2010-07-13
After any change you have to run
sudo update-grub

Did you scroll all the way down on the grub menu. If the box if full it only shows some but when you scroll down they appear.

---

### Post by Nephyron on 2010-07-13
i tried to scroll down, and also in the sudo-update screen in the terminal it did not show it either. Do i just save custom_40 with the info inside or do i need to 'run' it somehow after copying it in?

*EDIT* learning from my mistakes when crafting rainmeter skins, I decided to check the code one more time - an lo and behold, i had missed the final } off the end off the entry in Custom_40! Thanks for all your help, works perfectly now, and this concludes a long drawn out case of incompetence. 

Nephyron

*/EDIT*

---

