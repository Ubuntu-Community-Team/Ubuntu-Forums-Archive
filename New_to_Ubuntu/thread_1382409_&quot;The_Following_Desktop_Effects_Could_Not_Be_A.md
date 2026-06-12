---
title: "&quot;The Following Desktop Effects Could Not Be Activated&quot;"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by igelman on 2010-01-15
I am new to linux but not unix. I have been a Mac user since I was 2. Right now, I am currently having trouble figuring out how to activate some desktop effects using KWin. They are: Wobbly Windows, Desktop Cube, and Sharpen. My system specs are, surprise surprise: 13.3 inch MacBook Pro, 2.53 GHz intel dual core duo processor, 3 MB L2 Cache, Memory: 4 GB. If there's anything that I need to elaborate on in order help you more, just reply with the details.

---

### Post by igelman on 2010-01-15
bump

---

### Post by igelman on 2010-01-15
what is UP with you people? one guy just got 67,000 views on his post, and he posted his thread 3 minutes after I did! I'm starting to get the feeling that i'm being ignored...

---

### Post by iWolf on 2010-01-16
> **igelman said:**
> I am new to linux but not unix. I have been a Mac user since I was 2. Right now, I am currently having trouble figuring out how to activate some desktop effects using KWin. They are: Wobbly Windows, Desktop Cube, and Sharpen. My system specs are, surprise surprise: 13.3 inch MacBook Pro, 2.53 GHz intel dual core duo processor, 3 MB L2 Cache, Memory: 4 GB. If there's anything that I need to elaborate on in order help you more, just reply with the details.

All I need is the Video Card. I'm pretty sure your current Video Card will work with it, but to be safe, I need the company, make, and model of your Video Card

---

### Post by warfacegod on 2010-01-16
Activating the recommended driver for your video card should do the trick. Your in KDE (Kubuntu) so I don't know where to tell you to look in your menus. In Ubuntu it's in System> Admin.> Hardware Drivers if that helps.

---

### Post by igelman on 2010-01-16
thank you, this helps a lot.

---

### Post by warfacegod on 2010-01-16
Glad to help. Did you find what you need and get your effect working?

---

### Post by igelman on 2010-01-16
@iWolf

     My video card is: NVIDIA Geforce 9400M

@warfacegod

     Unfortunately, no. I don't exactly know how enable the driver. there seems to be no 'enable' checkbox or any equivalent on KDE, at least I think.

---

### Post by 3rdalbum on 2010-01-16
> **igelman said:**
> @iWolf

     My video card is: NVIDIA Geforce 9400M

@warfacegod

     Unfortunately, no. I don't exactly know how enable the driver. there seems to be no 'enable' checkbox or any equivalent on KDE, at least I think.

Refresh your package list from the Internet. I'm not sure of the GUI way to do it in Kubuntu, but you can always pop open the terminal (Konsole) and type:

```
sudo apt-get update
```

It will ask for your password; type it and press Enter. (you won't see any asterisks or anything as you're typing your password). When it has finished running the command, then try looking in the Hardware Drivers program again and you should see an entry for your Nvidia graphics too.

Now, I'm assuming you're running Kubuntu straight on your hardware, not inside a virtual machine. Virtual machines don't have direct access to the hardware and therefore no 3D acceleration, so no 3D effects.

---

### Post by igelman on 2010-01-16
oh, well... this IS awkward. I AM running KDE inside a vm. heh heh.

---

### Post by warfacegod on 2010-01-16
> **igelman said:**
> oh, well... this IS awkward. I AM running KDE inside a vm. heh heh.

Ergh! ;) Here, have some :popcorn: while you wait for your OS to install.

---

