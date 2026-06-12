---
title: "Persistent Screen Degradation Problem"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by Don Martin on 2011-02-06
[SIZE=4]After a couple of months using Ubuntu, most things are going smoothly but one problem persists.  When using the internet the screen image falls apart, beginning with the top bar and progressing.  I have a Gateway with an AMD Athlon 64 chip.  My video card is 

[/SIZE]   	 	 	 	p { margin-bottom: 0.08in; }  [SIZE=4]01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series][/SIZE]
 
[SIZE=4]I've attempted to attach some screen shots attached illustrating what happens.

Don


[/SIZE]

---

### Post by LewRockwellFAN on 2011-02-08
For whatever it is worth the second image looks like what I see on some web sites at some zoom levels. For me, getting a readable page in those cases is a matter of adjusting the zoom level. Not sure why that is.

---

### Post by sydbat on 2011-02-08
> **Don Martin said:**
> [SIZE=4]After a couple of months using Ubuntu, most things are going smoothly but one problem persists.  When using the internet the screen image falls apart, beginning with the top bar and progressing.  I have a Gateway with an AMD Athlon 64 chip.  My video card is 

[/SIZE]   	 	 	 	p { margin-bottom: 0.08in; }  [SIZE=4]01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series][/SIZE]
 
[SIZE=4]I've attempted to attach some screen shots attached illustrating what happens.

Don


[/SIZE]Let me begin by letting you know that you should not create large fonts and whatever (p { margin-bottom: 0.08in; }) is, because it very likely goes against forum policy and you might get a warning / banned. I have read a couple of your other threads where mods have changed the fonts, etc.

That said, it looks like your graphics card is no longer supported by ATI, but is probably using the open source driver to run. If you have any visual effects enabled, disable them and see if that improves your situation.

---

### Post by Don Martin on 2011-02-08
Thanks for taking the time to respond.  I've been searching everywhere I can think of but have not found any solutions so far.   Sometimes the problem occurs when I'm zooming in on Google Earth, but other times it occurs every time I try to access particular web pages, so perhaps there is more than one thing going on?

I'll try to do what you've suggested and see what happens.  I'm very new at all  of this.

As far as the font size goes, there is a little menu of font sizes on the menu bar, so I've been making use of it.  My eyes aren't very good and I find the tiny font hard to read.

Don

---

### Post by sydbat on 2011-02-08
> **Don Martin said:**
> Thanks for taking the time to respond.  I've been searching everywhere I can think of but have not found any solutions so far.   Sometimes the problem occurs when I'm zooming in on Google Earth, but other times it occurs every time I try to access particular web pages, so perhaps there is more than one thing going on?

I'll try to do what you've suggested and see what happens.  I'm very new at all  of this.

**As far as the font size goes, there is a little menu of font sizes on the menu bar, so I've been making use of it.  My eyes aren't very good and I find the tiny font hard to read.**

DonTo increase the size of the web pages you visit, hold down "Ctrl" then use the + or - buttons on your number pad. + will make the page size bigger and easier to read.

---

### Post by Tyggna on 2011-02-08
Your screen looks exactly like mine when I was using an outdated driver for my graphics card.   I would try switching to the open source ATI drivers and see if there's improvement.

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Don Martin on 2011-02-09
All of these replies have been helpful.  When I switched to Ubuntu from Windows, I got rid of Windows entirely so expect that I already have an open source ATI driver installed by default.  

In following the help trails which have been suggested, however, I came across the following in "The unofficial AMD Linux  Community" 'Ubuntu Lucid Installation Guide"

"If you run into stability problems with 3D applications using the radeon/radeonhd drivers, consider trying a more recent kernel. [mainline-2.6.34-lucid]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/") did the trick on a few machines."

 My Linux version appears to be 2.6.32 -28 - generic. I don't know whether Google Earth qualifies as a '3D application'.  Is this something that I should try?  Or that a beginner might even be able to do successfully?

Don

---

### Post by Tyggna on 2011-02-10
> **Don Martin said:**
> All of these replies have been helpful.  When I switched to Ubuntu from Windows, I got rid of Windows entirely so expect that I already have an open source ATI driver installed by default.  

In following the help trails which have been suggested, however, I came across the following in "The unofficial AMD Linux  Community" 'Ubuntu Lucid Installation Guide"

"If you run into stability problems with 3D applications using the radeon/radeonhd drivers, consider trying a more recent kernel. [mainline-2.6.34-lucid]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/") did the trick on a few machines."

 My Linux version appears to be 2.6.32 -28 - generic. I don't know whether Google Earth qualifies as a '3D application'.  Is this something that I should try?  Or that a beginner might even be able to do successfully?

Don

It is a "3D application" in the sense that it utilizes the graphics card pixel pipeline to show images.
It's not difficult to do--if ubuntu provides the packages.  Search in your package manager for "kernel" and a list of what's available should come up.  After you install it--it'll make a new entry on your boot menu, so you'll need to change which option is highlighted at boot.


If it doesn't have the kernel package, then you'll need to upgrade to a newer version of ubuntu--or change which distribution of Linux you use altogether.

---

### Post by Don Martin on 2011-02-11
Well, there is no other version listed in the package manager.  There is an Ubuntu 10.10 listed as the latest version at Ubuntu.com.  I have 10.4.  I'll try downloading a copy of 10.10, and see whether it helps.

Don

---

### Post by Don Martin on 2011-02-12
I've managed to upgrade to Ubuntu Version 10.10, with some difficulty.  It hasn't solved the problem though.  Still can't use Google Earth and still have some Web pages which I really would like to use, but screen falls completely apart.

Oh well.

---

### Post by LewRockwellFAN on 2011-02-13
I'm interested because, as I mentioned, I experience the same type of garbled screen as in your second illustration but only on a very few websites and in those cases I can cure it, sorta, by playing with the zoom until I find a level at which it displays "normally". Normally in those cases may suck, with microscopic fonts or images that disappear behind the screen edge and can't be scrolled but at least what is visible isn't garbled. It seems to happen only with sites that use tricky stuff like frames. Does that describe your experience also? 

Your first image shows something I do NOT experience but I do get something that looks a little bit like that, with rectangular areas of the screen suddenly being replaced with featureless gray. If I click on the titlebar it goes away. Actually, that only happens to me on one website, as a matter of fact, THIS one. I haven't really worked on trying to fix this much. I did try a firefox add on called Adblock because it seemed possible the gray blocks might be malfunctioning ads of the sort that pop up in response to your pointer being over a certain bit of text. But it didn't help.

I believe I experienced the same under 10.10 and under Narwhal as I'm experiencing now under 10.04 although I could be wrong as this didn't irritate me enough to pay close attention. I have updated to the latest proprietary graphics driver that Synaptic could find and I have all special effects turned off.

 If I run across a fix I'll report. I'm interested in hearing your further experiences.

---

### Post by Don Martin on 2011-02-15
For what it's worth if anyone is still following this thread, the problem which produces the garbled, white screen occurs when I attempt to use the 'contact us' feature after i have signed in to do my online banking.  As soon as I  click on the 'contact us' button the screen garbles out.

I've discovered, though, that if I use the 'contact us' feature in the generally accessible home page of my bank, before signing in, the image stays perfectly good.  While this makes the problem less irritating, I'd still like to resolve it if possible.

Does this information give anyone any clues?

---

### Post by walt.smith1960 on 2011-02-15
Is this a desktop or laptop?  If it's a desktop, is the monitor cable plugged into a port near the other ports (USB, ethernet etc.)? If so, it's using onboard video.  If the monitor cable is plugged in by itself, it's plugged into separate video card.  If you have a desktop, I think I would look into getting a new video card.  nVidia seems to be well supported in Ubuntu. You'd need to get the correct card e.g. PCI, PCIe, AGP.  Decent video cards can be pretty reasonably priced, you don't need the latest gamer's wondercard with its own refrigeration plant.

---

### Post by sydbat on 2011-02-15
> **Don Martin said:**
> For what it's worth if anyone is still following this thread, the problem which produces the garbled, white screen occurs when I attempt to use the 'contact us' feature after i have signed in to do my online banking.  As soon as I  click on the 'contact us' button the screen garbles out.

I've discovered, though, that if I use the 'contact us' feature in the generally accessible home page of my bank, before signing in, the image stays perfectly good.  While this makes the problem less irritating, I'd still like to resolve it if possible.

Does this information give anyone any clues?Is this the only website that does this? If so, then I suspect that, after logging in to the https area, your bank has something misconfigured.

If it also happens on other websites, then...?

---

### Post by GrouchyGaijin on 2011-02-15
> **Don Martin said:**
> For what it's worth if anyone is still following this thread...


I'm still lurking here waiting to find out the solution.

---

### Post by Don Martin on 2011-02-17
The screen turning instantly white does happen only on the one web page, so I'll see whether I can get the bank to check their configuration of the pages.

The problem with Google Earth still persists.  I uninstalled the version I had installed through the Google Earth web site, and then reinstalled it from the terminal.  In both cases the application opens just fine and I get a nice picture of the globe which I can set to spinning and so on, but as I zoom in, the screen starts to garble out, beginning with the top, Ubuntu, bar, and then spreading everywhere as I continue to zoom in.

As long as I know where the menu buttons are, I can still make them work for screen shots, shutting down and so on, and some of the icons and menu items reappear after I run my cursor over them, but that is all.

I'm going to see if anyone has managed to get Google Earth to run properly in Ubuntu on the hardware I've got.

Don

---

### Post by Don Martin on 2011-02-18
While looking to see whether anyone had Google Earth working on my hardware, I found a solution which I had seen previously, but for different hardware.  It had seemed to scary, and the instructions not clear enough for such a beginner as I am.  But now I have a little more confidence and found very clear instructions.  My screen no longer falls apart in any web page, so far as I can tell, and not in Google Earth, either.

I've lifted the following with only slight adaptations from a post by ELoXL from July 27, 2010.  They worked perfectly for this machine.  

Thanks to everyone for the help and hope this helps in return.

Don


  	 	 	 	p { margin-bottom: 0.08in; }  Go to Applications, Accessories, Terminal and type the following command:
 

 sudo gedit /etc/default/grub
 
It will then ask you for your password.  Type it in.

The GRUB file should appear and you can edit the contents.
 

 Search for the line: GRUB_CMDLINE_LINUX=” ”


 Type  [COLOR=#ff0000]nomodeset[/COLOR][COLOR=#000000] between the quotation marks as for, example below;[/COLOR]
 

 GRUB_DEFAULT=10
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[COLOR=#ff0000]nomodeset[/COLOR]"

You will notice the red text is what you need to insert between the quotes that will originally have nothing between them.

Be sure to select the "Save" button within that window and you will be good to close it from there, BUT....

You must update it within terminal for it to take effect. Within terminal type the following:

sudo update-grub

From there you will see some stuff going on; I reckon applying the changes to the file. Once you see "done" and your typical terminal prompt appears you should be good to go. Reset your netbook and godspeed. This worked for me and I hope it does for you. I'm more than glad to help out, but I will claim I am no genius; each one teach one.

---

