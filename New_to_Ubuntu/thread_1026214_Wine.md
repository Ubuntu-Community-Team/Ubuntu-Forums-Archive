---
title: "Wine"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by tchai on 2008-12-30
Can any other program besides Notepad be run on Wine?
I also don't get the configuration method of wine.
Could someone please explain?

---

### Post by eBoxNet on 2008-12-30
for wine compatible apps list check this :

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by Kellemora on 2008-12-30
Hi Tch

Virtually any Windows program that has an install.exe or setup.exe file will run in WINE, provided it does not make API calls.

Large accounting programs and many of the larger games make API calls, which is why they won't work.

Almost any program written for Doze 3.0, 3.11, 95, & 98 will run just fine.  For XP programs it depends upon the program itself.  But most still run A-OK........

I use Eudora Pro 7.1 for my e-mail in Wine, runs like a top!
And several Windows games too!

TTUL
Gary

---

### Post by snova on 2008-12-30
> **tchai said:**
> Can any other program besides Notepad be run on Wine?

Many, but not always. All you can do is try, or check here first: appdb.winehq.org

> **tchai said:**
> I also don't get the configuration method of wine.

What configuration? ;) Just try to run it.

---

### Post by tchai on 2008-12-30
OK.
Well, Internet Explorer 7 Garbage stayed true to it's Garbageness
Others to be tried until one works.

---

### Post by chrisod on 2008-12-31
Why are you using Linux? The point of Ubuntu is not to provide a stable platform to run Windows programs. Your time would be much better spent learning how to use the Linux equivalents (and in many cases improvements!) of Windows programs. If you want to run a lot of Windows programs using Windows is the way to go.

---

### Post by ajcham on 2008-12-31
> **chrisod said:**
> Why are you using Linux? The point of Ubuntu is not to provide a stable platform to run Windows programs. … … … If you want to run a lot of Windows programs using Windows is the way to go.

You're making some rather baseless assumptions there.  The OP gave no indication of which or how many Windows apps he/she intends to run, but for IE. It's not unreasonable to run mostly native Linux apps, but have Wine around for a few others that don't necessarily have satisfactory native equivalents.

And before you counter that there *are* much better alternatives to IE, there are still legitimate reasons for having it installed - web development being primary.

---

### Post by tchai on 2008-12-31
> **chrisod said:**
> Why are you using Linux? The point of Ubuntu is not to provide a stable platform to run Windows programs. Your time would be much better spent learning how to use the Linux equivalents (and in many cases improvements!) of Windows programs. If you want to run a lot of Windows programs using Windows is the way to go.
Let's see how it goes.......for the BEGINNER

---

### Post by tchai on 2008-12-31
> **ajcham said:**
> You're making some rather baseless assumptions there.  The OP gave no indication of which or how many Windows apps he/she intends to run, but for IE. It's not unreasonable to run mostly native Linux apps, but have Wine around for a few others that don't necessarily have satisfactory native equivalents.

And before you counter that there *are* much better alternatives to IE, there are still legitimate reasons for having it installed - web development being primary.
Nice one!!

---

### Post by jorj82 on 2008-12-31
> **tchai said:**
> OK.
Well, Internet Explorer 7 Garbage stayed true to it's Garbageness
Others to be tried until one works.

From the the WineHQ FAQ:

> 7.6. How do I install Internet Explorer in Wine?

If you just want an application to think you have IE installed, see My application won't run, and says it needs Internet Explorer above.

The Wine project does not support installing the real Internet Explorer, as it requires a huge number of native DLLs, which is hard to configure.

If for some reason you really, really need to run the real IE, see ies4linux, which is a script that does the necessary Wine configuration for you. (But please don't ask the Wine project for help if you run into trouble, ask the author of ies4linux.)

You could also try selecting ie6 in winetricks, but this doesn't really work yet. 

---

### Post by tchai on 2008-12-31
> **jorj82 said:**
> From the the WineHQ FAQ:
Thanks, I'll check it out.......

---

### Post by chrisod on 2008-12-31
Well, if you combine this:

> Can any other program besides Notepad be run on Wine?

with this:

> Well, Internet Explorer 7 Garbage stayed true to it's Garbageness
Others to be tried until one works. 

And then add in the number of people we see here that install Ubuntu and then immediately ask for help getting 15 different Windows apps running, reading the OP as one of them is not unreasonable at all. If I misread it, I apologize, and I'll try to make sure I stay out of the help forums until after my first cup of tea :)

And I disagree with with the web dev issue. If you are truly are concerned about making sure your site looks good for folks using IE, you need to look at with IE on Windows. It's probably going to look different in IE on Linux, if you could actually get it to work. The same site can regularly looks different in Firefox on a Windows box, Linux box, and Mac.

---

### Post by tchai on 2009-01-05
Well, the installer can run but it says that errors were encountered.
It advises that I retry the installation.

---

### Post by tchai on 2009-01-14
iTunes, Roxio, Firefox for Windows, Microsoft Shared View, QuickTime all installed. 
Internet Explorer poses a challenge stil.
Ubuntu is still serving my needs, though.

---

### Post by Peter6218 on 2009-01-16
> **Kellemora said:**
> Hi Tch

V...

I use Eudora Pro 7.1 for my e-mail in Wine, runs like a top!
And several Windows games too!

TTUL
Gary

Hope you can tell me how to set 8.10 so that I can paste into Eudora. Did it back in 7.10 days and it worked fine but I've forgotten the trick. Thanks.

---

### Post by SteveDee on 2009-01-16
> **chrisod said:**
> Well, if you combine this:



with this:



And then add in the number of people we see here that install Ubuntu and then immediately ask for help getting 15 different Windows apps running, reading the OP as one of them is not unreasonable at all. If I misread it, I apologize, and I'll try to make sure I stay out of the help forums until after my first cup of tea :)

And I disagree with with the web dev issue. If you are truly are concerned about making sure your site looks good for folks using IE, you need to look at with IE on Windows. It's probably going to look different in IE on Linux, if you could actually get it to work. The same site can regularly looks different in Firefox on a Windows box, Linux box, and Mac.

Anyone interested in checking how their website looks through the eyes of other browser/OS combos should go to: [http://browsershots.org](http://browsershots.org)

---

### Post by dcparham on 2009-02-27
i hope the context of your thread supports my question: trouble with ies4linux. installed wine 1.1.14, and cabextract; then downloaded ies4linux-2.99.0.1, but when running it ["in Terminal"], first it says i have too low a version of wine, which i fixed that error by modifying the ies4linux /lib/function.sh file [i found a post of someone who taught me this], so now ies4linux does not seem to crash upon install, but after it seems to install then the computer seems to reboot [very quickly]; it at least logs me off.  then i have to log on, and NO IES4LINUX apparent.  help??

btw, the "fix" in ies4linux "/lib/function.sh" file is like this:

# Find where wine is
function find_wine {
	which wine &> /dev/null || error $MSG_ERROR_INSTALL_WINE
	#wine --version 2>&1  | grep -q "0.9." || warning $MSG_WARNING_OLDWINE
	#see [http://ubuntuforums.org/showthread.php?p=6648742](http://ubuntuforums.org/showthread.php?p=6648742)
	wine --version 2>&1 | egrep -q "0.9.|-1." || warning $MSG_WARNING_OLDWINE
}

---

### Post by llamabr on 2009-02-27
Zingers and one liners aside, you didn't answer the question.  Why are you using wine?  It may be that whatever it is you're trying to do the long way around can be much more easily and efficiently natively.

And the main point is sound -- ubuntu is not at its top form as a platform for running a bunch of .exe's.  You're bound to eventual failure or hassle, both of which are avoidable by either going back to MS, or finding native applications that suit your purpose.

---

### Post by Ms_Angel_D on 2009-02-27
Op You may want to try Windedoors it will install ie6 as well as a few other windows programs.

[http://wddb.wine-doors.org/](http://wddb.wine-doors.org/)

---

### Post by stchman on 2009-02-27
> **chrisod said:**
> Why are you using Linux? The point of Ubuntu is not to provide a stable platform to run Windows programs. Your time would be much better spent learning how to use the Linux equivalents (and in many cases improvements!) of Windows programs. If you want to run a lot of Windows programs using Windows is the way to go.

AMEN, I am so friggin sick of the WINE whiners.  Too many people out there judge Ubuntu solely on it's ability to run Windows apps.

If you want to run Windows apps, RUN WINDOWS?

How many Linux programs does Windows run?

The only reason to run WINE is for an app that cannot be had in Linux and is a must need.  Those to me are few and far between.

---

### Post by Peter6218 on 2009-03-02
"Windows XP - Excellent computer virus detector.
Windows Vista - Most bloat for the money."

Excellent <g>

Mind if you want bloat wait till you see Windows 7 !!

Just loading the beta OS takes 460Mb !!

---

### Post by Kellemora on 2009-03-03
Hi Peter

Ctrl-V or Ctrl and the center mouse button both paste into Eudora.

I'll have to double check the next time I paste something to make sure though, I just do it by habit without thinking about it.

It's like the keys on the keyboard, I don't know where they all are, but my fingertips do.  In other words, I think my transcription work goes from my ears to my fingertips and bypasses the old gray matter enroute, hi hi.....

TTUL
Gary

---

### Post by stchman on 2009-03-03
> **Peter6218 said:**
> "Windows XP - Excellent computer virus detector.
Windows Vista - Most bloat for the money."

Excellent <g>

Mind if you want bloat wait till you see Windows 7 !!

Just loading the beta OS takes 460Mb !!

I did not expect Windows 7 to be leaner than Vista.  I have read that Windows 7 will implement DRM.  Great.  I will stick with Ubuntu and be DRM free.

---

