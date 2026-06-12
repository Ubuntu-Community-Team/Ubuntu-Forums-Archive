---
title: "Ctrl+Alt+Backspace"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-13
Two questions:

1) What is this *meant* to do?

and 2) When I press this key combination, everything shuts down and I am left with a blank screen with blinking white cursor up on the top left corner. Is this normal? I have read somewhere that this combination is supposed to restart Compiz or something.... I don't even get a command terminal or anything though! Just blinking cursor.

---

### Post by amadeus266 on 2009-03-13
That key combo restarts the x-windows system. Just like logging out. Basically the same thing as ctrl-alt-del to force a windows restart but the computer itself doesn't restart, just the GUI. You should be taken back to the login screen. If not, something is wrong and hopefully someone here can help you fix it.

---

### Post by humphreybc on 2009-03-13
Right so howcome it isn't working? Does it take a while to load up the login screen? I waited for about five minutes while the cursor flashed but nothing happened... the light on my computer does suggest the Hard Drive is being accessed, though.

---

### Post by Therion on 2009-03-13
> **amadeus266 said:**
> That key combo restarts the x-windows system.
That's what it did in Hardy...  And Gutsy and Feisty. But that function was, for whatever reason, disabled in Intrepid and appears disabled in Jaunty as well.

Too bad; it's a nifty feature I miss.

---

### Post by amadeus266 on 2009-03-13
I wasn't aware of the change, I'm using Hardy. Removing it makes no sense to me. Do they offer a replacement?

---

### Post by humphreybc on 2009-03-13
Oh damn so now when I press it it literally does *nothing* useful! It doesn't even open up a terminal window or restart the computer or anything... it just... kills Ubuntu and then does jack all about it! Stupid!

Is there a shortcut key to open up System Monitor (when in a fullscreen app) so I can terminate processes using the GUI?

---

### Post by amadeus266 on 2009-03-13
I have the system monitor app on my panel, just a click away.

---

### Post by nhasian on 2009-03-13
it is disabled by default but you can turn it back on in intrepid/jaunty.  

alternatively you can just type in a terminal:

```
sudo /etc/init.d/gdm restart
```

and if your using Compiz you can set a hotkey that executes the command as well.

---

### Post by Dr Small on 2009-03-13
What happens if you try to press ALT+F1?

---

### Post by humphreybc on 2009-03-13
How do I set a hotkey to restart Compiz?

> I have the system monitor app on my panel, just a click away.

That's all well and good when I can see the panel but I can't in fullscreen apps!

---

### Post by Therion on 2009-03-13
> **nhasian said:**
> it is disabled by default but you can turn it back on in intrepid/jaunty.
I'll PM you a dollar if you tell me how.

---

### Post by amadeus266 on 2009-03-13
You could try ctrl-alt-f1 wich should take you to a terminal screen with a login, then try the command given by nhasian.

---

### Post by Therion on 2009-03-13
> **Therion said:**
> I'll PM you a dollar if you tell me how.
Nevermind.  Found it...

[http://albertomilone.com/wordpress/?p=335](http://albertomilone.com/wordpress/?p=335)

---

### Post by amadeus266 on 2009-03-13
@Therion, you beat me to it by about 10 seconds. ;)

---

### Post by humphreybc on 2009-03-13
It appears that dontzap isn't available in the repositories anymore though...

---

### Post by Therion on 2009-03-13
> **humphreybc said:**
> It appears that dontzap isn't available in the repositories anymore though...
sudo apt-get worked for me just now...  

The install does, ironically enough, require that you restart X before the keystroke combo is effective though.

---

### Post by humphreybc on 2009-03-13
```


benjamin@ubuntu:~$ sudo apt-get install dontzap
[sudo] password for benjamin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dontzap
benjamin@ubuntu:~$ 


```

---

### Post by Therion on 2009-03-13
> **humphreybc said:**
> 

Couldn't find package dontzap

Sorry, dude.  It finds the package in Jaunty.

C'mon Ben! You know you want to install it...

How much longer do you think you can resist the mystic power of the Jackalope? Resistance IS futile you know.  Come over to the dark side of Ubuntu and experience the thrill of running your system in near constant Alpha-state! Breathe a sigh of *relief* when your OS goes BETA/RC-1!!

(Dear GAWD I think I need to change my shorts...)


Life on the edge, baby!!!!!!!!!

---

### Post by matthew.ball on 2009-03-13
I'm running Intrepid and the aforementioned key combination works fine - I haven't set up this dontzap thing (pretty much a default install here).

I actually get annoyed hearing that it is disabled in Jaunty :(

---

### Post by Kareeser on 2009-03-13
Ctrl-Alt-Backspace is also enabled on my vanilla install of Intrepid...

In fact, I use it all the time.. so for me, X isn't mature enough to disable such a handy feature.

Besides, it's not like someone would "accidentally" press it.

---

### Post by abybaddi on 2009-03-14
> **Dr Small said:**
> What happens if you try to press ALT+F1?

It just opens the Gnome-Menu.

---

### Post by martrn on 2009-03-14
Why remove Ctrl+Alt+Backspace ?

Very handy feature, and now every who doesn't have it will never install it and forever wonder why people will miss Ctrl+Alt+Backspace.

---

### Post by Therion on 2009-03-14
> **Kareeser said:**
> Ctrl-Alt-Backspace is also enabled on my vanilla install of Intrepid...
My mistake.  I was going by memory since I actually kinda skipped installing Intrepid altogether.  I can tell you for sure though, that's it's gone, gone, gone in Jaunty by default.  As you can imagine, there's a lot of discussion about it.  

Anyway, sorry for the mis-info.

---

### Post by Darkade on 2009-03-14
You can reenable it by editing your xorg.conf file

In graphical mode
```
sudo gedit /etc/X11/xorg.conf
```

In command line mode
```
sudo nano /etc/X11/xorg.conf
```

There you can look for the dont zap option.
Recently, in arch, I had to reconfigure X and I found that Ctr
+Alt+Backpace was diabled. When I went to check my xorg.conf I didn't found this zap thing, but a section that said something like "option $somenumber" I just commented it and it works again. I don't know if that helps.

BTW what the hell are you supposed to do if X frezees on you and this is diabled?

---

### Post by Dr Small on 2009-03-14
> **abybaddi said:**
> It just opens the Gnome-Menu.
That's funny. The GNOME menu requires X, and since he attempted to restart X and got a black blinking terminal, ALT+F1 would not open the GNOME menu. Instead, it should open a Virtual Terminal at VT1

---

### Post by amadeus266 on 2009-03-14
> **Dr Small said:**
> That's funny. The GNOME menu requires X, and since he attempted to restart X and got a black blinking terminal, ALT+F1 would not open the GNOME menu. Instead, it should open a Virtual Terminal at VT1

you need to press ctrl-alt-f1. alt-f1 is the menu.

---

### Post by Dr Small on 2009-03-14
> **amadeus266 said:**
> you need to press ctrl-alt-f1. alt-f1 is the menu.
Still, let me clarify.
If X is not running, how can it launch the GNOME menu?

If you are not in X, you don't need to press CTRL+ALT+F1, only ALT+F1

---

### Post by neu2buntu on 2009-03-14
maybe goto > system > preferences > keyboard shortcuts , and scroll down to "log out" and assign the ctrl-alt-backspace option there....maybe we will all have to do this in jaunty...who knows,but i will hang onto intrepid a bit longer anyway....................................................and a restart combo would be handy especially when i crash out using music apps such as lmms and rosegarden ,instead of having to resort to the hardkill switch>>>>>>>>>>>>>>>>>.

---

### Post by LollYouSuckZor on 2009-03-14
God, I loved ctrl+alt+del.

---

### Post by Dr Small on 2009-03-14
> **LollYouSuckZor said:**
> God, I loved ctrl+alt+del.
I know. I assigned that shortcut to launch htop :)

---

### Post by Penguin Guy on 2009-03-14
Sorry for double-post.

---

### Post by Penguin Guy on 2009-03-14
For me Ctrl+Alt+Backspace used to restart gnome, no problems. I think it must have been updated or something because it doesn't work anymore.

---

### Post by mvalviar on 2009-03-14
Ctrl+Alt+Backspace disabled?! Mine is working fine. I'm using ibex and I don't remember editing any config file since I installed last December. I have this...

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

same as everyone else.

---

### Post by Penguin Guy on 2009-03-14
> **mvalviar said:**
> Ctrl+Alt+Backspace disabled?! Mine is working fine. I'm using ibex and I don't remember editing any config file since I installed last December. I have this...

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

same as everyone else.
Try installing any updates that are pending and see if it still works for you; as I said, mine was working fine a few days ago.

---

### Post by mvalviar on 2009-03-14
I just ran an update. It was for the dkms thingy. Pressed the magic buttons and its still works. Drum roll and everything! Yey! I hope it stays that way.

---

### Post by humphreybc on 2009-03-14
> 

Sorry, dude. It finds the package in Jaunty.

C'mon Ben! You know you want to install it...

How much longer do you think you can resist the mystic power of the Jackalope? Resistance IS futile you know. Come over to the dark side of Ubuntu and experience the thrill of running your system in near constant Alpha-state! Breathe a sigh of relief when your OS goes BETA/RC-1!!

(Dear GAWD I think I need to change my shorts...)


Life on the edge, baby!!!!!!!!!



Heh funny you should say that, I was thinking of trying it out. How do I install the alpha upgrade? It'd just be an extra command on the sudo apt-get update or something?

> 
Ctrl-Alt-Backspace is also enabled on my vanilla install of Intrepid...

In fact, I use it all the time.. so for me, X isn't mature enough to disable such a handy feature.

Besides, it's not like someone would "accidentally" press it.

Hmmm that's odd. I haven't messed with my Xorg.conf too much, definitely nothing to do with any 'dontzap' thing. Here is my xorg.conf: (it has hardly anything in it!)

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

> You can reenable it by editing your xorg.conf file

What's the line that you add in look like if there is nothing there in the first place? Actually I presume that it is *enabled* because it does SOMETHING... like it kills X but it doesn't restart it so therefore it's.... broken?

> maybe goto > system > preferences > keyboard shortcuts , and scroll down to "log out" and assign the ctrl-alt-backspace option there

I had a look at this and I have that as ctrl+alt+delete set by default. I don't want to test it out right now because then I would lose all of this post if something went wrong(!) but I have a feeling that when I hit ctrl+alt+delete it brings up the shutdown menu giving you a selection of things (Restart, Shutdown, Hibernate, Suspend, Log off etc). Of course this wouldn't work if a fullscreen app froze on me...

> For me Ctrl+Alt+Backspace used to restart gnome, no problems. I think it must have been updated or something because it doesn't work anymore.

When you press it does anything happen at all?

> Try installing any updates that are pending and see if it still works for you; as I said, mine was working fine a few days ago.

> I just ran an update. It was for the dkms thingy. Pressed the magic buttons and its still works. Drum roll and everything! Yey! I hope it stays that way.

I am completely up to date and it still aint working!!


Hate to be the guy to bring Windows into this... but seriously, how easy was it to just hit ctrl+alt+delete in Windows, regardless of what status your computer was (fullscreen, windowed, frozen, unfrozen) and then just hit "end process" from a nice GUI. The system monitor in Ubuntu is pretty good and similar to that, but I would like to somehow assign a shortcut to load a process list that works regardless of window size...!


Man that was a lot of quoting. Phew.

---

