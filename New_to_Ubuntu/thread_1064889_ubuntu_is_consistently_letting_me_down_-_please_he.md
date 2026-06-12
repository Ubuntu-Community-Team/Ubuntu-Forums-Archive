---
title: "ubuntu is consistently letting me down - please help"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-09
I love ubuntu...I truly do...

But it seems she insists on making life as difficult as possible and I don't understand :(

Example....

I installed alien, it's says installed in SPM, but there is not a TRACE of it any where?  Nothing.
This happens with many apps...not just Alien.
ok, maybe this one is a command line app...no problem...but many aren't that also don't show or take lots of work to get them to.
Sometimes apps show, sometimes they dont.  Sometimes re-installing helps, sometimes not.

Also, I installed a printer and it works with "some" things but not others...ie...HTML pages with mixed text and graphics will print "some" of the graphics, but not the text...or it makes multiple pages out of a one page document because of spaces it inserts.  I've spent 4 days JUST on printing issues and STILL cant print? <pulling hair out>

Also, yesterday I could print PDF files just fine, today, it just blips on the screen as if its about to load then just as quickly vanishes ???
She wont even load PDF files today?   wth???
Rebooting does not help.

I REALLY want to become a ubuntu'er but seriously, I need to be productive and not spend 1% of my time productively and 99% of my time researching and fixing?  I'm beginning to see the dollar cost of WindowsXP (and it's issues) versus the massive troubles and time spend unproductively with ubuntu as a breaking point where it's more cost effective to use WindowsXP.

Why am I having so much trouble with ubuntu?  Am I missing out on a great community secret?

I want to give ubuntu the benefit of the doubt and think..."maybe it's my computer is screwed?"
It's an AMD64 Dual Core, 3GB RAM, less than 2 years old, 5200+ cpu.  Shouldn't that do?

I absolutely LOVE ubuntu and I'm so grateful for all the hard work that so many have obviously put into, but I'm wondering if maybe my expectations are too high?  This whole thing is grinding my affection away slowly.

Is ubuntu SUPPOSED to be a "fix daily", "research daily", "struggle daily" kind of environment?
Are you having issue like I am?  I'm just trying to use it as an Office computer for normal Office type things no gamin, nothing out of the ordinary.

I'm broken hearted at this point because I SO much want to use and live with ubuntu.

Help!

Drowning potential ex(again)-ubunt'er :(

Misty

---

### Post by PriceChild on 2009-02-09
Not all applications are graphical.

Alien for example works on the command line. alien something.rpm converts it to a deb. We don't reccomend using this at all though as it can easily break your system, even if it does "work".

Check out [https://help.ubuntu.com/8.10/add-applications/C/index.html](https://help.ubuntu.com/8.10/add-applications/C/index.html)

---

### Post by Kellemora on 2009-02-10
Hi Misty

I converted my entire office over to Ubuntu within a month of my first taste of Ubuntu.  Production is way up and problems are way down compared to when we used the DOZE.........

However, we are NOT trying to take Red Hat based programs and run them on a Debian based System either.  Although we do use some Doze programs in WINE.....

If you really want to run Red Hat and not pay for it, you could download and burn a CentOS .iso and install that on your computer.  Triple boot Doze, CentOS and Ubuntu.  I have a few machines set up that way myself.
CentOS IS Red Hat Enterprise Linux without support, not even a decent web site to help you out if you get stuck.  The web site forums here is what helped boost Ubuntu to the #1 Distro.

I'm in desktop publishing so we do one heck of a lot of printing to all kinds of different printers and have had less printing issues with Ubuntu than we suffered with the Doze.
Here is an excellent example too:  The Doze and msWord uses printer data to set up a document.  If you try to print that document on a different printer than what you had msWord set up to recognize, it normally will require reformatting for that particular printer to get it to come out right.
Ubuntu uses the CUPS printing system, it's the SAME for all Linux computers.  Open office Writer stands independent of any printer, so what you place on the document will print the same on virtually any printer you print that document to.
That one feature alone has saved us countless hours of reformatting work for various printers and printing companies that do our bulk printing.

One thing nice about CUPS is you can suppress blank pages that many web sites feed out.  Something that CANNOT be done in the DOZE at all.  You can take oversized pages and reduce them (scale them) to your printers limits easily.
Because we work full margin to full margin to produce brochures, we use a custom paper size of 9.5 x 13 and 9.5 x 16 for printers masks.  But CUPS will let us print these on standard sized paper with the factory set printer margin limitations, without messing the images and text up.  Try that in the DOZE using msWord and sending that document to a different printer than msWord was set-up for using sometime.  It's worse than a nightmare!

Since you have experimented with some things not designed for Debian Based Linux and maybe got some files changed to what they should not be for Ubuntu to run properly.  It might be a good idea to reformat your drive and start over with a clean install of Ubuntu.
Then find programs already configured for Debian based and have the bugs worked out.  There are like 30,000 or more free programs in Synaptic and Add/remove before you add extra repositories.  In other words, the program you want is probably there and already converted for Debian based and had the bugs worked out as well.

There are shortfalls in Ubuntu, partly because it's fairly new and secondly because manufacturers don't yet support Linux any flavor.  Thankfully Some are finally beginning to!

You can't go to a Ford dealer and buy a new hood for an LTD or Crown Vic and expect it to fit on your Chevy Camaro very well without MAJOR modifications and the equipment and knowledge to be able to make those modifications.  It would be cheaper and easier to buy a Chevy Camaro hood from the git go and alleviate yourself of all those problems.

Linux is like a Ferrari, compared to the DOZE which is more like a VW Bug in comparison of power.  But you'll have to learn to drive a STICK to utilize the full features of Ubuntu!  Although much of it is like an automatic-stick-shift, the BEST of both worlds, hi hi.........

Good Luck
TTUL
Gary

---

### Post by LowSky on 2009-02-10
I want to address some of your issues.

First, when you start out on Ubuntu or Linux in general it is good to have a safty such as Windows when yoaccidentally brick the Linux install (for most users this will happen).

Two, If you tried to install every package in Synaptic your system would most likely not work becasue of too many things that are contradicting each other.

Three, Settle on the apps you need not the apps you think you need. for instance, if you are using the machine for general office work then installing Compiz and Emerald, and add-on packages for this and that application, sooner or later something will break. Keep it simple and install what is needed not the cool stuff that you think you need.

Four, Never install a new unknown Operating System on a computer that is mission critical. If you break it its your fault, remember that.

Five, it may seem that Linux is Linux but it is not, Ubuntu and Redhat and all the other comparisons I can think of simply are not the same and shouldn't be treated that way. dont assume that a Redhat package will work on a Ubuntu machine. for that matter do not assume a Debian package will work on a Ubuntu machine. Even if they share many things, simple differences can spell disaster. Make sure the application you install  will run on Ubuntu or at least on the same Linux Kernel.

Six, A fresh install amybe your best option. If too many setting get changed and you have no ide to change them back, I suugest a fresh install. Most people whould suggest to back up you home folder, but in aLinux noob I suggest you only back up your actuall important stuff like written documents/pictures/videos/music, best idea is to have a backup strorage devie that can fit them, all like an external hard drive or large flash drive.

Seven, If your not sure about something ask a question.

---

