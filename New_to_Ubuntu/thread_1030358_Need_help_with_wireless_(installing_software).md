---
title: "Need help with wireless (installing software)"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by joeh100 on 2009-01-04
I'm trying to get wireless working on my computer (Xubuntu).  I know there are difficulties with my wireless card, and the only way I could get it working with SLAX Linux was to install wlassistant.  Strangely that card works out of the box with puppy linux with hidden broadcast and wpa2 security.

I tried to download wlassistant and install into xubuntu but it says dependencies missing or something like that.

I also heard that wicd is a good program for this also, but it seems you need an internet connection to install.  

I am a total newb to linux.  How do I get either wlassistant or wicd into my xubuntu computer from my windows machine.  I will be transferring the file with a thumb drive and can't use the package manager???  I think I need a certain "build", which I think is just compiled code set to work on a certain version of linux (my case Xubuntu).  I have no idea how to do this.

Thanks in advance,

Joe

---

### Post by twiz86 on 2009-01-04
Try to install it again and write down the dependencies it requires exactly as it outputs them. then open applications > Accessories > Terminal.

Type
Sudo apt-get install dependencypackagenamehere

once thats done try reinstalling it. 

Hopefully thats all you have to do, that is usually my first step when i have such problems. I am also a newb, been using for 4 months windows free now. Hope you grow to love ubuntu.

PS. you can also goto system > Administration > Synaptic package manager and search for it there, that may be easier.

---

### Post by gn2 on 2009-01-04
Welcome to the Ubuntu forums. :)

To install Wicd, first you need to mark network-manager for removal (don't mark it for complete removal) in Synaptic Package Manager, then install Wicd.

You can download the Wicd .deb from [here]("http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460") on your windowbox, then transfer it on your thumb drive.

If during the install process you get advised of any missing dependencies, make a note of them then you can search for and download them from [here]("http://packages.ubuntu.com/").

---

### Post by handydan918 on 2009-01-04
> **joeh100 said:**
> I'm trying to get wireless working on my computer (Xubuntu).  I know there are difficulties with my wireless card, and the only way I could get it working with SLAX Linux was to install wlassistant.  Strangely that card works out of the box with puppy linux with hidden broadcast and wpa2 security.

I tried to download wlassistant and install into xubuntu but it says dependencies missing or something like that.

I also heard that wicd is a good program for this also, but it seems you need an internet connection to install.  

I am a total newb to linux.  How do I get either wlassistant or wicd into my xubuntu computer from my windows machine.  I will be transferring the file with a thumb drive and can't use the package manager???  I think I need a certain "build", which I think is just compiled code set to work on a certain version of linux (my case Xubuntu).  I have no idea how to do this.

Thanks in advance,

Joe
Try downloading the deb [here]("http://downloads.sourceforge.net/wicd/wicd_1.5.0rc13_all.deb?modtime=1217680154&big_mirror=0")

and do ```
sudo dpkg -i /path/to-packagename
```

I haven't use xfce much so I'm not familiar with any gui frontends that may exist for installing a local package, maybe an xfce user will have a better idea.

---

### Post by joeh100 on 2009-01-04
Thanks guys, I got wicd installed but it didn't do the trick.  I know wlassistant will because it worked on the same computer with the same wireless card (on SLAX linux anyway).

The wlassistant file I tried to install wasn't a .deb file though, maybe that was the problem.

Now I have the .deb file of wlassistant.  When I try to install, I get the error: Dependency is not satisfiable: kicker

---

### Post by gn2 on 2009-01-04
> **joeh100 said:**
> When I try to install, I get the error: Dependency is not satisfiable: kicker

Satisfying dependencies manually is a P.I.T.A. 

You will need to get the relevant kicker package [here]("http://tinyurl.com/7jb2sd") and install it.

---

### Post by joeh100 on 2009-01-04
Well, I got the kicker package and it has dependencies.  Those depencies have depencies, etc.  I can see where this is going.

Is there a way to get the entire wlassistant package for xubuntu or am I just screwed.

This computer doesn't have a network card for a wired hookup.  It only has wireless.

---

### Post by gn2 on 2009-01-04
In similar circumstances as you are now in (dependency hell) I bought a cheap wired network adapter on eBay....

EDIT: But if you will primarily be using wireless, it might be better to source a known working wireless adapter.

---

### Post by kwacka on 2009-01-04
What card are you using?

---

### Post by ugm6hr on 2009-01-04
> **kwacka said:**
> What card are you using?

I would suggest you give more info before proceeding.  You may be mistaken about what the problem is; hence, wlassistant may not be the solution.

Give the output from:
```
lshw -class network
lspci
lsusb
```

---

### Post by joeh100 on 2009-01-04
The card is a linksys wpc54G.  Like I say, there are supposedly problems with the driver and there is supposed to be a workaround.  SLAX Linux and Ubuntu are using the same driver though because I used a command to find out.  Can't remember now but I'll post this evening.  I think it was something like bcm4306.  Broadcom chipset. 

I have been down this road before with SLAX Linux.  Someone there said to forget the driver issue and just download wlassistant and it worked like a champ.  I just downloaded it from the slax site and transferred it with a thumb drive.  [http://www.slax.org/modules.php?action=detail&id=383]("http://www.slax.org/modules.php?action=detail&id=383")It would be nice to try.

I will give the output from the following code this evening.  I don't have the linux pc running right now.
lshw -class network
lspci
lsusb

---

### Post by kwacka on 2009-01-04
Sometimes manufacturers swap internals but keep the same model number, searching this forum for WPC54G suggests that the card uses a Broadcom 43xx which is so common that it is unlikely to be the case.

If, as suggested, you can beg/borrow/buy a wired card there will be no problem - package b43-fwcutter will install the restricted drivers & problems over. (hopefully ;) )

BTW if you use ```
gksudo gdebi ./filename.deb
``` it will attempt to fetch & install dependencies - most (if not all) of which are likelt to be on the Xubuntu disk.

---

### Post by joeh100 on 2009-01-04
I've got it up for now on a wired usb net adapter.  I just updated the system for now, but I'll try to tackle the wireless problem again tomorrow.

Can anyone suggest a low resource browser that will do flash.  Firefox and Flash 10 are kinda maxing out the system (RAM).  I guess the swap is taking up the slack, but it's slow.

It only has 128 MB of ram right now but I'll probably add more if I can get it for this PC, and if I get wireless going.

This PC actually ran SLAX linux great, but SLAX was to buggy.

Thanks,

Joe

---

### Post by gn2 on 2009-01-04
Zenwalk might be worth a try, it's quite a polished distro based on Slackware.

---

