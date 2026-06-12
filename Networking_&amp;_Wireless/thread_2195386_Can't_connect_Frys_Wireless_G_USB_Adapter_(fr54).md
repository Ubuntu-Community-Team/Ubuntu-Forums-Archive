---
title: "Can't connect: Frys Wireless G USB Adapter (fr54)"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by sirsoar on 2013-12-23
Hello there guys~ Feel free to call me whatever you'd like. 

So recently, I installed Ubuntu 12.10 as a last resort to my Windows XP OS being broken for unknown reasons. 

My first problem, is trying to make my wireless adapter work so I can get some internet on this thing. I use a Frys Wireless G USB Adapter (fr54) and I've been
trying to install the drivers for it, but with too many errors in the way. I tried this "ndiswrapper" program, but I can't seem to install the package onto my system. 
I get a grayed out "Install" button in Ubuntu's software center. 

Second, I tried to install "mypaint" program, but I've no idea why it won't open... (extracted and it shows up on "Dash Home" but nothing happens when I click it)
I checked out some video guides on installing it, but whenever I use the "sudo ......" commands, it asks for a password which I cannot even input anything. 

Third, a question, how do you run .exe files to install or run programs? 

Thank you to anyone who helps me with these basic newbie problems. If this doesn't go well, I'll be switching back to XP. Vice versa I'll be staying to learn more about this os.

---

### Post by whitesmith on 2013-12-23
Welcome to the forum! First of all, Linux doesn't use the Win scheme of denoting an executable program by giving it an extension. Instead it uses permissions to determine what executes. Try```
info chmod
```for details or look up 'chmod (Unix)' on Wikipedia. For this very reason Windows EXEs won't run directly under Linux. That requires Wine. Stay with us. You will be rewarded with wisdom. Leave, and you will only encounter knaves who offer up bromides in return for your money. Seriously, we're a fun group working/playing with a fun OS!

---

### Post by devine.steve on 2013-12-23
.exe files are Microsoft programs. They are not going to run on your computer. But don't despair, for everything you can do in Windows there is almost always a comparable program in Linux.
sudo is the method by which you do 'administrative' tasks. the password is whatever your login password is.
Are you sure the wireless isn't working?

---

### Post by QIII on 2013-12-23
When yo are prompted for the password in the terminal, just type carefully and press enter.  Nothing will show on your screen.  That's normal.

---

### Post by Bucky Ball on 2013-12-23
Welcome. Can you get online with a cable? if so, do that, do an update and try the wireless again. Forget ndiswrapper. Nightmare which will probably cause more issues than you have already and largely superseded. Consequently, whatever how-to you're reading would be old, out-of-date, and likely won't work with a newer release. 

Plug in USB adapter, open a terminal (Applications>Accessories>Terminal but there's probably a quicker way) and add these commands, one after the other, hitting return after each:
```

lsusb
sudo lshw -C network
```

Post the results of each back here.

When you installed Ubuntu, did you try simply plugging the USB device in? If so, what happened?

* Update: After a bit of sniffing I'm thinking the wireless card used by your dongle is the Realtek RTL8192su. That works in Ubuntu without issue, as do most Realtek things, no ndiswrapper required (although that may well be now blocking anything else you try, including the correct driver). 

My advice is to completely remove ndiswrapper for now and provide the output of those two commands I gave, doesn't need to be in that order. ;)

This might help there:

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Uninstall_HowTo)

PS: No offence, but you may want to do a little more research on what Linux is and isn't so you have a better understanding of what you're working with. This is what it's not. 

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

PPS: As for mypaint, it is in the repositories (Software Centre) so just install it from there. Absolutely no need to start compiling, making, extracting. Just complicating things. Always look in the SCentre (or Synaptics) first, failing that, look for a .deb file (that will install automagically) or a PPA.

You could have also opened a terminal and simply:

```
sudo apt-get install mypaint 
```

Done.

.exe files problem is covered which leaves only the wireless issue. Consequently, I'll move this thread to somewhere you might get more focused help on that:

*Thread moved to **Networking & Wireless.***

(Just a tip: Post separate threads for individual problems. Less confusing and you will get better support. Also, descriptive thread titles will get you far. I have changed this one to help your cause. If you want it changed to something else, just PM me with a couple of suggestions. The new title only appears here on the first post but is the one that will appear in the list of support threads when people are looking to help. ;))

---

