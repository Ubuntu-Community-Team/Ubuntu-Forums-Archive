---
title: "Please help! Totally lost here"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by stevehambling on 2010-07-05
My hard drive crashed and I have installed a new one. I have just installed Ubuntu as the OS instead of Windows. The initial instal was smooth, but I have no Internet connection. All of the help that I search for is written in completely technical language. There is nothing in plain English. I really want to muse this system, but it has to be simpler than  I have seen so far surely?

I just need to install a driver to get my hardware working, but the answers on the web are impossibly technical. I'm just a normal user, not particularly technical. Please can someone point me at some simple non jargon filled help? I need something that says "install driver" not ndiswrapper lshw blah blah blah.

All help very gratefully received

---

### Post by howefield on 2010-07-05
How are you connecting ? 

If you can connect via a wired connection, perhaps you could try updating and looking at System > Administration > Hardware Drivers.

The easiest way of updating your list of available packages would be to open a terminal , Applications > Accessories > Terminal and typing

```
sudo apt-get update
```

You'll be prompted for your password which you won't see being typed, but it is, press enter.

Once it is finished updating, try the aforementioned Hardware Drivers.

---

### Post by stevehambling on 2010-07-05
Hi

Thanks for replying. I am writing this from my other pc. The ubuntu laptop has no connectivity at all, so an update is not an option. I can connect a CD drive and download from the pc to the CD. How do I even find out which hardware I have in order to find the drivers please? Control Panel in Windows was slow, but at least it listed everything

---

### Post by BikeHelmet on 2010-07-05
Are you trying to connect through wireless or wired?

Can you open a terminal window, then type this in, and copy the results back into a new post?

```
sudo lshw -C network
```
It'll prompt for your password, then spit out info on what your network adapter is, so someone smart can figure out what you need to do to get it working. ;)

And just to verify - you have tried clicking the little network icon, and telling it to connect? Some network adapters don't auto-connect.

I've got a NAS that didn't auto-connect in 10.04 - but a later update broke the wired support entirely, so I had to go back to Ubuntu 9.04.

---

### Post by LittleGyko on 2010-07-05
hi steve.

I was in your position a few weeks ago. i was trying to install ubuntu 10.04, informally called lucid lynx. 

in my case, the installation was smooth. since you say that you are an absolute beginner, are you having trouble with making partitions etc.? 

after installation, i connected my laptop to the network using a wired connection as it refused to auto detect my wireless, since some drivers were required to get my wireless adaptor working. once on the internet, ubuntu will automatically download the drivers and do the necessary, ( if my memory is correct). if this does not happen, then on the bar you see on the top of the screen go to System> Administration> Hardware Drivers. 

hope that is of some use.

WARNING: Since I am a newbie, you might want to take advice of others more seriously :)

---

### Post by stevehambling on 2010-07-05
Ok, I've tried that code, I just get "PCI (sysfs" then get the prompt again. I looked in Hardware drivers too, nothing there either.

---

### Post by BikeHelmet on 2010-07-05
Really?

Have you checked to make sure your wired isn't disabled in the BIOS?

Okay, try this one:
```
sudo lshw
```

It'll spit out TONS of output. Copy it all... :) (it may help to have a USB stick handy)

---

### Post by LittleGyko on 2010-07-05
it printed 600+ lines for me :)

---

### Post by stevehambling on 2010-07-05
Ah! good call. I had to disable everything a couple of weeks ago to get the hard drive to boot and recover my data. Rebooting now with everything enabled again.

Fingers crossed...

---

### Post by stevehambling on 2010-07-05
Bingo, I have Internet. thank you for the amazingly fast help.

Still worried about that terminal screen, it doesn't look like a step forward to me, but at least I'm up and running.

Thanks again

Steve

---

### Post by BikeHelmet on 2010-07-05
> **stevehambling said:**
> Still worried about that terminal screen, it doesn't look like a step forward to me, but at least I'm up and running.
It's not that hard to use. Ubuntu actually has GUI front-ends to most of those tools, like lshw. But they aren't installed by default, because of the 700MB download. Bundling them all would push it to 2GB+ :p

For situations like when your networking is broken... where downloading a GUI tool isn't an option... CLI to the rescue! ;) 

If it's any condolence, often in Windows these commands save the day. :P
```
ipconfig /release
ipconfig /renew
ipconfig /flushdns
```

Yes, they're command-line too.


> **stevehambling said:**
> 
Thanks again

Steve
Cheers, mate. :)

---

