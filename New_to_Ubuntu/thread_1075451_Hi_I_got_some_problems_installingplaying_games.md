---
title: "Hi I got some problems installing/playing games"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by SpaRa16 on 2009-02-20
I just installed ubuntu linux last night and today when I for example installed diablo 2 I can enter the game but it's kinda bugged I can't get full screen and it lags massive anyone knows what's wrong? I would like to know what's needed to play Cs 1.6, Diablo 2, World of warcraft.

I have been searching for info at the internet so don't tell me google it :/ I came here because I think there's some kind hearted people with patients enough to help me get this working.

---

### Post by rgb96 on 2009-02-20
Check out wine. You can learn most of what you need to know here.

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by konqueror7 on 2009-02-20
> **rgb96 said:**
> Check out wine. You can learn most of what you need to know here.

[http://www.winehq.org/](http://www.winehq.org/)

+1, check out wine first...most of the maintainers there post installation instruction regarding these applications...

---

### Post by SpaRa16 on 2009-02-20
> **rgb96 said:**
> Check out wine. You can learn most of what you need to know here.

[http://www.winehq.org/](http://www.winehq.org/)

I've already installed wine :p but I still got problems running the game it lags massive and cant enter fullscreen.

---

### Post by argail1980 on 2009-02-20
Hi,

1. how did you run diablo? with wine?
Maybe you have to run winecfg first (Press Alt+F2 and enter winecfg)
2. have you checked if 3d-accel (glx) is running? you can test that by opening a terminal (Applications-> Accessiores->Terminal) and entering "glxgears". This should open a small window with rotating gears. If that does run smoothly, then glx works. You stop the program by pressing Ctrl+C.

I heard of some people, having got WoW to work, but I have no experience there..

---

### Post by rgb96 on 2009-02-20
> **SpaRa16 said:**
> I've already installed wine :p but I still got problems running the game it lags massive and cant enter fullscreen.

That's weird. Wine hq has Diablo II listed as platinum, which means it should work out of the box without any configurations.

---

### Post by sydbat on 2009-02-20
Do you have the restricted drivers installed? System > Administration > Hardware Drivers. Make sure both Enabled and In Use are checked.

Also, are you running Compiz (Desktop Effects)? This has a large impact on game playing if it is running. To disable (when you play a game) System > Preferences > Appearance and choose the Visual Effects tab. Select None, then give the game a try.

---

### Post by Bölvaður on 2009-02-20
I got CS 1.6 running out of the box.
The only changes that I had before installing was

dinput (builtin)
dinput8 (builtin,native)

and I have whole range of directx9 drivers in my "/home/**your_user_name**/.wine/dosdevices/c:/windows/system32"
the most important one is probably d3dx9_34.dll or what ever the newest one is named.

---

### Post by SpaRa16 on 2009-02-20
I've installed directx 9 etc but now the game is flashing still like maniac this time at wow

---

### Post by Declanthedork on 2009-02-20
Yeah, I tried WINE with Guild Wars, and it got all glitchy. Try changing your graphics driver

---

### Post by SpaRa16 on 2009-02-20
Alright :D I've now done some progress after installing directx 9 and rebooting. It's not all gltichy let's see if I can make the same with diablo 2 I'll let u know

However I'm installing it all through playonlinux but I can't see anything about WoW lich king does this matter? I've not gotten this far yet but I just wonder.

---

### Post by LowSky on 2009-02-20
Odd, diablo 2 work right out of the box for me, only thing you shpuld have to do is disble Compiz.

---

### Post by tarps87 on 2009-02-20
What are your wine graphic settings?
Have you enabled virtual desktop?
Have you ran the Diablo graphics test?
What is the spec of your machine?

> **SpaRa16 said:**
> However I'm installing it all through playonlinux but I can't see anything about WoW lich king does this matter? I've not gotten this far yet but I just wonder.

WOW = world of warcraft so it doesn't matter
Have you tried using wine instead of playonlinux?

---

### Post by SpaRa16 on 2009-02-20
> **tarps87 said:**
> What are your wine graphic settings?
Have you enabled virtual desktop?
Have you ran the Diablo graphics test?
What is the spec of your machine?



WOW = world of warcraft so it doesn't matter
Have you tried using wine instead of playonlinux?

I were using wine at first but I had some problems then and a guy told me try this and it worked. But I'm still running the games through wine

---

### Post by tarps87 on 2009-02-20
Does that mean it is working now?

---

### Post by SpaRa16 on 2009-02-20
> **tarps87 said:**
> Does that mean it is working now?

I'm still doing some stuff but I've made progress and can open up the game without massive lag at log screen or flashing.

---

### Post by tarps87 on 2009-02-20
I don't know if it is useful but if you want to play Diablo over a lan you will need to edit the host file
```
sudo gedit /etc/hosts
```
No add you ip and host name

If your host name is wrong it will become extremely slow at the menu where you choose to host or join a game (as I found out :()
Without this line the game will use the wrong ip so you will not be able to connect

---

### Post by SpaRa16 on 2009-02-20
Problems with installing wow. 

The playonlinux won't help me to install wrath of the lich king :/ Only works for pre-tbc and tbc.... Is there any way to install lich king on dvd disc?

---

