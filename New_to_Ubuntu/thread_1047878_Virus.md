---
title: "Virus??"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by dave brown on 2009-01-22
Total newbee to Ubuntu, and have encountered a few difficulties, which I will address in a later post, but the current question is ......

If I set up a dual boot machine, with Windows in one partition, and Ubuntu in another and use  Ubuntu for all access to the internet, and e-mail, could a file downloaded here, infect the Windows side???

I'm thinking about dual booting my wife's laptop with Vista, and Hardy .... so that she can surf without jeopardizing the windows side, which is used for an accounting program... If this works.

Dave

---

### Post by emarkd on 2009-01-22
viruses are just programs.  it doesn't matter how the software gets to windows, if you run it you get "infected."  so if you were to download an infected email attachment in ubuntu but then transfer it to windows and open it, windows is now infected.  if you never share files between the two installations, then windows should remain clean.

---

### Post by dave brown on 2009-01-22
> **emarkd said:**
> viruses are just programs.  it doesn't matter how the software gets to windows, if you run it you get "infected."  so if you were to download an infected email attachment in ubuntu but then transfer it to windows and open it, windows is now infected.  if you never share files between the two installations, then windows should remain clean.
That makes sense ..... thanks

Dave

---

### Post by Dr Small on 2009-01-22
Yeah, if the two partitions never interact (you never transfer files from the Ubuntu partition to the Windows partition) then you are not going to infect the Windows Partition at all. Ubuntu can only run Windows Viruses inside of WINE, but then only WINE becomes infected, and not Windows.

---

### Post by jgoguen on 2009-01-22
> **dave brown said:**
> If I set up a dual boot machine, with Windows in one partition, and Ubuntu in another and use  Ubuntu for all access to the internet, and e-mail, could a file downloaded here, infect the Windows side???
It's not completely impossible, but the chances are pretty slim.  I haven't heard of it happening yet.  And if you don't mount the Windows partition in Ubuntu, the chances become a lot lower.  So take insanely low, then make it a lot lower :)

> **dave brown said:**
>  I'm thinking about dual booting my wife's laptop with Vista, and Hardy .... so that she can surf without jeopardizing the windows side, which is used for an accounting program... If this works.
What's the program called?  You should investigate whether it runs under WINE.  If it does, and it does everything you need, then there should be no need to keep Vista around (unless you want to of course).  If it doesn't run under WINE, there's one other possibility to avoid having to boot between systems.  If your Vista licence permits it (I believe permission is only granted for Vista Business and Vista Ultimate), and if your wife's computer is good enough for it, you may want to consider running Vista inside a virtual machine.  I know that Vista Home Basic and Vista Home Premium don't allow running them inside a virtual machine (although I don't know if that restriction is enforced by the system or if it's just in the EULA) so if you have one of those then the virtual machine idea won't work for you.

---

### Post by kyalee on 2009-01-22
I sure hope not, because that's exactly what we did on this computer. The windows side has the accounting program and the spreadsheets for the business while the Ubuntu side is for internet use. It's working pretty well so far.

---

### Post by dave brown on 2009-01-22
Hey!!!!....... I'm going to have a difficult time getting her to understand the idea of dual booting, much less anything as complicates as using wine ...... her idea of wine is Chardonnay.......

I THINK I can get her to understand Linux for internet/e-mail, and Windows (we won't confuse her with what version of either) is for the accounting program ...... particularly if I hide the icons for getting to those programs in Windows....

Thanks, though, as I will try your advice on MY machine ..... 

Dave

---

### Post by rosswmcgee on 2009-01-22
Open office does spreadsheets plus! Free

---

### Post by theozzlives on 2009-01-22
> **jgoguen said:**
> It's not completely impossible, but the chances are pretty slim.  I haven't heard of it happening yet.  And if you don't mount the Windows partition in Ubuntu, the chances become a lot lower.  So take insanely low, then make it a lot lower :)


What's the program called?  You should investigate whether it runs under WINE.  If it does, and it does everything you need, then there should be no need to keep Vista around (unless you want to of course).  If it doesn't run under WINE, there's one other possibility to avoid having to boot between systems.  If your Vista licence permits it (I believe permission is only granted for Vista Business and Vista Ultimate), and if your wife's computer is good enough for it, you may want to consider running Vista inside a virtual machine.  I know that Vista Home Basic and Vista Home Premium don't allow running them inside a virtual machine (although I don't know if that restriction is enforced by the system or if it's just in the EULA) so if you have one of those then the virtual machine idea won't work for you.

You can to run Vista Home Basic in VirtualBox.

---

### Post by achianese on 2009-01-22
> **dave brown said:**
> Hey!!!!....... I'm going to have a difficult time getting her to understand the idea of dual booting, much less anything as complicates as using wine ...... her idea of wine is Chardonnay.......

Dave

If the program works under wine, your wife might find using it this way to be easier than having to reboot to do different tasks. Once wine is installed, installing the accounting program is exactly the same as in Windows, and the shortcuts get automatically added into the Wine category under Applications

---

### Post by jimmy the saint on 2009-01-22
+1 for virtualbox.  It is incredibly easy to install.  You basically get a fake (virtual) machine that opens like a program.  You install windows to it and you don't have to reboot into windows.  You just open virtualbox and click the icon for your windows installation and watch it boot into its own window.  It functions the same and saves time.  plus you have a system restore feature that actually works because you can take a "snapshot" that you can restore almost instantly.

Did I mention that it is free? (as long as you already have a windows license of course)

---

### Post by MrKlean on 2009-01-22
If your doing accounting for a business...take a look at GNUcash.  I used it for my business and it worked fine.  That's when I switched to ubuntu full time ; )

---

### Post by jgoguen on 2009-01-23
> **theozzlives said:**
> You can to run Vista Home Basic in VirtualBox.
I know you physically can, but I thought that the licence says you're not allowed to?

---

### Post by jgoguen on 2009-01-23
> **dave brown said:**
> Hey!!!!....... I'm going to have a difficult time getting her to understand the idea of dual booting, much less anything as complicates as using wine ...... her idea of wine is Chardonnay.......
Then just don't tell her it's WINE, just tell her that it's the same program she's used to and she can click this right here to start it :)

When you install a program under WINE, it gets added to the WINE menu, under Applications -> Wine.  For example, I installed Microsoft Office 2007, and I have **Applications -> Wine -> Programs -> Microsoft Office** where all my MS Office shortcuts are.  If your accounting program works in WINE, then you could just install it and tell your wife "so now, you just go to Applications, go to Wine, then Programs, and click this icon right here".   You could even copy the item to the desktop if it isn't already done so she just has to double-click the desktop icon.  Wine is very simple to use.

---

### Post by billgoldberg on 2009-01-23
> **dave brown said:**
> Total newbee to Ubuntu, and have encountered a few difficulties, which I will address in a later post, but the current question is ......

If I set up a dual boot machine, with Windows in one partition, and Ubuntu in another and use  Ubuntu for all access to the internet, and e-mail, could a file downloaded here, infect the Windows side???

I'm thinking about dual booting my wife's laptop with Vista, and Hardy .... so that she can surf without jeopardizing the windows side, which is used for an accounting program... If this works.

Dave

No.

As long as you don't transfer files from Ubuntu to the Vista partition, your Vista partition is in no danger whatsoever.

---

### Post by leonardo_neo on 2009-01-23
Yes, Windows virus downloaded in Linux partition, once interact with Windows, then it can infect the Windows OS.

To keep it simple, I would recommend that, whatever you download from Linux, keep it in Linux partition itself. Windows can't access Linux partition, so your windows is safe.

---

