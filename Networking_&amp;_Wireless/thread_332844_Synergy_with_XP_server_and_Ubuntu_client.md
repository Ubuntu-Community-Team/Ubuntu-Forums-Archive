---
title: "Synergy with XP server and Ubuntu client"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Lerferz on 2007-01-06
I'm having some real problems setting up Synergy, I don't know what I'm doing wrong a real walkthrough would be nice.
I want my XP machine to be the server and I want my Ubuntu machine to be the client.

Both my machines are in the same workgroup, MSHOME and they are called deskluke and luke-laptop.

**deskluke** = xp machine, server
**luke-laptop** = ubuntu machine, client
**positioning** = 
ubuntu machine is to the right of my xp machine** / **
luke-laptop is to the right on deskluke.

On Ubuntu I'm pretty sure my *synergy.conf* should look like the following
```
    
section: screens
       deskluke:
       luke-laptop:
    end
    section: links
       deskluke:
           right = luke-laptop
       luke-laptop:
           left = deskluke
    end

```

On XP this is what I have set up;
[IMG]http://img.photobucket.com/albums/v311/koRnucopia/part1.png[/IMG]
I believe that's all right?
Can someone confirm this?

I start the server in XP/deskluke and hovering over the icon shows, Synergy 1.3.1: Waiting for clients.

I then try to start a client in unix by entering;
```
synergyc -f deskluke
```

It does this, it starts up the client "CScreen.cpp,38:opened client" but it continues to say
WARNING: synergyc.cpp,265: failed to connect to server: address not found for deskluke.

I think I know pretty much that it's not finding the server, but what have I done wrong?

---

### Post by actinium on 2007-01-07
have you tried QuickSynergy? I got that working, haven't really tried with just the synergy command though. 

Regards, 

Alan

EDIT:

i just tried with the command line client and it is working fine, try deleting your synergy.conf? since you won't be needing it if you are only using the client. Is your connection port open?

---

### Post by Lerferz on 2007-01-07
Thanks man, I didn't try quicksynergy but what I did do was instead of trying to connect to deskluke I tried the IP.
It works fine now.
Although thank you for helping man.

---

