---
title: "[SOLVED] Need Some Hardy Handholding"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by vikramaditya on 2008-07-06
I know this has been discussed before, but the solutions I've researched so far (thank you, kind contributors :)) have not worked.

I installed Hardy on my Dad's box a couple weeks ago (xp dual boot) and _everything_ "just worked".  So, what did I do next?  I installed wicd cuz I like it on my own machine.  **Bad, bad dog!**  Wicd failed to connect & I'm not enough of a guru to figure out why.  To make matters worse, I am now unable to restore network manager.  I've tried installing from the Live CD in the Synaptic repos, even disabling all other sources.  Synaptic still insists on grabbing it from a remote repo.  Also tried
> sudo apt-cdrom add
sudo apt-get install network-manager-gnome
to no avail.  Can someone give me a detailed, spoonfed, handholding, step-by-step procedure for reinstalling the frickin' network manager???  And, if it involves downloading the debs from **packages.ubuntu**, which ones should I get for the most recent Hardy kernel?

---

### Post by Arthur Archnix on 2008-07-06
Search for threads that explain how to connect to your wireless without any manager. All the underlying tools are there already. If you've got an unsecured network (bad!) it's as easy as adding a few lines to your interfaces file then restarting the network daemons and issuing a dhclient wlan. If you've got a secured network follow this thread

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

then just use synaptic to insall network-manager and it will take over on your next boot. 

Good luck.

Update: oh, and did try sudo apt-cdrom without the add. Then sudo apt-get update. Then sudo apt-get install package

It's possible the add isn't necessary.

Update 2: scratch all that. add is necessary

---

### Post by doas777 on 2008-07-06
one thing to try, is after disabling the other sources, you run:
```

sudo apt-get update

```

might help. usually sorts out the which repo kinda issues.
good luck

---

### Post by vikramaditya on 2008-07-06
> **Arthur Archnix said:**
> Search for threads that explain how to connect to your wireless without any manager
Sorry, I neglected to mention it's a wired connection.  Thanks for the response, though . . . :)

---

### Post by vikramaditya on 2008-07-06
> **doas777 said:**
> one thing to try, is after disabling the other sources, you run:
```

sudo apt-get update

```

might help. usually sorts out the which repo kinda issues.
good luck
Thanks, but already tried that beeyatch too! :(

---

### Post by Arthur Archnix on 2008-07-06
Post the output of these commands, we'll figure out the problem, then give you directions on how to fix.

```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
sudo aptitude show network-manage*
sudo apt-get install network-manager network-manager-gnome
```Output of each one please.

Oh, and just out of curiosity, does this computer have wireless, or just wired?

---

### Post by vikramaditya on 2008-07-07
> **Arthur Archnix said:**
> Post the output of these commands, we'll figure out the problem, then give you directions on how to fix.
Thanks, AA . . . I won't be at Dad's again until July 13, but I'll do as you suggest then.

His connection is wired only.

---

### Post by Arthur Archnix on 2008-07-07
No worries. In that case, remove wicd and network-manager, both are really only useful for wireless devices. Instead, gnome has a network ummm manager, that you can use to setup the connection.

It would be in system, then under networking I think. You just have to enable the device, and tell it to use dhcp or some such. Anyway, that's the route I recommend for wired only.

But post back if you have trouble.

Best,

---

### Post by vikramaditya on 2008-07-08
> **Arthur Archnix said:**
> Instead, gnome has a network ummm manager, that you can use to setup the connection.
Thanks for that useful info!  After googling a bit, I learned that Dad's ISP uses DHCP.  Correct me if I'm wrong, but that apparently means I can just nuke wicd & network manager, set the native gnome network thingy to DHCP, & it'll do all the dirty work automagically, resulting in (yayyyy!) instant internet! :D Or, will I still have to wade thru (ugh) a confusing sea of networking BS? :(

It's extremely irritating that nearly everything I find regarding connectivity in this OS has to do with wireless! :mad:

---

### Post by Arthur Archnix on 2008-07-08
Well, I only use wireless, so I've got a different take on that. :)

This link has a picture of what you're looking for. 

[http://www.gnome.org/projects/gst/](http://www.gnome.org/projects/gst/)

The network settings.

And yes, nuking network-manager and network-manager-gnome is a good way to clean up his internet connection and gain a little system performance to boot.

---

### Post by vikramaditya on 2008-07-09
Thanks again, AA :)

I'm gonna try this medicine on myself before mucking about with Dad's box.  Just wondering, should I take screen caps of the info now displayed in "Network Settings", or will it "just work" with DHCP enabled?  If I disappear for awhile, you can just assume I've bolloxed everything up! :(

---

### Post by vikramaditya on 2008-07-14
I nuked wicd on Dad's box today & went to System > Administration > Network > Unlock > checked "Wired connection" > clicked "Properties" > checked "Enable this connection" > set "Configuration" to "Automatic configuration (DHCP)" > clicked "OK" > clicked "Close" & voila - cable connection now working flawlessly! :) Thanks again, AA! =D>

---

