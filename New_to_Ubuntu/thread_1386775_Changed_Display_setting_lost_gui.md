---
title: "Changed Display setting lost gui"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-01-21
hi all

i was trying to watch a movie on my plasma tv and managed to wipe out my gui....

I changed some display setting, not sure which, andcan only boot into terminal...

can someone please get me out of this and if possible help me get a movie on the
tv since i am looking prettty foolish in front of my guests...:)

I probably caused more damage by using command
$rm -rf .gnome .gnome2 .gconf .metacity
$dpkg-reconfigure  xserver0-xorg

if I try
$xterm
i get 
$cannot open display 

wbg

---

### Post by bikeboy on 2010-01-21
Try removing your xorg.conf, the safe way.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.test
```

---

### Post by wannabegeek on 2010-01-21
hi bikeboy,

followed your command and cd into X11

i see the xorg.conf.test
i tried 
$X
for the hell of it and got a long error message and the suggestion to check  the log file
"var/log/Xorg.0.log"

I tried booting into safe graphics mode from LiveCD and that got me a flashing screen with a command prompt
ubuntu@ubuntu$
'
thx

---

### Post by warfacegod on 2010-01-21
xorg files are shipping blank now. Use:

```
gksudo nautilus
```

Browse to it and erase what's inside the file.

---

### Post by warfacegod on 2010-01-21
Scratch that last. You don't have a GUI.

I'd start by reinstalling gdm:

```
sudo apt-get purge gdm

sudo apt-get install gdm
```

---

### Post by wannabegeek on 2010-01-21
Hi war,

thanks for responding, my gf wants her machine back so I will have to work on this at school...
will there in an hour...

thank you a ton....
wbg

---

### Post by warfacegod on 2010-01-21
> **wannabegeek said:**
> Hi war,

thanks for responding, my gf wants her machine back so I will have to work on this at school...
will there in an hour...

thank you a ton....
wbg

Fixing a computer in physics class. What if you miss one tiny piece of info and you end up being the guy that creates monopoles with the LHC? Do you know how many people will be pissed about that?

---

### Post by wannabegeek on 2010-01-21
hey folks,

couldn't find my thread for a second...I need to stop smoking so close to school term starting... :)

anyways,

I ran the commands in terminal...awaiting further informed instructions
wbg

---

### Post by warfacegod on 2010-01-21
Try my first post from LiveCD. You shouldn't need to do gksudo Nautilus from there.

---

### Post by wannabegeek on 2010-01-21
ok...

rebooting into  LiveCD...selected 'Try...'...so far so good...
I see the usual graphic and the Ubuntu music...yeah...

how do I save these settings so that they are used when i boot from HD ?

thx

---

### Post by warfacegod on 2010-01-21
Use the LiveCD to browse through your HDD to get to your installed xorg file. When you reboot, it should use it automatically. What kind of video card are you using. If nVidia then try putting this in your xorg.conf if making it blank doesn't work.

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```

---

### Post by wannabegeek on 2010-01-21
on Dell 1150 notebooks the video card is part of the motherboard....
 
Sorry I'm a little lost...

I'm not sure if you mean that I should change the xorg.conf file or blank it...also
I'm not sure where it is ....i'm thinking you mean blank it...
can't I do this from terminal ? esp since I will need root priv...?

---

### Post by warfacegod on 2010-01-21
> **wannabegeek said:**
> on Dell 1150 notebooks the video card is part of the motherboard....
 
Sorry I'm a little lost...

I'm not sure if you mean that I should change the xorg.conf file or blank it...also
I'm not sure where it is ....i'm thinking you mean blank it...
can't I do this from terminal ? esp since I will need root priv...?

Blank it first. If that doesn't work then try changing it. It's in /etc/X11/xorg

You can do it from LiveCD or Terminal either is basically root. I suggested LiveCD because that will give you a GUI and I don't know how familiar you are with Terminal. I generally tend to lean more towards GUI instructions because of that.

---

### Post by wannabegeek on 2010-01-21
I think I can handle the terminal
...I nav to /etc/X11   then open the xorg.conf    in   nano  and erase all the text..
sound right...?

---

### Post by warfacegod on 2010-01-21
> **wannabegeek said:**
> I think I can handle the terminal
...I nav to /etc/X11/xorg  then open the xorg.conf in gedit and erase all the text..
sound right...?

Good, because there's been times I wasn't sure *I* could handle the Terminal.

Yes that sounds right.

---

### Post by warfacegod on 2010-01-21
> on Dell 1150 notebooks the video card is part of the motherboard....

Most laptops are that way. It will still be Intel or ATi or whatever.

```
sudo lshw
```

Will give you a rundown of your installed hardware. Your video card will be under display (naturally).

---

### Post by wannabegeek on 2010-01-21
hey warfacegod....I blanked it in nano, rebooted and everything is back to normal !!

I really need to learn about X windows....

do you have a suggested reading ?

also, I would like to be able to watch movies from this machine on my TV, 
i searched the threads a bit and didn't any solved ones dealing with this..

thanks again,

how's your winter ? i just noticed you're in Conn... I lived in Boston for a few years
man it was cold, especially inland....

wbg

---

### Post by warfacegod on 2010-01-21
> **wannabegeek said:**
> hey warfacegod....I blanked it in nano, rebooted and everything is back to normal !!

I really need to learn about X windows....

do you have a suggested reading ?

also, I would like to be able to watch movies from this machine on my TV, 
i searched the threads a bit and didn't any solved ones dealing with this..

thanks again,

how's your winter ? i just noticed you're in Conn... I lived in Boston for a few years
man it was cold, especially inland....

wbg

I need to learn about x windows too! I'm trying to get Mythbuntu talking with my Zenith (really an LG) with *S-video!*

First thing you'll need to do is use that last command I gave you to get your video specs. It's must have knowledge if you want TV.

Winter's bad. Not too much snow but I'm a Contractor so winter + economy = no jobs for me. I keep trying:

```
sudo apt-get purge winter

sodo apt-get install waitingspringcontracts
```

but it just keeps giving me errors and then gives me a strange look, like I'm weird or something.

---

### Post by wannabegeek on 2010-01-21
>    but it just keeps giving me errors and then gives me a strange look, like I'm weird or something. 

this explains why i see you logged on so much...no work and too cold outside...best to stay in and not spend any money.... for me, staying home and no work -->depression ---> beer, 420 and bad sci-fi movies.

---

### Post by SymphonicNerd on 2010-01-21
> **warfacegod said:**
> I need to learn about x windows too! I'm trying to get Mythbuntu talking with my Zenith (really an LG) with *S-video!*

First thing you'll need to do is use that last command I gave you to get your video specs. It's must have knowledge if you want TV.

Winter's bad. Not too much snow but I'm a Contractor so winter + economy = no jobs for me. I keep trying:

```
sudo apt-get purge winter

sodo apt-get install waitingspringcontracts
```but it just keeps giving me errors and then gives me a strange look, like I'm weird or something.

Warface all the post i see you write have always proven quite helpful thanks, but I love your sense of humor :$ if only our terminals could help todays economy and finding work

---

### Post by warfacegod on 2010-01-21
> **wannabegeek said:**
> this explains why i see you logged on so much...no work and too cold outside...best to stay in and not spend any money.... for me, staying home and no work -->depression ---> beer, 420 and bad sci-fi movies.

Can't spend money that doesn't exist. I didn't make enough this year to get me through the winter so I'm hurting pretty bad. When I busted my knee a few years ago, No work = Depression> Beer> +55 lbs.> And any Sci-Fi movies (I've seen This Island Earth too many times now to think it's bad.)

> **SymphonicNerd said:**
> Warface all the post i see you write have always proven quite helpful thanks, but I love your sense of humor :$ if only our terminals could help todays economy and finding work

If you like my humor, then this will liven your day:

[http://ubuntuforums.org/showthread.php?t=1379471]("http://ubuntuforums.org/showthread.php?t=1379471")

I'm glad you guys find my posts useful. It lets me know I'm not wasting my time here. Two days ago, I had another user accuse me of "fanboyism" and not knowing what I'm doing, in the link I just posted. Don't bother looking for his post, the staff removed it (and I wanted to leave it just to see how many users slammed him for it). So, thanks.

...And remember, I'm usually lurking about.

---

### Post by warfacegod on 2010-01-21
You may want to read that thread even more now. I got my TV to work as a monitor. Bad Sci-Fi here I come!

---

