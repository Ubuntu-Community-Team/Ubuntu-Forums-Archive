---
title: "Live Usb persistence"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by 13k on 2010-05-12
Hello,

Do Live usb's(usbs used as Live Cds) in general, with/without persistence affect the life of the usb being used.
Please answer(seriously and honestly)  this is my first question.












-Must Live

---

### Post by ubunterooster on 2010-05-12
All read/write operations are detrimental to life. Drives last best never used at all. That said, it has no greater detriment then regular read/write operations. And welcome to      
     	[[IMG]http://ubuntuforums.org/images/misc/ubuntulogo.png[/IMG]]("http://ubuntuforums.org/index.php")

---

### Post by warfacegod on 2010-05-12
Yes, using a USB as a Live disc can seriously shorten the life of the USB. Depending on how often you use it in this fashion. Live environments tend to have allot of read/write operations which reduce the life span. In fact I have found that the manufacturer also has much to do with this. For instance, I have three PNY drives, of various sizes, that will no longer boot as a LiveUSB (they still work otherwise for data transfer). However, I have 2 4 GB Gigaware USB's and either one of them has seen more Live environments than all three of my PNY's and yet both still function perfectly for Live.

---

### Post by earthpigg on 2010-05-12
yup, a little bit. just how much is up for debate.

you should use an old/cheapo 2gb thumb drive for this, and use the expensive 16 or 32gb thumb drive for other things. if possible. if not, one or two or five ubuntu installs on a thumb drive isn't going to kill it.

---

### Post by ubunterooster on 2010-05-12
I failed to mention that while a Live read/write is no worse than a regular read/write, it has more of them per minute; oops, sorry.:redface:

Also PNYs are not as good for live boot. I find SanDisk drives to work the best

---

### Post by warfacegod on 2010-05-12
> **earthpigg said:**
> yup, a little bit. just how much is up for debate.

you should use an old/cheapo 2gb thumb drive for this, and use the expensive 16 or 32gb thumb drive for other things. if possible. if not, one or two or five ubuntu installs on a thumb drive isn't going to kill it.

Actually, I got between six and a dozen different Live environments with my PNYs.

---

### Post by nhasian on 2010-05-12
the nice thing about usb thumbdrives is that they are getting cheaper every day.  so use the heck out of it.  if/when it does go bad in the future, just buy another one.  I just bought a OCZ Diesel 4GB USB 2.0 Flash Drive Model OCZUSBDSL4G from newegg.  It was $10.99 and included free shipping.

---

### Post by warfacegod on 2010-05-13
How do the OCZs hold up to use as LiveUSB?

---

### Post by nhasian on 2010-05-13
I have 3 usb thumbdrives.  I've never had any of them go bad on me yet.  I know theoretically they may some day, but so far so good.  I've used:

16 gig Corsair Flash Voyager
4 gig OCZ Diesel
2 gig Lexar

---

### Post by Zionoxis on 2010-05-13
Are you guys talking about installing Ubuntu from the USB or just booting from it? I had hoped to use mine to boot from for a while. Is it going to shorten my life that quickly?

*[I]I use a 8GB Staples Relay*
[/I]
What is its expantancy because I really do not want to kill it but I also need a boot disk via USB.

---

### Post by warfacegod on 2010-05-13
> **nhasian said:**
> I have 3 usb thumbdrives.  I've never had any of them go bad on me yet.  I know theoretically they may some day, but so far so good.  I've used:

16 gig Corsair Flash Voyager
4 gig OCZ Diesel
2 gig Lexar

Which company do you suggest as the most reliable? My Gigaware's are solid but slow ...like trying teach a gopher to fly.

---

### Post by warfacegod on 2010-05-13
> **Zionoxis said:**
> Are you guys talking about installing Ubuntu from the USB or just booting from it? I had hoped to use mine to boot from for a while. Is it going to shorten my life that quickly?

*[I]I use a 8GB Staples Relay*
[/I]
What is its expantancy because I really do not want to kill it but I also need a boot disk via USB.

If you stick to whatever you put on it for booting, you should be fine. The reason my PNY's failed is that I was constantly making them into various LiveUSB's. There are *lots* of different Linux distros that support being used as a Live Environment and I keep trying different ones out..

---

### Post by ubunterooster on 2010-05-13
@warface: SanDisks are fast and reliable as is my Lexar. (My Lexar has a E-ink capacity gauge so I use it most)

 What causes the failure is the frequent reformatting I assume.

---

### Post by warfacegod on 2010-05-13
Nah, I don't reformat them, just leave them as FAT32. I think it has something to do with where the boot info gets written going bad. I suppose I could try and fix the bad sectors or whatever but I really don't care at this point.

---

### Post by Nightstrike2009 on 2010-05-13
Its a bit off the mark, but wouldn't a USB enabled microdrive be a better option? Its basically a mini-hard drive and though bigger a USB drive should withstand more punishment that a USB drive while still being portable enough too fit in your pocket and durable? 

PS: Ive seen them around and 30gb comes in at about £40 ready to use

---

### Post by ubunterooster on 2010-05-13
But....USB thumb drives are geekier...Actually that makes more sense if you have one unless you are clumsy like me

---

### Post by Kevanx on 2010-05-20
Usage is everything, and as other people have mentioned, the jury is still out, mainly since it's difficult to quantify that sort of usage on a large scale.

I've had a persistent drive for a couple of years now, which, between XMarks, UbuntuOne, acts as my computer when I don't feel like carrying the laptop with me while travelling.

If you are looking to replace your computer with a persistent live version, for sure the shelf life won't be amazing, but it should last you quite some time.

I've heard it estimated that any given block of data on a USB key is good for 10,000 writes. If you don't make major changes to your installation on a regular basis, that can mean almost as many boots from the USB before you run into problems, possibly more than 10,000 boots if the first bad block is a non-critical file.

With a persistent install, there's a lot of reading, but not a whole lot of writing, relative the quantity of data. My stance would be: back up very regularly (particularly given the fragility and easy-to-lose factor of a USB drive), try to hold off on updates until there's an important one, or a lot of them available at once, but otherwise, forget about the fact that it's a persistent drive. I'd put good money that it makes its way through the laundry before you encounter a major error.

---

### Post by warfacegod on 2010-05-20
Don't know about the laundry but computer parts can be surprisingly resilient. Once ran all the electronics of a Compaq Evo (minus the PSU and HDD) through my dishwasher. After it dried, I put it back together and it worked just fine. It even survived me forgetting to remove the CMOS battery.

Parental Advisory: If you value your computer, do not let your children read this post. They will likely try to emulate it much like they do Backyard Wrestling. These stunts have all been performed by a professional geek and they should not be attempted at home.

No animals were harmed in the writing of this post.

---

### Post by ubunterooster on 2010-05-20
> **warfacegod said:**
> Don't know about the laundry but computer parts can be surprisingly resilient. Once ran all the electronics of a Compaq Evo (minus the PSU and HDD) through my dishwasher. After it dried, I put it back together and it worked just fine. It even survived me forgetting to remove the CMOS battery.

Parental Advisory: If you value your computer, do not let your children read this post. They will likely try to emulate it much like they do Backyard Wrestling. These stunts have all been performed by a professional geek and they should not be attempted at home.The water only will ruin things if there is enough current. The drying  cycle of the dishwasher, however...Top rack only!  However, solid state devices are thenselves only affected by very specific voltages and physical damage. I stick the drives on a USB extender cord so it can move if hit.

> No animals were harmed in the writing of this post.
Not even a Roo? [IMG]http://www.easyfreesmileys.com/smileys/free-happy-smileys-456.gif[/IMG]

---

### Post by warfacegod on 2010-05-20
Can't kill Roo's when you have two little girls, hoss. Much as I'd like to. I'd never hear the end of it, "You killed Winnie the Pooh's Friend!!" WWAAAHHH!!!!!

---

