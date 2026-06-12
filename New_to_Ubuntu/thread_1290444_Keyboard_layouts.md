---
title: "Keyboard layouts"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by snaudalius on 2009-10-13
Hello.
I have problems with my keyboard layouts. There are just two - US and LTU. I can switch between them with no problem until I restart my laptop. After restart pressing [Shift Alt] turns on Scroll lock and Greece language. I have to press [Shift Alt] few  times in order to find good layout. There are no Greece layout in keyboard settings. I tried to add layout plugin to my upper panel and it helped but it disapears every time I press [Shift Alt] after restart.

---

### Post by mick222 on 2009-10-13
system-> preferences-> keyboard layouts add there is a greek layout here .Hope that helps.

---

### Post by snaudalius on 2009-10-13
Sorry but I want to have two layouts - US and LTU. The problem is that I have the third from somewhere:confused:

---

### Post by cholericfun on 2009-10-13
you can remove a layout there too

---

### Post by snaudalius on 2009-10-14
I know  I can. But there is no Greek layout. I did not choose it. There are US and LTU. In settings I sett two languages and after restart [Shift Alt] turns on Greek which should not be there at all. Scroll lock turns on too.  I think my English is bad therefore you cannot understand. The PROBLEM: [Shift Alt] should switch between US and LTU but it turns on Scroll Lock and switches between US, LTU and GR. Language bar in panel helps for some time but it dissapears in a misterious way after i restart and push [Shift Alt] :)

---

### Post by lz1dsb on 2009-11-16
I'm having almost the same problem. In my case I'm using Ubuntu 9.04 on a VMWare virtual machine. I'm accessing it through VNC using the x11vnc package. Basically I try to use three layouts: US, DE and Bulgarian. So after the configuring the layouts I can switch between them, but for the special characters (Umlauts in German for example) I got a problem: they're replaced by some Cyrilic characters from my Bulgarian layout. And it's quite a mess, so I can't really use the three layouts and switch normally between them. 
What is even more strange is that after returning to defaults: US layout only. When I use the Alt+Shift it still switches between the three layouts, even though only US is configured, but this time correctly, I just don't get the normal indication on the panel, where only USA is indicated. I've reseted the X several times, and it's still the same. I also used the button Apply-System Wide on the keyboard layout configuration but the result is unchanged. So at the moment I'm switching between the layouts, but there's no such configuration what so ever, and because of that I don't have proper indication on the panel.
I still wasn't able to locate any registered bug in Ubuntu....

---

### Post by lz1dsb on 2009-11-16
I just forgot to mention that in the output of x11vnc I see messages like:
"added missing keysym to X display....."

---

### Post by lz1dsb on 2009-11-26
Hi folks, 
Just a short update on the problem I mentioned in my posts above. Today I found unintentionally that there seems to be a relation with the VNC client I'm using. I just connected to the station from another Linux machine using the KRDC client (when I mentioned about the problem initially, I was using RealVNC veiwer from a WindowsXP machine) and just tried the layout configuration I'm trying to use: US, Bulgarian and German layout. It works without problems, the way it should be. The layout indication is also correct. So I guess that's the reason why I wasn't able to find any bugs matching the problem I was experiencing. Quite frankly I'm a bit confused by this, as I've nevet thought that the VNC client could influence the keyboard change. I'll made a bit more of testing this days and will try to research on this, at least to get an idea how the VNC client is influencing the keyboard layout. I'll post whetever I find here...

Cheers, 
Boyan

---

