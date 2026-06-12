---
title: "Help me about resolution"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by jiantguk on 2011-04-11
hi, I'm a new ubuntu user

but I had a little trouble. is about my resolution, its just 800 x 600 :)

my laptop is axioo mnc 152

please help me, I'm just newbie...

thanks before...:D

---

### Post by Boatus on 2011-04-11
Don't get me wrong I a totally new too but when I rebooted (i'm using a duel booted Macbook 4,1 that uses GRUB to select which OS it boots in) some times the resolutions looks 1280x800 and others it seems to stick at 800x600!

I've got no idea why. Have you checked to see if you're starting it in the right mode? When I boot with GRUB it asks if I want to boot in normal modes or in recovery modes. I've not tried recovery mode but I presume it would reduce the resolution like windows does!

Give that a go,

Boatus

---

### Post by seawolf167 on 2011-04-11
Check two things:

[LIST=1]
[*]Install any available hardware drivers (System -> Administration -> Hardware Drivers), then reboot if you installed a graphics driver
[*]Go to System -> Preferences -> Monitors and change your resolution to the max supported by your screen
[/LIST]

---

### Post by ahkond on 2011-04-11
This morning my screen resolution is far lower than it was yesterday.  I did not install or alter anything yesterday, but today I am only allowed to use 1152x864 and all my desktop icons are huge.  I have checked my drivers and I have attempted to use the system/preferences/monitors tool, and higher resolutions are not available.  

I did not change anything and now the system is not behaving like it did yesterday.  Hooray.

---

### Post by seawolf167 on 2011-04-11
Take a look at [this thread ]("http://ubuntuforums.org/showthread.php?p=8595940")to manually change your resolution.

---

### Post by ahkond on 2011-04-11
> **seawolf167 said:**
> Take a look at [this thread ]("http://ubuntuforums.org/showthread.php?p=8595940")to manually change your resolution.

None of those solutions helped me.

---

### Post by KL_72_TR on 2011-04-11
Take a look at these to. I know there is a lot of using the Command Line (if you don't feel confident than don't use it) but maybe you can find something.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)
[http://ubuntuforums.org/showpost.php?p=129379](http://ubuntuforums.org/showpost.php?p=129379)

---

### Post by ahkond on 2011-04-11
> **KL_72_TR said:**
> Take a look at these to. I know there is a lot of using the Command Line (if you don't feel confident than don't use it) but maybe you can find something.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)
[http://ubuntuforums.org/showpost.php?p=129379](http://ubuntuforums.org/showpost.php?p=129379)


Thanks.  Did not help.  Much of what's in those threads I cannot understand.  The simple fixes (like running the automatic reconfiguration command for xserver) do not fix the problem.  Many of the solutions rely on external tools, and the links are broken.

---

### Post by Blasphemist on 2011-04-11
This may well be a good challenge for you. Your pc has a SiS M672 chipset with SiS Mirage 3 graphic engine. You can do a search of all forums here and see many threads on that. To make it potentially a bit more challenging, most all I say seem to have been related to the M671 version and I can't tell if that would work for you or not.

This link MAY help you to install a better driver;)
[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

You aren't the first with this issue. The following thread ends with a post 5 days ago from DrSeeman who is a new user. He seems to have found a workable solution. He refers to a post that is 71 pages long that he read all of so he may not be a mere mortal. Yet, he has been through it so there is hope.
[http://ubuntuforums.org/showthread.php?t=1548547&page=11&highlight=SiS+672](http://ubuntuforums.org/showthread.php?t=1548547&page=11&highlight=SiS+672)

---

### Post by ahkond on 2011-04-11
> **Blasphemist said:**
> This may well be a good challenge for you. Your pc has a SiS M672 chipset with SiS Mirage 3 graphic engine. You can do a search of all forums here and see many threads on that. To make it potentially a bit more challenging, most all I say seem to have been related to the M671 version and I can't tell if that would work for you or not.


What makes you say I have an M672 chipset and SiS Mirage 3?  I don't even know whether that's true.  I do not know how to even find out what kind of chipset and graphic engine I have ...

---

### Post by Blasphemist on 2011-04-11
Oh, sorry bout that. I just googled the pc you said you have. I got an indonesian site that had to be translated but this is what it showed.

spec: 

Processor: Intel Core ™ 2 Duo Processor T6400 (2.00GHz, 800MHz FSB, 2MB L2 Cache) 

Chipset: SiS M672 + SiS968 Chipset 

Memory: 2x 200 Pin SO-DIMM sockets Support DDR2 - 533/667/800 MHz (Known As PC4200/PC5300/PC6400) 1024MB DDR2 RAM - Expandable up to 4GB (256/512/1024/2048 MB DDR2 Module) 

Hard Drive: 250GB SATA 

Optical Drive: DVD Writer Dual Drive 1x PATA / SATA 

Display: 14.1 "WXGA TFT 

Display Max Resolution: (1280 x 800) 

Display Technology: SiS Mirage 3 + up to 256MB Support Microsoft 
DirectX 9.0 

Input Device: Winkey Keyboard Built-in Touch Pad (Scroll 
Functionally Included) 

Audio: High Definition Audio (HDA) 3D Stereo Enhanced Sound System S / PDIF Digital Output 

Camera: 1.3 MP 

Ethernet: 10/100 Mb Base-T Ethernet 

Modem: 56K Modem with v9.0 & V92 Complaint 

WiFi: 802.11 b / g Wireless LAN MiniCard 

Card Reader: 7 in 1 Card Reader support (MMC / RSMMC / SD / MiniSD / MS / MS Pro / MS Duo) 

I / O Ports: 3x USB 2.0 Ports (USB 1.1 Compatible). 1x External CRT. 1x Headphone Jack. 1xMicrophone Jack 1x Internal Microphone. 1x S / PDIF 1x RJ-45 Jack for LAN. 1x RJ-11 Jack for Modem MDC. 1x DC-In Jack 

Warranty: 1 Year Distributor 

Weight: 2.2 with 6 cell Battery & ODD 

From this site.
[http://translate.google.com/translate?hl=en&sl=id&tl=en&u=http%3A%2F%2Fwww.kaskus.us%2Fshowthread.php%3Ft%3D4259440](http://translate.google.com/translate?hl=en&sl=id&tl=en&u=http%3A%2F%2Fwww.kaskus.us%2Fshowthread.php%3Ft%3D4259440)

---

### Post by ahkond on 2011-04-11
> **Blasphemist said:**
> Oh, sorry bout that. I just googled the pc you said you have. I got an indonesian site that had to be translated but this is what it showed.

spec: 


I never said any of that.

---

### Post by Blasphemist on 2011-04-11
> **jiantguk said:**
> hi, I'm a new ubuntu user

but I had a little trouble. is about my resolution, its just 800 x 600 :)

my laptop is axioo mnc 152

please help me, I'm just newbie...

thanks before...:D

I'm sorry but I don't think I understand. The quote above is your original post. I googled the laptop you showed. I offered information.

Oh, now I get it. I was answering this original post not your response. Try to give us some information on what system you have please. It is hard to help without much to go on. If you look at the sticky's they help with how to pass on information that will help us.

---

### Post by jiantguk on 2011-04-11
thanks,
the trouble is about sis vga card, Mr [Blasphemist]("http://ubuntuforums.org/member.php?u=1165520")
but yesterday, i was download sis driver, and install it. 
my laptop is work properly now. 
but i can use normal and extra visual effects. but its no problem to me.

thanks, :)

---

### Post by ahkond on 2011-04-11
> **Blasphemist said:**
> I'm sorry but I don't think I understand. The quote above is your original post. I googled the laptop you showed. I offered information.

Oh, now I get it. I was answering this original post not your response. Try to give us some information on what system you have please. It is hard to help without much to go on. If you look at the sticky's they help with how to pass on information that will help us.

Sorry for the confusion.  "lspci | grep VGA" yields the following:

Video card: VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)

The system/administration/hardware drivers utility tells me I have "version current" of the NVIDIA accelerated graphics driver.  

Running Ubuntu 10.04 LTS. 

The monitor is an Acer "x243w" model which I have been using for a long time with no problems.  It is shared via a KVMP switch with 2 other computers.  These other computers are both Windows boxes which are working fine with large resolutions (1920x1200).  

The Ubuntu computer had the large resolution until yesterday.  Today I turned it on to find that 1024x768 is the new maximum.  

Not sure what other info would be relevant.

---

### Post by Blasphemist on 2011-04-11
ahkond-

My external display is also an Acer, but only 20". I've found the multiple display app from the software center that is a front end to at least part of xrandr is what I have to use to get my resolution and positioning right. Here is a screenshot of it from the software center.

Is it possible an update happened last night that changed things for you?

---

### Post by ahkond on 2011-04-11
> **Blasphemist said:**
> ahkond-

My external display is also an Acer, but only 20". I've found the multiple display app from the software center that is a front end to at least part of xrandr is what I have to use to get my resolution and positioning right. Here is a screenshot of it from the software center.

Is it possible an update happened last night that changed things for you?

Blasphemist: 

No, I do not have that software installed.  Maybe I should install it and use it as a front end, as you did.

UPDATE: I installed it, and it does not help.  The list of available resolutions does not include the higher resolutions I was using yesterday.

---

### Post by Blasphemist on 2011-04-12
> **ahkond said:**
> Blasphemist: 

No, I do not have that software installed.  Maybe I should install it and use it as a front end, as you did.

UPDATE: I installed it, and it does not help.  The list of available resolutions does not include the higher resolutions I was using yesterday.

Well ahkond you do seem to have a sticky problem. I'll keep working on this with you if you want. 

I think (and I admit that this is a somewhat educated quess) an update must have come through for your Xserver or your video driver. Are you possibly configured for auto install of updates?

In earlier posts others referred to other threads that had some entries that referred to this but it may have been hard to not miss. [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Have you already used this and if so what were the results? When you boot do you see the resolutions change and if so do you ever see what you think might be the higher resolutions on the external monitor? Are you running the 32 or 64 bit 10.04 LTS? Maybe not so coincidentally, a new NVIDIA driver release happened this week that I think affects your version. This is link for that update and its README. [http://www.nvnews.net/vbulletin/showthread.php?p=2417099](http://www.nvnews.net/vbulletin/showthread.php?p=2417099)

Anyway, let me know if anything has changed and if you are still attacking this.

---

### Post by ahkond on 2011-04-12
> **Blasphemist said:**
> Well ahkond you do seem to have a sticky problem. I'll keep working on this with you if you want. 

I think (and I admit that this is a somewhat educated quess) an update must have come through for your Xserver or your video driver. Are you possibly configured for auto install of updates?

In earlier posts others referred to other threads that had some entries that referred to this but it may have been hard to not miss. [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Have you already used this and if so what were the results? When you boot do you see the resolutions change and if so do you ever see what you think might be the higher resolutions on the external monitor? Are you running the 32 or 64 bit 10.04 LTS? Maybe not so coincidentally, a new NVIDIA driver release happened this week that I think affects your version. This is link for that update and its README. [http://www.nvnews.net/vbulletin/showthread.php?p=2417099](http://www.nvnews.net/vbulletin/showthread.php?p=2417099)

Anyway, let me know if anything has changed and if you are still attacking this.

Jim: thanks for sticking with me on this.  I did not know about the ubuntu wiki page about the resolutions.  I've tried using it but didn't get very far.  Specifically: 

1. I used 'cvt 1920 1200' to generate new resolution code for a 1920x1200 resolution.  This produced the following output: 

# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

2. then I used the following command to create a new resolution using this info: 

xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

3. Now, when I run "xrandr" I see the following: 

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1360 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
[... various other small resolutions omitted ...]
  1920x1200_60.00 (0x1f5)  193.0MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.8Hz


4. now I want to test this, presumably using something like this: 

xrandr --output default --mode 1920x1200_60.00 --rate 60

... but I got "cannot find mode".  

So it's not clear to me exactly which characters in the xrandr output constitute the new mode's NAME for the purposes of the above command.  Since I created the new mode using the name "1920x1200_60.00" that was my first attempt.  I've also tried this: 

xrandr --output default --mode 1920x1200_60.00 (0x1f5) --rate 60

But this gives me a syntax error because of the parenthesis.  

Then I tried using quotation marks: 

xrandr --output default --mode "1920x1200_60.00 (0x1f5)" --rate 60

This gives me "could not find mode".  I've tried including the "193.0 MHz" part (preceded by 2 spaces) but still get "could not find mode".  

To reply to your other questions: 

- I don't think I'm set up for automatic updates; I get prompted by the update manager frequently. It's possible that I installed a new update a few days ago and forgot about it, since I get prompted for updates almost daily.  
- I followed your link to the readme etc. for the NVIDIA driver update but found it overwhelming.

---

### Post by Blasphemist on 2011-04-12
> **ahkond said:**
> Jim: thanks for sticking with me on this.  I did not know about the ubuntu wiki page about the resolutions.  I've tried using it but didn't get very far.  Specifically: 

1. I used 'cvt 1920 1200' to generate new resolution code for a 1920x1200 resolution.  This produced the following output: 

# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

2. then I used the following command to create a new resolution using this info: 

xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

3. Now, when I run "xrandr" I see the following: 

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1360 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
[... various other small resolutions omitted ...]
  1920x1200_60.00 (0x1f5)  193.0MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.5KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.8Hz


4. now I want to test this, presumably using something like this: 

xrandr --output default --mode 1920x1200_60.00 --rate 60

... but I got "cannot find mode".  

So it's not clear to me exactly which characters in the xrandr output constitute the new mode's NAME for the purposes of the above command.  Since I created the new mode using the name "1920x1200_60.00" that was my first attempt.  I've also tried this: 

xrandr --output default --mode 1920x1200_60.00 (0x1f5) --rate 60

But this gives me a syntax error because of the parenthesis.  

Then I tried using quotation marks: 

xrandr --output default --mode "1920x1200_60.00 (0x1f5)" --rate 60

This gives me "could not find mode".  I've tried including the "193.0 MHz" part (preceded by 2 spaces) but still get "could not find mode".  

To reply to your other questions: 

- I don't think I'm set up for automatic updates; I get prompted by the update manager frequently. It's possible that I installed a new update a few days ago and forgot about it, since I get prompted for updates almost daily.  
- I followed your link to the readme etc. for the NVIDIA driver update but found it overwhelming.

Good work! Looking at this I wonder if you just missed the addmode step. It is the last line here.

Adding undetected resolutions
Due to buggy hardware or drivers, your monitor's correct resolutions may not always be detected. For example, the EDID data block queried from your monitor may be incorrect.

If the mode already exists, but just isn't associated for the particular output, you can add it like this:


  $ xrandr --addmode S-video 800x600
If the mode doesn't yet exist, you'll need to create it first by specifying a modeline:


  $ xrandr --newmode <Mode``Line>
You may create a modeline using the gtf or cvt utility. For example, if you want to add a mode with resolution 800x600, you can enter the following command: (The output is shown following.)


  $ cvt 800 600
  # 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
  Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
Then copy the information after the word "Modeline" into the xrandr command:


  $ xrandr --newmode "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
[COLOR="Blue"]After the mode is entered, it needs to be added to the output using the --addmode command as explained above.[/COLOR]

That may be why it can't find the mode. Let me know and I'll keep thinking.

---

### Post by ahkond on 2011-04-12
> **Blasphemist said:**
> Good work! Looking at this I wonder if you just missed the addmode step. It is the last line here.
 

That may be why it can't find the mode. Let me know and I'll keep thinking.

Yes, that's it.  Silly mistake on my part; where I come from, "add" and "new" generally do the same thing so I wasn't differentiating them properly.  

Once I used the addmode step I executed the test command again: 

xrandr --output default --mode 1920x1200_60.00 --rate 60

This produces the following output: 

xrandr: screen cannot be larger than 1360x768 (desired size 1920x1200)

This brings us back to square one: 1360x768 is NOT the maximum resolution supported by this monitor.  I am using a KVM splitter and my other (Windows) computers use 1920x1200 with the same monitor with no problem, and the Ubuntu box did the same thing up until yesterday.  Hence the application of the steps in the "adding undetected resolutions" section of that wiki page.  But adding this new mode apparently did not work in some sense.

---

### Post by Blasphemist on 2011-04-12
So we went forward and back to square one all at once. Dang.

Some of what I've learned in working on this with you is that nvidia open source drivers are built into the kernel. You could be using that or proprietary drivers. A new proprietary driver was released yesterday that should support your version. This is the link to download it but I'd caution you not to install it quite yet. [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Start with this please. In synaptic package manager, with all selected in the left pane, type nvidia in the quick filter and see what you have installed. If you select origin in the left pane you'll also be able to see if you have a nvidia proprietary package installed.

I've looked at so many threads related but not quite your issue that I'm unsure just where to go. On both these forums and those at nvidia. I know enough about troubleshooting to be thinking how did this change to begin with. And how should that be addressed to keep from breaking something that isn't the cause. Is there anything you can think back on from the session prior to this appearing that might have some way been related. Was anything done to change the environment in some way? Were desktop environment changes made that might seem unrelated? Have you reloaded the packages list lately? Changes made may not have shown up till you started the next session. Just trying to help make sure we're not overlooking anything.

This isn't something I've had to solve for myself yet. It looks like a person could mess things up pretty good working on the wrong thing for this. More than I'd understand how to recover from quickly at least. Look at the related packages you have installed. Are you 32 bit Ubuntu or 64? Just for grins, can you plug directly into the monitor to test? I'll keep looking into it.

---

### Post by ahkond on 2011-04-12
> **Blasphemist said:**
> So we went forward and back to square one all at once. Dang.

Some of what I've learned in working on this with you is that nvidia open source drivers are built into the kernel. You could be using that or proprietary drivers. A new proprietary driver was released yesterday that should support your version. This is the link to download it but I'd caution you not to install it quite yet. [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)


What a coincidence that my problem arose yesterday also ...

Maybe I should just upgrade to Natty Narwhal in two weeks and hope that clears everything up on the "clean sweep" theory.  

> **Blasphemist said:**
> 
Start with this please. In synaptic package manager, with all selected in the left pane, type nvidia in the quick filter and see what you have installed. If you select origin in the left pane you'll also be able to see if you have a nvidia proprietary package installed.


Here's what I see. (package | version)

nvidia-current | 195.36.24-0ubuntu1~10.04
nvidia-settings | 195.36.80-0ubuntu2
nvidia-common | 0.2.23
nvidia-173-modaliases | 173.14.22-0ubuntu11
nvidia-96-modaliases | 96.43.17-0ubuntu1
nvidia-current-modaliases | 195.36.24-0ubuntu1~10.24

> **Blasphemist said:**
> 
Is there anything you can think back on from the session prior to this appearing that might have some way been related. Was anything done to change the environment in some way? Were desktop environment changes made that might seem unrelated? 


The only remotely relevant things I can think of that happened during my last power session were: 
* I foolishly tried to watch a DVD using Movie Player, even though this has usually failed me in the past.  As usual, I got a data error (could not read from stream) so as usual I watched it on my Windows PC.  But this has happened before without ruining my resolution the next day. 

* I had been using the built-in desktop background which is an animated slideshow of astronomy photos.  I fooled around with some other backgrounds using personal images (.jpg, I think) but eventually went back to the slideshow.  When I discovered the resolution problem yesterday morning I changed it to simple brown.  

> **Blasphemist said:**
> 
Look at the related packages you have installed. Are you 32 bit Ubuntu or 64? Just for grins, can you plug directly into the monitor to test? I'll keep looking into it.

32-bit.  

not sure how to find 'related' packages.  

I unplugged the monitor and the ubuntu box from my splitter device, plugged the monitor directly into the ubuntu computer, and it looked the same for a moment and then the screen went dark and said NO SIGNAL.  

I could try making the same change while powered down, and then try booting.  Would that make any difference?

---

### Post by Blasphemist on 2011-04-12
Please do try the direct connection again from powered off state. If we're real lucky you have an external hardware issue. Thanks for the other information. I see another thread that might help going on now. I'll be reading and wait to hear.

---

### Post by ahkond on 2011-04-12
> **Blasphemist said:**
> Please do try the direct connection again from powered off state. If we're real lucky you have an external hardware issue. Thanks for the other information. I see another thread that might help going on now. I'll be reading and wait to hear.

I powered down, reconnected the monitor directly to the Ubuntu box, and restarted.  The screen came up in my accustomed large resolution (!) for a moment, then the screen went black.  

Then I reattached everything to the switcher and now everything seems OK, with the full resolution, except that my toolbar/panel icons are in the wrong place, as if they had been given new x coordinates based on the smaller resolution.  

This is a minor issue and not worth worrying about.  

So thanks for the suggestion!  Apparently the switcher box was somehow interfering with the computer's auto-detection of the monitor device properties, probably brought on by the new driver release.  

Thanks for all your help.

---

### Post by Blasphemist on 2011-04-12
Good to hear. Try changing out one at a time each cable and the switchbox port and see if that ends up telling you what is going bad. It sounds like you'll be able to get everything back to normal quick now.

---

