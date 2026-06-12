---
title: "upgrading and replacing gnome with icewm"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by dvdljns on 2009-09-17
Ok I tried everything I can think of or find on the internet. I can uprade to and run 6.06 but upgrading to 6.10,704,or 7.10 I lose my fonts. I can go up to 8.04 but do not have enough resources to run gnome. the xubuntu-desktop I lose my xserver and fall back to command line. I can run icewm but lose the ability to do updates. I beleive that is do to removing ubuntu-desktop. Heres what I decided to do!! upgrade to to 8.04 then download icewm. That way I do not have to worry about upgrading afterwords.  But heres my question. Is There some way to switch desktops without removeing the whole app. So far all the info I found has not worked. Or can I remove ubuntu-desktop and keep the upgrade & update part of gnome. I hear of people switching window manigers all the time. How do they do upgrades. Whats the best way to go here.

---

### Post by NightwishFan on 2009-09-17
You can update from the command line.
```
sudo apt-get update
```

Also, perhaps try LXDE desktop, which is very light. Or install just xfce4 and not Xubuntu. I would do a full reinstall of the latest version, Jaunty.

You could try Xubuntu, which should work, try a live CD.

---

### Post by SunnyRabbiera on 2009-09-17
You may want to try a lighter linux, like Puppy or damnsmall

---

### Post by swoody on 2009-09-17
> **NightwishFan said:**
> Also, perhaps try LXDE desktop, which is very light. Or install just xfce4 and not Xubuntu. I would do a full reinstall of the latest version, Jaunty.

I would agree with this as well. I think going with the latest release available, but a minimum installation would be the way to go. I would recommend going with the Ubuntu Minimal Installation, and only installing the few packages that you need, to avoid overhead and system bloat. Also, here's some more info that may be of interest to you:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

---

### Post by dvdljns on 2009-09-17
> **swoody said:**
> I would agree with this as well. I think going with the latest release available, but a minimum installation would be the way to go. I would recommend going with the Ubuntu Minimal Installation, and only installing the few packages that you need, to avoid overhead and system bloat. Also, here's some more info that may be of interest to you:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Interesting article. Ubuntu 8.04 loaded and is running fine except for the buttons on top right corner. I am taking a snapshot so you can see what I am talking about. I take it By the answers that no one else knows how to do this.:lolflag: ```
sudo apt-get update
``` did not work. Any way all I need to learn right now is how to replace gnome with icewm.

---

### Post by kerry_s on 2009-09-17
is there a reason your not doing a clean install?
what are your specs?

---

### Post by dvdljns on 2009-09-17
> **kerry_s said:**
> is there a reason your not doing a clean install?
what are your specs?

I do not have a way to burn A cd. 700 mhz centron,256 mb memory and 20 gb hd.

---

### Post by kerry_s on 2009-09-17
> **dvdljns said:**
> I do not have a way to burn A cd. 700 mhz centron,256 mb memory and 20 gb hd.

:lolflag:
i'm in the same boat, luckly i had the 9.04(jaunty) cd though, this machine is 450mhz 256mb ram, so in my case i just decided to strip gnome down to the bone & replace the heavy programs. i really don't want to use a window manager. it's not bad my startup ram use is in the 60's & a little over a 100 when bouncing around the net.

---

### Post by dvdljns on 2009-09-17
Not bad stats. I loaded icewm on 6.06 and liked it,but ubuntu seems to only like a full desktop. icewm would need some tweaking but I would eventaully learn to do that. I reinstalled firefox and now it seems to work. Out of all the versions I like 5.06 the best but could not the latest flash pluggin to install. I think I will keep 8.04 installed and learn to cutomize it. Once I learn enough I am going to load cherokee web server then as long as it works I should not have to do anything except update my web pages.

Till something else happens.:lolflag:
Where is the spell checker?

---

### Post by kerry_s on 2009-09-17
try some of these tips:
[http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/performance-0.html.en)

---

### Post by RedSquirrel on 2009-09-17
> **dvdljns said:**
> Or can I remove ubuntu-desktop and keep the upgrade & update part of gnome. I hear of people switching window manigers all the time. How do they do upgrades. Whats the best way to go here.


1. As mentioned above, you can keep your system up-to-date using the command line:

```
sudo apt-get update
```followed by:

```
sudo apt-get upgrade
```That's the only method I use to update my system.


2. If you still have synaptic installed, you can use that to keep your system up to date.

```
gksudo synaptic
```3. **update-manager** is the program you normally run to do updates while you're running GNOME. You can install that as well:

```
sudo apt-get install update-manager
``````
update-manager
```


> **kerry_s said:**
> i'm in the same boat, luckly i had the 9.04(jaunty) cd though, this machine is 450mhz 256mb ram, so in my case i just decided to strip gnome down to the bone & replace the heavy programs. i really don't want to use a window manager. 

No more jwm? What's the world coming to? :P

---

### Post by kerry_s on 2009-09-17
hey buddy, i miss you, you just aren't around enough anymore. :lolflag:

> No more jwm? What's the world coming to? 

naaa, i'm just lazier these days. i'll probably go back someday. i stopped using window managers when i got my new nettop, then my dads comp broke 2 days ago & i came home to his old rig sitting on the floor & my new rig was gone. :cry:
i had this: [http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012)

i'm thinking of getting the single core 1 to replace it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119014](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119014)

but i might just get the same thing, the dual core.

---

