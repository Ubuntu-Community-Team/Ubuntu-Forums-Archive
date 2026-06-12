---
title: "Ubuntu Installation"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by Nikhil Kenvetil on 2011-07-30
[COLOR=black][FONT=Verdana]This is my first Ubuntu/Non Windows installation.. So obviously, i have no clue wat am doin![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]i have an HP Pavilion laptop(model TX1004), with 4gig memory, 640 gig HDD, 1 GB ATI Radeon video card, running on an i5 proc..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]currrently it is on Windows 7 Ultimate, and i am assuming this shouldn’t matter.. but anyway..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]alright, so.. i downloaded the ubuntu v11.04 .iso file onto a FLASH DRIVE (2GB) from [[COLOR=#800080]http://www.ubuntu.com/download/ubuntu/download[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download"), by clicking the big orange button(changed it to 64 bit). It was around 690 MB[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]On my computer, an .iso file opens with winrar. so i extracted the files on the SAME pendrive that had the .iso file. it was NOT placed inside a folder or anything, but in the main page itself.. i dunno wat to call it though(root drive?)  ok.. lemme put it this way: the files were extracted to G:\, **[FONT=Verdana]and NOT G:\<Folder>, or anything[/FONT]**[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Ok.. while attempting to boot from the flash drive(by hitting F9 while POSTing), it said the disk had an error. i burnt .iso files onto a CD, using the default windows iso burner application[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]towards de end i encountered an error(i don't recall wat it was), but i am sure it happped AFTER it Verified the Disk[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]so this time i tried Booting fromthe CD, and it went thru.. it showed the UBUNTU insignia with some 5 dots below it trying to load something, but it didn't go beyond that. i tried this about 3 times but the same thing happened.. i know jus by reading this you'd say it is probably because it didn't burn correctly but if you have a diffent answer PLEASE HELP.. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]it would be great if you could also tell me if there is a seperate version of Ubuntu 11.04 for AMD procs and Intel procs..[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks in advance :)[/FONT][/COLOR]

---

### Post by Paqman on 2011-07-30
> **Nikhil Kenvetil said:**
> 
On my computer, an .iso file opens with winrar. so i extracted the files on the SAME pendrive that had the .iso file.

That's where you went wrong but don't worry, it's a reasonably common mistake. 

Go back to the download page and click on "Step 2 - Burn your CD or create a USB drive" click on the radio button for USB stick and click the "Show me how" button. It'll give you instructions for how to get turn the .ISO file into a bootable USB stick.

> it would be great if you could also tell me if there is a seperate version of Ubuntu 11.04 for AMD procs and Intel procs.

Nope. The 64-bit version is called amd64, but works exactly the same on Intel machines.

---

### Post by robgraves on 2011-07-30
i personally am a fan of unetbootin, and it can be downloaded for linux or windows here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

download unetbootin for windows in your case, then you have the option if you haven't downloaded an iso you can choose the distro and the usb stick and it will download and setup a bootable live linux for ubuntu for example
 
alternatively if you have already downloaded an iso, as it appears you have, you can click on the radio button for the iso, then browse and click on the iso from the location you have it stored, select the usb stick and then install a bootable linux.

---

### Post by Nikhil Kenvetil on 2011-07-30
thnx a ton bro.. will try dat n see if it works :D

---

### Post by robgraves on 2011-07-30
by the way i dunno if you're planning on setting up a dual boot system or just ubuntu, or just trying out ubuntu, but once you have installed it to the USB, you may have to go into your BIOS and if you have the option to set the boot order so that USB drive is ahead of the hard drive so that it will boot from the USB drive, then you can "test drive" ubuntu without making any changes to your computer.
      But if you have a typical windows installation and oly one hard drive, windows is probably occupying all of that, so if you intend to do an actual installation of ubuntu on your hard drive, you will need to shrink your windows partiton...pretty good tutorial here:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by Nikhil Kenvetil on 2011-07-30
Hello Rob.. thnx for posting!
 
i am planning not for a dual boot, but most likely triple boot..! planning to install Lion as well.. i have currently 6 partitions, around 100 gig each.. i dispise windows, n i have it **mostly** to run iTunes , n of course certain other applications like guitar pro(which i know runs on a mac as well) n some "PC based games".. i hate the monopoly of Microsoft!
 
i have reserved a partition each for ubuntu and Lion
 
pardon my ignorance, but i don't think i'd need to change the boot order from BIOS, as i can opt for the same by hitting F9 while POSTing/booting.. i might be wrong.. could you please clrify that?

---

### Post by Nikhil Kenvetil on 2011-07-30
> **robgraves said:**
> by the way i dunno if you're planning on setting up a dual boot system or just ubuntu, or just trying out ubuntu, but once you have installed it to the USB, you may have to go into your BIOS and if you have the option to set the boot order so that USB drive is ahead of the hard drive so that it will boot from the USB drive, then you can "test drive" ubuntu without making any changes to your computer.
      But if you have a typical windows installation and oly one hard drive, windows is probably occupying all of that, so if you intend to do an actual installation of ubuntu on your hard drive, you will need to shrink your windows partiton...pretty good tutorial here:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
Hello Rob.. thnx for posting!
i am planning not for a dual boot, but most likely triple boot..! planning to install Lion as well.. i have currently 6 partitions, around 100 gig each.. i dispise windows, n i have it **mostly** to run iTunes , n of course certain other applications like guitar pro(which i know runs on a mac as well) n some "PC based games".. i hate the monopoly of Microsoft!

i have reserved a partition each for ubuntu and Lion

pardon my ignorance, but i don't think i'd need to change the boot order from BIOS, as i can opt for the same by hitting F9 while POSTing/booting.. i might be wrong.. could you please clrify that?

---

### Post by robgraves on 2011-07-30
> **Nikhil Kenvetil said:**
> 
pardon my ignorance, but i don't think i'd need to change the boot order from BIOS, as i can opt for the same by hitting F9 while POSTing/booting.. i might be wrong.. could you please clrify that?

it may already be setup to boot from usb, i'm not exactly sure what your F9 in the boot process does, but if it boots from an external device, then cool, you're ready to rock, but if after setting up the usb with unetbootin or whatever, you reboot, and it just boots back into windows, then i would figure that something in your boot order in BIOS needs to be changed. are you using usb or CD? and have you tried creating a bootable USB/CD ubuntu live and rebooting yet?

---

### Post by Nikhil Kenvetil on 2011-07-30
> **robgraves said:**
> it may already be setup to boot from usb, i'm not exactly sure what your F9 in the boot process does, but if it boots from an external device, then cool, you're ready to rock, but if after setting up the usb with unetbootin or whatever, you reboot, and it just boots back into windows, then i would figure that something in your boot order in BIOS needs to be changed. are you using usb or CD? and have you tried creating a bootable USB/CD ubuntu live and rebooting yet?
yes sir. done dat. burnt de iso onto a CD, and extracted it to a flash drive.. either of dem don't seem to work(what exactly happens is mentioned in my initial query).. but like **paqman** suggested, i would try to download ubuntu again from [[COLOR=#800080]http://www.ubuntu.com/download/ubuntu/download[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download"), and go to step 2.. i was at atep one earlier.. so i'll have to hold ma horses until den.. but we'll see..

---

### Post by robgraves on 2011-07-30
> **Nikhil Kenvetil said:**
> yes sir. done dat. burnt de iso onto a CD, and extracted it to a flash drive.. either of dem don't seem to work(what exactly happens is mentioned in my initial query).. but like **paqman** suggested, i would try to download ubuntu again from [[COLOR=#800080]http://www.ubuntu.com/download/ubuntu/download[/COLOR]]("http://www.ubuntu.com/download/ubuntu/download"), and go to step 2.. i was at atep one earlier.. so i'll have to hold ma horses until den.. but we'll see..

you don't want to extract the iso, you either want to burn it to a CD using an option to either burn an iso or burn image, or using some program like unetbootin or pendrivelinux to use the iso to create a bootable USB

---

### Post by Nikhil Kenvetil on 2011-07-30
yup... i did burn it onto a CD.. BUT, encountered an error.. i don't quite recall what it was.. but i am positive that it was AFTER the disk was verified.. i recently upgraded to Windows 7 Ultimate.. whn i clicked on the iso file(i think it was called amd64 or something) i had an option to either extract to a location, or burn it onto a CD using the default windows iso burned.. i am sorry i dunno what the optioned was called.. it burnt to the CD fine, but i think while verification, there was an error..
 
though there was an error, it was booting from it.. it had the Ubuntu insignia, with 5 dots under it.. but that was it.. there was no progress after that..
 
hope this helps.. o_O

---

### Post by sadaruwan12 on 2011-07-30
Ok, First of all welcome to Ubuntu and to the community.

My dear friend it seems like that you're trying to run the installation processes from a USB but what you're doing if wrong and don't extract the files from the original ISO 'cos that'll break every thing.

Please, Install a CD/DVD burning program and that'll associate with your ISO winrar has been assigned to that task so normally winrar looks at the file as an archive so don't use that use Nero or something which are specialized for burning CD/DVD's.

And if you want to create a boot able USB use [UNETbootin]("http://unetbootin.sourceforge.net/") it's pretty easy and it has a windows version as well as linux versions. Use that program to create a boot able USB other wise it want work.

Also [read this]("http://www.nyutech.com/2009/03/easy-guide-to-getting-started-with.html") before you venture in to installing Ubuntu 'cos you're venturing in to a un-know territory so be prepared. It's a very easy guide to show windows converts how to do it properly.

Please, For your own good read before leap.

---

### Post by sadaruwan12 on 2011-07-30
> **Nikhil Kenvetil said:**
> yup... i did burn it onto a CD.. BUT, encountered an error.. i don't quite recall what it was.. but i am positive that it was AFTER the disk was verified.. i recently upgraded to Windows 7 Ultimate.. whn i clicked on the iso file(i think it was called amd64 or something) i had an option to either extract to a location, or burn it onto a CD using the default windows iso burned.. i am sorry i dunno what the optioned was called.. it burnt to the CD fine, but i think while verification, there was an error..
 
though there was an error, it was booting from it.. it had the Ubuntu insignia, with 5 dots under it.. but that was it.. there was no progress after that..
 
hope this helps.. o_O

OK, Please don't use the default CD burning utility that comes with windows it breaks some ISO file's [Use this]("http://www.imgburn.com/") it's free you don't have to pay try and please don't extract the ISO using winrar.

---

### Post by Nikhil Kenvetil on 2011-07-30
> **sadaruwan12 said:**
> OK, Please don't use the default CD burning utility that comes with windows it breaks some ISO file's [Use this]("http://www.imgburn.com/") it's free you don't have to pay try and please don't extract the ISO using winrar.
alright i will try to do that.. i found de application name to be titled "ImgBurn 2.5.5.0".. hope this is correct.. i am currently not at ma computer n i am doin this from ma work (der is not internet conenction at home).. if this works i will forever be grateful to all of you! :D

---

### Post by sadaruwan12 on 2011-07-30
> **Nikhil Kenvetil said:**
> alright i will try to do that.. i found de application name to be titled "ImgBurn 2.5.5.0".. hope this is correct.. i am currently not at ma computer n i am doin this from ma work (der is not internet conenction at home).. if this works i will forever be grateful to all of you! :D

My dear friend ok that is the software use this and burn a clean cd and try to boot from that please let us know what happened and if you're going to return later mark this as solved.

---

### Post by Nikhil Kenvetil on 2011-08-02
hello there.. i discarded windows and installed ubuntu 10.04 fresh.. i have a cd for 11.04 on me now.. is der a way i can upgrade it from this cd of 11.04?? if yes, how?

---

