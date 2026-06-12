---
title: "How-to and How-to?"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by hemajang on 2008-08-02
Hello all,

I'm writing this as a how-to for beginners(like myself) and a how-to? for the more advanced. I am no expert by any stretch, but these steps worked for me.

I've just recently started using Ubuntu(Hardy 8.04), or linux for that matter. But coming from a Mac background, I'm used to working with a CLI. 

Getting my ubuntu box hooked up to my wireless network was the first obstacle. 

First thing I had to do was install a wireless adapter. No biggie here. Once that was in, I connected my box to my router _with an ethernet cable_, powered up with the Ubuntu install disk inside. This brought me to the install screen. Hit install and filled in the install prompts. Ubuntu automatically detected my network hardware and set up the default DHCP settings from my router. I'm planning to use this box as a development server so I needed to install several packages(LAMP, SSH, etc). I accidentally chose not to install them when prompted during installation (I didn't know I needed to use spacebar to check them, hitting return(enter) instead. Moving on...

Once installation was done, I powered down, disconnected my ethernet cable and prayed I wouldn't have to configure much to get the wireless going(I spent the previous couple days reading how-tos and forums to prepare and was overwhelmed by the sheer numbers of issues and complexity of "fixes" ie ndiswrapper, ndatwrapper). Amazingly, it booted up without popping up that big warning "You Messed Up!" I had been dreading and dreaming about. First thing I did was to check if I was in any way connected. Nope. But after staring blankly at the desktop for a while wondering what I need to do, I noticed a little icon top right. Right clicked on it and lo and behold a menu dropped down with my network name on it. Clicked it and filled in my username and password. It worked! It said I was connected. So far so good.

But as I mentioned, I wanted to setup a development environment. LAMP installation went without a hitch using Synaptic. Once that was done I installed the SSH server. No sweat. Because I was setting it up as a server I needed to setup a static ip address. Very good tutorials out there to help you accomplish this. Just search "Ubuntu static ip". I wanted to test things out, so I jumped on the laptop, also on the network and tried SSH'ing in. No go. Terminal just hangs till "...Operation timed out". After some researching and tinkering(more tinkering) what worked for me was manually configuring my network settings. Reviewing my settings in Network Manager revealed that I was still connected to the network via ethernet adapter. I'm guessing this was from the installation setup when I was wired to the router, and that I wasn't connected to any other computers on the network, that I was just accessing the internet through my wireless adapter and the router? I could be wrong, anyone with any suggestions as to how this happened?

What worked tho was changing the network settings from the ethernet adapter to my wireless adapter, pretty much jus copying those settings over, and disabling the ethernet network connection. Now I could not only access the internet, but also access this box from another machine via ssh.

This is by no means an in-depth tutorial on how to get wireless running, just how I managed to get things to work for me(mostly).

Now I still have some issues and concerns:

[LIST]
[*]When I assigned a static ip, I simply used the ip address that was assigned to the machine through dhcp, I've read articles stating that you should use an ip address that is outside the range of the assigned ip's of the router(dhcp server). Do I need to change this? I have a feeling I may run into a conflict, especially when I add a new machine to the network.
[*]I would also like to set up a dns server on this box, so I can use a private domain, however, from all the tutorials on how to do this, it seems I have to set a static ip address for all the machines in my network. Is there a way to keep the dhcp assigned address on my client machines, and just have a static ip on the server?
[/LIST]

It would be great if someone could point me in the direction of how to setup a network like the following:

Server (Ubuntu 8.04) - development environment(LAMP server, SSH, DNS, etc

Client machine (Mac OS X Tiger) - Most of the coding done on this machine and then transfered and housed on the web development server above.

Client machine (Windows XP) - No coding and file transfers done on this machine. Just used to access the websites on the server via browser for design (html, css, IE) purposes. Oh and playing games.

Thank you

---

