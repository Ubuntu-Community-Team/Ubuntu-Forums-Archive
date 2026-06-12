---
title: "Uninstalling and reinstalling Ubuntu- Help please!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-21
Can someone please advise me on uninstalling and reinstalling Ubuntu? I have really ben patient  and hard working (I think ;) ) but don`t think I can fix whatever the HECK is wrong with Hardy Heron. First it took 3 weeks to get the sound working, and now I can`t play movies after clikckin on the `updates` icon and getting updates. For the last few days I`ve followed all the advice (lots of terminal commands and adding stuff) but movieplayer and vls just want to close. grrrrr!!  Is 8.10 ready, do y think? Anyway, I was considering starting over so I could have a dual OS with Windows (ONLY for the Photoshop, sorry I couldn`t get into Gimp lol). As a noob I thought I learned a lot, to install Hardy (the server edition, as I`m learning web serving and web design too)  but if someone can give me good advice I will do this (sigh) all over again.  I need 1)windows for PS 2) Ubuntu, maybe 8.10 to be a server, and my movies and music to play! lol Maybe it`s my drivers, but not sure how to check that.

---

### Post by jbrown96 on 2008-12-21
Here's what I would do:

1) backup all your files that you need
2) Boot the liveCD and setup your partitions. Get your swap, ubuntu, and Windows paritions set. Once you have written the partition changes, exit the installer. 
3) Reboot and install Windows.
4) Reboot and install Ubuntu.

It's will save you a lot of work to install Windows before Ubuntu. I think Intrepid is a good release, although I'm using Fedora 10 at the momment (Intrepid on my HTPC). If you are still having problems with sound, post output of ```
lspci
``` from a terminal. What applications are you using for music and video?

---

### Post by eagle416 on 2008-12-21
Intrepid Ibex (8.10) is released and stable, you could remove ubuntu and reinstall that.

Secondly, you shouldn't install the server edition if you're planning to play media (or have a GUI). It causes security risks and it doesn't run as smooth.

---

### Post by Captain_tux on 2008-12-21
You can't "uninstall" Ubuntu (or any operating system for that matter) as if it was an application.

Is Windows currently installed? If so, boot into a Live CD and use Gparted, QtParted, etc., to delete the Linux partition, and then expand the Windows partition. After doing that, use **fixmbr** to restore Windows' MBR.

Before any of that, however, were you able to watch movies before the updates? If so, is it safe to say you had the Medibuntu repositories installed??

---

### Post by jimmy the saint on 2008-12-21
Just a thought:  If all you need is photoshop, why not use a virtual machine rather than dual boot?  I use virtualbox to create a virtual machine which has XP installed and running photoshop just fine.  You won't be able to play intense 3d games but photoshop works just fine.  The nice thing is I don't have to reboot to run photoshop, I just open up virtualbox and start up the virtual machine!

---

### Post by Lakeside5 on 2008-12-21
Thanks everyone, I am `fellin the love` lol.  Jimmy I will definately check out the virtual box thing, sounds interesting. Maybe I am trying to do too much, on just one computer, but from reading ur posts, this is what I`m thinking of doing.  I know u can`t actually uninstall it Captain_Tux :) or I might have done it as that`s easier than..what I actually have to do :) TJo your questions: `Before any of that, however, were you able to watch movies before the updates? If so, is it safe to say you had the Medibuntu repositories installed??`Yes to both questions, and no I don`t currently have windows on here, I was trying to go cold turkey lol.  JBrown thanks for the advice, I will have to order the live CD (or download and burn it, if I can). I am (trying) to use movieplayer, vls, and thythmbox.  I want to have localhost for web development and also an online server, to host one or two websites, and I also need to view videos (tutorials) and music, and use Photoshop so...I will install Windows on one partition, then Intrepid plus a good web server for it (LAMP?). Do you all agree? thanks for all your help and the Best of the Season to you!

---

### Post by handydan918 on 2008-12-21
I'd recommend Hardy for server use. Just cuz an LTS release is less likely to get boned on updates.

---

### Post by lhb1142 on 2008-12-21
):P  You do not need a dual-booting machine just to run Adobe PhotoShop. This program works under Wine and, according to the WineHQ site, it works well under Hardy. I'm sure it would work just as well under Intrepid.

Here is my suggestion for you. You cannot "uninstall" an operating system but you CAN do this (and I myself have done it). Download < DBAN > ("Darik's Boot and Nuke") from SourceForge and create the DBAN disk. When used as instructed, this will completely "wipe" your computer's hard drive. The process takes several hours, depending upon the size of your computer's hard drive. You could have the process run over night and, when you awake the next morning, you will have a completely blank hard drive ready for whatever OS you wish to install.

Then install the Ubuntu version of your choice (Hardy or Intrepid). Once that is done and you have a) connected to the internet and b) downloaded and installed all of the updates, then go here:

< [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) >

Read all of this carefully and follow the instructions. You need only to "cut and paste" the terminal commands necessary taking care, of course, that you apply ONLY those commands that are relevant to your particular OS.

I suggest that in System->Administration->Software Sources->Third-Party Software you enable all of the "Universe" and "Multiverse" sources and install the "Medibuntu" as well as the "Launchpad" repositories. (You can "Google" for instructions to do this, if necessary.)

I have then found it helpful to go into the Synaptics Package Manager and < search > for "audio codecs," "video codecs," "win32," "w32," "winamp," "mp3," and whatever else you may think you may need. Go down all the lists of the programs you find under EACH of the listings (this will take a lot of time; you may wish to do this during a weekend) and install any that seem pertinent to you.

I also strongly recommend that you download and install RealPlayer 11 for Linux. You'll need it. You must go here:

< [http://www.real.com/linux](http://www.real.com/linux) >

to get this.

Keep in mind that the Synaptics Package Manager is a little "gold mine." You can even install Microsoft Truetype Fonts as well as myriad other programs. Just make sure that you are searching by "Description and Name" and enter any term of which you can think. You'll be amazed at the programs you'll find. (I really like "Stellarium" and "GoogleEarth.")

By the way, The GIMP is certainly not easy to master, requiring a fairly long learning curve, but the effort will be well-rewarded. Both my wife and I use it, on our respective Ubuntu computers, both of us having migrated away from PhotoShop. (Hardy comes with an older version of The GIMP. The latest version can be found here:

< [http://www.getdeb.net/](http://www.getdeb.net/) >

but you MUST make sure that you are looking for programs for your particular OS version and computer type [32 or 64]. I must warn you, however, that there are five [5] parts to installing latest version of The GIMP as well as the need for a terminal command [fortunately spelled out in the "error" message that appears] to be entered. The five parts are NOT entered in the order in which they appear; you will have to figure it out for yourself. But I have done it and the new version works just great. By the way, GetDeb is a great source for new versions of programs as well as some other useful programs which do not appear in the Synaptics Package Manager.) 

But, if you still wish to use PhotoShop, merely make sure that Wine is installed and then just install PhotoShop onto your Ubuntu machine.

It will work under Wine. I have always found that programs, having been tested and authenticate by WineHQ as working under Wine, work perfectly as indicated with Ubuntu Hardy. I should presume that will hold for Intrepid as well.

That should just about take care of everything you wish to do on your computer. Ubuntu is definitely not "plug and play" in the sense that some other products around you house are but the rewards are very much worth the effort. To wit, you can use a Mac or even Windows, but for every update in their OS, you must PAY - and pay, and pay, and pay. The same holds true for many, if not most, of the programs you have installed. (Look at the price of PhotoShop!) 

This is not the case with Ubuntu where everything is free. It may take a bit of effort to learn but at least money stays in your pocket and we can all use that! My wife and I have been using Ubuntu only since the end of May 2008 (we're both still "newbies") but neither of us will ever go back to Mac or Windows.

I hope the above is of some use and inspiration to you. In our opinion, Ubuntu Linux is as user-friendly as an Apple Mac and infinitely better in operation than ANY Microsoft Windows computer. Good luck to you. :)

---

### Post by Lakeside5 on 2008-12-21
I sure appreciate your long and thoughtful post ihb1142! I had tried to run photoshop with wine, and a few other things with wine, (even tried open office) but it did not work, but maybe it is just me :) I think I am going to print out (once I get the printer hooked up, hope it works on here lol) all your advice, plus the contents from the great links u gave me, plus some resources from others giving me advice, and then take the plunge! I had wanted the Hardy Heron ltd for a server as well, since it seemed to make sense, it included the server right in it but...I have found the opposite, that the updates are what did everything in, unless it was just a coincidence but everything seemed to be working before i clicked that update button..I think I will spend the Christmas season with my kids, while I await the Intrepid distro to arrive (ordering the cd) and try all this when they are back in school lol.  Merry Christmas everyone and thanks.

---

### Post by Captain_tux on 2008-12-21
Kudos to you for deciding to spend Christmas with the family instead of mucking around with the computer!

Can you download the .iso of Intrepid instead of waiting for the CD in the mail?

---

### Post by Lakeside5 on 2008-12-21
`Kudos to you for deciding to spend Christmas with the family instead of mucking around with the computer!` Ha Ha..I mean HO HO HO! Yes I probably could, but I haven`t burned a disc in a long time, and then only once or twice and I was not too good at it :) So where is the best place to dl the latest version (think I saw a post about not overloading the ubuntu servers too to dl it.). I have another problem I think, before I backup all my data so I can erase the hard drive and install Intrepid. My external hard drive which I bought new last year and is supposed to be 500GB, seems to read as only just over 100GB on here? Almost like Ubuntu can`t recognize it properly, or I am not reading it properly lol. But see, if if I dl and burn the ISO...it might be harder to keep away from the computer and take the kids out sledding (and any excuse for me, I hate winter when it`s cold like this, and baby it`s cooooold right now lol)

---

### Post by lhb1142 on 2008-12-22
:idea:  Okay, it's pretty obvious that you are VERY new to this, especially if you do not know how to burn an .iso disc.

May I respectfully suggest that you go here:

< [http://knowfree.net/2008/10/09/ubuntu-unleashed-2008-edition-covering-804-and-810.kf](http://knowfree.net/2008/10/09/ubuntu-unleashed-2008-edition-covering-804-and-810.kf) >

and scroll down the page until you see "Download Here" in blue letters. Then download this book.

(If the link does not work, merely Google this EXACT phrase [cut and paste it into the Google search box]: 

< Ubuntu Unleashed 2008 Edition: Covering 8.04 and 8.10 knowfree >

and the first result will be the one you want.)

It downloads as a .rar file (of only 12.5 MB) which must be extracted. If you do not know how to do this, perhaps you have an acquaintance who would be able to help you or, if you know any school children, maybe one of them could do it for you. Someone at your local library may be able to help.

If necessary, you could transfer the .rar file to a thumb drive and take it over to an acquaintance's house for extraction on his/her computer. Then the extracted book could be transferred back to your thumb drive and you could then place it onto your own computer.

Then --- READ the book! This will give you an excellent overview of Hardy as well as Intrepid. And by the time you have finished it, perhaps your Intrepid disc will have arrived (or you will indeed know how to download and burn a Ubuntu .iso disc and will have already done so).

I hope that you will be successful in this endeavor. I wish you and yours the best during this holiday season. ):P

---

### Post by Lakeside5 on 2008-12-22
Thanks, it looks like a great book (see, I can unrar and such lol. I can burn too, just don`t do it much or like it, but if it`s for a linux cd then..I guess I will ;But now I gotta shell out for blank discs, unless I try the usb way) ) You probably know how to tell if a computer is 64 or 32bit too? I`m assuming mine is 32bit form what I`ve been reading (it was built for me but was a normal cost, not extremely expensive like a 54bit). The advice I find is for people using Windows, but I know there is a terminal command for linux. I guess I  have a lot to keep me busy now, with the reading and installing and all- AFTER X-mas, promised the kids.  You have a great Christmas too ihb1142.

---

### Post by alzurzin on 2008-12-22
TO UNINSTAL UBUNTU AND REMOVE THE DUAL-BOOT OPTION

1. assume the Ubuntu was installed on a HD partition, eg D:
2. start Windows
3. format the D: drive
4. edit the "boot.ini" file to remove the line showing "ubuntu" (only this line!). save changes.
5. reboot. done.

for more info, go here:
[http://vlaurie.com/computers2/Articles/bootini.htm#edit](http://vlaurie.com/computers2/Articles/bootini.htm#edit)

good luck.

---

### Post by Lakeside5 on 2008-12-22
Hey Alzurzin :) This looks like an easy way to uninstall Ubuntu using Windows..only I don`t have windows on here, I wiped it out on purpose when I installed Hardy Heron last month. But thanks for the advice, and for the link (as it looks like another useful site I will have to check out), and a Merry Christmas to you too.

---

