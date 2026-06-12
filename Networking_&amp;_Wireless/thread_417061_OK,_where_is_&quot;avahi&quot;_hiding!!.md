---
title: "OK, where is &quot;avahi&quot; hiding?!?!"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by starbase1 on 2007-04-21
OK, so I've got my nice new Feisty Fawn CD, and I have booted into it. I am hoping to connect to my other PC sp I can use it's network connection. (I never did get a net connection working with older versions, but that was some time back...)

Anyway, the two machines are on a wired windows home network, using a crossover cable. I carefully wrote down the address and subnet mask of the machine I am booting into Ubuntu, figuring this should make sense to the network.

I fed the numbers into the network settings, and it now shows up as a wired connection, with a tick by it. (Does the tick mean everything should be working?)

Anyway, i cannot see anything when I try and browse the network. I thought that FF came with something called 'avahi' that was going to do this for me, but I cannot find it in the menus, and search does not find it either.

Am I missing something obvious? Or can I download and install the 'avahi' utility via another computer? I am thinking of something like an executable windows install file that I can move over on a memory stick...)

Any and all clues gratefully received,
Nick

---

### Post by spd106 on 2007-04-22
I'm going to assume that you have a windows PC with an Internet connection and you want to share this with your Ubuntu PC via a crossover cable.

Ubuntu ----- Windows ----- ISP

You should have Windows ICS setup and configured, this will start a DHCP server and give the Ubuntu PC an IP address and gateway. Then you should be online. The IP addresses you will see will be Windows: 192.168.0.1 and Ubuntu: 192.168.0.x, where x could be anything 2-254.

Avahi-autoip will give you an address like 169.254.x.x if it fails to find a DHCP server, much like Windows does when it says "limited or no connection...". There's more to it than that, but I've outlined the important part.

---

### Post by starbase1 on 2007-04-24
Thanks SPD106, your assumptions are correct, that's pretty much what I am trying to do.

From the stuff I had read about what is new in Feisty, I was expecting to find a tool on my desktop that I could run which would then let me poke around my network, and see what it could find - I assumed this is what 'avahi' was.

From what you have told me I guess if I get the windows end set correctly, the network tools should do what I want?

Cheers!

---

### Post by spd106 on 2007-04-24
> I was expecting to find a tool on my desktop that I could run which would then let me poke around my network, and see what it could find - I assumed this is what 'avahi' was.

Not really, Avahi is more of a backend tool that applications take advantage of, there are a few already such as Rhythmbox's DAAP sharing and network printer detection. Others are in the pipeline, including Bonjour iChat support in GAIM/Pidgin.


> From what you have told me I guess if I get the windows end set correctly, the network tools should do what I want?

I should do, if you run in to a problem then post back.

---

