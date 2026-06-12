---
title: "Questions?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by 3wells on 2009-03-07
After banging away at getting my modem installed and connecting.... Only have DUN where I live, no high speed anytime soon in my area... grrrrrrr!

1 - Ubuntu attempts to connect during boot up? However, it does not / is not seen by Firefox. Why?

I must disconnect using the 'network' icon next to the clock & reconnect using Gnome PPP. 

2) Once connected, the network icon does not show 'connected'? As for Gnome, the connecting screen remains on my desktop - does not go away?

Any help here would be great! An explanation would be great as well as the quick and easy fix! lol!

3) Been looking for eFax - in one *.deb pkg... can't seem to find it?

4) Been a year since I last played with Ubuntu (GG 7.1), where's the add progys/features button?  

EDIT: Found the 'button', it tells me I need a working internet connection? Which I have, as I write this note! What's up with this?

thanks!

3

---

### Post by Hobgoblin on 2009-03-07
> **3wells said:**
> 
1 - Ubuntu attempts to connect during boot up? However, it does not / is not seen by Firefox. Why?

I assume you are not using network manager to manage the connection, therefore Firefox thinks you have no internet connection.

Type **about:config** in the Firefox URL bar, accept the warning message then find toolkit.networkmanager.disable and set it to to true.

---

