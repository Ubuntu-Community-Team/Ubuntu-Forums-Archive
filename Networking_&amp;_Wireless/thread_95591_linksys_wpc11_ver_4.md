---
title: "linksys wpc11 ver 4"
date: 2005-11-26
forum: Networking &amp; Wireless
---

### Post by jaymill on 2005-11-26
I know that this has been done before, but I was trying to find out how to get it to work. I would appreciate ANY help, especially in baby steps, I am JUST begining in linux and I am a complete newbie. 

Thanks!

---

### Post by Permafrost91 on 2005-11-26
All this is on the web at:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

But this is what I did to get my WPC11v4 to work:

(0) Have a working internet connection (probably hardwired for now since your wireless isn't working yet) ... just give it five more minutes!! :p 

(1) install ndiswrapper-utils (I'm not sure if you have to enable multiverse/universe, but if you do, that's explained in the Starter Guide). Open System->Administration->Synaptic Package Manager and search for 'ndiswrapper-utils.' Click on the icon to the left of it and select 'Mark for Installation' then hit Apply at the top of the screen. Close out of Synaptic once the installation is done.

(2) Download the Win XP driver (I'm assuming you'll download to /home/user) from here (either site 1, 2, or 3 ... it doesn't matter):
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180](http://www.realtek.com.tw/downloads/downloads1-3.aspx?Keyword=8180)

(3) Extract the archive (a .zip file) into /home/user/wpc11

(4) open a terminal (Applications->Accessories->Terminal) then
```
$ cd /home/user/wpc11
$ sudo ndiswrapper -i NET8180.INF
$ sudo ndiswrapper -l
```

You should see this message:
```
Installed ndis drivers:
net8180 driver present, hardware present
```

If you see this, do
```
$ sudo depmod -a
```

Provided there is no error message, follow up with
```
$ sudo modprobe ndiswrapper
```

To load the module automatically at boot, add this line to your /etc/modules file:
```
ndiswrapper
```

(5) You should be able to use the network configuration tool provided by Ubuntu to set up your connection. I highly recommend installing wifi-radar too. It's an excellent tool that will choose automatically between found and pre-configured wireless networks at boot-time (you can rearrange the list of networks to your liking).

Hope this helps!

---

### Post by jaymill on 2005-11-27
hey, that worked perfectly! especially once I figure out I was spelling etc ect in the command line :)

---

### Post by Permafrost91 on 2006-01-21
use tab completion for directories and file names on the command line ... it's a great tool to avoid spelling mistakes plus it saves time!

---

### Post by bminor on 2006-01-30
halo
I am a newbie too
and I have a problem when I was installing ndiswrapper 1.8(i'm using WPC11 ver.4 also)
when I followed to the step "$ sudo modprobe ndiswrapper"
it returned "FATAL: Module ndiswrapper not found."
What's wrong?

P.S. I did step 1-4 worked fine until the step of "$ sudo modprobe ndiswrapper"

---

### Post by Permafrost91 on 2006-01-30
what kernel are you using? I had that problem with the 2.6.15 kernel in Dapper too so I went back to the Breezy stock kernel.

---

### Post by bminor on 2006-01-30
[QUOTE=Permafrost91]what kernel are you using? I had that problem with the 2.6.15 kernel in Dapper too so I went back to the Breezy stock kernel.[/QUOTE]
i am using the kernel 2.6.12.
so, is that ok?

---

### Post by Permafrost91 on 2006-01-30
hmm ... that's what I'm using (2.6.12-10-386)

what does

```
$ sudo ndiswrapper -l
```

output?

---

### Post by mpvano on 2006-01-31
What C compiler did you use to build ndiswrapper?

The WPC11v4 works great for me with the original preinstalled ndiswrapper in breezy, but if you try and build a later version from sources you will need to make sure it gets built with gcc-3.4 NOT the standard breezy gcc-4.0 compiler.

Kernels are typically compiled with earlier compilers for stability reasons. In this case, if you build kernel modules with the wrong compiler, they won't load and will give mysterious error messages.

Either figure out how to go back to the built-in ndiswrapper version, or figure out how to build the 1.8 version with gcc-3.4

I don't know what build method you used, but if you did it manually, you can apt-get gcc-3.4 and then temporarily replace the soft link linking gcc to gcc-4.0 with one linking it to gcc-3.4 (don't forget to put it back).

Another problem you may have, is that when your kernel gets an automatic update via ubuntu's update manager, you may need to rebuild ndiswrapper and reinstall it again (possibly after loading new headers). I think there's some devious way around this that module-assistant uses, but most normal build howto's don't do that.

By the way, for a card that's been such a pain in the whatsit  for such a long time (even under windows) that particular card is now working EXTREMELY well for me on a Sony Vaio using the latest XP drivers under breezy. It's fast, stable, sleeps and hibernates and It even scans properly.....

Mario

---

### Post by Permafrost91 on 2006-01-31
I didn't build ndiswrapper from source:

```
# apt-get install ndiswrapper-utils
```

---

### Post by bminor on 2006-01-31
[QUOTE=Permafrost91]hmm ... that's what I'm using (2.6.12-10-386)

what does

```
$ sudo ndiswrapper -l
```

output?[/QUOTE]
the output is:

Installed ndis drivers:
net8180 driver present, hardware present

---

### Post by bminor on 2006-01-31
[QUOTE=mpvano]What C compiler did you use to build ndiswrapper?

The WPC11v4 works great for me with the original preinstalled ndiswrapper in breezy, but if you try and build a later version from sources you will need to make sure it gets built with gcc-3.4 NOT the standard breezy gcc-4.0 compiler.

Kernels are typically compiled with earlier compilers for stability reasons. In this case, if you build kernel modules with the wrong compiler, they won't load and will give mysterious error messages.

Either figure out how to go back to the built-in ndiswrapper version, or figure out how to build the 1.8 version with gcc-3.4

I don't know what build method you used, but if you did it manually, you can apt-get gcc-3.4 and then temporarily replace the soft link linking gcc to gcc-4.0 with one linking it to gcc-3.4 (don't forget to put it back).

Another problem you may have, is that when your kernel gets an automatic update via ubuntu's update manager, you may need to rebuild ndiswrapper and reinstall it again (possibly after loading new headers). I think there's some devious way around this that module-assistant uses, but most normal build howto's don't do that.

By the way, for a card that's been such a pain in the whatsit  for such a long time (even under windows) that particular card is now working EXTREMELY well for me on a Sony Vaio using the latest XP drivers under breezy. It's fast, stable, sleeps and hibernates and It even scans properly.....

Mario[/QUOTE]
Thanks for your help.
But, i don't know how to install gcc3.4(i checked that i'm using gcc4.0 and i hv downloaded form the site, but it's just a file called "gcc-3.4.0.tar.gz". so  i can't install it using Synaptic)
And I can use the command "ndiswrapper". But i could not do the step of "modprobe ndiswrapper"

---

### Post by mpvano on 2006-01-31
Synaptic Package Manager certainly shows gcc-3.4 when I open it here!

Make sure you have "All" selected in the left panel - gcc-3.4 is part of the base installation repository. Simply click on the box next to it's name, select "mark for installation" and then click on "Apply" to download and automatically install it.

You ARE asking for help about Breezy (Ubuntu 5.10) aren't you? This subsection is for help about Breezy. If you're talking about Hoary or Dapper, Nothing anyone says here is probably correct.

If you still can't find the compiler, you probably shouldn't be doing this by yourself - building from source is not for beginners.

Mario

---

### Post by bminor on 2006-02-01
[QUOTE=mpvano]Synaptic Package Manager certainly shows gcc-3.4 when I open it here!

Make sure you have "All" selected in the left panel - gcc-3.4 is part of the base installation repository. Simply click on the box next to it's name, select "mark for installation" and then click on "Apply" to download and automatically install it.

You ARE asking for help about Breezy (Ubuntu 5.10) aren't you? This subsection is for help about Breezy. If you're talking about Hoary or Dapper, Nothing anyone says here is probably correct.

If you still can't find the compiler, you probably shouldn't be doing this by yourself - building from source is not for beginners.

Mario[/QUOTE]
Yes! I'm using Ubuntu 5.10, Breezy. Now, I can see four packages called "gcc "when I'm seraching in the Synaptc.It's "gcc", "gcc-3.3-base", "gcc-4.0" and "gcc-4.0-base"
Those are all installed. But I still could not run the step of "$ sudo modprobe ndiswrapper"
If so, Is that I can't install my wireless card by myself?
Thanks again!:)

---

### Post by ringjp on 2006-05-02
The directions originally provided by Permafrost worked great for me - provided I disabled WEP!  How do I get this to work with WEP?  I can't seem to get an answer that works.

---

### Post by monomaniacpat on 2006-05-02
Hi guys,

I had some success using the open source drivers, until it suddenly stopped responding. If you have any advice for such things, please read my [thread](http://www.ubuntuforums.org/showthread.php?t=167026).

Alternatively, if you think you can get my card to work using ndiswrapper, please tell me why I can't get it to detect my hardware. In the gui it says driver present: yes, hardware present: no. Also:

```
patrick@ubuntu:~$ sudo ndiswrapper -l
Password:
Installed ndis drivers:
net8180 invalid driver!

```

Little help?

---

### Post by Permafrost91 on 2006-05-02
I got the "invalid net8180 driver" message after upgrading to dapper's ndiswrapper package. This was a while ago but I think removing the old driver and installing it again solved the problem for me.

---

### Post by monomaniacpat on 2006-05-02
Actually, I've got the hardware detected now. But I still haven't worked out how to get network settings to list the hardware.

---

### Post by Permafrost91 on 2006-05-02
do you have wireless-tools installed? what does
```
$ iwconfig
```
say? can you scan for wireless networks in range?
```
$ iwlist wlan0 scan
```

---

### Post by monomaniacpat on 2006-05-02
```
patrick@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

patrick@ubuntu:~$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```

Basically, there is no wlan0 installed (I have insterted ndiswrapper, btw). It doesn't show up in network settings.

---

### Post by mrgumby on 2006-05-02
My sotec is now on my lap in the living room :) the wireless card is working nicely now!
I used the advice at the start of this thread to set it up way back, but it did not work.
I tried to use the driver from the CD that came with my hardware...(same name for the file)...but it would not work.

Only when I went to the web for the driver (in the link at the start of this thread) did it work.

Also, when I did: #sudo ndiswrapper -l 
it showed no driver installed.

I then tried to install the 8180 driver from the web.
When I did, it told me that the 8180 driver was installed already. (Does anyone know why this would happen??)

This might be something to check on if you are having problems. I guess when you look for ndiswrapper installs, they dont always show, but they are there??!!?? 

For me, even though they are the same name, the driver on the web does not load the same as the one on the web.

Hope this helps someone else. Good luck!

---

### Post by sfhscfc on 2006-05-11
This works great to activate my wireless card, it even sees the networks around me so i know it works sortof. When I activate it nothing happens though, i configure it for the DHCP but the internet just wont work. HELP

---

### Post by monomaniacpat on 2006-05-11
You sure it's on the right encryption? Hex/Plain?

---

### Post by sfhscfc on 2006-05-11
ya pretty sure, since its not password protected. Ill try changing it though.

---

### Post by sfhscfc on 2006-05-12
That didnt do anything.

---

### Post by sfhscfc on 2006-05-18
](*,) ya, im stupid. It need to be hex. But on anothe subject, i cant write in my /etc/modules file. It says its denied. Can anyone help??

---

### Post by kweejibo on 2006-05-25
Permafrost--

many thanks! I've been beating my head on the keyboard for a week with various Debian releases. I found Ubuntu, this forum, and your post and had my Wifi problem solved in less than 10 minutes! Hooray!

Josh

---

### Post by zappadragon on 2006-06-03
$ sudo ndiswrapper -l
Installed ndis drivers:
net8180 invalid driver!

I have followed all instuctions and can not get this to work

please help

---

