---
title: "Ubuntu Rookie. Really really rookie!! Need help with everything."
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Toxteth O'Grady, USA on 2010-07-05
Hi Guys and Gals,
 
I would like to start out by saying hello. I'm glad I found this forum. It seems there are lots of great people helping out others here. I live in Washington DC, and I'm not much of a computer guy. Surf the net and a few spread sheets here and there. However, I decided to install Unbutu on an old Dell Inspiron 1100(with a whopping 1G) to sort of play around. Kind of learn a new hobby. I was wondering if you guys could help me out with some bugs that I can't seem to work out.
 
First things first. The whole thing seemed to load up fine. Then when I start the laptop, all is good, but sometimes the screen doesn't come on. I *hear *the little jingle, but just blackness on the screen. I shut it down and re-start and sometimes it boots up fine. 
 
Also, I can't get DVD's to play. It seems as though I'm missing an update. Not a big deal, but then the big one is the NO INTERNET!!! AAARRRGGGHHHHH](*,):P So, I did a bit of searching and I have a Zyxel M-102 CardBus. Apparently this thing doesn't work without a lot of computer skills(which I have none).  I plugged in the ethernet cable to see if that would work, and that won't work either.  I tried to add it to the network connections, but nothing. I think if I could just get this thing online, I would be able to sort out the other problems. 
 
Oh, and I forgot, if I go to the screen saver section, anything that says "GL" with sent the old girl into some sort of bizzerk mode and I just get a box of vertical white lines blinking. Then it's totally frozen and I have to turn it off, but than the black sceen thing starts again!!! 
 
I'm using my other computer to talk to you guys. Just a regluar Dell Inspiron 1525, which I won't mess with:lolflag:
 
Thanks guys I really apprreciate the help. 
 
PS don't make fun of me!
 
Yours Truly,
 
Toxteth O'Grady, USA

---

### Post by Darkness Des on 2010-07-05
Welcome to Ubuntu! Good to have you here! Don't worry, we won't bite ;)

It looks to me, and this is just what I'm getting out of it, you're missing a Graphics driver for your card, and also a driver for your networks card. If you have MAC Filtering enabled on your wireless router, I suggest temporarily disabling that for a few minutes while you plug in with the Ethernet cable. Then go to System -> Administration -> Hardware Drivers. Let it scan, then install one for your graphics card and wireless card. Reboot. See if that works. That seems like a decent laptop though, I don't think you'd have too many problems with that (other than the minimal RAM). You may also want to try Xubuntu, or Lubuntu if you really think your laptop can barely support anything. I've personally had some problems with getting a Dell Laptop running on my network, so good luck with that.

EDIT:
I forgot about the DVD situation. Go into System -> Administration -> Synaptic. Put in your password when asked. Install ubuntu-restricted-extras. That installs support for MP3 files and pretty much every media format known to man. For DVDs, you need to go to Applications -> Accessories -> Terminal. Type in (or copy and paste, any one is fine)
```
[FONT=monospace]
[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh

```
and put in your password when asked. No dots or anything will show up, but it is being entered. After a long nonsensical output, it's done. Then you can play your DVDs all you want.

---

### Post by stderr on 2010-07-05
Hi & welcome.

With regard to your network, I'd give [this solution]("http://ubuntuforums.org/showthread.php?t=556714") a shot. It's not ideal - it uses the official Windows drivers from Zyxel's website and loads them using ndiswrapper - designed to run Windows drivers under Linux.

In brief this is what the author proposes (run each line in a terminal window - Application->Accessories->Terminal):

```
wget http://us.zyxel.com/upload/download_library/M-102\ Drivers.zip
unzip M-102\ Drivers.zip
cd M-102\ Drivers
sudo ndiswrapper -i net5513.inf
```

Line 1 downloads the drivers from zyxel.com and places them in your home directory.
Line 2 unzips the zip archive in your home directory.
Line 3 switches to the unzipped directory containing the drivers.
Line 4 installs the windows driver in ndiswrapper.

After this, check if ndiswrapper is loaded with:

```
lsmod | grep ndiswrapper
```

If it doesn't give any output, start ndiswrapper with:

```
sudo modprobe ndiswrapper
```

Now when you check for ndiswrapper again, you should see some output, something like this:

```
lsmod | grep ndiswrapper
ndiswrapper           185692  0 
```

I haven't got the same card to test myself, but from the responses it looks like it was working OK.

The graphics problems all point to a graphics driver issue. It would help if we knew which graphics card you have. I'd ask you to post some command line output, but without the Internet that's tough. If you run the command **lshw -C display**, could you try to post back just the sections I've highlighted in bold/underline below? And don't worry if it warns you that you should be running it as super-user, that just gives you more information we don't need.

```
ace@ace1:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: **_G92 [GeForce 9800 GT]_**
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: **_driver=nvidia_** latency=0
       resources: irq:16 memory:ea000000-eaffffff memory:c0000000-cfffffff(prefetchable) memory:e8000000-e9ffffff ioport:9000(size=128) memory:eb000000-eb01ffff(prefetchable)

```

---

### Post by AleksKeaton on 2010-07-05
It could well be that your disc drive is damaged. You might want to consider buying a new external one that hooks up by usb. They come with the drivers. You probably also want to consider a new graphics card. It will come with the drivers you need.

---

### Post by Jakiejake on 2010-07-05
> **Toxteth O'Grady, USA said:**
> Also, I can't get DVD's to play.

Since Ubuntu aims to be as open source as possible it does not play DVD's by default
You should be able to find some tutorials on Google by searching "Play DVD's On Ubuntu" Or "Play DVD's On Ubuntu 10.04" (The second one should be better for 10.04)

---

### Post by kimikrishna on 2010-07-05
Search for "ubuntu-restricted-extras" in software center and install it. 

This Will download and install codecs and as the name says, some restricted extras ;-)

---

### Post by Zintha on 2010-07-05
> **AleksKeaton said:**
> It could well be that your disc drive is damaged. You might want to consider buying a new external one that hooks up by usb. They come with the drivers. You probably also want to consider a new graphics card. It will come with the drivers you need.

Hate to say this but you're asking someone to buy what, very well may be, unneeded purchases.

Just buying new for the drivers instead of even working out if the thing is fixable is a horrible idea.

That said, ubuntu-restricted-extras is the way to go and looked like you're missing drivers for your wireless and graphics card, which happens.
As said, disable MAC address filtering on your router (if its on) and use a LAN cable to get on the internet and check out System->Administration->Hardware Drivers and see what it comes up with.
Others here have given more indetail help so I don't need to go into more :D If you still have problems then come back and we'll look into more solutions.

Welcome to Ubuntu

---

### Post by Toxteth O'Grady, USA on 2010-07-05
> **Darkness Des said:**
> EDIT:
I forgot about the DVD situation. Go into System -> Administration -> Synaptic. Put in your password when asked. Install ubuntu-restricted-extras. That installs support for MP3 files and pretty much every media format known to man. For DVDs, you need to go to Applications -> Accessories -> Terminal. Type in (or copy and paste, any one is fine)
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```
and put in your password when asked. No dots or anything will show up, but it is being entered. After a long nonsensical output, it's done. Then you can play your DVDs all you want.
 
 
Don't I have to be online to get this download? I know this sounds pretty stupid to you guys, but I'm totally lost.

---

### Post by partloer on 2010-07-05
Toxteth O'Grady,

Yes you do have to be online.  Usually your wired network card has better support once Ubuntu is installed.  So you might have to be connect with a wired connection but this way you can download software to try and get your wireless card working.  I would work on getting your wireless card working first then work on some of the other things next.

---

### Post by halitech on 2010-07-05
> **AleksKeaton said:**
> It could well be that your disc drive is damaged. You might want to consider buying a new external one that hooks up by usb. They come with the drivers. You probably also want to consider a new graphics card. It will come with the drivers you need.

it is possible but if he used the drive to install Ubuntu then chances are its not broken and just needs the restricted extras to get dvds to play.

as far as the video card, its an old laptop, chances are whatever he has is all he's going to be able to use.

---

### Post by Mark Phelps on 2010-07-05
According to Google, the Dell Inspiron 1100 came out in 2003 has built-in graphics with only 64MB of memory.  With that little memory, he's not going to be able to do anything much.  So, sending the OP off to find and install video drivers is wasting their time.

---

### Post by Toxteth O'Grady, USA on 2010-07-05
What's OP?

---

### Post by stderr on 2010-07-05
> **Toxteth O'Grady, USA said:**
> What's OP?

Original Poster (i.e. the instigator of the thread).

---

### Post by Darkness Des on 2010-07-05
Oh. Wow. Congrats on getting it to boot. I STRONGLY recommend Lubuntu, I've used LXDE before (on Fedora) and it's quite a good desktop environment while still being lighter than XFCE.

---

### Post by Toxteth O'Grady, USA on 2010-07-06
Hi Darkness,
 
Can I download Lbuntu from the internet on another computer, put it on a zip drive and then install it on the Dell 1100?
 
Thanks again guys,
 
Toxteth O'Grady, USA

---

### Post by Darkness Des on 2010-07-06
Of course. It's the exact same install process as it is with regular Ubuntu.

---

