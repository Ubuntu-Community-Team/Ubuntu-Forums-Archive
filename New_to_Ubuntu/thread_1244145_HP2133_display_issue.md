---
title: "HP2133 display issue"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Chalfont on 2009-08-19
Hi
I tried on some other forums with no real luck so am now trying here.

I have an HP 2133 netbook.  
Yes, I know it's about the worst I could have and still want Linux on it (I loved the people who wrote back in the other forums to say just buy a different netbook!).  I have put Linux Ubuntu 9.04 on it, I tried both the desktop and netbook variety, it currently has the netbook version loaded. 

The actual display on the screen only shows the left 75% and top 75% of the complete 'desktop'.  It cannot be scrolled or moved at all.

I have already tried all the permutations of changing the display/monitor settings in Ubuntu.

If I plug in an external monitor, I can then see the full desktop displayed but the mouse pointer does NOT display at all.

Apparently there is some underlying configuration issue in a config file.

Now my BIG problem is that what instruction/suggestion I have received in the past, or help files/results of Googling have always expected that I have a working knowledge of Ubuntu already.  I don't.

For example, I have been told to edit a file.  I cannot even find the file, even when following the steps on a forum.

So please, can anyone tell me in simple straightforward steps what needs doing to make this work?

If you have a working 2133 please tell me what you did in detail to make it work.

Thanks for your help.

---

### Post by SuaSwe on 2009-08-19
Do you still need help with this or have you decided to head for Windows? If not, I'd be happy to translate the guiding posts/articles you've found on this subject into easy-to-understand language for you. :)

---

### Post by SuaSwe on 2009-08-19
I take it you're using Jaunty?

Going from this article here:

[http://hp2133linux.blogspot.com/2009/04/installing-ubuntu-904-on-hp-2133.html](http://hp2133linux.blogspot.com/2009/04/installing-ubuntu-904-on-hp-2133.html)

- Open Terminal (Applications > Accessories > Terminal)
- In the Terminal window, type in 'gksu gedit /etc/X11/xorg.conf' (no quotes)
- You should get a Notepad-esque window with the contents of the xorg.conf file
- Find this section:

```

Section "Device"
Identifier "Configured Video Device"
EndSection

```

Add to it the text marked in red, in that position:

```

Section "Device"
Identifier "Configured Video Device"
[color="red"]Option "PanelSize" "1024x600"[/color]
EndSection

```

Save the file as per normal (File>Save or Ctrl+S), close, reboot machine. That should be everything!

---

### Post by Chalfont on 2009-09-03
Hi
Thanks for your reply, I have been away so didn't see it until today.

FINAL EDIT - disregard the rest of this - it turns out the path is case sensitive and I was typing x11 in lower case (why would they use upper case just in one subdirectory? sheesh!

Anyway, IT IS NOW WORKING!!!! Yaeh! :-)
Thanks for all your help.


---------------- Old post before edit -----------------
I followed your simple and clear instructions (thanks) and when xorg.conf opens it is blank (which suggests that I am creating a new file.

Would xorg.conf be somewhere else?
Can I create xorg.conf with just the 4 lines you have written there?

Actually just typed in teh four lines and tried to save it but it won't allow me to save it, says the file does not exist.  Does this mean I haven't loaded Linux correctly if this file is missing?

[By the way, to answer your earlier question, I cannot live with Vista on this netbook, it is sooooooooo slow! so no, I haven't decided to just live with Windows.]

---

### Post by SuaSwe on 2009-09-03
Sweet! It's great when people come back and say when something's worked so that others with the same problem have some reference - nothing worse than reading through a thread going "Yes, this is exactly the same problem as mine!" to find it just ending right in the middle, unsolved. :D

---

