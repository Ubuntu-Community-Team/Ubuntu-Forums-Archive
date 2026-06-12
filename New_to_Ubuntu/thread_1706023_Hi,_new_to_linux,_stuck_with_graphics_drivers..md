---
title: "Hi, new to linux, stuck with graphics drivers."
date: 2011-03-13
forum: New to Ubuntu
---

### Post by fusiomax on 2011-03-13
Hi, I'm Fusiomax. My level of ability with any form of Linux is nil, but I am considered tech support by most of my family.

Just yesterday I installed Ubuntu  as a dual boot on my vista pc (I'm not sure of the specifications off hand and am unsure of how to get them on Ubuntu).
All went well, so I decided to install GuildWars so I went about it as so:

```
sudo apt-get install wine

wget http://www.guildwars.com/downloads/gwsetup.zip
unzip gwsetup.zip

wine GwSetup.exe /complete
```Once it had installed I had an icon on my desktop, I used that icon to open GuildWars and got a familiar bunch of squiggles, the same squiggles i got when i installed it on vista and hadnt updated my drivers.

So i went about installing my drivers:

system>addministration>additional drivers

it opens nicely and i get 2 graphics drivers come up:
1. NVIDIA accelerate graphics driver (version 173)
2. NVIDIA accelerated graphics driver (version current) [recommended]

When i try to activate number 2 it gives me an error message saying:
SystemError:failed to lock /var/cache/apt/archives/lock

Thats where im stuck, the only other information i can give you is that im running onboard graphics.

Thanks for reading that long post.

---

### Post by PunkLV on 2011-03-13
> SystemError:failed to lock /var/cache/apt/archives/lock
This usually occurs if you have Synaptic open or updates are in progress. As linux allows only one application to handle the installed software at a time, for obvious reasons.

By the way, have you installed directx for wine?

---

### Post by fusiomax on 2011-03-13
thanks for the fast reply

no i havnt installed directx for wine, how woulld i go about doing that? and more importantly why do i need to do that? (i need to understand or i wont learn)

and what is synaptic and how do i tell if its active?

Probably sounds like newby questions but, you dont ask you dont learn;)

---

### Post by PunkLV on 2011-03-13
For directx refer to: [http://www.wine-reviews.net/wine-reviews/games/how-to-install-directx-in-linux-using-wine.html](http://www.wine-reviews.net/wine-reviews/games/how-to-install-directx-in-linux-using-wine.html)
And in Wine Configuration set Windows version to Win2000. To avoid a known bug, although I do not know if it had been fixed.

Close everything you have running and go to *Applications > Accessories > Terminal*
```
sudo apt-get update && sudo apt-get upgrade
```
Should do fine, otherwise you will recieve:
```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
In any case, post the results/errors/mark as solved

---

