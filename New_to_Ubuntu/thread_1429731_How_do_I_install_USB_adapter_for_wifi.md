---
title: "How do I install USB adapter for wifi ?"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by Chuck_N on 2010-03-14
I feel like a mosquito at a nudist camp......
I know what I want to do, but I don't know where to begin.

I have a WIFI network in my home, working fine. My laptop has no problem with it. The Compaq desktop I'm building up is presently hooked up directly to the router, working fine. But I want to use a 3com 3CRSHEW696 adapter instead, so I can relocate the desktop. 

I've done some searching, some reading, so attempting, but so far no success. I'm not a novice to OSes or DOS or computers or programming, just to Ubuntu 9.10 Koala and Unix, entirely.

Right now I'm operating on 256 meg, but plan to kick that up in the near future, to a gig or more.

Someone please hold me by the hand and walk me through....

Thanks, Chuck

---

### Post by howefield on 2010-03-14
Try opening a terminal and typing

```
sudo apt-get update
```

Then go to System > Administration > Hardware drivers. With the wireless adapter connected to your computer , are there drivers in there that you can install

---

### Post by Chuck_N on 2010-03-14
ummmmm.... I hate to ask, but......
    How do I open a terminal ??

---

### Post by rbc on 2010-03-14
System --> Accessories --> Terminal
or I believe the default keyboard shortcut is Alt + T
By the way, the "sudo" in that command means that you are attempting to do something as root. You will be prompted for your password. When you type it, you will not see the input

---

### Post by howefield on 2010-03-14
> **rbc said:**
> I believe the default keyboard shortcut is Alt + T

Almost.. Ctrl + Alt + T

---

### Post by Chuck_N on 2010-03-14
I did      sudo ...update
got a few dozen lines of info
then plugged in the adapter
then selected  system/administrative/hardware and screen went black
and stayed black
I think it was due to plugging in the adapter at that point
I am restarting with the adapter attached, and will await instructions......
remember, I now have adapter attached AND straight-cable to the router to the web

---

### Post by 2hot6ft2 on 2010-03-14
> **Chuck_N said:**
> I did      sudo ...update
got a few dozen lines of info
then plugged in the adapter
then selected  system/administrative/hardware and screen went black
and stayed black
I think it was due to plugging in the adapter at that point
I am restarting with the adapter attached, and will await instructions......
remember, I now have adapter attached AND straight-cable to the router to the web
Interesting.
My terminal is in
Applications > Accessories > Terminal
and Ctrl+Alt+T doesn't do anything.

Anyway. With the computer running and you're on the desktop, plug the usb wifi adapter in or leave it plugged in.
Then open a terminal.
Applications > Accessories > Terminal
use this in it
```
sudo apt-get update
```
Type in your password when prompted (it wont be displayed just type it in and hit enter).
When it finishes then go to
System > Administration > Hardware Drivers
and see if a driver is shown for your adapter.
If one is shown in the top box select it and click on Activate at the bottom.
It will download and install it for you.

You may want to run
```
lsusb
```
That's LSUSB in lower case in a terminal and post the results so we can see what chipset the adapter has. Put it in a Code box using the # at the top of the post box with the info highlighted to keep the formatting.

---

### Post by Chuck_N on 2010-03-14
seems like every time I boot with the adapter attached
or plug in the adapter after booted,
the computer freezes; I can move the mouse pointer
but cannot select anything.  Only can power down.
I am now running after booting without the adapter
and not sure what to do next.....

I think I'll send this first, then plug in the adapter and see if all freezes again.

---

### Post by Chuck_N on 2010-03-14
multiple times I've restarted the computer, and used it a bit
only to have it freeze or go to black screen
I'm on it now and will send this message now

---

### Post by Chuck_N on 2010-03-14
I'll continue to send a few messages, to see if the system is stable

---

### Post by Chuck_N on 2010-03-14
a few minutes ago, I flipped over to Mapquest
while I had the adapter plugged in also,
and tried to request a routing
each time I hit SEND to get a computation
the program blew up
I wonder if the adapter is interfering with the cord connection to the router?

---

### Post by Chuck_N on 2010-03-14
I have my laptop running, and can send/receive  messages from there if necessary.


Seems to be holding up okay now.

When booting up there are those half-dozen system options to choose from
I chose the first one this time. Usually choose the fifth one.

okay let's assume I'm up and running okay now, without the adapter plugged in....

should I go back now and try to pick up where I left off....?

---

### Post by Chuck_N on 2010-03-14
not sure yet if I can type messages from my laptop to here
at the same time as I'm using my desktop here.
I'm going to try it now

---

### Post by Chuck_N on 2010-03-14
I logged in on my laptop.  Could only see 3 messages, at 2, 7, and 8 hours ago.
Maybe that's not a good idea.  I logged out there.

---

### Post by Chuck_N on 2010-03-14
I'll go back now to step 7 from  2hot6ft2
and try to pick up from there...

---

### Post by Chuck_N on 2010-03-15
Okay, this will be slow but I need to chronicle what's happening.  I've opened a WORD file and I'll record each step here, and save the file.  Then I should have something ready to present to y'all.
 

 
[LIST=1]
[*]With the computer running and 	you're on the desktop, plug the usb wifi adapter in or leave it 	plugged in.
 	 	okay here goes, I'm plugging in the 	adapter. Reminder: the computer is also already plugged in to the 	modem.
 	Try #1 froze right away. I was not at 	desktop however. Will try again.
 	Try again.  Sat at desktop okay with 	adapter plugged in. Opened menus at the top with no problem. Then I 	tried to open Writer to update this page, and immediately went to 	black screen. Restarted;  copied the directions and sent them via 	email to my laptop so I can avoid opening up Writer here.  	
 	Went to desktop. Plugged in adapter. 	Pulled down menus for a minute. As soon as I selected Terminal,  	black screen.  All done.
 	Rebooted without adapter. Got to 	desktop. Mouse pointer and clicking did nothing.
 	Rebooted without adapter. Updated this 	document to copy and send to Forum.  Started up FireFox and came to forum. Pasted document into Quick Reply.  Firefox DISAPPEARED.   
 Not to be found.  Reopened Firefox. Pasted this here now. Sending now .

[/LIST]

---

### Post by 2hot6ft2 on 2010-03-15
I was hoping that someone would jump in with a solution but apparently not. So that you're not left hanging waiting on an answer that may not come since people hate to be the bearer of bad news (including myself). I'll go ahead and tell you what I've found and my opinion, so for what it's worth here it is.

This isn't going to be what you want to hear. 

I did some searching for your adapter and it didn't look good. There were a lot of results that were saying it causes system freezes and the newest driver I could find for it for linux was from back in 2006 [here]("http://ftp.kaist.ac.kr/ubuntu/pool/multiverse/a/at76c503a/at76c503a-source_0.12.beta23-4_all.deb") which may not even install on a current system. It looks like that adapter was made between 2002 and 2004 from what I could gather on it.

Hate to say it but you may want to consider just getting a different adapter. It looks like it has a Atmel at76c503a chipset.
Here are the results from the searches:
[Google search for ubuntu AT76C503A]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&q=ubuntu+AT76C503A&start=10&sa=N")

[Home of the OpenSource Linux Driver for Atmel AT76C5XXx-based Wireless Devices]("http://atmelwlandriver.sourceforge.net/news.html")

[And here's the google search for the 3CRSHEW696 chipset]("http://www.google.com/search?q=3CRSHEW696+chipset&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a")

If someone can find a better answer then by all means jump in here.

I really hate to hit the Submit Reply button on this one. I wish I had better news for you.

---

### Post by Chuck_N on 2010-03-15
I guess we agree on the adapter.  Here is what I recorded:


still running..... closed firefox and writer.   typing notes now in wordpad on my desktop
opened menus at the top and ran various selections. all seems fine.
plugged in adapter.   as soon as I clicked on the menu...black screen.
I think maybe this adapter cannot be used on this computer?  no?

---

### Post by Chuck_N on 2010-03-15
not a big deal.  Now, should I try my Hawking  HWU54D, which works on my laptop,
or where can I find a list of adapters to try, USB or internal, from which I can order an adapter?

---

### Post by 2hot6ft2 on 2010-03-15
> **Chuck_N said:**
> not a big deal.  Now, should I try my Hawking  HWU54D, which works on my laptop,
or where can I find a list of adapters to try, USB or internal, from which I can order an adapter?
I'll look for the chipset for that adapter and see what I can find out. If you can post the results of
```
lsusb
```
That's a lower case LSUSB
in a terminal
Applications > Accessories > Terminal
with it plugged it it will help to make sure of exactly which chipset it has.
Manufacturers have a nasty habit of using more than 1 chipset in any 1 model, I guess it's which ever one they can get cheapest that day.

Meanwhile here's some other options and info.

Most wifi adapters in the stores have Broadcom chipsets which can be made to work following this guide.
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

That and RaLink which is getting better.

RealTek RTL8187L chipset adapters work real good out of the box. Just plug it in and it works. Unfortunately they're virtually impossible to find in stores but they are plentiful and fairly cheap on eBay. You can find them by searching for either of these there:
[GSky]("http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1311&_nkw=gsky&_sacat=See-All-Categories")
[alfa awus036h]("http://shop.ebay.com/i.html?_nkw=alfa+awus036h&_sacat=0&_odkw=alfa+AWUS036H&_osacat=0&_trksid=p3286.c0.m270.l1311")

They both use the RealTek RTL8187L chipset and 500mW is plenty no need paying for the 1000mW model as it's really not twice as strong. They have been independently tested by users on other forums.

---

### Post by Chuck_N on 2010-03-15
whoops, past my bedtime.  I'll get back on this tomorrow evening.

---

### Post by Chuck_N on 2010-03-15
cancel that trip to bed.  I'll work on your post.

---

### Post by 2hot6ft2 on 2010-03-15
LOL, I'm about ready to call it a Night myself so don't feel bad if you want to pick it up in the Morning.

---

### Post by Chuck_N on 2010-03-15
here 'tis
chuck@chuck-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chuck@chuck-desktop:~$ ^C

oh, that's fun     SHIFT-ctrl-C to copy when in Terminal

---

### Post by 2hot6ft2 on 2010-03-15
> **Chuck_N said:**
> here 'tis
chuck@chuck-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chuck@chuck-desktop:~$ ^C

oh, that's fun     SHIFT-ctrl-C to copy when in Terminal
It doesn't even list it as being recognized
That shows the mouse, card reader and hubs but no wifi adapter.
And the first post from searching for the chipset in google didn't look good either. Take a look at the first result I click on it's pretty short and to the point
[http://osdir.com/ml/linux-wlan.user/2004-05/msg00071.html](http://osdir.com/ml/linux-wlan.user/2004-05/msg00071.html)

I'll keep looking in the morning though.

[Here's the google search for HWU54D chipset]("http://www.google.com/search?hl=en&client=firefox-a&hs=9zh&rls=com.ubuntu:en-US:official&q=HWU54D+chipset&start=10&sa=N")

---

### Post by Chuck_N on 2010-03-15
thanks 6ft2, I will eBay shop tomorrow and get one of those. Should I get USB or would an internal be just as good to get?

GOOD NIGHT !!

---

### Post by 2hot6ft2 on 2010-03-15
> **Chuck_N said:**
> thanks 6ft2, I will eBay shop tomorrow and get one of those. Should I get USB or would an internal be just as good to get?

GOOD NIGHT !!
You may as well get a usb adapter that way you can use it with more than just 1 machine easily. I have a GSky and it works great.

Good Night. Oh yeah and welcome

---

### Post by walt.smith1960 on 2010-03-15
TrendNet UB424 

[http://www.amazon.com/TRENDnet-54Mbps-Wireless-Adapter-TEW-424UB/dp/B000636JD8/ref=sr_1_7?ie=UTF8&s=electronics&qid=1268638787&sr=1-7](http://www.amazon.com/TRENDnet-54Mbps-Wireless-Adapter-TEW-424UB/dp/B000636JD8/ref=sr_1_7?ie=UTF8&s=electronics&qid=1268638787&sr=1-7)

Uses the RealTek 8187b chipset on the version 3.x. There was a version 2.x  which was not plug & play-I think it used an SIS chip or something like that. You won't know which version you're getting when you order it. The 2.x version is have is from several years ago so I suspect most stock by now is 3.x

---

### Post by 2hot6ft2 on 2010-03-15
> **walt.smith1960 said:**
> TrendNet UB424 

[http://www.amazon.com/TRENDnet-54Mbps-Wireless-Adapter-TEW-424UB/dp/B000636JD8/ref=sr_1_7?ie=UTF8&s=electronics&qid=1268638787&sr=1-7](http://www.amazon.com/TRENDnet-54Mbps-Wireless-Adapter-TEW-424UB/dp/B000636JD8/ref=sr_1_7?ie=UTF8&s=electronics&qid=1268638787&sr=1-7)

Uses the RealTek 8187b chipset on the version 3.x. There was a version 2.x  which was not plug & play-I think it used an SIS chip or something like that. You won't know which version you're getting when you order it. The 2.x version is have is from several years ago so I suspect most stock by now is 3.x
The RTL8187B works out of the box as well but the L is a better chipset.

The Hawking HWU54D doesn't look good either. After a bit of searching fruitlessly I checked the [Ubuntu WifiDocsWirelessCardsSupported page]("http://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") and it's not listed same as the other one.

Also when looking on eBay at the GSky and ALFA usb wifi adapters **if** you come across the ones that are N band. I have seen where some got them working while others didn't it uses a different chipset and it seems to depend on the version # of the adapter. **The ones that are G band are the ones with the RTL8187L chipset**.

The N band ones shouldn't show up in the search links I gave but just in case one does now you know. The GSky is like a knockoff of the ALFA and is a little cheaper.

---

### Post by Chuck_N on 2010-03-15
okay 6ft2,  I am back home and have looked through the adapters at ebay.  Looks like$20 or so from various places which accept paypal only. I'll have to work through getting my accounts active again; haven't used them in years.  Thanks so much for all the help.
-Chuck

---

### Post by 2hot6ft2 on 2010-03-15
> **Chuck_N said:**
> okay 6ft2,  I am back home and have looked through the adapters at ebay.  Looks like$20 or so from various places which accept paypal only. I'll have to work through getting my accounts active again; haven't used them in years.  Thanks so much for all the help.
-Chuck
Unless something has changed you can pay by credit card thru PayPal. But yeah $20 shipped is about right.

---

### Post by kaspin on 2010-06-17
[FONT="Comic Sans MS"][SIZE="2"][COLOR="RoyalBlue"]Not sure if I should start a new thread for this......
I'm trying to get my Trendnet TEW 424UB to work with Ubuntu 10.04.
Based on info in various forums, I discovered that it is recognised as Bus001, Device 005 ID 0457:0163. But, as I have the original installation CD containing the drivers for various flavours of  Winblows, I tried installing the WinXP driver (SIS163u.INF) using ndiswrapper (sudo ndisgtk) and got the message "SIS163u invalid driver". I retried, using the Win2000 driver (same name) only to be told "driver is already installed".
Nothing happens when I connect the wifi adapter.
If I look at System/Administration/hardware drivers, I'm told "No proprietary drivers are in use on this system"
Can anybody nudge me in the right direction, please?
Thanks in advance,  kaspin[/COLOR][/SIZE][/FONT]

---

### Post by Blackcamaro8 on 2010-06-17
Kaspin, have you performed the following command?:
> sudo modprobe ndiswrapperYou have to tell ndiswrapper to add the device to the network manager. 
I had this same problem using Ubuntu 9.04 on an old Dell laptop that doesn't have an integrated wireless card. Took me forever to figure out that I hadn't added it to Modprobe!

Good luck! :biggrin:

**EDIT:**

Also, yes. You should've technically started a new thread for this, but that's all well and good. :)

---

### Post by kaspin on 2010-06-19
[FONT="Comic Sans MS"][COLOR="RoyalBlue"][SIZE="2"]Hi Blackcamaro8,

Many thanks for replying so quickly. Sorry I didn't get back sooner (nothing to do with world cup football, of course...)
I tried "sudo modprobe ndiswrapper" both after and before the "sudo ndisgtk" instruction, but my usb wifi key is still not recognised.

Along the way, the terminal spewed out the following messages, which I don't understand:

(nm-connection-editor:1704): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

** (nm-connection-editor:1704): WARNING **: Invalid setting Wireless: ssid
module configuration information is stored in /etc/modprobe.d/ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

I looked in /etc/modprobe.d/ndiswrapper and found just this line:
alias usb:v0457p0163d*dc*dsc*dp*ic*isc*ip* ndiswrapper

It seems to refer to the Trednet driver, because in the WinXP .inf file it mentions "VID_0457&PID_0163,%01%"

Incidentally, looking at "modprobe" in the Wiki, it seems that modprobe is distributed as part of the software package "module-init-tools", which was already installed (by default, I think) in Ubuntu 10.04. 

So, despite your help, I'm still stuck. I'll carry on trying to solve the problem, and if I do, I'll post it here.

Thanks again,   kaspin):P [/SIZE][/COLOR][/FONT]

---

### Post by kaspin on 2010-06-20
[FONT="Comic Sans MS"][SIZE="2"][COLOR="RoyalBlue"]Hello again Blackcamaro8 (and anyone else who's interested),

I had a look at some other (older) forums and found (from [http://ubuntuforums.org/showthread.php?t=284683](http://ubuntuforums.org/showthread.php?t=284683)) that the WinXP driver downloaded from the Trendnet website works. It's a .zip file, so you right click on it to uncompress. It was well over 20KB in size whereas the version on my installation CD was under 14 KB.
I then deleted the old driver (.INF file) from the Windows XP directory which I had previously copied on to a USB stick from the TrendNet installation CD, and replaced it with the new one. It may not be necessary to put the .INF file in this directory but I got the following message at one point in the terminal -

"couldn't find "sis163u.sys" in "/media/A4DF-EB84"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/media/A4DF-EB84" -
installation may be incomplete"

 - so I guess that ndisgtk needs to be pointed to where the .INF, .sys and .cat files are together.

In the end it was so simple - type "sudo ndisgtk" (without quotes) in the terminal, select "install new driver", then navigate to the directory where the .INF etc. files are. Sorted.

Sorry if the above is long-winded, but the secret seems to be to download the latest available driver for WinXP from the TrendNet site before any of the suggested solutions can work....

Thank you again for your technical (and moral) support.=D>
kaspin
[/COLOR][/SIZE][/FONT]

---

