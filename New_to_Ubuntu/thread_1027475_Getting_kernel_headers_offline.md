---
title: "Getting kernel headers offline"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by -Chris on 2009-01-01
Hope someone may be able to help.  I'm a complete newbie to Linux; I've spent the best part of 3 days searching & reading without finding an answer before venturing to ask.

I've installed Ubuntu 8.04.1 (by downloading the latest .iso) as a dual boot on my Vista machine. I am able to use Vista to access the net & transfer to Ubunto via a usb memory stick. The machine has a wireless usb adaptor with Ralink rt73 chipset the existence of which isn't recognised by Ubuntu.  I need to install the driver.  Once the adaptor is accessible I can set up the connection to the ADSL wireless modem.

I've been looking at
[http://www.spinthiras.net/2008/09/20/ubuntu-and-the-ralink-rt73-chipset/](http://www.spinthiras.net/2008/09/20/ubuntu-and-the-ralink-rt73-chipset/)
which is very useful.

I´ve got hold of the tar.gz driver file & I've installed build-essential, but before I can make the driver I understand that I have to install the headers for the kernel (I run 2.6.24-9-generic) as mentioned in the above article.

The problem is that I haven't been able to find any way of getting hold of the headers without a Ubuntu connection, so it seems to be a Catch 22.

I can see from the post by Blastus in this thread
[http://ubuntuforums.org/archive/index.php/t-80974.html](http://ubuntuforums.org/archive/index.php/t-80974.html)
that further difficulties might lie ahead in any event.  I hoped that I might get round them by putting the plausible header packages into the usb memory (if it turns out that there are several such), adding -'uname -r' to the install command - I understand that it selects only the correct headers - at least when used on the repository as intended.

My first problem is: how to get the headers, when I can only get on the net when Vista is loaded.  Does anyone have any advice?

---

### Post by ibuclaw on 2009-01-01
What kernel version do you have? And what arch have you installed?

You can download the packages from package.ubuntu.com, but you need to know exactly which one to get, and all of it's dependancies.

I'm not too sure which kernel version comes with 8.04.1 installation, but this page will get you close to where you want to be looking at:
[http://packages.ubuntu.com/hardy/linux-headers-2.6.24-16-generic](http://packages.ubuntu.com/hardy/linux-headers-2.6.24-16-generic)

Regards
Iain

---

### Post by -Chris on 2009-01-02
Thanks for your very helpful advice.  I'm running kernel 2.6.24-19-generic on amd64, so it was a short hop from the page you ventured to the page I needed to get started.

I had no idea how long this would take - & now I've spent some time at it lost in the maze of depends, recommends & suggests I still don't.  Anyway I've paused fro the moment, to take a breather & to work out a better system for not getting lost.

Meanwhile, thanks once more for telling me what I wanted to know.

---

### Post by handydan918 on 2009-01-02
> **-Chris said:**
> Thanks for your very helpful advice.  I'm running kernel 2.6.24-19-generic on amd64, so it was a short hop from the page you ventured to the page I needed to get started.

I had no idea how long this would take - & now I've spent some time at it lost in the maze of depends, recommends & suggests I still don't.  Anyway I've paused fro the moment, to take a breather & to work out a better system for not getting lost.

Meanwhile, thanks once more for telling me what I wanted to know.
Save your sanity. the rt73 driver is in the repos. Open synaptic and search for rt73.

---

### Post by -Chris on 2009-01-11
I took your advice re saving my sanity & bought a long ethernet cable so I cocan use Synaptic.  I couldn't find any rt73 driver accessible via Synaptic, but I found the Ralink site's driver files for Ubuntu.  With Synaptic I installed the kernel headers & build-essential & then I built & installed the driver following Ralink's install notes & it works to this extent (WLAN_90 is my ADSL wireless modem) -
“wlan0     Scan completed : 
          Cell 01 - Address: 00:01:38:89:7F:AA 
                    ESSID:"WLAN_90" 
                    Mode:Managed 
                    Channel:6 
                    Encryption key:on 
                    Bit Rates:0 kb/s ”
which is fine, but it doesn't show on Network/network tools.  Ralink warn of this, & include terminal commands to configure it, but I can't get them to work; I get this - 
chris@chris_ubuntu:~$ iwconfig wlan0 mode managed 
Error for wireless request "Set Mode" (8B06) : 
    SET failed on device wlan0 ; Operation not permitted. 

Ralink also provide files to make a GUI, so I decided to go that route instead, but ti build the GUI I need gtk+2.0 installed – for which I first need to install glib, pango, atk & cairo.  I couldn't find them via Synaptic.  I could find, e.g. libcairo 2, but no cairo.  Both glib & pango were easy enough to google  & install but I'm getting bogged down with the last two – so I'm beginning to wonder if I'm missing something very obvious when I fail to find things with Synaptic.

I can see the package I would like to install at the end of the day at this url
[http://packages.ubuntu.com/es/source/hardy/libs/gtk+2.0](http://packages.ubuntu.com/es/source/hardy/libs/gtk+2.0)
but I can't see any way of accessing it to install it the easy way with Synaptic.  In the repository, the package is labeled 'universe'.  In Synaptic I search 'All' sources against both title & description with various combinations of gtk+  & I've tried changing to various different repositories under preferences (not forgetting to reload after) & I see plenty of packages for gtk but nothing like the Source Package: gtk+2.0 (2.12.9-3ubuntu2).

Is there some way of getting Synaptic to point at the url?  I feel I'm overlooking something fuundamental.

---

### Post by -Chris on 2009-01-21
In case anyone should look at this thread, I thought I'd mention that I sorted the problem in the end, though I had to abandon trying to collect all the bits to make Ralink's GUI.

In brief, the build instructions of the read-me in the Ralink driver tar worked to get the driver installed but I didn't have the Ralink GUI to configure it & I couldn't get the Ralink 'iwconfig [] mode Managed' to work - I still don't know why.  Network & Network tools don't work with this USB device, as I've seen confirmed elsewhere - but in the end I found a Spanish blog with a very easy answer - manual configuration via the net program (2 monitors icon, top RH corner) does work.  So now I have wireless.

This site also mentioned that the driver is lost whenever a new version of the kernel is installed but the configuration is saved, so you only have to re-install the driver from the Ralink tar.

Anyway - onwards & upwards! & thanks.

---

