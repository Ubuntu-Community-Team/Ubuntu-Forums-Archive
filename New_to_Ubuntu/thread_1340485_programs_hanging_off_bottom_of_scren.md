---
title: "programs hanging off bottom of scren"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by Red87 on 2009-11-28
I just installed ubuntu on the computer in our family room, which is connected to our TV. The TV is a 40 or so inch Panasonic HD which is wider than standard TVs, (I think it is 16:9) The computer is...old. the problem is that certain windows, when opened, seem to hang below the bottom of the screen. because they are too big, i cannot find a way to resize them, and therefore cannot do stuff in the bottom of them. It seems like the bottom bar of ubuntu is in the correct location though, so this is very confusing for me.I am also worried that some items may become inaccessible if placed to low on the screen. also, some things that get opened are just way too huge, like, twice the size of my desktop

this screen shot shows what i am talking aboot

[http://s805.photobucket.com/albums/yy338/dspin37/ubuntu/?action=view&current=Screenshot.png](http://s805.photobucket.com/albums/yy338/dspin37/ubuntu/?action=view&current=Screenshot.png)

currently, the resolution is set to 800*600, which is the highest it can go. all the other options are also 4:3

earlier this week we had windows xp running, and this was not a problem at all.

thank you in advance for your help

---

### Post by jbrown96 on 2009-11-28
You can move any window in Linux by holding alt then click and drag any part of the window. 

The main problem is your resolution. You probably need to activate a graphics driver. Post the output of ```
lspci | grep VGA
``` from a terminal (applications-->accessories-->terminal)

---

### Post by heyho on 2009-11-28
Out of interest, how are you connecting?  VGA?

---

### Post by pizza-is-good on 2009-11-28
Make sure you have recommended graphics card driver. 
System>>Administration>>Hardware Drivers

You should set all the aspect rations to 16:9.

Also, tell us which windows/programs are 'hanging off' and which ones are not.

If you see the bottom bar, then this shouldn't apply, but give it a try anyways.

On my HDTV, a Philips 49", you need to change the scaling of the input signal. It varies for different devises, and it comes to automatic by default, which doesn't always work. For example, if the PS3 input of the tv is in automatic scaling, then it will cut off about 3 inches from the left and stretch the rest.
Different TVs have different options, so give them all a try. Also, if you are sending on 4:3, like my DVD player does to my TV, then unless you change the scaling, top and or bottom parts of the screen can be cutoff.


Give us all the info you can (all of your computer specs, your TV specs, cable you are using to connect TV to PC, anything you can think of...), and then it will be easier to help.

---

### Post by Red87 on 2009-11-28
> ray@ray-desktop:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
01:09.0 VGA compatible controller: ATI Technologies Inc Rage 128 RE/SG
ray@ray-desktop:~$ ^C
ray@ray-desktop:~$ 

I believe it is VGA, thats what it looks like when i search for pictures of VGA

going to system>administration>harware drivers shows "no proprietary drivers in use" and nothing else.

i cannot find anything that will allow me to set the aspect ratio 16:9 on the computer or the TV

so, as far as i can tell, specs wise, VGA connection, Panasonic 16:9 big HDTV, and as far as the computer, i dont even know how to figure out. this thing is ancient. my dads office gave it to him for free because they didnt have a use for it anymore, i believe

---

### Post by Red87 on 2009-12-02
bump.

anyone have any ideas?

is the graphics setup straight up just too old?

the reason im asking is because it worked fine before in XP, so im fairly sure there is some way to get graphics to higher resolution, just damned if i can find it.

---

### Post by jbrown96 on 2009-12-02
You may need to install a newer version of the open source drivers. [Here's]("https://help.ubuntu.com/community/RadeonDriver") some instructions. Start at the section labeled "Removing the proprietary fglrx driver." X.org should get configured automatically, so skip from "Configuring X.org" to "Restart."

---

