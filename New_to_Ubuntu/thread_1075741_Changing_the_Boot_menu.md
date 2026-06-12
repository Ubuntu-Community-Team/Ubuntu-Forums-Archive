---
title: "Changing the Boot menu?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-20
I look this this file system in the edit folder for hours. AND I couldnt find a menu.list for which I can do a rm    and    cp  (the new menu.list) for the boot options for the script I made that can customize 8.04. BTW( If anyone wants it just ask and ill send it to them) but if someone could help me out It would be very appreciated.

---

### Post by hayden92 on 2009-02-20
Are you saying that you can't find menu.lst?

/boot/grub/menu.lst

I would try: gksu gedit /boot/grub/menu.lst

I hope that helps you out,

Hayden

---

### Post by Tek-E on 2009-02-20
lol. I havnt a clue as to what you are trying to ask help for :(

Please try and explain more clearly :)

---

### Post by hayden92 on 2009-02-20
If you can't find the file, it's because you are searching for "menu.list" when the file is actually called "menu.lst"

---

### Post by Tek-E on 2009-02-20
I beleive the whereis command could possibly find this.
try
```

whereis menu.lst

```

---

### Post by emshains on 2009-02-20
Just install qgrubeditor. You can do that by ```
sudo apt-get install qgrubeditor
```

---

### Post by Mercury_Alpha on 2009-02-20
Odd, whereis shows me several locations for menu.lst, none of which point to /boot/grub/

---

### Post by ericeclifford on 2009-02-20
Ok When you make the live cd. it makes a edit folder that has all your directorys of what makes up the live cd. I am trying to find the menu of the boot up that says   Start ubuntu. Or Install ubuntu or Check cd for defects or Memtest or boot from harddisk. I need to find the file for which I can change the list to just say start ubuntu or erase that list so it automatically starts ubuntu if that is possible to do.

---

### Post by ericeclifford on 2009-02-20
Btw there is no grub folder in the boot folder of the edit folder.
and No I need to make it so the script can do it by its self. even if that means coping the file and editing it in a text editor and then make it so the script can rm the old one and put mine in for each live cd creation.

---

### Post by Mercury_Alpha on 2009-02-20
Well, unless this is a CD-RW disc, there is no deleting of files. CD-R discs are read-only.

If you want to just use the Live CD as an operating system, you're going to want to install Ubuntu to a USB flash drive. However, many older computers will not boot from a flash drive.

The Live CD isn't really designed to work as a primary operating system. It's designed to let you test things out, or to fix problems with a pre-existing installation.

---

### Post by ericeclifford on 2009-02-20
lol I said I AM Customizing it ( ITS already on a harddrive.) I am rebuilding another live cd on this harddrive. But I do not want to have to do the command and open editors all the time so i wrote a script. My OS FOR which I am customizing it on is ubuntu 8.04 on a harddrive and I am trying to customize a live cd on this harddrive by using a script to do all the commands for me.

---

### Post by kaivalagi on 2009-02-20
> **Mercury_Alpha said:**
> Odd, whereis shows me several locations for menu.lst, none of which point to /boot/grub/

That's because whereis is not for that type of thing, running "man whereis" I see:

```
whereis  -  locate the binary, source, and manual page files for a command
```

Better off using "locate" instead, so run:

```
locate menu.lst
```

locate uses a db file for searches, so now and again it's good to update it. to update the db you run:

```
sudo updatedb

```

Hope that explains a few things for you :)

---

### Post by ericeclifford on 2009-02-20
If I remove grub from my cd what would happen will it just automatically start ubuntu.

---

### Post by kaivalagi on 2009-02-20
> **ericeclifford said:**
> If I remove grub from my cd what would happen will it just automatically start ubuntu.

nope...I have just extracted the iso contents and having a look for what you're after....I dont think it will be as easy as you might have thought. I suspect the grub files along with most other things are in packages and get unpacked on boot...I could be wrong though

---

### Post by ericeclifford on 2009-02-20
I see but there must be some kind of script I can just edit. or something along those lines. I did do a search for the grub folder for my extracted iso image folder (Edit) and found that there is a few grub folders. But I dont see any menu listings that say the titles of what actually gets listed after you make and run the live cd.

---

### Post by kaivalagi on 2009-02-20
Right, here's a hunch.

First off, grub is not used with the installation discs, isolinux is. If you extract the iso contents and go into the isolinux folder you will find a whole range of files. There is one file I think you will be interested.

I assume (I haven't tried so don't know) that if you edit the isolinux.cfg/menu.cfg file you can change the options available on boot.

I found this site on isolinux details (there are probably many more websites with help):

[http://members.chello.at/bobby100/ILpart1.htm](http://members.chello.at/bobby100/ILpart1.htm)

Let us know how you get on. I can imagine removing all but the live boot option from a live cd is useful when you want a totally readonly system which retains no settings :)

Hope that helps

[COLOR="Navy"]edit: text.cfg in the same folder looks interesting...see this bit of text in there :)

```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
```[/COLOR]

---

### Post by ericeclifford on 2009-02-20
nice that look like it will do it what I did was copy it and erased the 4 options I didnt want and copied that and wrote in my script to do a rm and cp command and I am making the cd now from sript will let u know. Thank you.

---

### Post by kaivalagi on 2009-02-20
If I were you I would edit the iso using something like isomaster (in the repos) then run the new iso in a VM....saves on disks

I am now playing with the isolinux menus too, got it doing what you want ;)

It works, although it would be nice just to get it booting straight away...I think it is just a case of understanding isolinux properly

---

### Post by ericeclifford on 2009-02-20
true but I also want to see if this code will work as well
so I am running the whole script. If you want a version of it I will send it to you. It has detail descriptions on what to do and what you need to do to customize a lot of the customize cd from just using the script so you dont have to repeat the process a million times. Nice man. thats lovely I appreciate it again.

---

### Post by kaivalagi on 2009-02-20
Sounds interesting what you are doing

I meant to start having a play with remastersys...have you looked at that for creating a custom os...are you using that as well as creating customize scripts?

I am not sure I fully understand what you are trying to achieve

edit: are you trying to get a script organised to modify any future iso image from ubuntu, so when 9.10 is out for example you can quickly run something which creates your own version?

---

### Post by ericeclifford on 2009-02-20
Well it can be modified for all version of ubuntu its just a script that does the whole process of commands and stuff to customize a ubuntu live cd. It also puts in java,flash and all that crap for you and can customize the background and now change the boot menu and pretty soon the rest of the stuff and it does it all from this script(not a program just a script) but you need to edit the files for some of them like isolinux.cfg and the wallpapers.xml files to your own liking and then the script will tell u what to do with it. and it will then create it.

---

### Post by kaivalagi on 2009-02-20
Nice

Post back some details when you've made some progress, I wouldn't mind having a play with it.

If I can spare enough time I'll do a bit of testing here and there if that will help

---

### Post by ericeclifford on 2009-02-20
Much obliged I am testing it as we speak it takes awhile cause I added lots of sources removed lots of crap and added lots of programs so it takes a while to use but atleast you dont have to retype everything.

---

