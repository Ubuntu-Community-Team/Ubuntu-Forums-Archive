---
title: "[SOLVED] Xubuntu Sharing with XP"
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by darkan9el on 2008-03-04
Hi all, I have installed Xubuntu trying to get my network card to work, but that's another story... See after the question.

How do I share files, what do I need to do to set this up properly?

**things I've done:**
[LIST]
[*]Made a cup of tea
[*]Stared out of the window
[*]Found the Ubuntu forum and registered
[*]Tried to create a shared folder but told I need to install, either:
[INDENT]Unix networks Support (NFS)[/INDENT]
[INDENT]Windows Networks support (SMB)[/INDENT]
[*]Clicked 'install services' but nothing happened
[*]Scratched head and opened browser to Ubuntu forum...
[/LIST]
I'm assuming I can install both of these services and if so how do I go about doing so? 
The reason I ask is I have a mate that has a MAC so I'm thinking the Unix service would come in handy for that and I dual boot a desktop with XP Pro and Ubuntu 7.10 Gutsy Gibbon installed.

------------------------------------------------------------------------------------
End of my actual question, below is some background on how I got to it.
------------------------------------------------------------------------------------
**Back to the network card trial. This is actually a success story so I thought I would add it to help others.**
 I have previously tried:
[LIST]
[*]Fedora 8 KDE Live *Didn't work wouldn't boot*
[*]Fedora 8 Live *Installed but with errors*
[*]Damn Small Linux - Not *Installed fine but too light and not enough bling*
[*]Mepis *It was OK*
[*]Mandriva *Too resource hungry for my system with the latest KDE*
[*]Debian 40R-3-1386 *Again too big, too slow*
[*]Arklinux *I like this little OS it has a nice balance between function and looks*
[*]Gentoo *Just didn't light my fire*
[*]Ubuntu 7.10 Gutsy Gibbon *A bit too big for my laptop (see my laptop specs)*
[*]Mandrake 10 *Again too much for my poor little PIII*
[/LIST]

None of the above could install my card and none could run my card using ndiswrapper, in fact I found ndiswrapper to be a right pain. So, after almost losing the will to live I returned to Unbuntu and went for the smaller and not so adventurous xubuntu. to my surprise it installed my card while setting itself up. this happened more out of absent-mindedness than skill. here's what I did or should I say didn't do.

[LIST]
[*]Downloaded Xubuntu Gutsy gibbon
[*]Burned to CD @ 16x
[*]Placed in Laptop CDROM drive and pressed the laptop 'ON' button
[*]Forgot to remove the Floppy Disk with the WPC54G v7.1 Drivers on
[*]Accidently left the WPC54G PCMCIA card plugged into the PCMCIA slot
[*]Basically let Xubuntu do its thing until it asked for a User name and a Password, which I dutifully created
[*]Logged on a bit later and noticed the WPC54G lights were flashing
[*]Went into: Applications | System | Network
[*]Gobsmacked at discovering Wireless Connection, clicked on it and selected Properties
[*]Unchecked 'Enable Roaming Mode'
[*]Typed in my Network Name: MSHOME or similar
[*]Chose the encryption method WPA Personal
[*]Typed the Network password  or as it is also called (Pass Phrase)
[*]Set the Connection settings to 'Static IP Address' (tried the others they didn't work)
[*]Typed an IP address i.e. 168.192.1.? (?= a number between say 3 and 254)
[*]Subnet was done automatically but is normally something like 255.255.255.0
[*]typed my gateway IP: which would be something like 192.168.1.1 (this is normally a Linksys router IP)
[*]Clicked the DNS tab and found the gateway IP already there but if it isn't add it.
[*]Clicked on Firefox and found google.
[/LIST]

I'm still not sure how I did it or if I actually did anything at all, but thats how I got my WPC54G PCMCIA card to work using the Atheros Drivers from the floppy... I think.

Laptop Spec:
Umax Actionbook 860T (a450)
CPU Pentium III
HDD 20Gb
Memory 123Mb
OS Unbuntu 7.10 (gutsy) Kernel Linux 2.6.22-14-generic

---

### Post by jeffus_il on 2008-03-04
If you are interested in file sharing between the computers using simple and easily installable software, you can install "openssh" on your linux machine and access linux from windows using a neat free gui called filezilla.

---

### Post by darkan9el on 2008-03-04
Hi sorry for appearing thick but how do I do that please :confused:

Just done a search on my Synaptic package manager and I have openssh client installed and downloaded filezilla

---

### Post by jeffus_il on 2008-03-04
You're not thick, you made a cup of tea and that's an art. You didn't offer me but I guess it would be cold by the time it arrived here...

Start by running Synaptic package manager, search for a package called openssh, mark it for installation and click on the "apply" button.

Go to the windows machine, Google for "filezilla" download and install it.
Run filezilla, set up a new connection, using your machine name or address, your Ubuntu username and password and set the connection type as sftp. Then say a quick prayer and hit the "Connect" button.

but drink your tea first, it's getting cold.

---

### Post by darkan9el on 2008-03-04
It was all going very well, I'd finished my tea. when my router decided to start playing up. I have a Dlink DSL-2740B and every now and then it decides to be arsey and not let me into the pages, I think it must be over heating slightly as I have it on pretty much all the time. Anyway after that I can't get the WPC54G to connect so I can't test your brill idea.

I also forgot I have CuteFTP installed, but that's what ya get when  ya past 45 and have +25Gb of software installed lol!

Sooooo! in the meantime I got bored while I was waiting for the WPC54G to try and connect,  I browsed on over to the Kubuntu site and watched a few videos and decided to install Kubuntu to see what its like lol! 

I can blame 'Roblimo' for this diversion lol!  ;)

Anyhoo, I will be back to report on the openssh and filezilla combo link, after I've installed Kubuntu but thanks up to yet.

Ooh! it looks very pretty!

---

### Post by Eiríkr on 2008-03-05
Incidentally, when your mate comes over with his Mac, you should be able to share to his machine quite easily via your file browser (Nautilus in regular Ubuntu, Konqueror in Kubuntu).  In Nautilus, his machine should show up in the Network (click Go -> Network).  In Konqueror, click the address bar and type [font=courier]fish:/USERNAME@IPADD:22/[/font] (replacing USERNAME with a username that works on his machine, and IPADD with his machine's IP address).  Bob's your uncle, and you're good to go.

Cheers,

Eiríkr

---

### Post by darkan9el on 2008-03-15
A slight delay in replying, got busy at work, people seem to break PC's in groups, syncronised corruption lol!

Ok my issue was the Dlink router overheating, I placed a 120mm fan underneath it and up to yet it hasn't misbehaved, well it should really being as though it has a force 9 gale blowing through it lol! Think I might put two on and see if I can get it to hover lol.

Tried Eirkr tips and they work fine. I have also got my Powerbook G4 up and running after replacing the screen, and linked with that, I tell ya Networking with Macs is sooooooooo easy.

Oh by the way I went back to Xubuntu, it runs better on the laptop, might try Xfce as a desktop next

thanks for the great help

respects to all

Lee

---

### Post by Eiríkr on 2008-03-17
Glad to hear things are working for you.  If that resolves your troubles, please also remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Cheers,

Eiríkr

---

### Post by venik212 on 2008-03-17
I like to use Krusader for ftp transfer from Kubuntu to Windows.  I run vsftpd as an ftp server, and Krusader as the client.  It works just like the Total Commander under windows: a two sided file manager, complete with a nice synchronization feature to synchronize two directories.

---

