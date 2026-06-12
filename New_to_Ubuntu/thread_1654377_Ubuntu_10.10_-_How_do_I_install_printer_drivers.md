---
title: "Ubuntu 10.10 - How do I install printer drivers?"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by jpollman on 2010-12-28
Hi folks!

I've had a friend trying to get me to make the switch to Ubuntu for years. I recently upgraded my laptop from Vista to Windows 7. Same old story, not very stable and a different set of problems than I was having with Vista.  I decided to try Ubuntu. Took me a while and several attempts but I finally got it installed and working. It looks pretty good so far and I like it. But then I realised that I need to install my printer drivers.  I just bought a Brother MFC-J415W. I went to the Brother site and there are Linux drivers available but there are a bunch of them and I haven't got a clue as to which one I have to install. It looks like I need one for printing and one for scanning. I don't need to FAX so I don't care about that one. 

Even if I do find the one I need, the instructions look like they're written in Greek. I have absolutely no idea where to even start. I'm just about ready to go crawling back to my Windows 7 and tough it out.  

Any ideas?

Thanks for any input!

John

---

### Post by Bucky Ball on 2010-12-28
What computer? I can probably decipher this for you. At the brother page for your printer in linux now.

---

### Post by davidmohammed on 2010-12-28
hi there and welcome to the forums.

Have you installed the 64bit version or 32bit version of ubuntu 10.10?

If the 64bit - follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=1653321")

If the 32bit then I think you can follow the same instructions except you dont/cant do step 4.

---

### Post by runeh76 on 2010-12-28
umm does it work if u just plug ur usb?
Ubuntu have own scan-program no need to drivers.

---

### Post by Bucky Ball on 2010-12-28
> **runeh76 said:**
> umm does it work if u just plug ur usb?
Ubuntu have own scan-program no need to drivers.

Also an option. Plug in and switch on. See if detected and you are offered the drivers. They look like they need to be downloaded from Brother though, and unsure if they have drivers for 10.**

---

### Post by jpollman on 2010-12-28
Wow, that was quick! LOL

Sorry about that, I'm running it on an Acer Aspier 5515 laptop. It's the 32 bit Ubuntu. I'm hoping to be able to use the wireless printing/scanning function of this machine.

Thanks

John

---

### Post by Bucky Ball on 2010-12-28
OK. Try just plugging a cable in to see what happens but if nothing, try this. Go to System->Administration->Synaptic package manager and search for 'sane-utils'.

If it's not installed, install it. (In 8 here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#prereq))

Now, go to this page and download the 'cupswrapper driver' deb for your machine at the bottom of your machine's section (Format=deb).
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J415W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J415W)

Once downloaded, double click and install. You will see if there are dependency issues as the driver will not install and it will tell you what's missing.

---

### Post by jpollman on 2010-12-28
Thanks for the help Bucky Ball. But I don't think it's going to work. I fumbled my way through your instructions and it looked like it might work. I think I installed that utility you referred to. Then I downloaded and installed those drivers. When trying to setup a printer, I again clumsily worked my way through things and had it search for a network printer and my printer came up. I clicked on it and then it went to another section where I was supposed to select the brand and model of printer. I selected brother and a long list of models came up, unfortunately mine wasn't in the list. It looks like this isn't going to work.

I don't have the time or inclination to become a programmer and learn all of this stuff just to print a document. It looks like I'm going to go back to Windows 7 and forget Ubuntu. It looks like a good idea but it's just too darn complicated.

Thanks for trying!

Take care

John

---

### Post by jpollman on 2010-12-28
I decided to keep on trying for a while and I started over. That utility that is required is apparently already installed. I deleted anything previously downloaded and downloaded the driver again. Upon trying to install it, a screen comes up and there is an install button, but clicking on it does nothing.  In a box below the bar with the install button is this message.,,

[COLOR=Blue]**"Dependency is not satisfiable: MFCJ415WLPR"**[/COLOR]

Maybe there isn't a driver available for 10.10. Could I try to download and install an earlier version and see if it works?  Just a thought.

John

---

### Post by runeh76 on 2010-12-28
nah..windows is much better ;)

---

### Post by Bucky Ball on 2010-12-28
> **jpollman said:**
> I decided to keep on trying for a while and I started over. That utility that is required is apparently already installed. I deleted anything previously downloaded and downloaded the driver again. Upon trying to install it, a screen comes up and there is an install button, but clicking on it does nothing.  In a box below the bar with the install button is this message.,,

[COLOR=Blue]**"Dependency is not satisfiable: MFCJ415WLPR"**[/COLOR]

Maybe there isn't a driver available for 10.10. Could I try to download and install an earlier version and see if it works?  Just a thought.

John

System->Administration->Synaptic Package Manager. Search for '[COLOR=Blue][B]MFCJ415WLPR'. 

[/B][/COLOR]Install and try again. If there is another unsatisfied dependency the drivers won't work for 10.10 (unless we're going for the wrong one).

After installing the cupswrapper driver did you install the 'LPR Driver' (Format=deb) just above it then plug the computer in and switch the computer on?

One point: if you manage to get your printer setup, it will stay setup until you re-install or screw with the configuration file (and as you aren't into that it's unlikely).

---

### Post by jpollman on 2010-12-28
Looking at the release dates of the drivers and the Ubuntu versions, it looked like the drivers Brother had on their site may not have worked. They were dated a couple months prior to 10.10. I decided to bit the bullet and download 10.04 which was released prior to the date on the drivers on the Brother site. I went through and reinstalled everything. Got booted up and online. Things appeared to be working so I downloaded the printer drivers and installed them.  I tried the cupswrapper and that gave me the same dependency issue warning. I then downloaded the LPR driver in deb format. I installed it and it appeared to work.  Everything looked fine and it completed all of the processes.  When I go to set up the printer, it also appears to work and finds the printer on the network, but when it actually goes to find the driver a list comes up and my brand is there but not my model.  This is getting old REAL fast. I don't know how you do it.  Yes, Windows has issues. It may not be as secure and has glitches, but doing something as simple as setting up a printer is SIMPLE.

From what I've seen so far, you can have Ubuntu! I've spent the better part of a full day screwing around with this stuff and still don't have a working system.

John

---

### Post by davidmohammed on 2010-12-28
from my post at the beginning - did you follow the instructions as per the hyperlinked post?

---

### Post by jpollman on 2010-12-28
I saw that post and I read through it. It makes absolutely no sense to me at all. Thanks for the link though. I've got almost 24 straight hours of screwing around with this stuff and it's still not working. Say what you will about Windows, but it's EASY to work with for the most part. I'm going to shut down and put my other HD back in this machine with Windows 7 on it and get on with my life.

You guys can have your wonderful Ubuntu. I've got better things to do with my life than spend it becoming a programmer just to install a printer in my system. 

Thanks again for all the help, but I'm not going to be a convert! Take care and have a wonderful day.

John

---

### Post by davidmohammed on 2010-12-28
shame - sometimes stuff like this can be very frustrating.

I'm still around for a while to talk you through stuff.  Otherwise, good luck.

---

### Post by Bucky Ball on 2010-12-28
Never mind. Brother will eventually catch up. Ya see, your wasting your time blaming Ubuntu as many manufacturers do a half-assed job of creating Linux drivers so they look like they are supporting the Linux community. In fact, most don't really try that hard. When a new Windows comes out they rush to create the right driver for the job. Money talks.

If you had a HP printer on the other hand you would have been enjoying your Ubuntu OS for the last 23 hours and fifty minutes.

Good luck.

---

### Post by newbeeman on 2010-12-29
> **Bucky Ball said:**
> If you had a HP printer on the other hand you would have been enjoying your Ubuntu OS for the last 23 hours and fifty minutes.Good luck.
Not so sure about that! I've been trying for the last 3 days to install an HP  Photosmart 7760 on a 64 bit Ubuntu 10.10 Raid 1, and I'm still none the wiser.
Strange as I had it installed and working fine on my original 32 bit set up. Who said 64 bit is better?????????

---

### Post by judedawson on 2010-12-29
Hi jpollman,

Perhaps you may find some clues to help you with this problem at:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/BrotherPrinters/2070NLaser)

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters)

I can relate to your frustration. 

I too had problems with my printer (Canon Pixma iP1700) not working with Ubuntu 10.10. After checking the Ubuntu forums and trying out the suggestion contained therein, I arrived at one conclusion. This particular model may not just be compatible with Ubuntu. This is based on my observation that there are linux drivers for many Canon printers - BUT not for the model I have. I could be wrong here - it may be that I just haven't searched hard enough.

So, what I did was look for a printer that was compatible with Ubuntu straight out of the box (as this is what a normal end-user would want). Lo and behold! To my pleasant surprise, HP printers work effortlessly with 10.10. 

A friend gave me a HP F2410 (which prints, scans & copies). And whaddayaknow... printing OOo documents was easy. Scanning using the 'Simple Scan' app also worked with no problems at all. 

In summary, as an end-user & IMHO, the quickest and easiest thing to do is to use hardware that is compatible with Ubuntu.

Don't give up. 

From,
Jude

---

### Post by Bucky Ball on 2010-12-29
> **judedawson said:**
> 
in summary, as an end-user & imho, the quickest and easiest thing to do is to use hardware that is compatible with ubuntu.

Don't give up. 

From,
jude

+1. And if you have hardware that doesn't work with Ubuntu, get onto the manufacturer about giving a damn for Linux users and providing some decent, appropriate drivers for Linux. This stuff has not a lot to do with 'Ubuntu sucks'. Generally about manufacturers sucking for not giving a toss about anything but Micro$oft and Mac (not all manufacturers, of course!). ;)

---

### Post by judedawson on 2010-12-29
Thanks Bucky Ball,

That's very true...

Anyways...it's nearly the end of the year, so...in advance...HAPPY NEW YEAR 2011, all :p

---

### Post by Bucky Ball on 2010-12-29
And to you, Jude and everyone else. I'm having a 'day-before-new-year's-eve' beer to celebrate the occasion!

---

