---
title: "b4318 wireless broadcom, going cross-eyed and no net yet"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Rachel Evans on 2009-09-18
Hey guys,

My first time using ubuntu, with little linux experience. I've been working on this since 1 am last night (yes I did sleep!) 

I've mulled over every forum, googled as much as I can and I'm not seeming to have any luck getting my broadcom working!

I'm not sure what I need to post so let me know and I'll do it promptly!

On a side note I don't have sound either, but the net has priority.

---

### Post by achase79 on 2009-09-18
should just have to install the b43-fwcutter package to extract the firmware from the wireless card.

---

### Post by LowSky on 2009-09-18
do you have any intent access through ethernet?

see this link
[http://ubuntuforums.org/showthread.php?t=1137204](http://ubuntuforums.org/showthread.php?t=1137204)

supposedly all you need is to enable this in terminal command
```
sudo apt-get install b43-fwcutter
```

---

### Post by Rachel Evans on 2009-09-18
> **achase79 said:**
> should just have to install the b43-fwcutter package to extract the firmware from the wireless card.

tried that. get:

```
Err http://archive.ubuntu.com jaunty/main b43-fwcutter 1:011-5 
Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter_011-5_amd64.deb Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, try running apt-get update or apt-get --fix missing

```

Neither of the end codes will resolve the problem.

---

### Post by Rachel Evans on 2009-09-18
> **LowSky said:**
> do you have any intent access through ethernet?

see this link
[http://ubuntuforums.org/showthread.php?t=1137204](http://ubuntuforums.org/showthread.php?t=1137204)

supposedly all you need is to enable this in terminal command
```
sudo apt-get install b43-fwcutter
```
I am unable to hard wire my computer unfortunately without 45 feet of cable.

---

### Post by HarrisonNapper on 2009-09-18
Make sure you're connected to the internet with your ethernet cable first, which should still work.

---

### Post by Rachel Evans on 2009-09-18
> **HarrisonNapper said:**
> Make sure you're connected to the internet with your ethernet cable first, which should still work.

Unfortunately I cannot hardwire this computer. I should clarify that, it's a beast of a desktop that is totally wireless internet wise.

---

### Post by achase79 on 2009-09-18
From another computer download the b43-fwcutter package from [http://packages.ubuntu.com]("http://packages.ubuntu.com")
Then you need to download [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2]("http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2") 
When you install b43-fwcutter you will get an error.  It is trying to downlad that broadcom file itself
extract broadcom-wl-4.80.53.0.tar.bz2
in terminal cd into the directory that wl_apsta.o is in then type ```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o
```
This will extract the firmware to the correct directory.
Then you should restart the computer and be ready to go.

p.s. if b43-fwcutter gives you any more errors after you already have gotten your wireless working you can uninstall it without breaking anything.

---

### Post by Rachel Evans on 2009-09-18
> **achase79 said:**
> From another computer download the b43-fwcutter package from [http://packages.ubuntu.com](http://packages.ubuntu.com)
Then you need to download [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) 
When you install b43-fwcutter you will get an error.  It is trying to downlad that broadcom file itself
extract broadcom-wl-4.80.53.0.tar.bz2
in terminal cd into the directory that wl_apsta.o is in then type ```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o
```This will extract the firmware to the correct directory.
Then you should restart the computer and be ready to go.

p.s. if b43-fwcutter gives you any more errors after you already have gotten your wireless working you can uninstall it without breaking anything.

Alright, I'm pretty sure you lost me at extract... I extracted it (back on to the usb that I put it on, so it is now a folder but I'm trying to put it in the directory and it says I don't have the permissions to have that as a destination folder.

---

### Post by achase79 on 2009-09-18
just leave it in your home directory

---

### Post by Rachel Evans on 2009-09-18
permission denied 

What now? I'm on the only account on the OS...



(the first time hurts the most... right? :-p)

---

### Post by lkraemer on 2009-09-19
Rachel,
What he is telling you is to:
download the file named:   broadcom-wl-4.80.53.0.tar.bz2
Then extract the folder named:  broadcom-wl-4.80.53.0   to your home folder.
```

tar -xvf broadcom-wl-4.80.53.0.tar.bz2

```
Use the Terminal to change to that folder from your home with:
```

cd broadcom-wl-4.80.53.0
cd kmod
sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o

```

lk

---

### Post by Rachel Evans on 2009-09-19
> **lkraemer said:**
> Rachel,
What he is telling you is to:
download the file named:   broadcom-wl-4.80.53.0.tar.bz2
Then extract the folder named:  broadcom-wl-4.80.53.0   to your home folder.
```

tar -xvf broadcom-wl-4.80.53.0.tar.bz2

```Use the Terminal to change to that folder from your home with:
```

cd broadcom-wl-4.80.53.0
cd kmod
sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o

```lk

Thank you both VERY much. I am proud to say I'm typing this in ubuntu!

---

### Post by Tempelton on 2010-09-17
> **achase79 said:**
> [SIZE=1]From another computer download the b43-fwcutter package from [http://packages.ubuntu.com](http://packages.ubuntu.com)
Then you need to download [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)[/SIZE] [SIZE=1]
When you install b43-fwcutter you will get an error.  It is trying to downlad that broadcom file itself
extract broadcom-wl-4.80.53.0.tar.bz2
in terminal cd into the directory that wl_apsta.o is in then type ```
sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o
```This will extract the firmware to the correct directory.
Then you should restart the computer and be ready to go.

p.s. if b43-fwcutter gives you any more errors after you already have gotten your wireless working you can uninstall it without breaking anything.[/SIZE] 
Thank you, thank you! Thanks to your guide I've finally managed to configure my WPC54g PCMCIA card on Linux. I've been trying to make it work for ages. All other solutions, including the *ndiswrapper* one failed. Then suddenly I find this post and everything starts to work flawlessly. :D

---

### Post by irunwithscissors on 2010-09-19
Maybe I'm missing something here mentally or on my new ubuntu 10.04.1 install...

I've downloaded the broadcom build file and the b43_fwcutter...deb file and extracted the broadcom file to my home directory...

but when i use the command you have given: sudo b43_fwcutter -w /lib/firmware wl_apsta.o    it errors out telling me its not a command

i've also tried spelling out the whole b43_fwcutter_1build blah blah thing using the above command and it doesnt like it...

ive tried dpkg -i and it does what you said trying to download the broadcom file itself...

so im at a loss as to what im doing wrong to get this 4318 working... if i load the backtrack 4 final live cd the card is working so i know it can be used...

---

### Post by lkraemer on 2010-09-19
Try copy, then Paste.  CNTRL C  then CNTRL V

sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o

is different than

sudo b43_fwcutter -w /lib/firmware wl_apsta.o

Simple mistake.....

lk

---

### Post by irunwithscissors on 2010-09-19
> **lkraemer said:**
> Try copy, then Paste.  CNTRL C  then CNTRL V

sudo b43-fwcutter -w /lib/firmware/ wl_apsta.o

is different than

sudo b43_fwcutter -w /lib/firmware wl_apsta.o

Simple mistake.....

lk

yes it is... but either way it didn't work... but I did manage to get it working with a simple copy command...

[http://ubuntuforums.org/showthread.php?t=1470146&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=1470146&highlight=broadcom+4318)

if you venture down to solution #2 it gives you a tar file with the firmware in it... all you have to do is copy the b43 and b43legacy directories to the /lib/firmware directory... reboot... VIOLA! wireless network connections available... \\:D/

---

