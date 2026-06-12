---
title: "Netgear WG311 v3"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by fpvdrif6 on 2008-03-22
Hi all,

I'm using Ubuntu 7.10 and I only have wireless access.  I've read [this link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") and my card is not listed :(

I've read through [this link]("http://ubuntuforums.org/showthread.php?t=402076") as well, but I can't see what version he was using, but I'm guessing it's not 7.10 as the last post date was May 13, 2007.

Any ideas where I can find complete how-to for a newbie to this stuff to get my drivers to work?  At the moment, it does not even recognise any wireless device at all.  I only get the option of wired, which is my motherboard onboard network port (unconnected).

Thanks for any help.  I am posting from Vista (dual boot setup), so ideally I would like to save any files I need on my hard drive and then should be able to access them from within Ubuntu.  I would also like to print out a full set of instructions, if I can find them.

Also just to note, this is a brand new install, I haven't done anything else yet - and I'd be happy to reformat/upgrade/downgrade etc... if it's recommended or somebody thinks it will work.

Cheers in advance

Troy

---

### Post by dstew on 2008-03-22
[This document]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3") seems to be straightforward. Only, you do not need to download the Debian ndiswrapper packages.

You should install the ndiswrapper packages ndiswrapper-common and ndiswrapper-utils using the synaptic package manager (System --> Administration --> Synaptic Package Manager). Then, post the output of ```
lspci -n
```to show the exact name of your card. Once you have the PCI I.D. info, you can find the current driver on the [Marvell site]("http://www.marvell.com/drivers/search.do"). Once you have the Windows driver archive on your computer, you can follow the instructions to install the driver into ndiswrapper.

---

### Post by fpvdrif6 on 2008-03-23
Hi dstew, thanks for your reply!

I'll reboot into Ubuntu now and find out what PCI I.D. I have. :)

I'm rather proficient with hardware, and also in Windows, but this linux stuff just blows my mind! :confused: Bear with me - I appreciate it!

Cheers

Troy

---

### Post by fpvdrif6 on 2008-03-23
Okay, I'm back!

I had a really fun time in there, I have to admit - Ubuntu boots heaps faster to the desktop than Vista!

I found the Synaptic Package Manager and installed those two packages, but then when it was finished installing I was unable to type anything into the code box, I could only click on the "Close" button...

So I went searching and eventually found the Terminal, is that where I was supposed to input the code and post the output for you?  Here's the results, anyway:

```
hts@hts-desktop:~$ lspci -n
00:00.0 0600: 8086:29c0 (rev 02)
00:01.0 0604: 8086:29c1 (rev 02)
00:1a.0 0c03: 8086:2937 (rev 02)
00:1a.1 0c03: 8086:2938 (rev 02)
00:1a.2 0c03: 8086:2939 (rev 02)
00:1a.7 0c03: 8086:293c (rev 02)
00:1b.0 0403: 8086:293e (rev 02)
00:1c.0 0604: 8086:2940 (rev 02)
00:1c.3 0604: 8086:2946 (rev 02)
00:1c.4 0604: 8086:2948 (rev 02)
00:1d.0 0c03: 8086:2934 (rev 02)
00:1d.1 0c03: 8086:2935 (rev 02)
00:1d.2 0c03: 8086:2936 (rev 02)
00:1d.7 0c03: 8086:293a (rev 02)
00:1e.0 0604: 8086:244e (rev 92)
00:1f.0 0601: 8086:2918 (rev 02)
00:1f.2 0101: 8086:2921 (rev 02)
00:1f.3 0c05: 8086:2930 (rev 02)
00:1f.5 0101: 8086:2926 (rev 02)
01:00.0 0300: 10de:0611 (rev a2)
03:00.0 0106: 197b:2363 (rev 02)
03:00.1 0101: 197b:2363 (rev 02)
04:00.0 0200: 10ec:8168 (rev 01)
05:02.0 0200: 11ab:1faa (rev 03)
hts@hts-desktop:~$
```

Is it just me, or is that rather unhelpful?  Or is there another place I'm supposed to insert that code?

Thanks in advance, once again :)

Cheers

Troy

---

### Post by dstew on 2008-03-23
> when it was finished installing I was unable to type anything into the code box, I could only click on the "Close" buttonThat's how it should be. When the programs are installed, you are done. To configure ndiswrapper, you will use the terminal.

> Is it just me, or is that rather unhelpful?Sorry, try **lspci** without the **-n** to get the verbal information. The -n switch gives an extra piece of data that might help us pick the correct driver.

---

### Post by fpvdrif6 on 2008-03-24
Hi again, thanks for sticking with me :)

Okay I managed to get in there and try **lspci** without the -n switch.  Unfortunately, I've lost the formatting this time, so bear with the .txt file output...  Well after a post preview, it looks like the formatting is fine after all! :lol:

```
hts@hts-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
hts@hts-desktop:~$ 
```
So looking at that, I can see my Nvidia video card (Unknown device) still needs drivers.  That's my next task to tackle after the wireless internet is connected and working!

Also, (and more important to us in this thread), down the bottom I can see "05:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)", so that looks like it, eh?  Sweet work my man, now I'm off to research that thread again in the hopes that I can do something with that information.

Cheers

Troy

---

### Post by fpvdrif6 on 2008-03-24
Okay I've just been researching some more,  I've found what may potentially be a crucial difference in which driver to use.  Or possibly, it may be the same driver for them both...

In my code, the device has the following:
```
88w8**3**35
```

On the page to which you linked ([here]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")), it has this:
```
88w8**8**35
```

The difference, in case you didn't quite catch it, is the 3 and the 8 that I have put in bold.

I had a look on the Marvell website driver download page, but I can't make any sense out of that page.  I don't know what version of the driver to select for Ubuntu.

Any further help here would be awesome!

Cheers

Troy

---

### Post by dstew on 2008-03-24
Here is where the number from the lspci -n output helps. The unique identifier is 11ab:1faa. The best thing to do is use this number to do google and forum searches to see what driver people used. A good place to start is the ndiswrapper site itself. They maintain a [list of cards that work with ndiswrapper]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/"), along with what driver people used.  You have a Netgear card, so go to the [M-N page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/"). When you get there, search for the identifier 11ab:1faa using your browser's search function (on Firefox it is Edit --> Find in this page) and you will find several references to what people did to get it to work. It seems that it works with a variety of drivers, but some drivers do not work. There are links there to the driver files also. It looks like the driver wg311v3 would be a good one to try first. You can try to get it from the CD that came with the card, or download it. If the download is a .exe file, you can try to get the drivers out of it with the cabextract program:```
cabextract *driver_package.exe*
```However, if someone has the extracted .inf and .sys files ready to download, you might be able to find those somewhere.

---

### Post by prshah on 2008-03-24
> **dstew said:**
> However, if someone has the extracted .inf and .sys files ready to download, you might be able to find those somewhere.

You will find the INF and the SYS files in \windows\inf\wg311v3\

Keep an eye on the case (uppercase, lowercase) of the above folders/files.

Once you get to the above folder ```
sudo ndiswrapper -i wg311v3.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

(again, keep an eye on actual case as in your system)
and wireless will start working in a few seconds. If you want to confirm wether it's loaded; ```
iwconfig
``` will indicate the wireless card, usually wlan0

btw, NETGEAR uses the Marvell chipset, which is a pure OEM company.

---

### Post by dstew on 2008-03-24
One more thing: once you have ndiswrapper working, do ```
ndiswrapper -l
```If the output lists an alternate driver, you will probably get better function if you blacklist the alternate driver. Post back for how to do that.

---

### Post by fpvdrif6 on 2008-03-25
Hi there, and thanks for joining in prshah!

I cannot find the files required in that directory.  I eventually tracked down that I'm already using a Marvell driver (I remember Windows Update changed it about 2 months ago) called MRVW13B.sys and it's located C:\Windows\system32\DRIVERS\

I am unable to find a relevant .inf file on my system, any ideas?  I went searching (through my computer boxes in the home office here) but could not find the original box and/or disc that came with the wireless card.

I tried the cabextract function from within Ubuntu but it gave me an error that cabextract was not installed.  I tried to install it (it told me how!), but then it gave me another error saying that the component called universe would need to be installed.  I have no idea what universe is or where it is located.

Of course, I could just install the whole thing in Vista and then go find it, but I'd prefer to continue using the Vista Network Manager to configure the whole thing (as I've been doing).  The Netgear program gave me some hassles. :(

Is it just me, or are we all really having fun here? :lolflag:

So all I really need is the appropriate .inf and .sys files, and I'm guessing it might take me a few different tries to find one that works properly with my system.

Let me know if you find something or have any further relevant information for me.

Cheers

Troy

EDIT: Well, I do know what the universe is, just not the type of universe that's related to Ubuntu somehow! #-o

---

### Post by dstew on 2008-03-25
> the component called universe would need to be installed"Universe" is the name of a software repository. It is all the programs that anyone can write. It is not officially supported by Ubuntu, but the programs usually work, since they are open-source. You need to enable the Universe repository in the synaptic settings tab.

---

### Post by prshah on 2008-03-25
> **fpvdrif6 said:**
> 
So all I really need is the appropriate .inf and .sys files, and I'm guessing it might take me a few different tries to find one that works properly with my system.


Netgear does not ship the INF and SYS files "in the open" on their driver CD. You need to install their SmartGear software which will then install the inf and sys files. If you can't find it in \windows\inf\wg311v3, then look in "\program files\netgear\driver", which is where they used to put it in v2.

Or try this; (assuming your windows partition is sda1)```
cd /media/sda1
ls -R | grep -i wg311

```

This should list any filenames with wg311 in them.

If you still don't get it, PM me your email address and I will email them to you (small; about 256kb).

I use wg311, with v2, it "just worked" right out of the box with native Atheros drivers; with v3 I had to take the ndiswrapper route, but even so it works just fine.

CAVEAT: Installing Netgear's Smart Wizard or whatever will DISABLE fast user switching in XP!! To re-enable it, open the registry, search for and delete the key called "ginadll", which will point to a file called "MrVGINA.DLL" (That's the original capitalization, I'm not making this up!)

---

### Post by fpvdrif6 on 2008-03-25
Okay thanks both for more helpful responses. :)

dstew: Where can I find the "synaptic settings tab"?  If it's not officially supported by Ubuntu, it wouldn't make sense to me that it would be included in the installation (or an option thereof). :confused:

prshah: I am currently using Vista (not XP), and I don't care about fast user switching anyway - I am the only user.  But judging from your post, you have the same version of card as mine and you got it working?  I will PM you for those files as I would prefer not to install the Netgear program (in Vista) again to get the driver files required.  When I first installed the wireless card, I was having a few dropout issues that were being caused by the Netgear program.  The Vista Networking Centre manages it just dandy. :)

I really appreciate the comments here.

Cheers

Troy

---

### Post by dstew on 2008-03-26
> Where can I find the "synaptic settings tab"?System --> Administration --> Synaptic Package Manager, click on Settings.> If it's not officially supported by Ubuntu, it wouldn't make sense to me that it would be included in the installationI was referring to cabextract, not synaptic. I guess I shouldn't say the Universe programs aren't supported by Ubuntu, because in a sense they are. The programs are packaged and tested by Ubuntu developers, so they are usually safe to use. They are not *maintained* by the Ubuntu developers though, like the main part of Ubuntu. So, if you install a program from there, and it doesn't work, you have to report back to the original maintainers, usually on [Sourceforge]("http://sourceforge.net/").

---

### Post by fpvdrif6 on 2008-03-26
Hi again,> **fpvdrif6 said:**
> dstew: Where can I find the "synaptic settings tab"?  If it's not officially supported by Ubuntu, it wouldn't make sense to me that it would be included in the installation (or an option thereof). :confused:Unfortunately, my comment here was correct.  My thinking was that it wouldn't be available directly, but would need to be downloaded.  After attempting to enable the universe depository (I think it said Community-Supported Software), it gave me a network error that it was unable to connect to archive.ubuntu.com :roll:  So it's the old chicken and egg argument, once again!

I have PM'd prshah to see if he can send me the files.

Cheers

Troy

---

### Post by fpvdrif6 on 2008-03-27
Hi there,

You know, I don't think I'm going to get this working without at least a wired connection as well.  It'd just be a hassle to move my computer so I can plug it in to the ethernet cable.  I think I'll slot it in some time for a "to be done" job, which - of course - there's never any time to achieve these types of projects :lol:

If you could kindly reiterate the steps to take (assuming I have internet connected), then when I eventually get around to it, I'll be able to refer here for instruction.  As I understand it:
[LIST][*]Enable the Universe repository
[*]Install cabextract
[*]Extract files from installation .exe file
[*]And then something about ndiswrapper and the two files (.inf and .sys)
[/LIST]Does that look about right?

Many thanks, you've both been most helpful.

Cheers

Troy

---

### Post by dstew on 2008-03-27
Yes, that is the basic outline. If you can get the Windows drivers .inf and .sys files in a form other that an .exe file, then you do not need cabextract. Maybe you can get them directly from a CD or some helpful friend, that also works.

---

### Post by fpvdrif6 on 2008-03-28
> **dstew said:**
> Yes, that is the basic outline. If you can get the Windows drivers .inf and .sys files in a form other that an .exe file, then you do not need cabextract. Maybe you can get them directly from a CD or some helpful friend, that also works.Hi there,

Well I can't find the CD, and prshah has not responded yet to my PM or emailed me the files.  Nonetheless, thanks heaps for all your help, and I'm sure once I grab the files I will be back here asking, "ummm, what was it next, again?" :lol:

I'll definitely keep you posted, and if anybody has the files or can find them available for download, or just downright has any more helpful information, I'd be more than glad to hear it (or read it!).

Cheers

Troy

EDIT: And if it all comes down to it, I'd be tempted to install another copy of Vista and extract the files there - which would mean I should be able to grab what I need.  I have the hard drive space, but just not the time... :)  Such is life!

---

### Post by dstew on 2008-03-28
Googling around, I see there are various drivers for that card, some work with some systems. others not. [Here is a link to a driver archive]("http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz") (tar.gz) that worked in a Debian system for one user. Maybe try this driver first.

---

### Post by prshah on 2008-03-28
> **fpvdrif6 said:**
> 
Well I can't find the CD, and prshah has not responded yet to my PM or emailed me the files.  


Sorry for the delay the files were on a customer's computer; just sent them now.

---

### Post by prshah on 2008-03-28
> **prshah said:**
> Sorry for the delay the files were on a customer's computer; just sent them now.

Ooops message bounced with "illegal attachment" for a zip...

An alternate email ID thru PM would be fine...

Or I welcome your suggestions...

> 
This report relates to a message you sent with the following header fields:

  Message-id: <47ED4A61.6030806@xxxxxxx.in>
  Date: Sat, 29 Mar 2008 01:13:29 +0530
  From: Pxxxxxxn Sxxh <xxxxxx@xxxxx>
  To: [email]fxxxxxx6@gmail.com[/email]
  Subject: WG311v3

Your message cannot be delivered to the following recipients:

  Recipient address: [email]fxxxxxx6@gmail.com[/email]
  Reason: SMTP transmission failure has occurred
  Diagnostic code: smtp;552 5.7.0 Illegal Attachment 
  Remote system: dns;gmail-smtp-in.l.google.com (mx.google.com ESMTP y11si1898913pod.9)


email addresses are x'd out.

---

### Post by prshah on 2008-03-28
> **prshah said:**
> Ooops message bounced with "illegal attachment" for a zip...



OK apparently gmail checks the CONTENTS of attached archive files and will not allow any files with sys, exe, com, dll, or such executable extensions;

so; made a zip, renamed it to a txt; then zipped and emailed that to you;

so you will have to copy the email zip; extract it somewhere; rename the .txt file to .zip; extract that to get your inf and sys files.

EDIT: OK on review, I should have PM'd this info to you rather than post it here... apologies.

---

### Post by fpvdrif6 on 2008-03-29
Hi prshah,

i received the files.  Something in the email said 4th attempt???  So much appreciated for your efforts there!

I believe I will try the ones you sent me first, and if they don't work, then I'll follow the link dstew sent second.

Once again,  when I get time :roll:  Such is life, I suppose!  I hate having to work long hours 6 days a week. :(

Cheers

Troy

---

### Post by fpvdrif6 on 2008-03-30
Hey there,

I'm posting from within Ubuntu wirelessly! ):P

This is so cool...  Now onto my graphics card drivers, and then the printer.

You guys have been most helpful, I can't thank you enough.  I owe you both one!

Cheers

Troy

---

### Post by fpvdrif6 on 2008-03-30
Okay well I'm back to bother you again (that wasn't long, was it?)

Every time I reboot, I have to input the code:
```
sudo modprobe ndiswrapper
```
To get the wireless working again.  Obviously the final part of the tutorial that is supposed to save the settings does not work in my system.  All I have to do is type in that code, I don't have to select the wireless SSID and re-type my password - it remembers that stuff...

So how can I get it to remember the lot?

Cheers

Troy

p.s. got the NVIDIA drivers installed, after this final problem is sorted, in goes the printer!

---

### Post by prshah on 2008-03-30
> **fpvdrif6 said:**
> 
Every time I reboot, I have to input the code:
```
sudo modprobe ndiswrapper
```

just add "modprobe ndiswrapper" to your /etc/rc.local file. While you are doing this, it's a good idea to read what's written in that.

---

### Post by fpvdrif6 on 2008-03-30
Hi prshah,

Is there a short tutorial on how to do this?  Or would you be able to give me some quick instructions?

Cheers

Troy

---

### Post by prshah on 2008-03-30
> **fpvdrif6 said:**
>  Or would you be able to give me some quick instructions?
Troy

EITHER
1) ```
sudo gedit /etc/modules
``` and add "ndiswrapper" to the end of the file, then save and exit

OR
2) ```
sudo gedit /etc/rc.local
``` and add "modprobe ndiswrapper" to the end of the file, then save and exit

---

### Post by fpvdrif6 on 2008-04-01
Hi prshah,

Success!

I did the first one (because you posted it first) and it worked.

Many thanks,

Troy

---

### Post by ibm450 on 2008-04-05
> **fpvdrif6 said:**
> Hi prshah,

Success!

I did the first one (because you posted it first) and it worked.

Many thanks,

Troy

I GIVE UP......this is too hard to follow, linux isnt user friendly especially when it comes to finding out simple ip address / mac address....too much mucking around...too many command lines that dont make sense at all....going back to windows, its true what they say, you get what you pay for...and i can see why linux wont dominate normal desktop OS, its slow and cra*
hello windows....

---

### Post by fpvdrif6 on 2008-04-06
> **ibm450 said:**
> I GIVE UP......this is too hard to follow, linux isnt user friendly especially when it comes to finding out simple ip address / mac address....too much mucking around...too many command lines that dont make sense at all....going back to windows, its true what they say, you get what you pay for...and i can see why linux wont dominate normal desktop OS, its slow and cra*
hello windows....

Hi there,

This post is rather random, if you ask me - why are you posting in my thread?  Do you have a specific problem that needs help?  Are you trying to get assistance to get wireless working correctly, and you have the same card as me?

As for "it's slow and .....", I completely disagree.  Linux (Ubuntu) is much faster, it boots faster to the desktop, it loads programs faster, it's lighter on resources - all this compared to Vista and XP.  Now don't get me wrong, I love Windows and I think it's a very good OS - but it's "large" and "bloated", simply because Microsoft have done their best to make it **all** things to all people.

As for linux, it seems to be the makers design it to be **common** things to all people, and any specific extras need to be added - which isn't easy for the average "Windows" user.  For everything I have achieved, I have followed tutorials, how-to guides, and then there's this thread, which I was having a little extra trouble with...  But I wanted it to work, and as a newbie to linux, I knew I'd have to explore a little.

So I'm sorry, but your little rant is meaningless at the moment.  If you would like help, I'm sure you'll be helped, and gladly, by many of the wonderful people who know what they're doing and offer their time and expertise freely.  But, don't expect it if you're just going to whine and complain.

Cheers

Troy

---

### Post by BradC78 on 2008-04-09
Hi Everyone.  I'm trying to get my WG311v3 card working also.  I followed the excellent instructions up to the point where I try to install the drivers, then it gets a little fuzzy.  I'm running Ubuntu 7.10.  THANKS!  Here's where things fall apart...

```
brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ dir
WG311v3.cat  WG311v3.INF  WG311v3.sys  WG311v3XP.sys

brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ sudo ndiswrapper -i WG311v3.INF
[sudo] password for brad:
driver wg311v3 is already installed

brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ sudo ndiswrapper -m
module configuration already contains alias directive

brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ sudo modprobe ndiswrapper

brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ 

```

---

### Post by prshah on 2008-04-09
> **BradC78 said:**
> 
brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ sudo modprobe ndiswrapper
brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/Windows2000$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
[/CODE]

Try restarting the network ```
sudo /etc/init.d/networking restart
```

Actually, better do it over again```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo /etc/init.d/networking restart
iwconfig
```

You can ignore errors, if any, for the rmmod statement.

if it doesnt work, please post output of ```
ndiswrapper -l
```

Maybe using Win2000 drivers are a problem? :-/

---

### Post by prshah on 2008-04-09
> **BradC78 said:**
> 
```
brad@ThinkCentre:~/Desktop/[color=red]WG311v3V1.0[/color]/Driver/Windows2000$ dir

```

WHOA! You're using drivers for WG311v1... do you actually_have_ v1 or maybe v2/v3?

```
lspci | grep -i wg311
``` will give the answer...

---

### Post by BradC78 on 2008-04-09
Thanks for the quick response!  I am using WG311v3.  It is the v3 driver, I think it's just version 1.0 of that driver:  **WG311v3**v1.0.  I'll try the commands you gave tonight and let you know what happens.  THANKS!

---

### Post by BradC78 on 2008-04-09
OK, I tried the code above, but got the same result.  I also tried the windowsXP driver, with the same result.  Here's the output of ndiswrapper -l
```
brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/WindowsXP$ ndiswrapper -l
wg311v3 : invalid driver!
brad@ThinkCentre:~/Desktop/WG311v3V1.0/Driver/WindowsXP$ 
```
It seems like when I try to install the driver, it says they are already installed.  Is there something I need to do in order to remove the old driver?  THANKS!

---

### Post by BradC78 on 2008-04-09
It works!!!  In case anyone else is having the same issue, here's what I did to resolve it.  I don't know which of these steps were actually helpful, but I'm listing them all just in case.

```
brad@ThinkCentre:~/Desktop/Driver$ sudo ndiswrapper -e wg311v3
brad@ThinkCentre:~/Desktop/Driver$ sudo ndiswrapper -l
brad@ThinkCentre:~/Desktop/Driver$ sudo ndiswrapper -i WG311v3.INF
installing wg311v3 ...
brad@ThinkCentre:~/Desktop/Driver$ sudo ndiswrapper -m
module configuration already contains alias directive
brad@ThinkCentre:~/Desktop/Driver$ sudo modprobe ndiswrapper
brad@ThinkCentre:~/Desktop/Driver$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
brad@ThinkCentre:~/Desktop/Driver$ sudo rmmod ndiswrapper
brad@ThinkCentre:~/Desktop/Driver$ sudo modprobe ndiswrapper
brad@ThinkCentre:~/Desktop/Driver$ sudo /etc/init.d/networking restart

```
I re-tried the iwconfig command, and HORRAY!  There is was:
```
brad@ThinkCentre:~/Desktop/Driver$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
brad@ThinkCentre:~/Desktop/Driver$ 

```
Thanks for your help prshah!  Hopefully one day I'll be able to return the favor helping another noob! \\:D/

---

### Post by BradC78 on 2008-04-09
I spoke too soon.  My wireless router is now being recognized (a step in the right direction!) but I still can't connect to the internet.  Here's the output of iwconfig...
```
brad@ThinkCentre:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11g  ESSID:"ClouserNet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:4A:0E:B7   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
brad@ThinkCentre:~$ 

```
Anybody have any suggestions?  Everything works when I plug into my router through my wired network adapter, but not through the wireless.

---

### Post by BradC78 on 2008-04-09
Yes, I realize I'm essentially having a conversation with myself.  I just realized that if I disable WEP encryption on my router, my wireless works just fine in Ubuntu.  Now I'm crawling the web trying to figure out why I can't get my WEP hex key working.  Right now my router is unencrypted, but I don't want to leave it that way forever.  I'll report back what I find.

---

### Post by prshah on 2008-04-10
> **BradC78 said:**
> Yes, I realize I'm essentially having a conversation with myself.  I just realized that if I disable WEP encryption on my router, my wireless works just fine in Ubuntu.  Now I'm crawling the web trying to figure out why I can't get my WEP hex key working.  Right now my router is unencrypted, but I don't want to leave it that way forever.  I'll report back what I find.

I have WEP 64 bit setup on Key #3; that means I have to specify in iwconfig```

iwconfig wlan0 key [3] xxxxxxxxxx
``` where the x's are the hex code

Also, for _SOME_ wireless network cards ```
iwconfig wlan0 commit
``` is required for the config change to be effective; but I have never used this yet. (In the sense that everytime I used it, I got a "feature not supported" error, but my card worked fine nevertheless).

Note that even when using XP, though it finds my network, it will NEVER connect unless I do advanced setup and specify the key index as 3.

Do you imagine this may be relevant to your problem, or am I just leading you up the garden path?

---

### Post by BradC78 on 2008-04-10
Hmmm, that didn't work as well.  Can you make sure I'm tying it in correctly?
```
brad@ThinkCentre:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brad@ThinkCentre:~$ iwconfig wlan0 key [1] bdc3201978
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not permitted.
brad@ThinkCentre:~$ 

```
I'm using key 1.  Does it make a difference if the key is typed in upper or lower case?

---

### Post by prshah on 2008-04-10
> **BradC78 said:**
> 
brad@ThinkCentre:~$ iwconfig wlan0 key [1] bdc3201978
[/CODE]
I'm using key 1.  Does it make a difference if the key is typed in upper or lower case?

forgot "sudo". and I meant the "key" part as just an example, you have to put the whole thing; like
```

sudo iwconfig wlan0 essid something channel 6 key [1] BDC3201978
sudo iwconfig wlan0 commit

```

But all said and done it is strange you are having such problems; for me, except for the key issue mentioned above, all works fine.

The second line may give an error that you can ignore.

---

### Post by BradC78 on 2008-04-10
Thanks Prshah.  I tried the commands above, and it actually locked up my system.  I could no longer type command lines, or open a new window.  That makes me think there might be something wrong with my WG311v3 driver that is causing trouble trying to use the encryption.  For now, I'll turn down the signal strength on my wireless router until I have time to investigate further.

Thanks for all your help getting my wireless up and running.  I can tell already I'm going to love Ubuntu.  I just need to get familiar with the Linux commands.  THANKS! :)

---

### Post by Noctemii on 2008-04-12
> **BradC78 said:**
> Thanks Prshah.  I tried the commands above, and it actually locked up my system.  I could no longer type command lines, or open a new window.  That makes me think there might be something wrong with my WG311v3 driver that is causing trouble trying to use the encryption.  For now, I'll turn down the signal strength on my wireless router until I have time to investigate further.

Thanks for all your help getting my wireless up and running.  I can tell already I'm going to love Ubuntu.  I just need to get familiar with the Linux commands.  THANKS! :)

BradC78,

Here's a link to the original wiki that I use on my own system.  I have a Netgear WG311v3 in my desktop computer (AMD Athlon64 3500+, 1GB ram, nVidia 6600GT video card) that dual boots Windows XP and Ubuntu 7.10.  With this guide, my card works flawlessly (WEP works, WPA works, and all with NetworkManager.  No fancy iwconfig work needed here).

[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

Hope that this works out for ya, and good luck on your ubuntu adventures :)

---

### Post by jezza323 on 2008-05-19
I am having some trouble with my WG311v3 atm.

Was working okish with my Netgear DG834G modem/router, but was dropping the connection every couple of days, the only way to reconnect was to disable the network adapter and re-enable.

However the modem was also dropping ADSL connection frequently, so i got myself a nice Billion 7404VGP. set it up last night, no problems. got my XP laptop and XP box up and onto the network/internet straight away (i just used the same ssid/key so shouldnt have to change any settings). but now the ubuntu box wont connect at all?

i can scan the network, but cant connect to it.

any ideas?

---

### Post by tombot on 2008-05-25
I too am having a WEP problem with this type of card.  I am using a Netgear WG311T with the madwifi driver.

NM scans the local networks and finds mine correctly, I choose to connect and it will then correctly prompt for the WEP key.  I enter the key and after a minute it will ask again and again.

The key is correct, and if I use my belkin USB adaptor it connects instantly on WEP, thus I can rule out a NM problem.

I have used the Netgear adaptor successfully on aircrack-ng and managed to decrypt my own WEP key, so I know the adaptor is functioning ok.

What should I do?  I want to keep using the madwifi driver so that I can use aircrack-ng.

---

### Post by jezza323 on 2008-05-25
just thought id let u know i got mine working.

i needed to specify that the key was open in the connection command

sudo iwconfig essid "XXX" key open XXXXX

think that was the right command...

---

