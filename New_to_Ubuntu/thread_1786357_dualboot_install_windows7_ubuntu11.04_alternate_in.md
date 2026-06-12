---
title: "dualboot install windows7 ubuntu11.04 alternate install cd"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by brianbeswick on 2011-06-19
Hi, I'm a newbie to linux. I've had a laptop with Fedora5 and 7, and recently installed ubuntu on the same machine, but I have totally broke it trying to make more room. I didn't allocate enough disk space to begin with. Anyways what I really need is some advice on dual booting windows 7 and ubuntu11.04 on a differnt laptop. It has windows factory instaled and I have a ubuntu11.04 alternate install disk. The computer has a 250gb hd and windows is taking up about 110gb total.I would like to have around 200gb for windows and about 50gb for ubuntu.I have never installed a dualboot machine and I don't want to mess up my windows instal, since I don't have a windows install disk. Any advice would help. Thanks in advance.:???:

---

### Post by jerrrys on 2011-06-19
do some reading first

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot&sa=Search&cof=FORID:9#941](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot&sa=Search&cof=FORID:9#941)

---

### Post by nzjethro on 2011-06-19
I found [this article ]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")very useful for a Maverick Meerkat/Windows 7 dual boot. I imagine most of the theory would apply to 11.04/Win7 too.

---

### Post by Rubi1200 on 2011-06-19
Hi and welcome to the forums brianbeswick :)

I think you will find the information you need in the following links:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

You can create restore disks for Windows following this guide:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Most important of all before you start, backups!

---

### Post by Arbayong on 2011-06-19
I guess all windows 7, ubuntu natty 11.04 questions have been answered. my hdd is also 250gb and the laptop came with windows 7 preinstalled. am running natty narwhal and windows 7 on same pc. more so i use nattty to access my in the windows (ntfs) partition. welcome to ubuntu.

---

### Post by brianbeswick on 2011-06-19
Thanx guys, I did find the articles you are referring to. And I was able to shrink my windows partiton and install ubuntu. Thats how i'm posting this, and why it took so long to reply. so far so good, but I'm having trouble with my display. My laptop monitor is cracked and I'm running an external monitor. It seems to be working except not all of the windows are 100% in the workspace. When I click on the icon to change work spaces I can see the rest of the window in the other workspaces. I hope you can understand all that. And again thanx for the info. much appreciated.

---

### Post by nzjethro on 2011-06-19
Good to hear you got the install doing what you wanted. The windows-between-workspaces is an Ubuntu feature desinged so that you can easily transfer your open programmes or windows between virtual desktops (i.e. workspaces). If you want your windows to be entirely on one workspace, click the top menu, and drag the window to where you want it. Alternatively, if you double click the window menu-bar at the top, it will maximise the window to its current workspace, so that the entire window will be on the one desktop.

---

### Post by brianbeswick on 2011-06-19
Thanx again. On my older dell (farewell):sad: with ubuntu 11.04 I never noticed not all of the windows not being entirely in the same workspace.huh?:???:Anyways hows the XFCE desktop. I've seen an example awhile back and thought about it. I really liked kde on my fedra machine and thought about FC14. The desktop i have now isn"t the same as the one one on my dell. Ghnome is what it had. I'm not sure what I did different but its not ghnome I don"t think. Oh well thanx . Oh ya, can I run xfce on this install?

---

### Post by wildmanne39 on 2011-06-19
> **brianbeswick said:**
> Thanx again. On my older dell (farewell):sad: with ubuntu 11.04 I never noticed not all of the windows not being entirely in the same workspace.huh?:???:Anyways hows the XFCE desktop. I've seen an example awhile back and thought about it. I really liked kde on my fedra machine and thought about FC14. The desktop i have now isn"t the same as the one one on my dell. Ghnome is what it had. I'm not sure what I did different but its not ghnome I don"t think. Oh well thanx . Oh ya, can I run xfce on this install?Hi, yes you can run xfce, just install if from synaptic or software center.

---

### Post by brianbeswick on 2011-06-19
> **wildmanne39 said:**
> Hi, yes you can run xfce, just install if from synaptic or software center.
Cool Thanx! On my fedora install I could run kde or Ghnome at the login screen. Will this be the same thing.

---

### Post by zero244 on 2011-06-19
I have a HP laptop which I tried to dual boot with Windows 7. Unfortunately HP uses four primary partitions, so I was unable to install Ubuntu alongside Windows.
If I had some decent 64 bit disk management software I could of probably got it work, but I don't.

So on this laptop I said heck with it and got rid of Windows altogether.
This is the first time Ive owned a computer that I didn't at least dual boot with Windows and I don't miss it.

Im running Lucid and really like it.
I was going to install Pinguy but it is still a little rough around the edges so I settled on the very solid Lucid.
Ubuntu and Linux in general have come a long way since I started using linux.

Ubuntu 11.04 was working good as well, but I think I prefer gnome.

---

### Post by nzjethro on 2011-06-19
@ Brianbiswirk: Yes it will. I have Xfce and Gnome on here, and when I log in I can choose which to run. Run

```
sud apt-get install xubuntu-desktop
```

This will install the Xfce DE, and the necessary Xfce packages (like thunar file manager). I really like Xfce, I find it a lot more customisable than Gnome, and more intuitive, but that's just me. They say Xfce is lighter too, but I haven't noticed any performance increase (I think because it is Xfce on Uuntu with Gnome, as opposed to a minimal Ubuntu install with Xfce overtop).

To install KDE as well, use

```
sud apt-get install kubuntu-desktop
```

But be warned, this will download all the Kubuntu applications (like Konsole, Abiword, etc.) and these will appear in your menus as well as the Gnome apps whichever DE you are in. Some find this a convenience, but I personally didn't like it. Also, the format of the kubuntu-desktop package (it's an empty package that just points to the required packages such as Konsole etc) means that if you want to remove KDE, you must manually remove all of the Kubuntu apps, rather than running apt-get remove kubuntu-desktop.

---

### Post by brianbeswick on 2011-06-19
> **zero244 said:**
> I have a HP laptop which I tried to dual boot with Windows 7. Unfortunately HP uses four primary partitions, so I was unable to install Ubuntu alongside Windows.
If I had some decent 64 bit disk management software I could of probably got it work, but I don't.

So on this laptop I said heck with it and got rid of Windows altogether.
This is the first time Ive owned a computer that I didn't at least dual boot with Windows and I don't miss it.

Im running Lucid and really like it.
I was going to install Pinguy but it is still a little rough around the edges so I settled on the very solid Lucid.
Ubuntu and Linux in general have come a long way since I started using linux.

Ubuntu 11.04 was working good as well, but I think I prefer gnome.
Thanx for the input. I to gave  xp the other boot for FC5 upgraded to FC7, then on to ubuntu, unfortunately I can"t get my cdrom drive to work any more, bad connection on the MB, on that computer or I'd still be using it.I some how managed to lose my fstab file while trying to make more room. Lesson learned. But in the destruction came the laptop I have now, a $5.00 box of parts from the flea market, Acer aspire 5534 Athlon 64 x2, 4gb ram, ati radeon 3200 250 gb hd. I had to fix the AC plug, and it has cracked screen otherwise its been great. Anyways hows Lucid?  I've never heard of pin guy. oh well thanx for the input.

---

### Post by brianbeswick on 2011-06-19
> **nzjethro said:**
> @ Brianbiswirk: Yes it will. I have Xfce and Gnome on here, and when I log in I can choose which to run. Run

```
sud apt-get install xubuntu-desktop
```

This will install the Xfce DE, and the necessary Xfce packages (like thunar file manager). I really like Xfce, I find it a lot more customisable than Gnome, and more intuitive, but that's just me. They say Xfce is lighter too, but I haven't noticed any performance increase (I think because it is Xfce on Uuntu with Gnome, as opposed to a minimal Ubuntu install with Xfce overtop).

To install KDE as well, use

```
sud apt-get install kubuntu-desktop
```

But be warned, this will download all the Kubuntu applications (like Konsole, Abiword, etc.) and these will appear in your menus as well as the Gnome apps whichever DE you are in. Some find this a convenience, but I personally didn't like it. Also, the format of the kubuntu-desktop package (it's an empty package that just points to the required packages such as Konsole etc) means that if you want to remove KDE, you must manually remove all of the Kubuntu apps, rather than running apt-get remove kubuntu-desktop.
Yeah, I'm still debating on that. I wish I could have done that before the ubuntu install, I guess I'm a little impataint when it comes to important things, Ha! but I think I will try it tomorrow. Thanx for the lines!

---

