---
title: "help i have a problem!!!!"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-01-14
right where do we start...
i have windows vista and sick of it tbh and wud like 2 use linux ubuntu. my mate yesterday gave me a cd with it but something was wrong with it coz theyre were some scratches and it would say I/O boot error (reboot) when i tryed to f12 boot it.
so i didnt have any blank cds left so i gave him my 1 gig usb drive so he can copy the program he downloaded on to it and gave it back to me this morning, which has the 690 odd mb program on it, i try to copy it to the cd but it wont work saying its a squashfs problem try again, also i have downloaded infra recorder trying to burn the big app onto my cd but no luck so far because i cant find a iso file??? and i am getting a headache now and thinking of scrapping linux altogether,
please help!! 
thanks
and also i bought some blanc cds so waiting for instructions and help from u guys!!

---

### Post by Dougie187 on 2010-01-14
Why don't you just download the ISO? It's available on ubuntu.com.

What files are on the USB drive that your friend gave to you?

---

### Post by blazemore on 2010-01-14
You need to burn the disk image to a CD, and make sure you don't just burn the .iso file itsself to a CD.

For more information, read the [documentation]("https://help.ubuntu.com/community/BurningIsoHowto#Windows").

---

### Post by Lord Stig on 2010-01-14
The file you have isn't an app itself, it's an image to create a bootable CD for you. It's got all the Linux goodness wrapped up in itself and sounds like when it went onto the USB drive it unpacked itself. The squash-fs reference I believe is to do with that drive already having been made bootable and been used during a boot (others can correct me). Have you tried booting straight off the USB drive? 

What I think you need is to download the .iso file again from the wesbite - .iso at the end of the filename indicates an image file.
Most burning programs will allow you to burn an image to CD - this is what you need to do. You must select the 'burn image' option otherwise the burning software won't make the CD bootable and all you'll have is a useful but unbootable backup of Ubuntu. You could consider burning the CD at a low speed to reduce the risk of any errors during the burn process.

Hope I have the right end of the stick and this is helpful.

---

### Post by vnpifhf on 2010-01-14
lol, i have a cd with everything ready but it is scratched!!!

hes when i click on it it works and it boots bit it tells me theres an i/o error when i boot it presumably because it is scrached,

so what my friend has done is copied the download file from ubuntu.com and put it directly on the usb

i am asking all the files are separate on the usb when u click on it (not in 1 wubi application) and i cant paste it onto cd because of squash thing!
i do not understand!!

lemme paste sum pics below
also i cant download it again because i have a 3 usb modem and i have a download cap of 1 gig and it is way too big for me to download so i ask a mate for a favour)
also i have tried to boot it off a usb but the system dont recognise it

[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/pic1.jpg[/IMG]


[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/pic2.jpg[/IMG]

[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/pic3.jpg[/IMG]

please help as i cant download anything again!!!

---

### Post by tom.swartz07 on 2010-01-14
okay. 

First off. Dont install using WUBI. theres a problem with the current version, and its been making many peoples computers unstable.


Ask your friend, one more time, to burn the .iso. You need to follow this step-by-step: 
[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)
Heres another guide that was mentioned.
[https://help.ubuntu.com/community/BurningIsoHowto#Windows](https://help.ubuntu.com/community/BurningIsoHowto#Windows)

Burn it at a slow speed- it will reduce errors. Before you leave, ask your friend to boot to it and select 'check cd for errors'. It only takes about 3-5 minutes, but it will save you headaches in the future.


Once you have a fresh install cd, scratch free, put it in and boot to it.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Honestly, Installing another operating system takes time and patience. Give yourself about 1 hour, maybe an hour and a half to just take a break and install it.


I would suggest, in your case, when you get to the partition page of the install, select 'install side by side' this allows you to still keep windows, just in case you dont like it.



Hope this helps!
Heres an amazing guide that will walk you through installing it. It has lots of pictures so you could follow along.

---

### Post by charlier653 on 2010-01-14
will your computer allow you to boot from the USB?

If you can, try that.

---

### Post by oldos2er on 2010-01-14
You can order a free CD from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by vnpifhf on 2010-01-14
u dont get it i cant because i cant see him for another month!!!

just tell me how to pack those unpacked files back to an iso file!!!



i think he didnt paste the iso file but pasted it unpacked and i need to stick it all together to paste it on the cd!!
please stop me from giving up and gimme another chance at this ubuntu

many thanks!!!

---

### Post by pricetech on 2010-01-14
Before you install Ubuntu in a dual boot;

Turn off system restore.  (you'll turn it back on after you're done.
Clean up temporary files.  (I like ccleaner for this, available from ccleaner.com)
Defrag your hard drive.

The first time you boot into winders after installing Ubuntu, it will want to run a checkdisk.  Let it.

Welcome to Ubuntu

---

### Post by tom.swartz07 on 2010-01-14
> **jahangir99 said:**
> u dont get it i cant because i cant see him for another month!!!

just tell me how to pack those unpacked files back to an iso file!!!



i think he didnt paste the iso file but pasted it unpacked and i need to stick it all together to paste it on the cd!!
please stop me from giving up and gimme another chance at this ubuntu

many thanks!!!

im sorry- i didnt catch the part where you cant see him.

unfortunately, As of right now, you dont have anything thats usable. you have all of the files, but theyre unpacked and unbootable. when your friend copied the .iso to the usb drive, the files were unpacked to a bad boot image.

the only way you could get ubuntu, right now, is to download the .iso and re-make the bootable usb.


ive had a lot of experience making bootable USB's for my friends, and i know that there are many chances for the files to just 'not work'. 

Like I said before, a little patience with this goes a long way. If you rush into it with bad files, you could potentially end up with a broken computer. I would much rather see you wait a bit and get a perfect install. 


You could order a cd from the Ubuntu website. They will ship it to you for free. If you cannot, for any reason, download the .iso  and burn it to a cd yourself, I would recommend doing it that way. The official cd from Ubuntu is almost guaranteed to work, with no scratches :D


Good luck.

---

### Post by vnpifhf on 2010-01-14
what are u talking about!! i cant do anything until i get all the unpacked files back into the iso packed file to burn onto me cd

please thats all im asking unless youve got something else i can try, read all my posts above so u understand what situation i am in.

i am starting to believe that i should have never changed from windows because i am finding this too much hassle :(

---

### Post by ymra on 2010-01-14
What you have is a bootable usb flash drive.  Leave the drive plugged in and reboot your computer.  You don't need to burn a cd.

---

### Post by tom.swartz07 on 2010-01-14
> **jahangir99 said:**
> what are u talking about!! i cant do anything until i get all the unpacked files back into the iso packed file to burn onto me cd

please thats all im asking unless youve got something else i can try, read all my posts above so u understand what situation i am in.

i am starting to believe that i should have never changed from windows because i am finding this too much hassle :(

Im sorry, but you really cannot easily repack those files into a .iso file. Once theyre unpacked and written to your usb key, thats how they are. There are some methods, but they are rather technical and much beyond the grasp of someone who just started using Ubuntu; even I have trouble with it, and Ive been using Ubuntu for over 2 years.

In order to help you, we need information about what you have done. You never specified if you actually installed Ubuntu on your computer, you just said that you could not boot to your discs. 

If you DID install Ubuntu on your system, and it is now unstable, we need to know that, along with any error messages you receive. 


My honest opinion is, if your Vista install is still working. Wait. Order a cd from the Ubuntu website and install it when it arrives. If you try now using the corrupt files, you will only end up breaking your system, and you wont have a computer at all.

HOWEVER, If your computer is not usable, let us know, and I will try to get it back to a working state for you.





Honestly, Ubuntu is not a hassle if you follow the instructions. Im not trying to insult or condemn you, but simply following the directions on the website makes it very easy. You simply need to take your time and focus. Quite frankly, I would suggest you read about Ubuntu before you jump right in, as it may not be right for you at this current time. 
Here are some informational guides for you to read before you jump: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[www.ubuntupocketguide.com/](www.ubuntupocketguide.com/)


Either way, let us know what state your computer is in so we could continue

---

### Post by tom.swartz07 on 2010-01-14
> **ymra said:**
> What you have is a bootable usb flash drive.  Leave the drive plugged in and reboot your computer.  You don't need to burn a cd.

He had previously mentioned that his bootable USB was corrupt. Unless something went wrong the first time to give him the error, I dont think its a valid install, and he might end up with a corrupt Ubuntu install.

---

### Post by J V on 2010-01-14
Edit: Scratch that

---

### Post by vnpifhf on 2010-01-14
i have used ubuntu a year ago and deleted it as i could not access the internet, that was a different story,,,

i have a win vista 1.5gigs ramm home edition 160 gh hdd

lol please i have a lot of open files

just tell me how to make it wubi again and pack it
PLEASE

and please dont try insulting me again or i will unsult you back ;)

---

### Post by tom.swartz07 on 2010-01-14
> **jahangir99 said:**
> i have used ubuntu a year ago and deleted it as i could not access the internet, that was a different story,,,

i have a win vista 1.5gigs ramm home edition 160 gh hdd

lol please i have a lot of open files

just tell me how to make it wubi again and pack it
PLEASE

and please dont try insulting me again or i will unsult you back ;)

You still didnt answer the question. Can you boot to vista?




I understand your want to keep your data. Thats just as important to me- Im replacing my entire HDD because its on its way out.

**You cant 're-pack' WUBI files.** Its one continuous file that installs within Windows. _Currently, the WUBI version that is out has lots of errors._ In the past 2 days Ive seen almost 13 counts of broken WUBI installations, so I cannot recommend it for you.

Im sorry if you were insulted, I by no means meant to insult you or your skills. Because this is an 'Absolute Beginners Forum', the posters here aim for the easiest and most simple ways to explain things, and much more difficult tasks are relegated to the appropriate sub-forums.

---

### Post by vnpifhf on 2010-01-14
i am an IT technichan in real life, im just not used to dealing with ubuntu.

i have dealt with sun micro operating systems, microsoft, apple and dos commands and i have only heard of this 'ubuntu' recently, i have had experience with other aspects of linux bot NOT this one.

i can handle it!

just tell me how to pack the wubi files!

---

### Post by J V on 2010-01-14
no-one half competent enough to use ubuntu would paste an iso unpacked on a disk, its obviously been installed with unetbootin, if it won't work, then tough luck, you need to download a new ISO...

---

### Post by tom.swartz07 on 2010-01-14
> **J V said:**
> no-one half competent enough to use ubuntu would paste an iso unpacked on a disk, its obviously been installed with unetbootin, if it won't work, then tough luck, you need to download a new ISO...

Thanks JV. Thats what Im trying to get across.

You have a bad file on the USB and cant use it. You cant re-pack the file in any way. The only viable option is to re-download the .iso, install it on the USB key again, and try once more.

Since you are an IT technician, you probably understand the importance of file continuity. When you download a file, theres a chance the file misses some bytes and loses continuity. Same thing when you write it to your USB key.

I would suggest checking your md5sums for the files when you download them and burn them.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hope this helps.

---

### Post by ymra on 2010-01-14
> **tom.swartz07 said:**
> He had previously mentioned that his bootable USB was corrupt. Unless something went wrong the first time to give him the error, I dont think its a valid install, and he might end up with a corrupt Ubuntu install.


No he did not.  The dvd that he has is scratched.  From what I am reading he has not even tried booting off of the flash drive.  He is compleately focused on making an unnessiary cd.  He has a bootable flash drive just look at his screen shots.

---

### Post by tom.swartz07 on 2010-01-14
> **jahangir99 said:**
> lol, i have a cd with everything ready but it is scratched!!!

hes when i click on it it works and it boots bit it tells me theres an i/o error when i boot it presumably because it is scrached,

so what my friend has done is copied the download file from ubuntu.com and put it directly on the usb

i am asking all the files are separate on the usb when u click on it (not in 1 wubi application) and i cant paste it onto cd because of squash thing!
i do not understand!!

lemme paste sum pics below
also i cant download it again because i have a 3 usb modem and i have a download cap of 1 gig and it is way too big for me to download so i ask a mate for a favour)
[COLOR="Red"]***_also i have tried to boot it off a usb but the system dont recognise it_***[/COLOR]

[IMG]http://i892.photobucket.com/albums/ac121/jahangir99/pic3.jpg[/IMG]

please help as i cant download anything again!!!

> **ymra said:**
> No he did not.  The dvd that he has is scratched.  [COLOR="red"]From what I am reading he has not even tried booting off of the flash drive.[/COLOR]  He is compleately focused on making an unnessiary cd.  He has a bootable flash drive just look at his screen shots.

He says in this post that the WUBI file is not working. If the USB was created properly, the WUBI installer should work. Since it doesnt, that points to an improperly made USB installer file.


Im reaching the point of frustration here. 

Order a CD. Wait 1 week for it to be delivered free of charge in the mail. Install it without worrying that you have a corrupt install.

Because you have a download cap of 1 gig, do not waste your data on another download, even to download WUBI again (WHICH I REITERATE, HAS SEVERE PROGRAMMING BUGS).


I appreciate the willingness to help, but Im sure that the OP, as well as I, do not appreciate information that is not useful or relates to already hard established facts.

Im not here to argue. This is the Beginners forum. I am here to help, and guide new users in their quest to get a handle on Ubuntu.

---

### Post by slushee on 2010-01-15
jahangir99, if you haven't scrapped ubuntu just yet and you do decide to come back to this forum, just know that patience will go a long way here. i'm sure we've all had our share of computer difficulties and the best thing to do is take a breath and step back for a moment. i've lost a lot of files because i was hellbent on punching bill gates in the face. slow down, listen to the advice with an open ear, and co-operate the best you can.

as has been explained, you're current copy of ubuntu will not work; trying to install that file currently on your usb will only add to your frustration. follow tom's advice in this thread, all of it. forget the wubi install and order the legit disc directly from ubuntu, free of charge. i downloaded the .iso from the ubuntu website and i can tell--with a very fresh memory--that the install process from a legitimate copy is incredibly easy. don't give up. it's not ubuntu that's the problem here, it's the medium you're trying to install it with; you're current copies won't work, get one that does.

---

### Post by lisati on 2010-01-15
+1 for two suggestions already made:
The CD the OP has is scratched and the USB stick seems to be unusable.
[LIST=1]
[*]order a free CD from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) -or-
[*]Download from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and burn it to disk yourself (see [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto))
[/LIST]

---

### Post by Tyke91 on 2010-01-15
> **jahangir99 said:**
> u dont get it i cant because i cant see him for another month!!!

just tell me how to pack those unpacked files back to an iso file!!!



i think he didnt paste the iso file but pasted it unpacked and i need to stick it all together to paste it on the cd!!
please stop me from giving up and gimme another chance at this ubuntu

many thanks!!!


if you don't have any CDs and only have that USB drive, then follow these instructions (delete EVERYTHING on the usb drive)


[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


Basically what you will have to do is (assuming you have no CDs)


[LIST]
[*]download an ubuntu ISO file (torrent if possible, to be friendly :P)

[*]mount the ISO with daemon tools

[*]put the clear USB drive in the comp and run usb-creator.exe from the ubuntu ISO that you mounted

[*]????
[*]profit!
[/LIST]

you can get daemontools lite from [here](http://www.disk-tools.com/download/daemon), it's a very handy program that basically does the linux command "mount"


BTW: the disc image should only be a 700 mb download, well within your cap.

PS: Ubuntu is a somewhat internet intensive linux distro... you're going to want to go over your cap :^P

---

### Post by SushiR on 2010-01-15
> **jahangir99 said:**
> i am an IT technichan in real life, im just not used to dealing with ubuntu.

i have dealt with sun micro operating systems, microsoft, apple and dos commands and i have only heard of this 'ubuntu' recently, i have had experience with other aspects of linux bot NOT this one.

i can handle it!

just tell me how to pack the wubi files!

If your an IT man - which I doubt - than you're pretty capable to head over to ubuntu.com, read the instructions how to download and create a bootable cd or a bootable usb pen. And I guess you can understand that the files you have got are, well, worthless. Sorry to sound harsh, but I think you're trying to fool around.

---

### Post by dzon65 on 2010-01-15
> **sushir said:**
> if your an it man - which i doubt - than you're pretty capable to head over to ubuntu.com, read the instructions how to download and create a bootable cd or a bootable usb pen. And i guess you can understand that the files you have got are, well, worthless. Sorry to sound harsh, but i think you're trying to fool around.

+1

---

### Post by mlentink on 2010-01-15
If I may, I would also want to respectfully ask you not to use text-lingo. Please consider that many, if not most, participants in this forum are non-native speakers and could have trouble following your post and thus not be able to help you.

Apart form this forum, which you will come to appreciate, Ubuntu has excellent support pages on its website. You will find that if you follow the directions on [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) you will be able to install Ubuntu easily. If you run into problems following the directions there, please report back and try to be as specific as possible, not only in your post itself, but also with its title. This will help those with better knowledge of your problem to identify it more quickly.

---

### Post by mlentink on 2010-01-15
Wups! Sorry, error

---

### Post by vnpifhf on 2010-01-15
i have followed toms advice and someother people and managed to pack all the ubuntu files altogether :)

i can assure you i am an it technichan for a small school.

i am an expert with other operating systems i.e mac/windows

i have now got the prob fixed and i am finding ubuntu very very good presuming that it is free software!

sorry if i have frustrated you :/

thanks

you may close

---

### Post by mk1w86 on 2010-01-15
> i have now got the prob fixed and i am finding ubuntu very very good presuming that it is free software!


Yes, Ubuntu is mostly free software apart from various 'binary blobs' in the kernel required to make certain pieces of hardware work.

> you may close


See my signature, you do not close the thread but mark it as solved. :)

---

