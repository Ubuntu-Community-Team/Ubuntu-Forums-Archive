---
title: "Set Color Depth to 16-Bit"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Redmage913 on 2009-08-12
Greetings,

I'm trying to decrease the color depth to 16-bit in an attempt to increase the efficiency of one of my wine programs (Starcraft).

Any suggestions would be appreciated.  I have little experience with Xubuntu (running 9.04), and have no idea where to look to change this setting.

Thanks,
Redmage913

---

### Post by Diabolis on 2009-08-13
```
gksudo gedit /etc/X11/xorg.conf
```

In the section "Screen" add the line **DefaultDepth 16** so it will look similar to this:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    16
EndSection

```

Then restart the xserver by loging out and then loging in.

---

### Post by Redmage913 on 2009-08-16
When I type in the gksudo command, the terminal sits for a few seconds, then it displays another prompt.  nothing happens.

Any suggestions?

--Red

---

### Post by 4Orbs on 2009-08-16
Since you are using xfce, your text editor is probably mousepad rather than gedit. Just replace gedit with mousepad in the above command.

---

### Post by Redmage913 on 2009-08-16
Thank you much!

Quick question though - is gksudo different than sudo? This is the first time someone suggested to me to use the gksudo command.

I just made the edits, and will be restarting the computer to see if it took effect.  Is there any way of verifying that it is indeed 16-bit?

--Red

---

### Post by stwschool on 2009-08-16
Gksudo just makes that graphical prompt for your password come up where sudo asks for it in the terminal. Other than that it's the same.

---

### Post by Redmage913 on 2009-08-16
Also, if I want to change back to true color, should i set the color depth to 24 or 32? I've read they're virtually the same thing and the last 8 bits are empty or something like that...it was in technical-ese so I didn't quite understand it

---

### Post by 4Orbs on 2009-08-16
Use gksudo when you need admin access to an app with a gui. Use sudo when you are using only the terminal. Once you are using the 16 bit depth, it should be obvious because the colors will be greatly reduced. The desktop won't look as sharp and as nicely colored as it does with 24 bit.

---

### Post by Redmage913 on 2009-08-16
Well, if that's the case, I am unsure if it worked.  The desktop looks the same to me, along with firefox. I checked my favorite webcomic (PLUG: Questionable Content), and it still looks the same.

Here is the xorg.conf file where I edited:

Section "Device"
               Identifier              "Configured Video Device"
EndSection

Section "Monitor"
               Identifier              "Configured Monitor"
EndSection

Section "Screen"
               Identifier              "Default Screen"
               Monitor             "Configured Monitor"
               Device                     "Configured Video Device"
           DefaultDepth        16
EndSection

---

### Post by Shig on 2009-08-16
Running the following command in a terminal is a good way to see what BPP your display is running at:
```
xdpyinfo | grep "of root"
```

The grep "of root" bit simply filters the output of the command, you can run xdpyinfo by itself to get a lot more information if you wish.

---

### Post by Redmage913 on 2009-08-16
> 
matthew@handy-dandy-notebook:~$ xdpyinfo | grep "of root"
  depth of root window:    16 planes
matthew@handy-dandy-notebook:~$ 


success?

---

### Post by Shig on 2009-08-16
> **Redmage913 said:**
> success?
Success!

---

### Post by Redmage913 on 2009-08-16
success.

okay, to set it back to default, plug in 24 or 32 for the color depth in xorg.conf?

---

### Post by 4Orbs on 2009-08-16
EDIT: Disregard this post due to slow typing and lack of expertise.

I guess my method of verification was a bit crude and subjective. There probably is a command you can enter in a terminal to verify the change to 16 bit, but I don't know what it would be. If you are using an nVidia proprietary driver, you can open the nVidia Display Settings Mgr and look under Monitor 0 and it will show the color depth (but it pulls that info from the xorg.conf, so I don't know if that would be legitimate verification). Eventually, one of the forum's Ubu-gurus should post a satisfactory answer for you.

---

### Post by Redmage913 on 2009-08-16
I found a way to check your color settings with this website:

[http://www.cywarp.com/faqtruecolortest.htm](http://www.cywarp.com/faqtruecolortest.htm)

Thanks for all your help, fellow geeks.

---

### Post by 4Orbs on 2009-08-16
Does your video game run better now?

---

### Post by Redmage913 on 2009-08-16
it's better - a little choppy, but muuuch better than before.  you'd think starcraft could be emulated on a modern laptop (dell mini 9)....*shrug* i'm just glad it works.  i wasn't looking forward to having to install windows *just* to play it.

---

### Post by 4Orbs on 2009-08-16
I don't know if this would apply to Starcraft, but when I play Diablo2 on my old computer, I set it to run in 2D rather than 3D and it performs as well as it does on Win XP. Actually, it performs better than 3D on XP. It runs flawlessly in wine at 2D. The lack of 3D is a minor sacrifice when weighed against the performance increase.

---

### Post by theo77 on 2010-11-30
Hi! I would like to do the same, but i do not have this xorg.conf file. I need the 16 bit color depth on my eee pc, since I experienced with windows that this way the battery time is ca 30 percent longer. Now I'm a satisfied Ubuntu 10.4. user. But still it can be better :) and longer :D
Any idea?

---

