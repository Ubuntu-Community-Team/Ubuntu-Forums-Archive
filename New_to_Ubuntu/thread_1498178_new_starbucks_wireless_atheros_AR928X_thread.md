---
title: "new starbucks wireless atheros AR928X thread"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by henry cow on 2010-05-31
The old thread about my Acer Atheros wireless laptop not connecting at Starbucks was getting cumbersome.

We (several of us, THANK YOU !) have exhausted at least a dozen otherwise sound ideas that did not work.

It seems painfully obvious to me that neither the native Linux drivers nor the Windows 7 drivers can be made to run this card. I am tired of trying, and don't want to keep junking up clean Lucid installs.

In fact, when and if I make this work, I intend to spend a couple of hours and do yet another clean pure install wherein the wireless connection is the first thing that goes up on it.

Now I believe I know enough to create a concise and straightforward request - 

I want to find, download, and install a Windows XP-64 driver (or Vista if someone actually vouched for it, rather than just taking a stab in the dark) for the Atheros AR928X wireless card, and get it running under Lucid desktop AMD-64.

Just that, for now at least.

Googling: Atheros AR928X driver returns what looks like a plethora of choices but they all seem bollixed up one way or another. 

I have already downloaded "MRDWLL-00203979-XP.EXE" and "Wireless LAN_Atheros_7.7.0.343-Vistax86_A.zip" which looked promising, but I have not done anything with them yet.

Also, I am not experienced at extracting and executing files under Linux, there seem to be a lot more steps than in Windows.

Who is ready to help a very nice but very frustrated guy?

---

### Post by Penguin Guy on 2010-05-31
Can't offer any help apart from suggesting you check [COLOR="Green"]System -> Administration -> Hardware Drivers[/COLOR], but I can point you to a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557414"). Good luck.

---

### Post by NUboon2Age on 2010-05-31
1) The .zip file is much easier to work with so I'd start with that.  Once you've unzipped the files (using file-roller probably which will likely pop open automatically if you double-click on the .zip file)... 

2) {skip down #3 and only return here if the .zip file doesn't contain what you need and it comes to requiring what is in the .exe file}... I'm not sure, but I'm guessing it is an installer.  One approach would be to install Wine (no problem using Synaptic), then select the file and open it's properties and check the box that allows it to be an executable file).  Then double click on it and as it (hopefully) it goes through its installation routine and puts the files somewhere where you can find them (Search for Files for the corresponding .sys and .inf files).

3) Since this is one of those cases where you're needing to use a Windows driver, **If** in the things you've downloaded you've got the correct Windows drivers and therefore the correct .inf (and .sys) files, **then** here's how to get them installed: **ndisgtk**.  ndisgtk will properly install and handle all the blacklisting of other drivers and modprobe and all that jazz. ** Go to link #2 **in my signature for my complete rundown of how I used it to get my system working.

---

### Post by NUboon2Age on 2010-05-31
This bug seems to be what you're experiencing: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/557414) It would benefit yourself and others if you would sign on, affirming that its a problem for you and subscribe to it and leave a note commenting that you're experiencing it too.  Here's a link that helps us beginners on bug reporting:  [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by henry cow on 2010-05-31
Hey folks - 

I am typing this via a wireless connection on my Atheros AR928X via Lucid!

Can you believe it, I can't.

NUB had the answer, (so did Dave) the Windows XP driver worked like a charm. Obviously, the later stuff just hasn't caught up yet.

If any of you are reading this because your Atheros AR928X wireless card will not work under Lucid, get the Windows XP driver and run that. One of these days there may be a better choice, but this worked for me when everything else failed. I wish I had tried it first instead of 15th.

There are a few strange anomalies, for example the switch button for the antenna seems to work now, but not the LED. It stayed on solid after the latest clean install of Lucid, even though not connected, but installing the wireless driver seems to have turned it off permanently. Mildly annoying, but no biggie.

Whether ethernet or wireless, it seems that whenever I make any connection change such as unplugging the ethernet or switching the button off or on, I am dead until I reboot. Is there not "hot switching" in Linux? In Windows I can go back and forth at will.

All-in-all, this has been quite a learning experience for me, and an acid test of my dedication to my migration from Micro$oft. If I had not been trapped in a hotel room out of town for weeks on end I am not sure if I could have pulled through.

Meanwhile, if anybody else has an Atheros wireless card under Windows 7 that will not run under Lucid, don't waste countless hours trying convoluted fixes, get the XP driver below and be online in minutes. 

Trust me, that is the way to go.

---

