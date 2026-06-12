---
title: "Install over lan to laptop with broken cd rom"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by tfultz33 on 2009-12-11
I want to install ubuntu karmic from my desktop pc running karmic  to a laptop with a broken cd rom drive. I have no usb drives. My internet connection connects at 26.4kbs so no chance of using the internet.

I have the ubuntu karmic koala desktop normal cd.

How can i install it across a wireless home network on the laptop?

The laptop can boot from lan according to the bios.

Can i install over the network using all the packages on the cd instead through the internet?

Thanks
Edit: The desktop also runs xp home

---

### Post by Geoff918 on 2009-12-11
I'm clueless, friend.

I have a broken DVD-RW drive, but I just make the USB images.

I maybe found this for you, though?

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

or this?

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

I think the first seems more helpful. Hopefully this will get what you need accomplished.

EDIT:

I found something else, it's for Hardy, but I'm sure could be easily adapted.

[http://news.softpedia.com/news/Alternative-Installation-Methods-for-Hardy-86977.shtml](http://news.softpedia.com/news/Alternative-Installation-Methods-for-Hardy-86977.shtml)

---

### Post by cartisdm on 2009-12-11
Personally I haven't had very good luck with booting from USB.  So many drives are just finiky.  You can order an external DVD reader for like 20 bucks online or if you are in a hurry pick one up from staples for about 65

---

### Post by marshmallow1304 on 2009-12-11
Also have a look at this one: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by tfultz33 on 2010-06-30
HI. I never did find out how to install over a windows network with no internet. Im too tight to buy a drive. LOL I would just like to make the laptop somewhat useful again. It runs an old debian distro like 4 or something.

Any help would be greatly appreciated.

---

### Post by nothingspecial on 2010-06-30
> **tfultz33 said:**
>  I would just like to make the laptop somewhat useful again. It runs an old debian distro like 4 or something.



Why not just stick with what you`ve got, assuming it is a working system, and update the packages you want to use on it.

I have a netbook with a broken keyboard that finds use as a digital photo frame, controlled remotely.

I also have it`s other half (broken screen) which has been a file server and is currently a tv/video player in my bedroom (external monitor).

---

### Post by hogarth on 2010-06-30
Hi tfultz33,

In regards to your original question (installing over LAN), did you try what marshmallow1304 suggested? Because i'm pretty sure that will work.

If, however, you don't want to install over the internet, the softpedia link in Geoff918's post does work, as that's what i used to install karmic on an older laptop of mine with the same problem (a minger cd/dvd drive). I know you said you don't want to buy a usb flash drive, but a 1GiB one is honestly $10 online... Just abstain from two subway meals :) Besides, $5 for a footlong is ridiculously overpriced when you get barely any meat...

As far as i know, booting from USB or installing over LAN are the only two options if you don't have a working cd/dvd drive. Someone can correct me if i'm wrong (in which case i apologize)...

Hope that helps!

---

### Post by tfultz33 on 2010-06-30
I cant install over the internet. Im in the boonies. My internet connection is 26.4 k thats about 2 k a second. I cant update what i have since it's so old I would have do download it all. So absolutely no internet involved. Surely I can hook it to a windows computer and install off a  a cd or a cd image?

Thanks for the help though.

---

### Post by corrytonapple on 2010-06-30
Not sure if it works with other computers but...
With macs you can use the other computer's cd drive. You put the ubuntu disc in and connect the two via ethernet cord, then select where you want to install ubuntu to, which would be the laptop.
Don't know if it works but worth trying.

---

### Post by Chamillion02 on 2010-06-30
As an alternate installation solution, you could use a flash drive. That is if you have a functioning USB port on your computer.

Here's a guide to help you do this - [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
Good Luck! -Chamillion02

---

### Post by tfultz33 on 2010-07-01
Thanks guys, for the replies. I'll probably just break down and get a flash drive or a cd drive one of these days.

---

### Post by tfultz33 on 2011-09-04
I got this working a good while ago using tftp and apache. The tfp config file was missing tabs but I got it figured out. Thanks for help guys.

---

### Post by snip3r8 on 2011-09-04
> **corrytonapple said:**
> Not sure if it works with other computers but...
With macs you can use the other computer's cd drive. You put the ubuntu disc in and connect the two via ethernet cord, then select where you want to install ubuntu to, which would be the laptop.
Don't know if it works but worth trying.

Macs also come with a pretty good standard operating system that supports alot of linux stuff if you know what to do:) This among other features such as flipping the universe on its head and sending data to alien races who are completely stunned by this "Thunderbolt earth tech", all wrapped up in a paper thin sheet of aluminium.

---

