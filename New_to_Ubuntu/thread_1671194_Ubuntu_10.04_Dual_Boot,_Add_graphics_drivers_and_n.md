---
title: "Ubuntu 10.04 Dual Boot, Add graphics drivers and now wont boot!"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by Bugsy_malone 666 on 2011-01-19
Ok so getting fairly annoyed with windows 7 now and have been gradually turning to the darkside with ubuntu on nearly all my machines now, so tonight it was more fed up than usual with my main PC and decided to install Ubuntu 10.04LTS on it.

Its an AMD64 Dual core X7750, 4gb mem, soundblaster audigy, AMD crossfire motherboard and an ATi HD4650 graphics card.

So install 10.04 and it works fine, start setting up the sound and get it balance just right. the system tells me that in order for my graphics card to run properly it will need propriety drivers and lists the ATi ones (written by them?).

I set it about its duties and then restarted when it was done, it now wont boot up past the ubuntu logo with the 5 dots (all red quite quickly) and the graphics appear to have changed a little (almost like it was lower resolution!).

So I went in via recovery mode and did some updates as it was a fresh install to see if that might help.

hour updating, restart and same thing.

So question is what command will I need to impose to go back to normal drivers and what other driver options are available?

I did a bit of a search on here but it would appear everyones problem is slightly different and while its a toss up between the open source and ATi direct drivers, I dont even know how to get back to where I was before the ATi install to try something else?

Please help :)

---

### Post by coffeecat on 2011-01-19
To uninstall the proprietary ATI driver and revert to the open source driver, try this. Boot up in recovery mode and:

```
apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev
```

That will (hopefully) remove all the fglrx dross. Then you need to disable the xorg.conf file:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Be careful with case in that command. X11 = capital-X, eleven.

Now reboot and see if you can get a GUI. With that card you shouldn't need the proprietary fglrx driver anyway - even if it worked. From Lucid/10.04 onward the open source driver should give good performance, including compiz, with your card.

---

### Post by Bugsy_malone 666 on 2011-01-21
Hi coffee cat, thanks for this it kinda worked! But I am still not in the clear!

When I typed in the first line of commands, it did not reconise 'fglrx-amdcccle'.

That said I then rebooted and it seemed to be ok apart from the fact the ubuntu start up screen seems to be running at a low resolution stretched to the screen size.

I seem to now also have some other problems that werent apparent before but I dont know if these are related:

Basically when playing a CD through rythembox it would normally play whole tracks fine, put in a disc I had been listening to a day previous and it would get maybe 30 seconds into the song and then skip to the next track saying there was some sort of issue working with the existing track!


I have also hit another problem which is graphics related, I hooked up a 2nd monitor today to see how it would behave, to start with operated on a low resolution so I bumped the res up (I have a 19" square monitor 1280x1024 and a 19" widescreen 1440x900) and the screens appeared and I clicked I am happy with this as the display was correct looking however my mouse pointer appears to only be able to scroll round an area of monitor 2 thats about 800x600 pixels, I couldnt get it back to monitor 1 to even shut it down or get to any menus!


I dont know if this is related or that I need to get some different drivers of something?

---

### Post by coffeecat on 2011-01-21
The failure to recognise fglrx-amdcccle doesn't matter. That command should have uninstalled everything fglrx-related. Presumably fglrx-amdcccle wasn't there. As a double-check, it might be worth opening Synaptic and searching for 'fglrx' and uninstalling anything with fglrx in the package title.

The startup splash screen problem is odd. It's the proprietary fglrx driver that makes it look ugly; it should be OK with the open source one. So I don't know what's going on there.

Rhythmbox - you need to start a different thread. This will be an unrelated issue. Sorry I can't help; I don't use Rhythmbox.

---

### Post by Bugsy_malone 666 on 2011-01-21
well the only reason I mentioned about rythembox is I wondered if it might be a related issue.

The new problem I have though is as mentioned above where my mouse stays on screen 2 in a restricted size area.

could it be that only half of the uninstall process happened?

---

### Post by coffeecat on 2011-01-21
> **Bugsy_malone 666 said:**
> could it be that only half of the uninstall process happened?

In case that is so, that's why I suggested searching in Synaptic for anything fglrx related and uninstalling it.

Also - might be worth doing - while you have Synaptic open, mark the packages libgl1-mesa-glx, xserver-xorg-core and xserver-xorg-video-ati for re-installation, and re-install. I'm not sure that will help, but at least it will mean you can be sure everything that is needed for the open source ATI driver is installed.

As far as the problem when using a second monitor - I don't know. Sorry.

---

### Post by Bugsy_malone 666 on 2011-01-25
I'll mark this as solved for the time being as you helped cure my initial problem :) Thanks for that :)

I'll start a new thread for my new problem!

---

