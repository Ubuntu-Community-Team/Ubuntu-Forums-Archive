---
title: "internet monitoring software for 64-bit linux. The alternative? WINDOWS! X_X"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by mooglinux on 2008-01-05
I am in need of a replacement for Spector Pro 6 for 64-bit ubuntu. Really the best thing is software that can monitor all internet traffic and logs the web-pages visited, and it needs to be useable by someone who is not computer savvy (a GUI is a must) and cannot easily be deactivated. It would be great if it would sent a message or log something to say that it had been deactivated, even by root. 

The trouble with other solutions i have seen, such as Dansguardian and Net Accountability is that they do not function under 64-bit linux. I already had to do one reinstall after installing dansguardian and finding that i could not access the GUI. I have looked at things such as Wireshark but thats too complex and creates massive logs that are too cumbersome to work with. 

So to sum up, i need a solution to do the following:
1) Keep close track of websites visited
2) Have a GUI that is easy to use 
3) Be impossible to circumvent, and as hard as possible for someone with just the sudo password to disable. Preferably have its own password? At minimum it should log whenever it was disabled, even send an email.
4) Work in 64-bit ubuntu, if at all possible. Changing to 32-bit will be an absolute last resort. The alternative is *shudder* Windows!

---

### Post by mooglinux on 2008-01-06
Another quesiton, will squid or another proxy do this? or can it be setup to do this?

---

### Post by Miademora on 2008-01-06
If you have the rootpassword you can do all you want just like on windows. If you have the ability to open the pc or boot from a cd/usb-stick/floppy/netboot you can surf where you want without any traces. Or just plugin a laptop in the wall and youre done. Not to mention there are several sites available that gladly proxy http-traffic so most of these blocklists are not really efficient and as soon as https-traffic is involved you cant look at anything.

Your best choice would be a separate pc/router in a secure location where you define rules wich traffic gets routed and wich websites get accessed. With an enforced proxy like privoxy/squid. Then setup notifications for accessviolations.

So who do you want to control? secretary? kid(age?)? wife? coworker? how good is their technical knowledge? financial opportunities?

Ive seen several patches for dansguardian 64bit. Maybe its better to follow that road. Dont know if youve already tried hard enough.

---

### Post by mooglinux on 2008-01-06
Well, a seperate pc would be possible, but not easy. As for getting around the root acess issue, if it sends an alert to notify someone that it is being deactivated, that may be sufficient. While it would be possible to tamper with the program files, that will probably be too much trouble.  I have not seen any 64-bit patched for dansguardian, if you could point me in the right direction that would be great. 

while there are always ways to get around barriors, i would like to make it difficult enough that it wont be worth it.

---

### Post by Miademora on 2008-01-06
I havent tried these myself but 64-bit versions seem available here:

[http://linuxappfinder.com/package/dansguardian](http://linuxappfinder.com/package/dansguardian)

[http://packages.debian.org/en/sid/dansguardian](http://packages.debian.org/en/sid/dansguardian)

As soon as you have root you can easily block any external notification with a simple iptables rule and then do whatever you like. Just modify logfiles later. A kernelspacemodule could possibily still get something off if you dont unplug the cable but i dont know if something like that exists. Nothing can stop root :)

---

### Post by mooglinux on 2008-01-06
modify the iptables? sounds a bit tougher than the average user can do, even with root. doable, but definatly more secure than nothing at all. first thing i should have done is search synaptic because i found that there is a dansguardian package right there, presumably compatible with 64-bit. ill give that a go and see how things are

---

### Post by mooglinux on 2008-01-06
Well dansguardian itself works fine in 64-bit, but i need a gui to access it from, rather than toying with logfiles. Another option i have come across is smoothwall, so does anyone know how wel that would work for me?

---

