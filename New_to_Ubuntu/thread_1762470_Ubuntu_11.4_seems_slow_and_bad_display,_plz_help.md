---
title: "Ubuntu 11.4 seems slow and bad display, plz help?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by Jonesy_sa on 2011-05-19
Hi all,
I am new to Ubuntu and was wondering if you could throw some expertise my way.
I have always wanted to give it a try and recently installed it with Wubi on my pc after windows gave me the S**ts. 
My PC:
P4 2.4
512ram
MSI Nvidia TI4200 8x 128ddr
Monitor 19" Acer AL1916W (wide-screen)

Basically windows was always loading and always hanging and very darn slow to start and load programs. Thus Wubi and 11.4.

My problems:
Picture quality is terrible. On windows i had to download some special driver as my video card was pre-widescreen days and it wouldnt allow the correct resolution (this issue was resolved with the driver).
I seem to have the same picture images now with Ubuntu. 
Under monitors it has selected:
1440x900
75hz
Everything looks really small, text is tiny and seems a bit blurred so i changed the settings to:
1280x800
This made my desktop items larger etc which i wanted but it did not increase the size of text much, plus now all text in browsers, the names in my applications menus in Ubuntu etc all look very blury?
I know my hardware is a tad old but what can i do to fix this? Is it like a cleartype issue that some windows machines have?

Further, Ubuntu seems as laggy as WinXP. It doesn't load on and off for no real like windows but opening and closing programs, clicking between tabs on Firefox etc is actually quite slow compared with windows. I am running the classic view and i presume its 64bit ubuntu... Is there a reason for this lag, can i speed it up?
I honestly love it many times over compared with Windows but its not usable unless my video issues are resolved and i can speed it up a little....
Ideas?

---

### Post by Mr Stoozer on 2011-05-19
> **Jonesy_sa said:**
> Hi all,
I am new to Ubuntu and was wondering if you could throw some expertise my way.
I have always wanted to give it a try and recently installed it with Wubi on my pc after windows gave me the S**ts. 
My PC:
P4 2.4
512ram
MSI Nvidia TI4200 8x 128ddr
Monitor 19" Acer AL1916W (wide-screen)

Basically windows was always loading and always hanging and very darn slow to start and load programs. Thus Wubi and 11.4.

My problems:
Picture quality is terrible. On windows i had to download some special driver as my video card was pre-widescreen days and it wouldnt allow the correct resolution (this issue was resolved with the driver).
I seem to have the same picture images now with Ubuntu. 
Under monitors it has selected:
1440x900
75hz
Everything looks really small, text is tiny and seems a bit blurred so i changed the settings to:
1280x800
This made my desktop items larger etc which i wanted but it did not increase the size of text much, plus now all text in browsers, the names in my applications menus in Ubuntu etc all look very blury?
I know my hardware is a tad old but what can i do to fix this? Is it like a cleartype issue that some windows machines have?

Further, Ubuntu seems as laggy as WinXP. It doesn't load on and off for no real like windows but opening and closing programs, clicking between tabs on Firefox etc is actually quite slow compared with windows. I am running the classic view and i presume its 64bit ubuntu... Is there a reason for this lag, can i speed it up?
I honestly love it many times over compared with Windows but its not usable unless my video issues are resolved and i can speed it up a little....
Ideas?

First up, to find out if you're running x64 or not.
Press Ctrl+Alt+T
type this into the terminal and press enter:
```
uname -m
```
The ouput of which will show whether you're running x86 or x64

As for the laggy performance, maybe try installing 'preload'
You can do that by typing into the terminal;
```
sudo apt-get install preload
```

You should set your display to show your monitors native resolution (probably 1440x900). If the text is too small for you, go to the Appearance in Preferences, switch to the Font tab and increase the text size to your liking. You can also tweak the font rendering in the same place if it looks blurry.
Hope this helped. :)

---

### Post by wildmanne39 on 2011-05-19
> **Jonesy_sa said:**
> Hi all,
I am new to Ubuntu and was wondering if you could throw some expertise my way.
I have always wanted to give it a try and recently installed it with Wubi on my pc after windows gave me the S**ts. 
My PC:
P4 2.4
512ram
MSI Nvidia TI4200 8x 128ddr
Monitor 19" Acer AL1916W (wide-screen)

Basically windows was always loading and always hanging and very darn slow to start and load programs. Thus Wubi and 11.4.

My problems:
Picture quality is terrible. On windows i had to download some special driver as my video card was pre-widescreen days and it wouldnt allow the correct resolution (this issue was resolved with the driver).
I seem to have the same picture images now with Ubuntu. 
Under monitors it has selected:
1440x900
75hz
Everything looks really small, text is tiny and seems a bit blurred so i changed the settings to:
1280x800
This made my desktop items larger etc which i wanted but it did not increase the size of text much, plus now all text in browsers, the names in my applications menus in Ubuntu etc all look very blury?
I know my hardware is a tad old but what can i do to fix this? Is it like a cleartype issue that some windows machines have?

Further, Ubuntu seems as laggy as WinXP. It doesn't load on and off for no real like windows but opening and closing programs, clicking between tabs on Firefox etc is actually quite slow compared with windows. I am running the classic view and i presume its 64bit ubuntu... Is there a reason for this lag, can i speed it up?
I honestly love it many times over compared with Windows but its not usable unless my video issues are resolved and i can speed it up a little....
Ideas?
Hi, first if you are running it in wubi you are still running it in windows, setup that way it is just another windows program. With 512 ram that is probably just not enough to run 2 operating systems at a time. Also we need to know which version of ubuntu you are running. You have to install drivers to get your nvidia card to work right. Go to administration click on additional or restricted drivers ans see if there is one there for your card, you have to be connected to the internet to do this.:)

---

### Post by Mr Stoozer on 2011-05-19
Running Ubuntu via Wubi doesn't mean you are running 2 OS does it?
We're talking about Ubuntu 11.04 (as per the title of the thread).
+1 for checking out your GPU driver.

---

### Post by jrozo17 on 2011-05-19
With that amount of RAM, i would recommend 10.04 LTS or 10.10... 11.04 was really slow on my computer too. I'm personally just going to wait for 11.10 and see if Unity improves.

---

### Post by wildmanne39 on 2011-05-19
> **Mr Stoozer said:**
> Running Ubuntu via Wubi doesn't mean you are running 2 OS does it?
We're talking about Ubuntu 11.04 (as per the title of the thread).
+1 for checking out your GPU driver.
Hi, I think so, I am not real familiar with wubi, tell me do you open it from with in windows or do you boot into it instead of windows when you turn on your computer?

---

### Post by WJSimacek on 2011-05-21
I'm having same slowness problem. I ran uname -m in a terminal and received back i686. Now what?

---

### Post by syntr on 2011-05-21
> **WJSimacek said:**
> I'm having same slowness problem. I ran uname -m in a terminal and received back i686. Now what?

That means you're running 32-bit Ubuntu, as you should be :)

> **wildmanne39 said:**
> Hi, I think so, I am not real familiar with wubi, tell me do you open it from with in windows or do you boot into it instead of windows when you turn on your computer?

No, Wubi does not run 2 operating systems at the same time. It creates a disk image on your Windows partition that Microsoft's boot manager (like GRUB) boots.

> **jrozo17 said:**
> With that amount of RAM, i would recommend 10.04 LTS or 10.10... 11.04 was really slow on my computer too. I'm personally just going to wait for 11.10 and see if Unity improves.

I think the OP would be better suited running xfce (xubuntu) instead, with its lower system requirements.

---

