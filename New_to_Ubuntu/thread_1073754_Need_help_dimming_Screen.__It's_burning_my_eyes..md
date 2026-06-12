---
title: "Need help dimming Screen.  It's burning my eyes."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by concerto on 2009-02-18
I just bought a new laptop and I noticed that the screen is blinding bright.  So bright that after looking at it for a while, if I pull away from it and look around the room I cant see a thing.  I really hate to complain but I absolutely need a fix.

I right clicked on the brightness control and added the brightness control to the panel.

The Icon has a big red circle with a line through it so I can't change anything.

There has to be another way.


Also My function Keys are not working Right now.  any Suggestions would be great.

I have a :
Sony Vaio FW-378J
With the full HD Screen

Any help at all would be awesome.  

Thank you so much

---

### Post by rgb96 on 2009-02-18
I don't know about Sony, but I do know that Fujitsu laptops have major trouble adjusting brightness in intrepid. It seems to be a bug that just hasn't been fixed yet in their case. Just make sure you have the most up to date kernel is about all I can tell you.

---

### Post by rgb96 on 2009-02-18
oh, and search if there are any bug reports for sony brightness issues. You may be able to find a workaround that way.

---

### Post by capnthommo on 2009-02-18
hi concerto
i expect you already tried this but did you look in system>preferences>screensaver>power management?

like i say, i suppose you did but sometimes we overlook...
cheers
nigel

---

### Post by tomxyz on 2009-02-18
hi concerto,

Just an idea, I have an Hp laptop and (under windows) I could not control the brightness of the screen at all. No fix from Hp although according the internet a lot of similar cases.
Until the computer wizz at work said I should try to change the brightness using the keyboard keys and then push the little switch that is pushed when you close the lid of your laptop. Strangly that works and I've been doing it like that eversince. Ofcourse in power management it can't be set to hibernate or shutting down when closing the lid.

---

### Post by concerto on 2009-02-18
It's so nice to have everyone's input.

It seems that my function Keys don't work in Linux either so now I'm thinking if I can get my function keys to work I might have a round about way to fix it.

I still need everyone's input on this.  I really need this fixed.
Thank you all that have replied.

Any other suggestions welcome.

---

### Post by concerto on 2009-02-19
?

---

### Post by T2manner on 2009-02-19
Well you have an ATI graphics card right?
Have you installed the proper driver?

---

### Post by concerto on 2009-02-19
I Have an ATI RADEON card. yes.

How do I make sure everything is installed correctly?

Thank you.

PS.   Under Hardware drivers is says ATI/AMD proprietary FGLRX Graphic driver in use

---

### Post by T2manner on 2009-02-19
System > Administration > Drivers
i believe that's it.

I also had a very similar problem ( I have a sony vaio too) but my graphics card is Intel, so what helped me probably will not help you.

---

### Post by concerto on 2009-02-19
:(

---

### Post by concerto on 2009-02-20
I am still not having any luck with this.  Let me know if anyone has any suggestions.

---

### Post by rgb96 on 2009-02-20
Found this on another forum. See if it helps at all

"same here, using Ubuntu Gutsy,
but doing an 
"echo -n VALUE > /proc/acpi/video/VGA/LCD/brightness" works,
thanks, MZ
"

---

### Post by concerto on 2009-02-20
so I put ""echo -n VALUE > /proc/acpi/video/VGA/LCD/brightness"" into the terminal?

If it messes anything up can I undo it?
How exactly does this work?

Just wondering.

Thank you

---

### Post by snova on 2009-02-20
> **concerto said:**
> so I put ""echo -n VALUE > /proc/acpi/video/VGA/LCD/brightness"" into the terminal?

I don't know the specifics of this file, but it appears to contain the current state of the display brightness. If I use the function keys to dim my screen, it changes.

So, first we'll print out the contents, as doing so will give us a list of brightness settings. Post the output of:

```

cat /proc/acpi/video/VID/LCD/brightness

```

For comparison, mine looks like this when I dim it slightly:

```

levels:  100 60 12 24 36 48 60 72 84 100
current: 84

```

Choose one of the lower options, and run this command to change its value (which I tested, and works as expected- nifty!):

```
echo *<brightness setting>* | sudo tee /proc/acpi/video/VID/LCD/brightness
```

> If it messes anything up can I undo it?

Yes. At the worst, with a reboot.

> How exactly does this work?

It's a special file created by the kernel (it doesn't actually exist on your hard drive). By reading from it you obtain status information, by writing, you change options.

---

### Post by concerto on 2009-02-20
concerto@Sony-VGN-FW:~$ cat /proc/acpi/video/VID/LCD/brightness
cat: /proc/acpi/video/VID/LCD/brightness: No such file or directory
concerto@Sony-VGN-FW:~$

---

### Post by snova on 2009-02-20
```
ls /proc/acpi/video
```

Possibly just the wrong directory... lets see what's in there.

---

### Post by josvanr on 2009-02-24
on my PB easynote bg46 the screen brightness controls also don't work. I have to use sunglasses in the evenings for now......

josvanr

---

### Post by concerto on 2009-02-24
This is hard  :(

---

### Post by Aris+ on 2009-02-25
> **T2manner said:**
> I also had a very similar problem ( I have a sony vaio too) but my graphics card is Intel, so what helped me probably will not help you.

What exactly was it that helped you? I have an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller and my brightness isn't working (not to derail the thread... maybe you can PM me if it's OT here). I've been searching for days...

---

### Post by pme 72 on 2009-02-25
I had a similar problem with my desktop machine using Gutsy and an ATI Radeon Xpress 200 integrated graphics card. The problem went away when I upgraded to Hardy Heron. Intrepid Ibex offers even better graphics performance with open source drivers for that card.

---

### Post by frankenstein1000 on 2009-10-27
Has any one found a solution yet? I just installed jaunty a few day a got and enabled a dark theme to reduce the light but since most web pages are white browsing is a pain.

---

### Post by skompier on 2009-10-27
If you can run Compiz..then look at this.

[http://www.youtube.com/user/gotbletu#p/u/6/30hgV2XX6CU](http://www.youtube.com/user/gotbletu#p/u/6/30hgV2XX6CU)

---

### Post by xubu_caapn on 2009-10-27
Adjusting the brightness via the laptop's function keys is not a 'round-a-bout' way to fix this, it's the proper way. Fixing this is probably just a matter of configuring xmodmap, google is your friend on this.

---

