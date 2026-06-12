---
title: "Easiest way to Dual Boot XP &amp; UNR for AAO-250?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by NiacinFlush on 2009-07-24
First of all, I apologize for this utterly newbish question, and I am sorry if this is one of the most asked questions. I'm just really confused as to what I should do.

Ok, so the website OSDisc sells USB drives with UNR on the USB-stick, so I may order that. Now once I receive that flash drive, do I:

Just plug it in, boot up the Aspire, then press F12 repeatedly, and whallah? Then follow the instructions?

What if I have that and want to permanently install it by partioning it on my hard drive? I would love to just boot up the computer and choose either UNR or XP on the black screen menu. 

Thanks for any help, I know I asked a lot of questions, but I am just looking for answers. :confused:

---

### Post by pbotros1234 on 2009-07-24
> **NiacinFlush said:**
> First of all, I apologize for this utterly newbish question, and I am sorry if this is one of the most asked questions. I'm just really confused as to what I should do.

Ok, so the website OSDisc sells USB drives with UNR on the USB-stick, so I may order that. Now once I receive that flash drive, do I:

Just plug it in, boot up the Aspire, then press F12 repeatedly, and whallah? Then follow the instructions?

What if I have that and want to permanently install it by partioning it on my hard drive? I would love to just boot up the computer and choose either UNR or XP on the black screen menu. 

Thanks for any help, I know I asked a lot of questions, but I am just looking for answers. :confused:

First off, its always good to ask questions. After all, how else would we learn? :) Questions are always welcome here.

And if I might suggest, there's no need to order a pre-done USB off the internet. Do it yourself! (as long as you have a USB stick that has nothing important or non-backupped on it).

Just follow this guide [HERE]("https://wiki.ubuntu.com/UNR/Installation/Easy"). Feel free to ask more questions. :)

And the whole part about pressing F12 repeatedly, that is to boot off the USB thumb drive. You'll press F12, and then a menu will pop up (your BIOS menu). It's different for every computer, but generally there will be an option or tab that will let you put your USB drive on a higher boot priority than your hard drive.

This way, your USB will boot, and UNR linux will start right up.

If you want to install to your netbook's hard drive, just start up the UNR linux and there will be a walkthrough installer on the desktop. Grub (a boot manager) will install, and you'll get that nice, two-option screen. :)

---

### Post by snakeman21 on 2009-07-25
During the installation process, you can choose to use your entire hard disk, or tell it to use only a portion.  This leaves your other operating system untouched, and when you boot, you can choose which OS to use.

---

### Post by NiacinFlush on 2009-07-25
Thank you for your post. 

I looked at the website you posted, but it seems confusing on some parts.

I do not have a USB drive at all, so if I order that from the website, do I basically not have to do anything the website entails?

I just plug in the USB, push F2 or F12, install it, and then Grub will somehow already be on there?

EDIT: My AAO-250 is a 32bit system, correct?

---

### Post by LewRockwell on 2009-07-25
this was my experience with an Acer Aspire One:

(note that I was responding to an Asus owner with Mint wireless issues - [http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious](http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious))


> **LewRockwell said:**
> I had an eerily similar experience with my Acer Aspire One AOA-150-1864 (seems many of the internals are the same as your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom). I picked the netbook up used "on the cheap" and at first I thought I had been sold a piece of crap. It came with Windows XP Pro SP3 and the damn thing gave me fits connecting to my home wireless(Motorola Surfboard SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed around with that netbook for several hours resetting this and that and rebooting numerous times. Then I went into the router settings and started banging around there also. The one thing I did that might have cracked the nut was I switched from G-only to mixed(but after it started connecting I switched it back and it's still connected flawlessly).

After getting the wireless working and installing my favorite stuff on windoze(and using them to clean, spruce-up, and defrag windoze) I then set about partitioning the 120GB hard drive using a LiveCD of Puppy Linux(Gparted) via an internal cd-rom drive I had laying around and one of these gadgets which, I must say, no tech or hobbyist should be without([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)).

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

After the partitioning ritual(reducing the windoze partition in several smaller steps with the obligatory reboot into windoze between each reduction so checkdisk could do it's thing and so I could defrag with each reduction) I installed Puppy Linux and was pleased that it worked very well from the get-go(Puppy installation slipped the Grub bootloader in place also). Then it was off to the races to install Ubuntu 9.04 Jaunty Jackalope (full version) which also went without any problems at all. It took a minimal amount of time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it looking "just right" and a couple of reboots into each system, but I must say that I am pleased with the performance and overall experience. I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it bothers my eyes more quickly than the bigger screens. I plugged it's VGA output into a nice 17 inch monitor I have on the tech bench and it looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a wireless keyboard and mouse assisting, it being a reasonably energy-efficient alternative to the regular desktop monsters consuming hundreds of watts unnecessarily.

.

of course, my regular LiveCD of full version Jaunty had been used successfully several times previously so I knew I had a good burn

I think you should just install the full version and not the UNR

.

---

### Post by NiacinFlush on 2009-07-26
What are the differences between Jaunty Jack and UNR?

---

### Post by brucesmith on 2009-08-10
pbotros1234...are you saying in your last sentence that UNR install includes that slider thingy like regular Ubuntu that makes is possible to set up UNR in dual boot? I did that with Hardy on my desktop and it worked fine, but everything I've read says UNR install does not include that utility and I would have to use something called "gparted" to accomplish partitioning for dual boot. I am new and unsure and I've totally avoided clicking the "install" option and instead run "live" from a thumb drive on my Acer AOA150 becasue I'm afraid I'll trash the hard drive...I have to keep XP on my Acer for my work, so taking over the entire drive is NOT an option for me.

---

