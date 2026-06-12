---
title: "Youtube (blank?)"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Albert Wesker on 2009-06-04
Okay, IDK what could be causing this since I haven't installed anything new but youtube was working yesterday, has been for about a week since I got it working with the help of this forum, and today it displays a title and under it a blank white area where the video should be and then the rating.

What could be causing this?

---

### Post by pawnrocket on 2009-06-04
What Firefox add-ons or extensions do you have installed?

---

### Post by Albert Wesker on 2009-06-04
I know I have adobe flash plugin and the Java plugin.

I don't know how to check to see what add-ons I have installed.

---

### Post by UbuntuNerd on 2009-06-04
under the tools menu in firefox click add-ons and then plugins

---

### Post by Albert Wesker on 2009-06-04
I have
Windows Media Player Plug-in 10
VLC Multimedia Plugin
Shockwave Flash
Quick Time Plug-in 7.2.0
libnpjp2.so
DivX Web Player
Default Plug-in
Demo Print Plugin for Unix/linux

---

### Post by pawnrocket on 2009-06-04
Please insert: Ubuntu Version - Computer type (mostly interested in cpu and graphics card)

I had a similar problem when 7.10 came out. I removed flash and then reinstalled it. Fixed my problem I think, if I am remembering correctly

to remove open a terminal Applications -> Accessories -> Terminal

```
$sudo apt-get remove flashplugin-nonfree
```

to reinstall

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by pastalavista on 2009-06-04
> **Albert Wesker said:**
> I have
Windows Media Player Plug-in 10
VLC Multimedia Plugin
Shockwave Flash
Quick Time Plug-in 7.2.0
libnpjp2.so
DivX Web Player
Default Plug-in
Demo Print Plugin for Unix/linux
Those are all the right plugins, what about extensions? Are you using AdBlock Plus? It needs to be disabled on most video sites nowadays.

---

### Post by pawnrocket on 2009-06-04
With adblock you "Allow for site" don't disable it.

---

### Post by LewRockwell on 2009-06-04
I've never had any problems with Adblock plus

---

### Post by Therion on 2009-06-04
If you're QUITE sure you correctly installed the Adobe Flash plugin open Synaptic and put "SWF" in the search bar.  Remove any packages related.  I can't rattle of the package names specifically, but trust me...  You'll know which ones you need to remove when you see them.

Ad Block Plus has never given me problems like this either, btw...

---

### Post by Albert Wesker on 2009-06-04
@Pawnrocket - followed those instructions before and did it again and sorry nothing

@LewRockwell- I don't have adblock, just the Ubuntu extension and Stumble extension

---

### Post by pawnrocket on 2009-06-04
Did you log out and in?

---

### Post by Albert Wesker on 2009-06-04
> **Therion said:**
> If you're QUITE sure you correctly installed the Adobe Flash plugin open Synaptic and put "SWF" in the search bar.  Remove any packages related.  I can't rattle of the package names specifically, but trust me...  You'll know which ones you need to remove when you see them.
remove all of them?

---

### Post by Albert Wesker on 2009-06-04
> **pawnrocket said:**
> Did you log out and in?
why did that work, just curious I did it and it fixed the problem

---

### Post by Therion on 2009-06-04
> **Albert Wesker said:**
> remove all of them?
I'm stuck behind a Windows PC at my office at the moment so I can't open Synaptic right now, but if memory serves there aren't that many packages that should come up using that search.  One of them should be something along the lines of **swf-mozilla-plugin** though.  Remove that one for sure...  Employ a little common sense and you should be fine.  Again, there shouldn't be that many.  

I've ALWAYS had to do this; the two different Flash players conflict I think.  You want to use the Adobe plugin so you need to remove all other Flash-playing related packages.

---

### Post by pawnrocket on 2009-06-04
There is a way to do the same thing without logging out. Generally with the rare exception you shouldn't have to reboot or log out for anything. There are commands dedicated to that stuff however I haven't figured them out yet. 

If I remember correctly I did later have the same problem. Usually after installing a firefox add-on. Again I uninstalled flash and reinstalled it. 

If you are not completely updated you could have continuing problems.

Just to be safe open a terminal and run

```
sudo apt-get update
      sudo apt-get upgrade
```

After which I recommend you download sbackup
```
sudo apt-get install sbackup
```

until you find a backup solution that fits your needs.

---

### Post by Albert Wesker on 2009-06-04
Thank you everyone for your help in this matter:p

---

### Post by pawnrocket on 2009-06-04
No problem... good luck

---

### Post by rbueno on 2009-06-04
Why not directly to Adobe. install Flash Player.
Choose  .deb for Ubuntu 8.04+
Open with Synaptic.
End.

Thats how i do it for every time i reformatted my pc :)

---

### Post by pawnrocket on 2009-06-04
Dunno.. I suppose because it takes so much longer then typing 
```
sudo apt-get install flashplayer-nonfree
```
[CENTER]or[/CENTER]
```
sudo apt-get install ubuntu-restricted-extras
```

---

