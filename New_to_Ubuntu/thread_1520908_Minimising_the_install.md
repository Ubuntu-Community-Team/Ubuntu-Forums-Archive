---
title: "Minimising the install"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by tqprvn on 2010-06-30
hi all

I have an old eeePc 701 currently running 9.10 Ubuntu netbook. Picked it up mostly as a toy from some online liquidator for a hundred bucks or so, but it is obviously well past its hey-day, but I like traveling with it, web things and so on.

I'd like to go up to 10.04, but the updater says I do not have enough drive space for the upgrade - about 700mb short - which on a 4 gb drive, is kind of a lot!

I suspect I can clean install it from a USB and wipe it all (no problem, all my data is on an SD card that I leave in it permanently anyhow), but even then I am going to be going very close to filling the whole drive with just the OS.

Is there a way during the installation process where I can 'pick and choose' what applications will be installed during the OS installation?  Ubuntu comes with a bunch of bundled apps, games and so forth, which I basically never use...can I custom install so that they are never there, rather than having to go and manually remove them later?

Just clicking around 9.10 - all the games - don't want them. Movie player and rhythmbox - dont want, can just use VLC...Office - don't want Draw (do people really do illustrating on screens this small?), f-spot, i keep my photos elsewhere, Evolution, no thanks....and so on. I suspect there is a couple hundred meg of wasted drive space in apps, and I'd rather have the space.

Are there other elements I can remove that will reduce the total footprint of my installation otherwise?  

I know Macs a whole lot better, and, for example, when I was installing OSX a while back, I chose to not install a bunch of language packs and printer drivers, and scraped a couple hundred meg off the installation right there.  I know Ubuntu starts off a whole lot leaner, but any suggestions to this end would be appreciated.

Thanks

Matt

---

### Post by ankspo71 on 2010-06-30
Hi,
You could free up some space in your repositories cache folder. What the following command will do is delete all *.deb packages in the cache. Open your terminal and paste the following:
```
sudo apt-get clean
```

You could also install a package called "bleachbit" (it's in the repositories in Karmic too I think). With that package I am able to remove about 1GB worth of uneeded things like localizations and *.deb files (like above). It's a system cleaner actually, and here is the list of features [http://bleachbit.sourceforge.net/features](http://bleachbit.sourceforge.net/features)

You can do both of those ideas before and after you upgrade, since 4gb isn't a whole lot of space to work with.

I would recommend a minimal install using the [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD"), but I don't know what packages make up the netbook edition's special desktop (other than gnome). By the way, this only installs the core of Ubuntu with no desktop (command line only), so it is not recommended unless the person has a list of packages to install. There must be a minimal netbook install tutorial around here somewhere. 
hope this helps.

---

### Post by tqprvn on 2010-06-30
ya, it suggested the get clean thing on the screen where it told me I didn't have enough space, and that took the 'you need 750 mb more space' error down to 'you need 680 mb more space' haha...

I'll check bleachbit, but I really doubt that I have that much there to flush :)

I looked at the minimal thing as well, but yes, same concern, the Netbook desktop etc...was kind of hoping there would be a nice little button that said 'custom install' where I could merrily check off all the things I don't want!

---

### Post by Lety on 2010-06-30
**tqprvn**, I have the same problem.
I've installed Ubuntu Netbook 10.04 on my EEE PC 701 4G, after that 
there was 1,1Gb free. Then I installed all available updates, SMPlayer, eee-control(or how it's called...) and uninstalled Evolution, Totem.
Now I have ~ 400Mb free. When I look through Synaptics, I don't know what else I can delete to free several hundred megabytes. 

By the way, I have two mount points: / and swap(200 mb, which is normally empty), maybe there is better way to part the 4Gb SSD?

---

### Post by kerry_s on 2010-06-30
have you tried lubuntu? it's the lightest/smallest version right now.
[http://lubuntu.net/blog/lubuntu-1004-now-available-download](http://lubuntu.net/blog/lubuntu-1004-now-available-download)

---

### Post by tqprvn on 2010-06-30
hmm. thanks for the suggestion, but there's no Netbook version by the looks of it.  I have no performance issues by the way. No speed issues with the window systems in the way that Xubuntu etc function on lower powered/older desktops, performance wise I am fine, only issue is the drive space, same as Lety.

---

### Post by Matt__ on 2010-06-30
how about a minimal install and then work up from there adding only what  you need?
[minimal.iso]("https://help.ubuntu.com/community/Installation/MinimalCD")

there is even this handy script to help you set up the basic system
[Andy  Duffels minimal script]("http://andyduffell.com/techblog/?p=689")

of course you could create you own script too, with the boot, desktop  and file manager of your choice, after which you you install whatever  you want. (including the netbook interface if you so wish)

---

### Post by snowpine on 2010-06-30
I agree with the suggestion to use the Ubuntu Minimal CD. You should be able to get your install under 1gb if you are very selective and use a lightweight windows manager. Here is a good tutorial: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you are willing to look beyond the Ubuntu family, you have some excellent "lightweight" options such as Puppy (100mb), SliTaz (30mb), and Tiny Core (10mb).

Also don't forget you can use a USB stick and/or SD card for extra storage.

---

### Post by kerry_s on 2010-06-30
> **tqprvn said:**
> hmm. thanks for the suggestion, but there's no Netbook version by the looks of it.  I have no performance issues by the way. No speed issues with the window systems in the way that Xubuntu etc function on lower powered/older desktops, performance wise I am fine, only issue is the drive space, same as Lety.

it does have a netbook setup "lubuntu-netbook" that you can select at the session menu.

the point is it's a minimal setup that can easily be made to fit your needs.
you can run it live like any standard ubuntu based system so it won't hurt you to try it. i find it to be the perfect starting point with out having to start from a minimal/cli install. i think the iso is like 500+mb, theres no games, no openoffice, theres no heavy programs at all, its a lot easier to remove what you don't want or add to it to get what you want.

give me a minute to switch computers & i'll add some pics.

---

### Post by kerry_s on 2010-06-30
pic #1 what my normal looks like
pic #2 lxlauncher, thats used in the lubuntu-netbook session. you won't have favorites, i added that when i was using it.
pic #3 hardinfo summary (my cpu is 450mhz, this laptop is a vaio pcg-f430 from 1999)
pic #4 hardinfo filesystem use
pic #5 menu

---

