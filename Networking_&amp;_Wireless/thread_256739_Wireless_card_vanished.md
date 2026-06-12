---
title: "Wireless card vanished?"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by themusicwave on 2006-09-13
My wirless was working perfectly until recently.  I tried to install a VPN client upplied by my college campus and now everything is all messed up.

When I run iwconfig I no longer have any wireless extensions:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

My wireless network card is also no longer showing up in the network manager.    I'm not sure what happend.  I have the gnome network maanger installed.

Basically it seems like my wireless card just vanished.

The wireless card is an Intel Pro wireless 3945 card.  I tried reinstalling it the same way I installed it the first time and it has not worked.  I am really not sure what to do at this point.  I'm getting kind of frustrated since I have been trying for several days to get it working.

Any ideas?

---

### Post by george314 on 2006-09-13
My network card vanished after I installed Ubuntu 6.06.  However it worked with the live cd.  This is a similar problem, but I also don't know how to fix it.

---

### Post by mepaco on 2006-09-13
Let me add my useless "me too".  My wireless card shows up while running the Ubuntu or Xubuntu Live CD but not under my actual installation of Xubuntu.  I'm attaching a picture of my wireless card accoring to the Gnome device manager.  I'm still a noob so any help would be appreciated.

EDIT: I was working through some of the troubleshooting guides and found that when I insert the card and tail messages, I get the following:

```
Sep 13 19:09:40 localhost kernel: [17179723.124000] pccard: PCMCIA card inserted into slot 0
Sep 13 19:09:40 localhost kernel: [17179723.124000] cs: unable to map card memory!
Sep 13 19:09:40 localhost kernel: [17179723.124000] cs: unable to map card memory!
```

Thanks,
Paco

---

### Post by themusicwave on 2006-09-13
I don't even see my wireless card in th device manager anymore.  Whatever the install script for the VPN client did, it was bad.

Also, the wireless light on my laptop will not turn on at all.  I have a Dell E1505 and even when I hit FN+F2 the light still remains off.

I think part of my problem is the ieee80211 install that worked before is still partially there, but is corrupted.  This is just a hunch though.  What makes me think this is that when I try to reinstall them it tells me that they are already there or it reports something like 0 installed, 0 removed, 10 unchanged.

Hopefully someone can help us out.

---

### Post by mepaco on 2006-09-13
Bwa ha ha ha!  I fixed it.  This is probably your problem too george314.  I read through a couple of troubleshooting guides that kept talking about a file called [FONT="Courier New"]/etc/pcmcia/config.opts[/FONT].  Well, my [FONT="Courier New"]/etc/pcmcia/[/FONT] directory was completely empty.  So here is what I did:

[LIST=1]
[*]Restart and boot from the Live CD.
[*]Now mount your existing hard drive:
[LIST]
[*][FONT="Courier New"]sudo mkdir /mnt/hda1[/FONT]
[*][FONT="Courier New"]sudo mount /dev/hda1/ /mnt/hda1/[/FONT]
[/LIST]
[*]Now copy the file to your hard drive ([FONT="Courier New"]sudo cp /etc/pcmcia/config.opts /mnt/hda1/etc/pcmcia/[/FONT])
[*]Restart
[/LIST]

Now there are lots of other files in the pcmcia folder when you boot up from the Live CD (and I have no idea what they do) but just copying config.opts did it for me.  My wireless card now shows up in System->Networking and I can connect to my access point.  themusicwave, you might want to check this out too.  I'd also suggest this post for some other potential solutions:

[WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Can any of you experienced users tell me why this happened?  Is this a bug?  I would think that at least some of those files should be present after installation.

-Paco

---

### Post by themusicwave on 2006-09-13
I'm glad you got yours working.

I looked at the guide a bit, I ran the lshw command and the only entry under network is my wired ethernet card(which is working fine).

I tried following the guide, but most of the commands didn't return anything, so I didn't really know what to do.

I'm hoping a wireless guru will come by and help me out cause at this point I am stumped.

Edit:I tried the live cd trick, and the config.opts file from the live cd appears to be exactly the same as the one currently in the folder.  Any other ideas?

---

### Post by themusicwave on 2006-09-14
still no luck.......bump

---

### Post by george314 on 2006-09-16
Well, unfortunately now even when I use the live CD there is no wireless.  I don't know why that is.

George314

---

### Post by davide.del.vento on 2008-04-28
> **mepaco said:**
> Bwa ha ha ha!  I fixed it.  This is probably your problem too george314.  

Your fix didn't work for me,  but I found another one, which I'll describe below.

By the way, I'm speechless about the fact that the license for the b43 wireless firmware requires that you download it: how are you supposed to download the software that you need to make your network work? Those people are *@#$$*%&&*!

By the way, I solved with just typing what follows on the command line:

sudo apt-get install b43-fwcutter 

(of course I needed a working wired network connection, which some people may not have)

If you have a similar problem, you may figured out what to do in this way: re-running the "live" and carefully inspect what was going to happen there. In my case, the above mentioned package has been installed in the live, but not on the hd-installed system.

Last, but not least, I think that this is a really bad bug in HH (which is a really good distro: thanks to all the developers, you rocks :guitar:). If the "live" recognize the hw and propose the right package to install (namely the b43-fwcutter), why the same is not happening on the installed system? Folks, you have to fix this asap!

Bye,
;Dav

---

