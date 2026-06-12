---
title: "Yet another Linux-Newbie with a wireless problem"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by iago4096 on 2007-12-31
Yes, well, another one.

But please, do not think of me as one more of *those *types. No, I don't think Linux is meant to do everything for me. I know, I have to make a few things as well, *and *I am prepared to do so.

I have been fooling around with a few distros (knoppix first, a little dsl, then debian) on my

[B]Toshiba Satellite 2060CDS
K6-2-3D 333MHz
160MB RAM
4 GB HD[/B]

until I installed Xubuntu (7.10) and I am very happy with it. The Laptop initially ran Win98, then I put WinXP on it, but it is just too slow for all this. I am living in student accomodation now and we have broadband wireless Internet. I purchased a 

[B]Belkin Wireless G Notebook Card
F5D7010 (Ver.7000uk)
[/B]
which works well under WinXP.

Xubuntu, however, shows me the cold shoulder. (no PCMCIA, no USB, no TERMINAL?!?)

I read around a lot and found the "depth=24" bug, so now I have a TERMINAL (yay!)

I fixed a BIOS IRQ-Problem, which apparently gave me USB under Xubuntu (good!)

Now to my card...

What I am trying to do is use NDISWRAPPER (yes, I know, many people don't like it) to load my original WinXP-driver (the same one I use on the other OS)

**lspcmcia **says:
```
Socket 0 Bridge:        [yenta cardbus]         (bus ID: 0000:00:13.0)
  CardBus card -- see "lspci" for more information
Socket 1 Bridge:        [yenta cardbus]         (bus ID: 0000:00:13.1)

```

**lspci** answers that:
```
00:13.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev07)
00:13.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev07)
01:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)

```

**ndiswrapper -l **finally tells me:
```

blkwgnv7 : driver installed
        device (1799:701F) present
```

Everything looks peachy up to here, but as I try **modprobe ndiswrapper**, my box tells me
```
Segmentation fault
```

hm?

Where does this come from? And how will it go away?

Some help please! Come on, guys, save another soul from the vicious fangs of Mr. Gates and I shall spread the good news and continue to make the world a brighter, fuzzier and more colourful place!

**Iago4096**

---

### Post by kegobeer on 2007-12-31
Take a look at this:

[http://ubuntuforums.org/archive/index.php/t-207614.html](http://ubuntuforums.org/archive/index.php/t-207614.html)

Does that help?

---

### Post by iago4096 on 2008-01-01
What?

That thread is over a year old!?! 
Xubuntu 7.10 comes natively with a ndiswrapper 1.49 and your answer is to update to version 1.19?
Thank you, but I was looking for a leeetle more insight than that.

Anybody else?

---

### Post by tcdrewiv on 2008-01-01
Had similar problem with Belkin pre-N card

For a start you can look at the ndiswrapper site for a list of compatable versions with your specific card.  [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/")


The list will show what version of ndiswrapper has worked for others and which windows driver to use.
You may find that a more recent version may work also but it will be trial and error.

Someone with your specific card may be able to tell you what version of ndiswrapper and which windows driver works best.

Note:For me I had to remove the ndiswrapper version that was installed and install an earlier version to get it to work and use a netgear and not belkin windows driver.  Also my card under windows only supported wep encryption.  With ndiswrapper it now supports WPA.

---

### Post by kegobeer on 2008-01-01
> **iago4096 said:**
> What?

That thread is over a year old!?! 
Xubuntu 7.10 comes natively with a ndiswrapper 1.49 and your answer is to update to version 1.19?
Thank you, but I was looking for a leeetle more insight than that.

Anybody else?

Perhaps you should ignore the version and read the thread.  Regardless of the version, had you understood the thread you would've tried to remove ndiswrapper and then download the latest version.

You might also try searching the fourms and the 'net for your error message.  How do you think I found that thread?

---

### Post by iago4096 on 2008-01-01
@keg o' beer: I did read net and forums, and I have also read the forum you sent me too. If what you meant was "remove ndiswrapper and install the latest version", then you might well have said something like "remove ndiswrapper and install the latest version", right? No offence.

According to NDISwrapper.sourceforge.net the only changes from Ver 1.49 to 1.51 were:

```
Fixed an smp issue that may cause ndiswrapper to stop transmitting packets after a while (noticed with Marvell Pre-N USB driver) 
Added support for 2.6.24-rcX kernels 
Fixed issue with changing mac address (with 'ifconfig hw ether ') - its broken since 1.45-rc2. Now one can also edit appropriate .conf file to set the NetworkAddress setting to whatever mac address should be used by the driver (e.g., NetworkAddress|0123456789ab) 
Fixed kernel crash observed with mrv8335 in ad-hoc mode 
``` 

none of which applies here. Really, I would lie to actually get to the core of this problem and not "trial and error" around.

@tcdrewif: The list of supported cards lists a number of different Belkin F5D7010, not specifically mine, though, apparently I will have to "trial and error".

Thank you guys all the same.

---

### Post by iago4096 on 2008-01-01
Just wanted to keep the forum informed, that I am now on the internet!

What it took was a good deal of trial and error, as well as ndiswrapper, I am afraid. 

I simply had to download a driver from Realtek. Why the Belkin driver for my card I used under XP didn't work and why the Realtek one does is beyond my scope.

Realtek also provides a linux driver, but I was sadly not able to install that.

Now the only thing left is getting through the PPTP setup to enter my university's VPN.

We shall see.

---

### Post by kevdog on 2008-01-01
Whats the link for the Realtek driver?

---

### Post by iago4096 on 2008-01-02
It was the Win98 one that did it for me in the end, but please try...

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L")

to clarify this:

I downloaded the one labelled "Windows ME driver", but that archive comes with an ME and a 98 driver.

---

### Post by kevdog on 2008-01-02
Ok, thanks, I didnt know you went the Win98 driver route.  A lot of people have reported success with the win98 driver, however it doesnt work for all people.

---

