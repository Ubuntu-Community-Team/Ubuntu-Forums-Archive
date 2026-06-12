---
title: "[SOLVED] ndiswrapper and rtl8185"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by samexner on 2007-07-03
I have a rtl8185 pcmcia card. i get it set up with ndiswrapper by using ndiswrapper -i *.inf and then modprobe ndiswrapper
i enabled roaming for wlan0 and the connectivity percentage gets to 96% but It's not connected at all, and I can't browse the web freely.
can anyone help?

---

### Post by kevdog on 2007-07-03
What driver did you use?  I read in another forum that someone had luck with the Win98 rather than Winxp driver!

Could you also post the following:
lshw -C network

Thanks

---

### Post by samexner on 2007-07-03
i used the one on the forum. ill try out the win98 driver tonight that came with the CD and post back in the morning.

night!
samexner

---

### Post by samexner on 2007-07-04
> **samexner said:**
> i used the one on the forum. ill try out the win98 driver tonight that came with the CD and post back in the morning.

night!
samexner

oops... i mean on realtek's website
](*,)
let me go do what you said now...

---

### Post by samexner on 2007-07-04
errrgh...
i broke ndiswrapper
oops.
it says it cant find some dir in the kernel headers and i keep reinstalling it
well...
ill do a reinstall later, after i try out mandriva (i'm distro-hoppin' for my laptop for now) because it works fine with pclinuxos, but pclinuxos is sloowwwwwwww

ill switch back to ubuntu if i dont succeed with mandriva

thanks

---

### Post by samexner on 2007-07-26
woo hoo! solved!
if i use the win98 driver, it works fine, with no problems at all
hope this helps people.

---

### Post by JustBrowsing on 2007-07-30
> **samexner said:**
> woo hoo! solved!
if i use the win98 driver, it works fine, with no problems at all
hope this helps people.
Thank you for your post ... it has helped me out tremendously with this internet wifi card. With Fiesty, as we all know RTL8185's built in driver is black listed, while you can un-"blacklist" the file, there are problems connecting for me. And you have to add a "x" or another symbol for the wireless card to work.

Using NDiswrapper and the Windows 98 Drivers available from Realtek's website does work, you may have to reboot a few times for Ubuntu to see it, eventually it should show up. Not only that, by doing it this way, it unlocked WPA/WPA2 security as well, which is a major pain in the rear.

Also, wireless signal strength is finally correct. It shows the correct 90-50% percentage for the wifi.

Thank you so much for your post! Maybe I can actually try to get sound working on this machine. wooo hoo -- I've missed tinkering with Ubuntu since I've bought this new laptop back in february.

---

### Post by teajay on 2007-08-03
Hello.

What do you (JustBrowsing) mean by the Win98 driver?  When I go to RealTeks website ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)) and download the driver under "Windows XP/2K/ME/98SE driver" it downloads a ZIP folder that contains only one type of *.inf file i.e. it seems as though the driver covers all OS's and will self detect the version of windows that is running.  How can I get this Win98 specific driver you speak of?

I have an RTL8185 and would also appreciate if you could point me to a step-by-step way to install NDISwrapper as the way mentioned on the NDISwrapper website doesn't work for me.

Thanks!

---

### Post by kevdog on 2007-08-03
teajay 

Im not sure what you are talking about, I downloaded the file your referenced from your link and there are separate folders for winxp,win2000,winme,winxp,win98,winX86,winx64,x64.  I would assume you simply extract the inf, cat and sys files in the win98 folder.

---

### Post by teajay on 2007-08-03
I found the Win98 as a subfolder in the complete package (including UI etc) downloadable from their website.  I'm just restarting Ubuntu right now after having installing NDISwrapper and the Win98 driver...

...First attempt to manually set wireless resulted in freeze/crash...

...Second attempt - hard reset required because Ubuntu froze during startup...

...Third attempt - another crash during startup - another hard reset necessary :( ...

...Fourth attempt - freeze during start-up...

I'm going to give up for the meantime.  I've tried Linux a few times over the years but never seem to have much luck.

I don't know what to do now, maybe the next version of Ubuntu will work with the card.

---

### Post by climatewarrior on 2007-08-13
The Win 98 driver also worked perfectly with me with ndiswrapper. Im using feisty fawn 7.04

---

### Post by climatewarrior on 2007-11-01
Just in case somebody need it here's the .Inf file for the windows 98 driver for the rtl8185.

Just remove the .txt extension from the end.

Bye

---

### Post by barnacleboy on 2008-03-02
Just posting to say thanks to climatewarrior and to bump this thread as this win98 driver is currently unavailable at Realtek's website.

---

### Post by ockron on 2008-03-23
Hi all.

I just changed my XP into a dual boot with Ubuntu Feisty and have problems getting my WLan to work. (realtek rtl8185 chipset)

Thanx for this post as I will try my very best to make it work!!

I noticed on the reaktek website a "Linux driver for kernel 2.6.X" posted on 2007/4/16 - has anyone used it?

([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true))

---

### Post by coolbrook on 2008-03-23
> **barnacleboy said:**
> Just posting to say thanks to climatewarrior and to bump this thread as this win98 driver is currently unavailable at Realtek's website.

The Windows 98 driver is indeed currently [available](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true).  It's the same as the Windows ME.

---

### Post by Bob Dduc on 2008-03-24
> **ockron said:**
> Hi all.

I just changed my XP into a dual boot with Ubuntu Feisty and have problems getting my WLan to work. (realtek rtl8185 chipset)

Thanx for this post as I will try my very best to make it work!!

I noticed on the reaktek website a "Linux driver for kernel 2.6.X" posted on 2007/4/16 - has anyone used it?

([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true))
Tried it, no joy!
Used ndiswrapper and win 98 drivers, works like the kats meow!

---

