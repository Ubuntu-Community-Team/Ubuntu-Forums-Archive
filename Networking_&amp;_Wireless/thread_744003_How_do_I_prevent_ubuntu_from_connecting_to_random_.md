---
title: "How do I prevent ubuntu from connecting to random wireless networks?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by abh83 on 2008-04-03
How do I prevent Ubuntu 7.10 (network manager) from connecting to random wireless networks in the neighborhood?

I've got my own locked wireless home network set up. However, there are other open wireless networks in the neighborhood. On many occasions Ubuntu will connect to a random network other than mine which is very annoying.

Is there something like an exclusion list?


Help is greatly appreciated!

---

### Post by finer recliner on 2008-04-03
system > admin > network

highlight wireless 
click properities
uncheck "roaming mode" and put in your router's information instead

---

### Post by kutjara on 2008-04-03
> **finer recliner said:**
> system > admin > network

highlight wireless 
click properities
uncheck "roaming mode" and put in your router's information instead

Unfortunately, this is a pretty clunky solution. If you disable roaming and manually configure your home setup, you then have to reenable roaming if you want to take your PC to a coffee shoe. When you switch back to manual, you have to reenter your password to get back on the home network. I find it easier to leave roaming on and  just remember to select my home network from the nm-applet dropdown whenever I boot up.

What's really needed is a "preferred network" solution, where Ubuntu would learn which networks you regularly connect to and prioritize connection accordingly. Sadly, I haven't yet found an application that will do this.

---

### Post by abh83 on 2008-04-03
i agree with kutjara. This would be a pain in the @$$ :D

also i seem to have issues when i turn off roaming and enter my router info manually. At times it just refuses to connect and i have to re-enable roaming.

I'm quite disappointed at the lack of feature with NM. An exclusion list is quite standard these days and shouldn't be too hard to implement 

any other ideas?

---

### Post by Seisen on 2008-04-03
You can install WICD and ditch gnome-network-manager, with WICD you have the option to make a AP the default one to connect to.

---

### Post by kutjara on 2008-04-03
> **Seisen said:**
> You can install WICD and ditch gnome-network-manager, with WICD you have the option to make a AP the default one to connect to.

Cool! Thanks for that tip. I'll definitely try that out.

---

### Post by tangibleorange on 2008-04-03
yeah i definitely think that is the best solution. WICD also has support for static IPs which NWM doesn't have, and I need a static IP for bit-torrent and such...

---

### Post by Seisen on 2008-04-03
> **tangibleorange said:**
> yeah i definitely think that is the best solution. WICD also has support for static IPs which NWM doesn't have, and I need a static IP for bit-torrent and such...

That is one of the reason's why I like WICD, I tried setting up a my wireless as a static ip in Nm and it would not work at all.

---

### Post by kutjara on 2008-04-03
> **Seisen said:**
> You can install WICD and ditch gnome-network-manager, with WICD you have the option to make a AP the default one to connect to.

WICD doesn't appear to be ready for primetime under Hardy.

I've installed it and got the tray icon working, but it doesn't like connecting on its own. I have to right click the tray icon and choose "connect," which brings up the wicd main application. This pretends to connect to my preferred network for a minute or two, before deciding it can't. If I then try to manually connect, wicd freezes and I have to Force Quit.

The only way to connect seems to be to bring up the wicd application, cancel the connection attempt already in progress, and then click the "connect" button under my desired network in the list of available networks. Then it'll connect.

Currently therefore, on Hardy, wicd makes gnome network-manager look like a model of good design and ease of use (not something I'd ever imagine I'd say). I think I'll have to go back to nm for awhile.

---

### Post by abh83 on 2008-04-03
thx for ur quick review kutjara! ;)

I hope I don't run in with the same issues on gutsy gibbon!

i'll give this a try tonight!

thx everyone!

---

### Post by LukeCarrier on 2008-04-03
> **abh83 said:**
> thx for ur quick review kutjara! ;)

I hope I don't run in with the same issues on gutsy gibbon!

i'll give this a try tonight!

thx everyone!

Gutsy tends to be more stable, you probably won't have any problems, hopefully.

---

### Post by abh83 on 2008-04-03
i do have one more question though:

i don't really wanna ditch NM. Can I simply disable it and set WICD as my default network manager?

:confused:

cheers

---

### Post by kutjara on 2008-04-03
> **abh83 said:**
> i do have one more question though:

i don't really wanna ditch NM. Can I simply disable it and set WICD as my default network manager?

:confused:

cheers

When you install wicd using the instructions on the wicd website, it automatically uninstalls nm. Seems it doesn't like having it around for some reason.

---

### Post by abh83 on 2008-04-03
Well I'm proud to announce that I'm online via wicd!! Seems to be working fine and it only took me a couple of seconds to establish a connection to my home network!

Thx to all for your help!

Now I'll have to observe wicd over the next few days.

btw. does wicd have a netowrk info/monitor  feature for the gnome panel (just like nm)?

---

### Post by kutjara on 2008-04-03
> **abh83 said:**
> Well I'm proud to announce that I'm online via wicd!! Seems to be working fine and it only took me a couple of seconds to establish a connection to my home network!

Thx to all for your help!

Now I'll have to observe wicd over the next few days.

btw. does wicd have a netowrk info/monitor  feature for the gnome panel (just like nm)?

Yes it does, but you have to enablel it:

Hit Alt+F2 to bring up the Run Application window. Then type /opt/wicd/tray.py. That will put the applet into your gnome-panel.

To run the applet every time you boot, Go to System -> Preferences -> Sessions and add a new item called something like "WICD." Enter the same /opt/wicd/tray.py instruction in the "Command" box.

You should be all set.

---

### Post by abh83 on 2008-04-03
perfect, I just read that on their FAQ but never-the-less thx for your help kutjara!:)

---

### Post by kutjara on 2008-04-03
> **abh83 said:**
> perfect, I just read that on their FAQ but never-the-less thx for your help kutjara!:)

My pleasure. Now I just have to figure out how to get the damned thing to work properly in Hardy. :)

---

### Post by abh83 on 2008-04-03
i wish i could help but i'm no pro. it might simply be due to the fact that hardy is still beta and not many apps have been configured to work properly with it? :confused:

---

### Post by kutjara on 2008-04-03
> **abh83 said:**
> i wish i could help but i'm no pro. it might simply be due to the fact that hardy is still beta and not many apps have been configured to work properly with it? :confused:

That's most probably it. WICD works well enough once I've gone through the song-and-dance of connecting to the network, and that's something that'll no doubt be sorted out in the next few months.

---

### Post by motin on 2008-06-28
> **abh83 said:**
> How do I prevent Ubuntu 7.10 (network manager) from connecting to random wireless networks in the neighborhood?

I've got my own locked wireless home network set up. However, there are other open wireless networks in the neighborhood. On many occasions Ubuntu will connect to a random network other than mine which is very annoying.

Is there something like an exclusion list?


Help is greatly appreciated!

There is a bug report related to this issue at [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/46123)

However, the most useful comment is found in one it's duplicates' comments. Basically, it explains that in Hardy, NM will only attempt to automatically connect to the networks listed in nm-editor (right-click on the Network Manager applet -> Edit wireless networks). Then remove the networks that you do not want to automatically connect to.

---

