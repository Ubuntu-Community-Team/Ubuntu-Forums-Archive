---
title: "Atheros card - how to load restricted modules"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by Ethelbert2 on 2007-03-02
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]I have spent weeks trying to get going in Linux (Ubuntu 6.10 and Xubuntu 6.10) - especially on establishing a wifi connection which seems to be vital in order to do almost anything. I finally manged to get a broadcom card going after discovering it needs firmware, finding said firmware and finding out how to install it - (actually I felt overjoyed when the system connected and I could run Synaptic etc). 

But now I have an Atheros chipset (5212) card for a second v old computer which I am trying  Xubuntu on. I got this card because I had read it supposedly works "out of the box" and I could avoid yet another long arcane sequence (OK I could repeat the Broadcom but had bought this other cared during the frustration period).

But Atheros does not "just work".  Though it is listed after "lspci" on the command line - nothing else happens. 
Other people had this problem (which indicates no driver) and I discover I need Madwifi which was developed as the Atheros driver  

- but that is supposed to be there anyway in Ubuntu it turns out.  

Long forum reseach gave vague knowledge and produces the mysterious instruction: 

"try installing linux-restricted-modules-$(uname -r)" 

which might make sense if I understood what these were, and what uname means and whether I just type this in or have to alter it. But other people seem to find this OK so I thought it might be the answer.

But - exactly HOW do you go about this? 

I have no Internet connection of course (that's why I want the card to work).   

Anyway I typed the above on the command line which produced a response telling me no such module can be found.

So obviously something else is required - or it should be written differently.  Or maybe there is no source since I have not INternet but - should I put in a CD or download stuff onto my Win computer and transfer it on a USB card?

But if I do - how do I rewrite the instruction above to find these modules? Will there be lots of dependencies and other stuff I only half grasp?[/FONT][/SIZE][/COLOR]

[FONT="Tahoma"][SIZE="2"][COLOR="Navy"]<bit of a rant-ignorable>Why is Linux SO complicated for the simplest things?  OK I know - but PLEASE will those helping us new people (and we ARE grateful for your time despite the frustrated tone of most postings), understand that we DON't KNOW ANYTHING. 

Arcane instructions suggesting "download and install such and such" simply raise 8 million other questions - with what sequence instructions, from where, what else is needed, how tdo I get a connection anyway, and if not where can I load it from - a CD maybe - so how do I tell the computer to look for the CD or will it find it automatically etc etc ? 

I don't say this to be irritable - just that Linux users finally persuaded me that it was worth trying and easily usable - and when I get here, it is not (without learning lots). 

That's OK if you only ever want intensely geeky people using Linux - but I gathered from a million earnest Internet postings that Linux users think the world should be encouraged to use Linux. That is the point of Ububntu n'est-ce pas? 

It won't happen if us new people have to tear all our hair out to do it.

Sometimes things are well explained step-by-step (eg modem driver installation on the wiki) but very often critical bits are left hanging and unexplained. 

I know - this is all voluntary and who I am to complain? - I agree - but then **I **don't feel driven to make others use Linux - and am barely hanging in here as a new user anyway.(/rant>[/COLOR][/FONT][/SIZE]


[FONT="Georgia"][COLOR="DarkGreen"][SIZE="3"]Excuse the emotionality but please someone tell me simply how to get this card working?[/SIZE][/COLOR][/FONT]

---

### Post by cookfromfrozen on 2007-03-02
Hi there

Sometimes with 6.10, the Atheros card is picked up during installation, but the "linux-restricted-modules" are not installed so the card does not work after Ubuntu is installed.  This can especially happen if you use the "alternate" edition of the CD.  I think this is a bug in Ubuntu.

The MadWifi driver is in the "linux-restricted-modules-*" package because it is still subject to some copyright/legal issues.

Luckily, it is provided on the Ubuntu CD so you should be able to install it from that if you don't have a working net connection.

Put the alternate CD in the drive, open a terminal and try the following command:

```

sudo apt-get install linux-restricted-modules-`uname -r`
```

Notice that uname -r is surrounded with backticks.  "uname -r" is the command that tells you what version of the Linux kernel you are running, so this substitutes the version in and installs the modules (drivers essentially) for your kernel.

"sudo apt-get install linux-restricted-modules-2.6.17-10-generic" should be the equivalent.

If you have not modified any of the repository settings in Synaptic, it should look for the modules on the CD-ROM and install them.  If it doesn't, and tries to go on the internet, you will probably need to go into Synaptic.  Try Settings > Repositories and go on the CD-ROM tab.  You can then "add" the CD-ROM you used to install.  If you haven't modified any settings, you shouldn't have to do this.

If all goes well and it grabs the files from the CD, try the following command in a terminal (or just reboot):

```
sudo modprobe ath_pci
```

This loads the MadWifi driver and starts it up.

If that works, great.  It should have all happened automatically, but for some reason it sometimes doesn't.  If not, please post back and I'll see what I can do.  There are definitely a few other things we can try.

---

### Post by Ethelbert2 on 2007-03-03
[SIZE="3"][FONT="Georgia"]Thanks for a nicely written reply - I will be away today and cannot try for at least 12 hours but will post back progress later.[/FONT][/SIZE]

---

### Post by Ethelbert2 on 2007-03-03
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]Well your brilliantly clear instructions worked a treat.

I had almost got there before, trying to put in this instruciton about the restricted modules - but it was a question of using the backtick quotes - I had been using ordinary quotes.

The difference was magic - the command line went beserk and then asked me to say yes to installation - once that happened and I entered the second command, the Atheros showed up beautifully in the network manager and configured simply - as soon as I put the network ap on "pairing" it found it and lo everything was lightness and ease.  I am now upgrading everything in the Synaptic (fingers crossed that does not break the connection again!! In which case I guess I have to repeat the operation.)

Thank you very much for your patience and clarity.[/FONT][/SIZE][/COLOR]

---

### Post by Ethelbert2 on 2007-03-04
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]Well back to questions today.

As I feared - once I ran the automatic updating stuff on Synaptic - the card stopped working.

Not only that it **disappeared** from the Network Manager.

I assumed the problem would be that the new stuff makes the original "restricted modules" package out of date and I would have to install the restricted modules again after finding an updated version (though why can't this just be automatically updated along with everything else???)

So I found a deb file for the number given in the command line error message --   very long, repeating 2.6.17etc. I downloaded it (i386 version) on my Win computer and carried it over and double clicked it - the installer said it the same pacakge was "software available" and I should use that alternative which makes no sense (why is the card now not working then if the package is available?) And where is this "software available" version?

So I installed this new one anyway - except it would not install and said I need linux-image. I assume that needs updating too.

But I have the feeling I am embarking on a never ending journey. And will have to keep a main Win computer to do it.

Do I now have to find that deb file and install it?  Are there other things that that needs? And will I have to do this everytime things are upgraded?  It is going to become ultra-tiresome.

Is this the answer now or is there an easier way? *Apart from reverting to Win.*

[/FONT][/SIZE][/COLOR]

---

### Post by spd106 on 2007-03-04
cookfromfrozen's post was very good, but it missed one critical point.

To aid the upgrade procedure ubuntu uses so-called meta packages, these are empty packages that exist to ensure dependencies are maintained properly.

So if you install the linux-restricted-modules-generic meta package, you should be ok for future upgrades. While you're at it you might as well install the linux meta package too.

Compared to many other users you actually have it pretty good. Those using the latest ndiswrapper have to recompile kernel modules again after every kernel ABI bump. But that's the price you pay for cutting edge.

---

### Post by Ethelbert2 on 2007-03-04
[SIZE="3"][FONT="Georgia"]Thanks for the answer - do I get the meta package via Synaptic?

 - or do I have to find it somewhere else - and what it is the name I would use for apt-get install procedure?

(I suspect I will have to re-install the CD version of Xubunutu in order to follow the cookfromfrozen procedure again - because otherwise I have no Internet connection - unless this is all on the CD - I also have the Ubuntu dvd - both now outdated of course) 

So what order will I need to do things in? Or can I avoid going through a reinstall by finding stuff on the Win computer and moving it over?)
[/FONT][/SIZE]

---

### Post by spd106 on 2007-03-04
Open synaptic if you have it available, it much easier to use that just apt-getting random packages, unless you know what you are doing.

First ensure that you have refreshed the package list with the sources you have available. If you have no Internet connection most of them will fail. Add the packages I mention above, those are the exact names and they are available on the CD (old) and in the official main repository (new).

You will probably have a list of options available when you boot (press Esc when prompted). Choose one that you know you have a matching linux-restricted-modules-`uname -r` package. This will allow you to get online. 

Now mark all upgrades, apply and you should be done.

---

### Post by cookfromfrozen on 2007-03-04
I did neglect to mention the linux-restricted-modules-common in the first post; I was going to wait until it was working before adding more confusion, but I probably should have mentioned it initially. :(

The updates probably installed a newer kernel, so if you reboot the machine, hit escape when the timer is counting down.  This lets you pick which kernel you want to boot.  Boot the older version, "Ubuntu, kernel 2.6.17-10-generic".

Your wireless should now be working, so this will let you install the "linux-restricted-modules-common" package.  You can either do this through the graphical interface, Synaptic, or you can type the following command:

```
sudo apt-get install linux-restricted-modules-common
```

Once this is done, reboot your machine as normally (no need to press escape), and wireless should now work even on the updated kernel and will not break in future updates.

Let us know how it goes :)

---

### Post by Ethelbert2 on 2007-03-04
[SIZE="3"][FONT="Georgia"][COLOR="DarkGreen"]OK - slightly long-winded because I did a re-install (had not fully understood the "esc" bit which would have been better on boot up) but that got the card going again and this time I marked up Linux-generic for install which seemed to automatically bring linux-restricted-modules-generic onto the list too.

And then I ran an update with the boxes including those generics all ticked on the list too.

Everything went very sweetly and the card continues to work in the updated situation. So excellent and I am very grateful to you and spd106 for the information and advice. I am warming towards Linux, but need to learn some more. 

With the card going there is less pressure to sort out the modem - though I would like to eventually - have run scanModem and sent off a file to Linmodems - so I will wait and see on that
[/COLOR][/FONT][/SIZE]

---

### Post by cookfromfrozen on 2007-03-04
Glad to hear you got it working.

I was in the same situation as you.  I had an Atheros card in my laptop and no ethernet port so if I couldn't get it working I was screwed.  It was a little frustrating with all the various restricted packages at first, but you learn quickly and now it is pretty much second nature for me, with a little "practice." :)

The boot loader is the black screen that says "GRUB loading...press esc to enter menu" and counts down quickly.  If you blink you'd miss it, but pressing esc lets you choose which version of the kernel you want to boot.

Good luck with Linux in the future.

---

### Post by Ethelbert2 on 2007-03-05
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]Thanks again - I have spotted the boot up menu now (after doing the re-install!) and it will come in handy in the future I suspect.

One final question - do you have any favoured wifi utilities - I gather wifi-radar is very good?
Or should I make this a separate thread?[/FONT][/SIZE][/COLOR]

---

### Post by cookfromfrozen on 2007-03-05
I use WPA for securing my wireless network but I haven't used any sort of GUI, I just use the wpa_passphrase command provided with wpa_supplicant and use that to set up WPA support.

However, if you find yourself hopping between access points a lot or connecting to a lot of WPA/WPA2 networks, the app you hear talked about a lot is called network-manager-gnome.

This is supposedly very similar to the wireless network browser in Windows -- click the access point and you're away.  I never got it to work with Xubuntu but I'm more comfortable editing conf files for wpa_supplicant anyway -- I feel I learn much more.

I haven't tried wifi-radar either but it looks good.

It's still quite easy to switch between unsecured access points even from the command line, so if you had a free access point you'd just use:

```
sudo iwconfig ath0 essid MyAccessPoint
sudo dhclient ath0
```

---

### Post by spd106 on 2007-03-05
Network Manager will be default in Feisty, so I suggest you familiarise yourself now [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

