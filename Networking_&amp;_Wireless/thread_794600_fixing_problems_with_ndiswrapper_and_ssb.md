---
title: "fixing problems with ndiswrapper and ssb"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by TheMightyGirth on 2008-05-14
Hi All,

have been seeing loads of issues with ssd and ndiswrapper so thought I would post a cleaner fix (rather than bodging with bootscripts).

The problem seems to be that ssd is loaded from within the initrd so normal blacklisting doesn't work.

only use this method if you don't need ssb (most people by all accounts...)

This is an "it worked for me" fix. Parts of this code are stolen from [http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/]("http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/")

```

mkdir fixinitrd
cd fixinitrd
cp /boot/initrd* ./initrd.gz
mkdir initrd
cd initrd
gunzip < ../initrd.gz | cpio -i --make-directories
gedit ./etc/modprobe.d/blacklist
cd ./etc/modprobe.d
cp blacklist blacklist.old
echo blacklist ssb >> ./blacklist
cd ../..
find ./ | cpio -H newc -o > ../initrdfixed
cd ..
gzip initrdfixed
cp ./initrdfixed.gz /boot/initrd.img-`uname -r`

```

restart a couple of time just to be sure

remove the fixinitrd directory (this removes most backups)

Hope this helps people.

---

### Post by Ayuthia on 2008-05-14
I decided to take a look at this to see what was in the initrd.  When I went into /etc/modprobe.d/blacklist, it looked identical to my current blacklist.  This leads me to believe that each kernel update will copy your current blacklist and update initrd.  Is this a correct assumption?  My concern is that 2.6.24-17 is in hardy-proposed so it is going to be released soon (if it hasn't already).  Will the changes made here be wiped out unless they place the same information in /etc/modprobe.d/blacklist (not the one in initrd)?

---

### Post by TheMightyGirth on 2008-05-15
That may well be the case, i'm not sure. If there are any of the kernel dev team or apt-get team around who could confirm that would be good.

From what I have seen, ssb should not be enabled by default anyway. At least not for a stock kernel. It is the driver for a little used bus which is in some embeded devices.

You could make a script from the code and replace line 3 with this

cp /boot/initrd.img-`uname -r` initrd.gz

that would then work for any currently running kernel. And would only need runing once.

---

### Post by Ayuthia on 2008-05-15
> **TheMightyGirth said:**
> 
From what I have seen, ssb should not be enabled by default anyway. At least not for a stock kernel. It is the driver for a little used bus which is in some embeded devices.
Actually, ssb is used for the new Broadcom drivers.  The b43 (wireless) and b44 (wired) drivers will load ssb automatically.  

> 
You could make a script from the code and replace line 3 with this

cp /boot/initrd.img-`uname -r` initrd.gz

that would then work for any currently running kernel. And would only need runing once.

When you say once, you mean that it would need to be run for any updates that update initrd, right?  You will also need to update the script to check and see if ssb is already there.  Otherwise you are going to have a file that can have multiple ssb entries.

You might also want to put a warning for those who do have a Broadcom wired card.  If they do this, they will lose their wired connection.

---

### Post by Ph83drus on 2008-05-15
I am having problems with my broadcom wireless.  It won't work on my dell d600 latitude with hardy.

Supposedly the ssb is messing this up.

But I'm so confused about this issue.  There are at least 3 or 4 major threads on fixing your broadcom wireless right.   I'm typed so many things into the terminal, and I have no idea if what I doing is causing permanent complications for down the road.

It's frustrating.  

I'm heading to my local computer shop to buy a usb wireless device.   and hopefully this broadcom stuff can get sorted out.

---

### Post by MurDoK on 2008-09-18
You can also try: sudo update-initramfs -u.
I think it does the same (it worked for me).

---

### Post by albesan on 2008-11-21
> **MurDoK said:**
> You can also try: sudo update-initramfs -u.
I think it does the same (it worked for me).

You are the man... thanks.
I was reading through the posts on the thread and when I got to yours I went like, "of course!!" Thanks again

a.

---

