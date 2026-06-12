---
title: "desparate help needed for graphics :( :( :( :("
date: 2011-01-22
forum: New to Ubuntu
---

### Post by spulkit on 2011-01-22
Hi I have installed ubuntu 10.10 today( first time ever).at first it kept freezing and hanging randomly and only option was hard reboot. Finally figured out that it was related to graphics with the help of this forum site. So I set visual effects in appearence to none. Now now no random freezes but as soon as I start some 3D app like game or something my pc freezes like it used to before. Also i tried the unity 3D interface and even in it my system freezes totally as soon I login or 5 min after that at max.


I think it must be some problem related to drivers especially display driver.
I have a chipsets of some company named mercury( the name comes written on startup screen) with Intel core 2 duo processor 2.4 giga and a 2gb RAM. And 250gb SATA disc.it has video memory of 128mb and I don't have any other graphic card installed.


I have a dual boot with windows 7 


The windows update automatically finds graphic accelerator driver for my pc 
It downloads some 82945 G graphic accelerator for chipsets
Windows run absolutely fine.
I really seem to like ubuntu and would like to explore it. Plz help . Thanks in advance.

---

### Post by spulkit on 2011-01-22
The driver downloaded by windows update is by company intel

---

### Post by LinuxFox on 2011-01-22
> **spulkit said:**
> The driver downloaded by windows update is by company intelIntel driver, I'm using an Intel 965 on my laptop.  I don't think there is a Linux driver for it.  I remember going to System > Administration > Hardware Drivers, only to find nothing.  I use to have to use that to enable effects on my ATI card on my old computer.  Though I don't have problems.

As for 3D freezing up, do you have any effects on?  Go to System > Preferences > Appearance, click visual effects tab and set it to none.  When I did that on my old computer, anything 3D worked for me.

I hope this information helps somewhat, I'm just saying what I remember when I ran into problems.

---

### Post by sandyd on 2011-01-22
try xorg-edgers ppa

---

### Post by spulkit on 2011-01-22
> **LinuxFox said:**
> Intel driver, I'm using an Intel 965 on my laptop.  I don't think there is a Linux driver for it.  I remember going to System > Administration > Hardware Drivers, only to find nothing.  I use to have to use that to enable effects on my ATI card on my old computer.  Though I don't have problems.

As for 3D freezing up, do you have any effects on?  Go to System > Preferences > Appearance, click visual effects tab and set it to none.  When I did that on my old computer, anything 3D worked for me.

I hope this information helps somewhat.


It is already set to none in gnome. things work as long as they are not 3d. Unity keeps freezing suggesting its some sort of 3d problem only.
Thanks for replying by the way. :)

---

### Post by spulkit on 2011-01-22
> **sandyd said:**
> try xorg-edgers ppa

I am not sure about how to use commands . do i write these in terminal. As i said its only my first day with Linux

---

### Post by spulkit on 2011-01-22
One thing more ihad started the recovery console which made some sort of update while in command like mode .and it changed generic version to24 from 22

---

### Post by LinuxFox on 2011-01-22
> **spulkit said:**
> It is already set to none in gnome. things work as long as they are not 3d. Unity keeps freezing suggesting its some sort of 3d problem only.
Thanks for replying by the way. :)You;'re welcome.  I just remembered the 3D problem I have and just wanted to suggest it.  Maybe someone else can help you out if what I said didn't work. :)

As for a "PPA command", you add PPAs to the Software Sources under System > Administration.  I haven't tried that PPA myself, maybe someone who has could explain it more.

---

### Post by spulkit on 2011-01-22
> **LinuxFox said:**
> You;'re welcome.  I just remembered the 3D problem I have and just wanted to suggest it.  Maybe someone else can help you out if what I said didn't work. :)

As for a "PPA command", you add PPAs to the Software Sources under System > Administration.  I haven't tried that PPA myself, maybe someone who has could explain it more.

can u give me a forum link that can explain more about ppa

---

### Post by LinuxFox on 2011-01-22
> **spulkit said:**
> can u give me a forum link that can explain more about ppaSorry I don't know a forum link, but I can explain what a PPA is.  A PPA is a Personal Package Archive.  By adding a PPA to Software Sources you add another "repository" for Ubuntu to use.  It makes it easier to install software when one is added.

Hopefully I explained what a PPA is.  Sorry I can't be more help as I never used that PPA.  Hopefully someone who has could be helpful.

---

### Post by spulkit on 2011-01-22
> **LinuxFox said:**
> Sorry I don't know a forum link, but I can explain what a PPA is.  A PPA is a Personal Package Archive.  By adding a PPA to Software Sources you add another "repository" for Ubuntu to use.  It makes it easier to install software when one is added.

Hopefully I explained what a PPA is.  Sorry I can't be more help as I never used that PPA.  Hopefully someone who has could be helpful.
thanks again . but last i need to ask how do i add this repository in software sources . and thanks again.

---

### Post by LinuxFox on 2011-01-22
> **spulkit said:**
> thanks again . but last i need to ask how do i add this repository in software sources . and thanks again.I don't know the software that PPA mentioned above has, but I'll be happy to explain how to add one.

1. Go to System > Administration > Software Sources.  Enter your password when asked (this is normal).
2. Click the Other Software tab.
3. Click Add and paste the PPA there and click Add Source.
4. Click Close and reload when asked.

---

### Post by spulkit on 2011-01-22
> **LinuxFox said:**
> I don't know the software that PPA mentioned above has, but I'll be happy to explain how to add one.

1. Go to System > Administration > Software Sources.  Enter your password when asked (this is normal).
2. Click the Other Software tab.
3. Click Add and paste the PPA there and click Add Source.
4. Click Close and reload when asked.
thank you so much . ii m installing xorg-edgers now . will post if it helps.

---

### Post by spulkit on 2011-01-22
no help. started game called foobilliard and the whole thing froze. still unsolved

---

### Post by sandyd on 2011-01-22
> **spulkit said:**
> no help. started game called foobilliard and the whole thing froze. still unsolved
run
```

sudo apt-get update
sudo apt-get upgrade
```sorry, I was disconnected due to XO Communications screwing up again....

---

### Post by Rasa1111 on 2011-01-22
One could simply just not use "3D". 
Tis what I do.. 
and I have no problem with it. 

 If your going to have "visual effects" set to "none"..
as I always do.. 

You may want to enable the "compositing manager". 

Either by hitting Alt+F2, typing in gconf-editor
navigating to Apps>Metacity>General> 
and Check off the "compositing manager" box. 

or by installing and using Ubuntu Tweak. 
(easier for noobs).

But,
 I learned that my PC would not handle the 3D graphics that many find so "crucial".. lol
So I simply do not use them..
Which Im totally fine with. 

I have a PC that actually works now! (ie, no windows)
So I don't care in the slightest if I can or cannot use , pretty (though useless) 3D renderings. 

 I don't mind a little compromise. lol

(if it don't work, don't use it!)

As long as I can keep and use Ubuntu..
I'm good.

 But, if video games is ones aim..
Ubuntu may not be your best decision anyway.

---

### Post by forestgril on 2011-01-23
> **Rasa1111 said:**
> 

 I don't mind a little compromise. lol

(if it don't work, don't use it!)

As long as I can keep and use Ubuntu..
I'm good.

 But, if video games is ones aim..
Ubuntu may not be your best decision anyway.

rather pathetic... this is soooooobad that the computer crashes.... sooo bad, people will start to keep away from Ubuntu ;(

---

### Post by Rasa1111 on 2011-01-23
I dunno about that. 

I never used Ubuntu, or any Linux distro until a year ago. 
and Ive never had such an easy, and nice, smooth, fast computer experience ever! lol

I wouldnt use compiz/3D even if my PC could handle it. 
and I don't play games at all. So where is the bad? 

Still, 
 My old PC (7+ years old) running Ubuntu 10.10..
runs faster and better than those I know with PC's that are a year or two/three years old, running XP, vista/win7. 

I fail to see what's "pathetic" about any of that. 
(on Ubuntus side anyway) lol
Perhaps your hardware is at fault. 

 and contrary to your comment..
more people are starting to use Ubuntu now. 

I alone have switched my whole family, most friends, and some of the familys friends to Ubuntu.. 
All who are noobs, and most of them pretty "computer illiterate"..
and they all get along just great with Ubuntu.
 Have for months! :D 

The PC Im typing on now would be in a dumpster had I not found Ubuntu! 
No kidding. 
Same with another 2 computers that were about to get junked. 
Ubuntu made them all like new computers again, literally. 

 Pathetic! lol

:P

 I freekin love ubuntu. <3

---

### Post by adeee on 2011-01-23
> Hi I have installed ubuntu 10.10 today( first time ever).at first it kept freezing and hanging randomly and only option was hard reboot. Finally figured out that it was related to graphics with the help of this forum site. So I set visual effects in appearence to none. Now now no random freezes but as soon as I start some 3D app like game or something my pc freezes like it used to before.

Me too guys i also cant play any game. i cant use Awant window navigator, docky, compiz.

my pc is 4 years old. but there is other fact its very very fine for me.
i use ubuntu smoothly.

in graphics side ubuntu just support incoming technology. not compateble with past. i  am talking about less then 2 or 3 years technology.
On the other hand people moves to windows after moving ubuntu while this 3d problem occurs.
Windows seven has no any kind of this problem.
In KDE i use 3d effects. but mostly i use gnome so i turned it to none.
 
if any suggestion how to use 3d then must reply.
i want to see how ubuntu looks in high graphics.

---

### Post by spulkit on 2011-01-23
> **adeee said:**
> Me too guys i also cant play any game. i cant use Awant window navigator, docky, compiz.

my pc is 4 years old. but there is other fact its very very fine for me.
i use ubuntu smoothly.

in graphics side ubuntu just support incoming technology. not compateble with past. i  am talking about less then 2 or 3 years technology.
On the other hand people moves to windows after moving ubuntu while this 3d problem occurs.
Windows seven has no any kind of this problem.
In KDE i use 3d effects. but mostly i use gnome so i turned it to none.
 
if any suggestion how to use 3d then must reply.
i want to see how ubuntu looks in high graphics.

seriously this is a problem coz of which windows gets in a big advantage............... i am starting to love ubuntu but then hardware compatibility is also must.
my is pc is just like 2 and a half yrs old .......that should be called old but ubuntu is starting to make me feel that

---

### Post by Rasa1111 on 2011-01-23
I just said my PC is 7+ years old and runs beautifully. 

@ adeee, 

 You need to at least have "compositing manager" On to use AWN.
That works great for me. 
If you can't use "compiz"/visual effects"
and you have not turned on "metacity compositing manager"..
AWN will look weird.
So try to turn on "compositing manager" in "configuration editor"
If you don't know where to find it, just ask.

But AWN works great even on this old relic. lol
see here~[ATTACH]181831[/ATTACH]

---

### Post by clhsharky on 2011-01-23
spulkit

Did you update/upgrade as sandyd suggested after adding PPA, otherwise nothing was changed. Update Manager can all so be used after adding PPA.
Intel chips can do 3D in Ubuntu so don't give up, search your chip on forum.

adeee
What GPU chip do you have?
I have many ATI/Nvidia cards and 3D works on all that are less than 9 years old.

Distros don't write drivers for GPUs, manufactures and OSS community do.


Sharky

---

### Post by adeee on 2011-01-24
> **Rasa1111 said:**
> I just said my PC is 7+ years old and runs beautifully. 

@ adeee, 

 You need to at least have "compositing manager" On to use AWN.
That works great for me. 
If you can't use "compiz"/visual effects"
and you have not turned on "metacity compositing manager"..
AWN will look weird.
So try to turn on "compositing manager" in "configuration editor"
If you don't know where to find it, just ask.

But AWN works great even on this old relic. lol
see here~[ATTACH]181831[/ATTACH]

Well i just install AWN and its appears but it still demand to select Normal graphics mode. 
see pic.
[ATTACH]181836[/ATTACH]

Am sorry to say but seriously i am not following you.
Well i have both packages in Application-->other-->Metacity and Compiz.
And another thing your desktop pretty good. 

> What GPU chip do you have?
I have many ATI/Nvidia cards and 3D works on all that are less than 9 years old.

Distros don't write drivers for GPUs, manufactures and OSS community do.

i put this command 
```
lspci -v
```

then it will give me this answer..
```
VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
    Subsystem: Micro-Star International Co., Ltd. Device 7507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at cfd80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec00 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at cfd40000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915
```

---

### Post by Rasa1111 on 2011-01-24
> **adeee said:**
> Well i just install AWN and its appears but it still demand to select Normal graphics mode. 
see pic.
[ATTACH]181836[/ATTACH]

Am sorry to say but seriously i am not following you.
Well i have both packages in Application-->other-->Metacity and Compiz.
And another thing your desktop pretty good. 

Ahh, No problem. 

That should be simple to "fix", 
and you should be able to get AWN looking good with a few clicks. 

Hit Alt+F2, 
A little window will appear. 
[ATTACH]181837[/ATTACH]
type this into the little window/box.
```
gconf-editor
```
(or copy&paste)

Then click "run"
(see pic)

 a new window will open, 
Look on the left side pane, for the top in the list, called "Apps", click on the arrow by it. 

a list will extend in the same pane..
scroll down to the "m's" and find "metacity"
[ATTACH]181838[/ATTACH]
(see pic)
click on "metacity" , now look to the right, 
(where my cursor is sitting), 
 click metacity, then "General"
Make sure the box for "compositing manager"" is Checked/ticked..
Once you turn that on,
you can exit out that window. 

Now start AWN, and you should be set.

hope it helps.
 thanks. glad you like it.

---

### Post by adeee on 2011-01-24
> **Rasa1111 said:**
> Ahh, No problem. 


hope it helps.
 thanks. glad you like it.

Thanxs dude i really appreciate your massage and work. 
but as you now this is ubuntu and difficult for beginner to learn the behavior so
After applying your changes 
 this happens with my embaded Terminal. lolz
[ATTACH]181841[/ATTACH]

On hardly boot direct switch off of computer(unfortunately mistakes).

[ATTACH]181839[/ATTACH]

And after taking screen shot from keyboard(print button) top pannel is disappear.
[ATTACH]181840[/ATTACH]

And logout and then log in
[ATTACH]181842[/ATTACH]

Looks like my terminal is playing hide and seek with me. :P

remember i use embaded terminal as a startup application via devilspie

there is a script i use in /.devilspie/DesktopConsole.ds


```
(if
        (matches (window_name) "DesktopConsole")
        (begin
                (set_workspace 1)
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)
                (wintype "utility")
                (geometry "+50+50")
                (geometry "400x726")
        )
)
```

So how could fix it. and another one is which awn theme you used.:p

---

