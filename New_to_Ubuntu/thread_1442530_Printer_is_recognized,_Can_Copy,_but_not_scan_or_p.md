---
title: "Printer is recognized, Can Copy, but not scan or print an actual 'job.'"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by bytescribe on 2010-03-30
Hi again! :-D

Well, I successfully installed my HP F4480 all-in-one printer. Mostly. There's a bit of a hiccup I need some help with. I can copy, but not print off the web or off my hard drive. Nor can I scan anything, though I was able to scan my ink cartridge alignment page, but that was only once. Now I keep getting this blinking orange light when I push the scan button.

The steps I took to even get the printer going are as follows:

1) Went to the terminal and attempted to install the latest HPLIP drivers from the synaptic, using the 'sudo apt-get install' command. (I am using 8.04 Hardy) This is what that effort produced:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
hplip is already the newest version.
The following packages were automatically installed and are no longer required:
  libdns35 libnss3-dev libnspr4-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

2) Used the recommended command to delete recommended files. Files were successfully removed, and printer is, technically speaking, recognized, and I was able to install my ink cartridges and align them. So far so good.

However, when I went into the "Printer configuration" dialog box, I noticed a tiny difference in information. According to the header that says "Device URL," the computer is recognizing that I have a F4400 series printer. But according to the header that says "Make and Model," the listed "Make and Model" is F4100. I clicked on the button that says "Change," and up pops a box that says something about "Postscript Printer Description," (What exactly does this mean, beyond the acronym?) and that I would need to go into the accompanying Windows-based disk and grab those PPD drivers in order for the printer-specific functions to work. I clicked on the radio button that says "look for your printer in the database" So I looked in the "database" to see if I could locate my specific printer. They DID have the F4100 listed, but not the F4480. 

To help you out in helping me solve my problem, this is what the "Make and Model" line says, specifically:

*HP DeskJet F4100 Foomatic/hpijs, hpijs 2.8.2*

In addition to possibly needing to grab those PPD drivers off the Windows disk (using my parents' computer) and put them on a flash drive to take back up to my Ubuntu machine, a thought just occurred to me while looking through and clicking on the various printer models in the "database." Some of the older series printers needed something called CUPS (and from what I read in the Synaptic descriptions of this driver, it has something to do with spooling--whatever that means, exactly, I am not sure. I've only seen it in conjunction with just operating off printers that have already been installed on someone else's machine).

Since the F4100 series (and later!) seems to run on this "Foomatic" driver (I would love to know what in blue blazes this means, too! :P), would the CUPS driver(s) installed on Hardy Heron be completely interfering with the reading of any Foomatic driver function? And would the CUPS driver interfere enough that the "Foomatic"-based driver would not function, even if I got the PPD files off the Windows-based CD-ROM?

And since I cannot scan (except for that one time), I am going to assume that those PPD files ARE necessary. I know I can get them from the Windows-based disk that came with my printer, but what file folder do I need to look under when I access the disk? And after I get the PPD files to my flash drive and on my Ubuntu desktop, what exactly do I need to do with them as regards the step-by-step process of changing this:

*HP DeskJet F4100 Foomatic/hpijs, hpijs 2.8.2*

to [I]"HP DeskJet F4480....etc...etc.."
[/I]
And what about this CUPS thing? Would I need to do anything with that? If so, what do I need to do (in step-by-step process, if you can)?

Thanks a Bunch,
Kat ^.^

---

### Post by redbook4574 on 2010-03-30
Have you tried using hplip, I have the f4280 and all works perfectly.

---

### Post by bytescribe on 2010-03-30
> **redbook4574 said:**
> Have you tried using hplip, I have the f4280 and all works perfectly.

According to the terminal readout, my Ubuntu OS (Hardy Heron 8.04) has the latest version of hplip, and that no updates were needed.

---

### Post by bullet311 on 2010-03-30
I don't think I saw it in there..is this printer wired or wireless? It makes a difference.

---

### Post by bytescribe on 2010-03-31
Oh, this printer is wired all right, man...if printers ran on coffee, we wouldn't have to worry about making anything wireless because the printers would be wired all the time. *mischievous grin*

Seriously, though...

My printer has wires.

---

### Post by bhmildy on 2010-03-31
Here's a cache of a web page where someone running linux mint (ubuntu plus stuff) had the same problem and fixed it by uninstalling hplip and reinstalling latest version.  You're running Ubuntu v 8, which is the same one that they had problem with.

[http://74.125.93.132/search?q=cache:R5DEwwlLit0J:www.linux-solved.com/post/Now-my-new-scanner-doesnt-detect-HP-Deskjet-F4480-SOLVED-46935.html+hp+f4480+linux&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a](http://74.125.93.132/search?q=cache:R5DEwwlLit0J:www.linux-solved.com/post/Now-my-new-scanner-doesnt-detect-HP-Deskjet-F4480-SOLVED-46935.html+hp+f4480+linux&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)

I don't think that you're ever going to get buttons on hp device to make the computer do something, because it takes software on computer to process commands coming from buttons on hp device, and there's no hp control center software for ubuntu.

scanning: use xsane or simplescan.  simplescan not quite done yet, has bugs, doesn't auto rotate docs to proper orientation, or allow cropping to proper page size on subsequent sheets of multipage scan.  s/b better by time 10.04 rolls around, hopefully.

---

### Post by bytescribe on 2010-03-31
Thank you for the tip, though I have absolutely NO clue about manually compiling much of ANYthing using ANY tarball something-or-other. I am also resisting upgrading past the version of Ubuntu that I'm using since that would mean dealing with reinstalling my wireless drivers. And I don't know if the version of ndiswrapper/ndisgtk I am using is going to be compatible with Ibex, Jackelope or Koala.

BUT...IF I must manually compile, can ANYone direct me to a step-by-step process of how to work with such things and not assume I know stuff? I'm in "Absolute Beginner Talk" for a reason, and honestly, I admit I don't have a lot of patience in doing my own research since I don't know precisely what it is I'm supposed to be looking for, don't know what that something might look like (even if I think I've found it), or more importantly, how to understand the jargon once I DO realize that I've found what I need. 

So until I gain a little more confidence (and a loss of fear of completely screwing something up), I need someone to give me some "training wheels," so to speak.

I mean, I am far from crazy about Windows, but I don't have the money or the bookshelf space to buy the books I feel I need to learn Ubuntu (or Linux in general) properly on my own.

Frustrated with the Geek-Speak that I Don't Know Yet,
Kat ^.^

---

### Post by bytescribe on 2010-03-31
Okay, so I went into Synaptic and found an unchecked box that said hplip ppd files. I installed those and turned on my printer just to see if these files would work. However, as I suspected, these are obviously the files for a slightly older all-in-one printer model (the F4100). 

A friend of mine here at the Ubuntu forums mentioned using the autoinstaller for the newest version of hplip, but how do I go about USING it? Meaning, once the new version of hplip is downloaded and stored on my desktop, how do I install it, apart from changing the directory in the terminal? 

Can I assume I need to completely uninstall the preinstalled version of hplip that came with Hardy?

Or should I just say "screw it," back all my favorite files up and upgrade to a version of Ubuntu that has the newest version of hplip so all I have to do is get the ppd files off the Windows-based CD-rom if I have to go that route? It will mean not having wireless for a few days, but dammit, I am about to upgrade if that's what it takes to get my all-in-one going.

---

### Post by bhmildy on 2010-03-31
I'm kind of a noob, too, so take with grain of salt.

Forget about compiling, for now, if ever. Take-away message from that site: upgrades may fix problem.  this problem can be solved.  i think they compliled because they didn't feel like upgrading OS.

check your wireless card maker's website, see if they have linux driver.
check also comments in amazon for the card, they're very good at discussing linux compatitility.
check ubuntu hardware compatibiity list to see if they're listed.

go here
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
compare current version with your installed version.  if older,
get recent hplip files, double-click on them to install.
I picked my wifi card because comments in amazon said it worked great in linux. website said nothing, so crossed my fingers and purchased card.  box said it had linux drivers, though. Sabrent PCI G802 $15

Pushed it in, installed ubuntu, installed automatically, works perfectly.  your current card might be installed automatically by 9.10

but don't upgrade yet. go to hp first and download and install, then see.

---

### Post by bytescribe on 2010-04-01
Well, at least I'm not the only one who's a noob. That makes me feel better.

As far as compiling? Eventually I'd like to learn it, but I'm still a green coffee bean. :P

I have the website link you mentioned. I got it from another Ubuntu user, and I know that I don't have the current hplip driver. It's knowing how to actually install the driver. Do I need to uninstall my current (old) hplip driver first? If so, what's the command line? OR...can I uninstall in the Synaptic? 

You said just double click the hplip icon to install it once it's on my desktop (which is where I have most files downloaded to anyway)? I must admit it sounds too easy. :P 

As for my wireless, I have a USB dongle from Cisco/Linksys with the Wi-Fi router downstairs and the necessary drivers sitting on my desktop, and when I configured my wireless internet last year, I remember having to download the ndiswrapper and ndisgtk drivers as well. Even if I chose to upgrade to Karmic, I am going to assume I will need to download the latest version(s) of ndiswrapper and ndisgtk just because I'm using a proprietary USB dongle with no Linux compatibility available. It was my dad's idea to use Linksys (and he's WAY more of a computer noob than I am!) so I really don't have much choice in changing brands, since I don't know about cross compatibility, product-wise. I mean, I would think a signal is a signal, but if certain product brands/models are meant to work together...*shrugs* I mean, I don't wanna spend a bunch of money for something that's Linux compatible and not detect the signal from downstairs just because the product is different. :P

I'm not doing a thing with my computer until tomorrow anyway, when someone has had a chance to reply to this. :P

---

### Post by egalvan on 2010-04-01
Can't fault you for not wanting to "upgrade" a working system...

I am also using Hardy on my main "work" machine, and have no wish to disturb it.

But...
10.04 Lucid will be released at the end of this month, 
and it's a LTS.

Plus, it's got two years of "experience" over 8.04 on it...
Hopefully wireless will have gained big-time!
And maybe printing will have gained something also.

You may want to check on this, if the time is not a factor...
(but I also hear that the beta's have been extremely stable...
But then that's what LiveCD's are for, right?)

Me, I plan on letting Lucid "cook" for a few weeks, maybe a month.
This should boil out the big errors...
(The standard "up-date" cycle will push out 10.4.1 around October,
but that's too long to wait for me :P)

Then it's "up-grade" time for me!
I'll probably up-grade all seven of my machines...
and a bunch of customers, also. ;)

---

### Post by bytescribe on 2010-04-01
> **egalvan said:**
> Can't fault you for not wanting to "upgrade" a working system...

I am also using Hardy on my main "work" machine, and have no wish to disturb it.

But...
10.04 Lucid will be released at the end of this month, 
and it's a LTS.

Plus, it's got two years of "experience" over 8.04 on it...
Hopefully wireless will have gained big-time!
And maybe printing will have gained something also.

You may want to check on this, if the time is not a factor...
(but I also hear that the beta's have been extremely stable...
But then that's what LiveCD's are for, right?)

Me, I plan on letting Lucid "cook" for a few weeks, maybe a month.
This should boil out the big errors...
(The standard "up-date" cycle will push out 10.4.1 around October,
but that's too long to wait for me :P)

Then it's "up-grade" time for me!
I'll probably up-grade all seven of my machines...
and a bunch of customers, also. ;)

Hmmm...my boyfriend just bought me a copy of the Ubuntu 9.10 magazine at Borders yesterday, so it seems a shame to completely jump to Lucid (Lynx, is it?) and waste my boyfriend's hard-earned money. So maybe if I DO upgrade at least to Karmic, I will have the following:

1) Potentially better-performing wireless even if ndiswrapper & ndisgtk are a necessity(absolutely MUST have internet in my room!!!)

2) Software that's compatible with my new flat-screen monitor (I have not removed it out of the box until this issue with my printer is settled. Or maybe I shall upgrade to Karmic first, install my new monitor and THEN worry about the wireless and the printer!)

3) Software that has the newest version of hplip + ppd's for my all-in-one. Surely Karmic has got to be SOMETHING of an improvement over Hardy in this specific arena. I'm an "Avon lady" as well as a computer geek, so I REALLY need my printer to work the way I need it to in order to gain and retain customers. Which is why the notion of upgrading is not all that unpleasant anymore. 

ESPECIALLY if upgrading gets my printer to work and allows my new monitor to work "out of box. :P

I would be a bit quicker to upgrade if I felt I could afford to buy the DSL cable length necessary so I can completely avoid wireless! I've had wireless for about a year, and I still want that reliable connection with no stinkin' extra drivers needed. :P

Thanks for the greetings and acknowledgement, egalvan. You made me feel okay about wanting to stick with something I know...

On the other hand, my new monitor and the potential of a working printer call to me...so I may be munching cyber-eucalyptus anyway.

---

