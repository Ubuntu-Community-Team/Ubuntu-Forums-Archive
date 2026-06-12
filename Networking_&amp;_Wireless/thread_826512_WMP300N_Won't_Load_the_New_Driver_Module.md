---
title: "WMP300N Won't Load the New Driver Module"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by Inc0ming on 2008-06-11
When I type

```
ndiswrapper -l
```

it says

```
bcmwl5 : driver installed
        device (14E4:4329) present
```

But when I type these two commands

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I get no response after either of them. I am using [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") and I'm on step 3.5

---

### Post by Ayuthia on 2008-06-12
If you don't get a response, that means that it did not run into any problems.  However, you are using a Broadcom card so you might be running into problems with the b43 driver.  You might try the following:
```
sudo modprobe b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
If that does not help, please post your ndiswrapper -v and lshw -C network.

---

### Post by Inc0ming on 2008-06-12
This is in order for the commands you told me

```
FATAL: Error inserting b43 (/lib/modules/2.6.24-16generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown paramter (see dmesg)
```

I had no responses to the "sudo depmod -ae" or "sudo modprobe ndiswrapper"

ndiswrapper -v:

```
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at http://ndiswrapper.sourceforge.net
```

lshw -C:

```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version
        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hard
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc.)
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc.)
        -quiet          don't display status
        -sanitize       sanitize out (remove sensitive information like serial numbers, etc.)
```

This is a huge pain to manually type out :(

---

### Post by Ayuthia on 2008-06-12
> **Inc0ming said:**
> This is in order for the commands you told me

```
FATAL: Error inserting b43 (/lib/modules/2.6.24-16generic/kernel/drivers/net/wireless/b43/b43.ko): Unknown symbol in module, or unknown paramter (see dmesg)
```

I had no responses to the "sudo depmod -ae" or "sudo modprobe ndiswrapper"

ndiswrapper -v:

```
modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

You may need to upgrade driver and/or utils to latest versions available at http://ndiswrapper.sourceforge.net
```

lshw -C:

```
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version
        -version        print program version (B.02.12.01)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hard
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc.)
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc.)
        -quiet          don't display status
        -sanitize       sanitize out (remove sensitive information like serial numbers, etc.)
```

This is a huge pain to manually type out :(

I didn't know that you did not have a wired connection.  Sorry about that.  After reading your post, I noticed that I made a typo.  The command for the removal of the b43 modules should have been:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```
However, I don't think that was your problem.  Either you are in a directory where there is an ndiswrapper file of some sort or else you don't have either ndiswrapper-common or ndiswraper-utils-1.9 installed.  Did you install ndiswrapper through the repositories or the live CD?

Also the lshw command should have been:
```
lshw -C network
```That is why you received that long message.  This command should list your network cards and show which driver it is trying to use for your wireless.  You might want to check the end of dmesg when you load ndiswrapper (sudo modprobe ndiswrapper).  It might give you some information about ndiswrapper.

---

### Post by Inc0ming on 2008-06-12
Through the repositories. Don't have the disc.

---

### Post by Inc0ming on 2008-06-12
Yes I have ndiswrapper-common and ndiswrapper-utils-1.9 installed via flash drive.

lshw -C network (not entering first part since its ethernet interface):

```
 *-network UNCLAIMED
      description: Network controller
      product: BCM43XG
      vendor: Broadcam Corporation
      physical id: 1
      bus info: pci@0000:05:01.0
      version: 01
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master
      configuration: latency=32
```

---

### Post by Ayuthia on 2008-06-12
> **Inc0ming said:**
> Yes I have ndiswrapper-common and ndiswrapper-utils-1.9 installed via flash drive.

lshw -C network (not entering first part since its ethernet interface):

```
 *-network UNCLAIMED
      description: Network controller
      product: BCM43XG
      vendor: Broadcam Corporation
      physical id: 1
      bus info: pci@0000:05:01.0
      version: 01
      width: 32 bits
      clock: 33MHz
      capabilities: bus_master
      configuration: latency=32
```

Can you try the following again:
```
sudo modprobe -r b43 ssb ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
dmesg
```
Look at the end of the dmesg results and see if ndiswrapper has any error messages.  If you are not for sure about what you are looking for, please attach the results:
```
dmesg>~/Desktop/forumdmesg.txt
```
This will take the dmesg results and put it into forumdmesg.txt.  This document can be found on your desktop.  Just attach the document to your post.

---

### Post by Inc0ming on 2008-06-13
File size is too large for me to upload directly to this site. None the less, here's the link to it.

[http://www.2shared.com/file/3429519/e0553048/forumdmesg.html](http://www.2shared.com/file/3429519/e0553048/forumdmesg.html)

---

### Post by Ayuthia on 2008-06-13
```
[  126.909133] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
```
This part is saying that you need to use a Windows 64-bit driver since you are using a 64-bit system.  You might try the driver in this [link]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R140746&SystemID=INS_PNT_P4_9400&os=WXPX&osl=en&deviceid=9805&devlib=0&typecnt=1&vercnt=2&formatcnt=1&libid=5&fileid=187886").  It comes from the NDISwrapper [site]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")  (Item 9).

---

### Post by Inc0ming on 2008-06-13
Alright, I got that driver installed. But when I opened Wireless Network Drivers, it says

```
bcmwl5
Hardware present: No
```

and yes I do have bcmwl564.sysi and bcmwl5.inf all in same directory (desktop).

One last thing, when I type ndiswrapper -l, it comes up with this:

```
bcmwl5 : driver installed
```

in stead of showing

```
{name of driver} : driver installed
       device ({Chipset ID}) present
```

---

### Post by Ayuthia on 2008-06-13
> **Inc0ming said:**
> Alright, I got that driver installed. But when I opened Wireless Network Drivers, it says

```
bcmwl5
Hardware present: No
```

and yes I do have bcmwl5.sys, bcmwl564.sys, and bcmwl5.inf all in same directory (desktop).

One last thing, when I type ndiswrapper -l, it comes up with this:

```
bcmwl5 : driver installed
```

in stead of showing

```
{name of driver} : driver installed
       device ({Chipset ID}) present
```

That usually means that it does not like the driver.  Do you have any other drivers?

---

### Post by Inc0ming on 2008-06-13
Yes, I do have another driver. I used [this one]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859959649&packedargs=sku%3D1144763512962&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5964912962B03&displaypage=download")

I used the Vista drivers since the XP ones didn't work.

Now, when I go back to typing in ndiswrapper -v, it still gives me that same thing I got last time (module version is too old)

---

### Post by Ayuthia on 2008-06-13
> **Inc0ming said:**
> Yes, I do have another driver. I used [this one]("http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859959649&packedargs=sku%3D1144763512962&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5964912962B03&displaypage=download")

I used the Vista drivers since the XP ones didn't work.

Now, when I go back to typing in ndiswrapper -v, it still gives me that same thing I got last time (module version is too old)

NDISwrapper is not able to use Vista drivers yet. :(

---

### Post by Inc0ming on 2008-06-13
Oh god, this mean I'm S.O.L?

---

### Post by Ayuthia on 2008-06-13
> **Inc0ming said:**
> Oh god, this mean I'm S.O.L?

No, I am sure that there is another driver.  I am trying to search for one.

---

### Post by Inc0ming on 2008-06-13
Wait, wow. I got it working!

I had to insert the CD that came with my PCI card (WMP300N). As soon as I placed those .sys files (bcmwl5.sys and bcmwl564.sys) it started picking up connections immediately. I hope that if people do search and find this, they have the best of luck.

I've used search through this and some have said they need to disable their WEP/WPA/WPA2 to be able to access their router, I didn't have to disable my WEP for mine to get working.

Thank you for using your time to help me Ayuthia.

Now editing my post using Ubuntu 8.04. Internet just as fast as running XP FF RC2. Lovin' it.

---

### Post by Ayuthia on 2008-06-13
You might try the driver posted here:
[http://dd-wrt.com/phpBB2/viewtopic.php?t=8726](http://dd-wrt.com/phpBB2/viewtopic.php?t=8726)

I don't think that you will need to download the .rar file though unless you need the special features.  I found the link from here:
[http://forumubuntusoftware.info/viewtopic.php?f=7&t=808](http://forumubuntusoftware.info/viewtopic.php?f=7&t=808)

Hope that helps.

EDIT:
I just saw your recent post.  That is wonderful!!!  Congratulations!

---

