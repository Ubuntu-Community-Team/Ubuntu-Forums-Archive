---
title: "Display"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by Kaladin72 on 2011-05-01
So I just downloaded Linux for the first time. I am relatively good with Windows and computers in general but I'm completely ignorant regarding Ubuntu/Linux. I downloaded it and rebooted and chose Ubuntu at the boot menu. It loads and it is all messed up. The desktop is like repeated three times to the left and I have no idea what to do. Can anyone help?

---

### Post by Hedgehog1 on 2011-05-01
Hello!

Please tell us what version of Ubuntu you have downloaded (I think it is Natty 11.04, but I want to be sure), and what Video card you are using.

Right now it sounds like you need the proper video drivers loaded.  If you are running Natty and you are able to make out the triple-screen, please go to the power button in the upper right hand corner of the screen and select the last menu item:

Please run the **Additional Drivers** application from the **Control Center**:

[IMG]http://img820.imageshack.us/img820/7027/nattysystemsetting.png[/IMG]

Once the correct restricted drivers are loaded, you should (We all hope) be able to see a single screen after you reboot.


***The Hedge***

:KS

p.s. If you can select 'Classic with no effects' instead of 'Ubuntu', the screen may work better and make it easier to load the video driver.  [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

---

### Post by nothingspecial on 2011-05-01
If you can't use your screen, press Ctrl-Alt-F2

login with your username and password. (you won't see your password as you type it).

type```
 sudo jockey-text -l
```

If it throws up any drivers then type```
 sudo jockey-text -e <driver>
```

Change <driver> for the name of the driver jockey gives you. ( the bit at the beginning of the line).

This just does exactly what The Hedge described but if you can't make anything out on your screen.

---

### Post by Hedgehog1 on 2011-05-01
> **nothingspecial said:**
> This just does exactly what The Hedge described but if you can't make anything out on your screen.

Thanks **nothingspecial**! I was hoping there was a way to do this without going blind looking at a messed-up screen.

*I am making a note of it...*


***The Hedge***

:KS

---

### Post by Kaladin72 on 2011-05-01
I'm running the newest version. I just downloaded it straight from the site. So I reckon 11.04. I don't have the time right now as I have to go to work but I will try all these solutions tonight and hopefully it'll fix my problem. Thanks for the replies, guys, and have a good day. :)

---

### Post by Kaladin72 on 2011-05-01
Alright well, I booted up Linux and I got to the System Settings thing. I opened up Additional Drivers but it said there were none to be found so I did the Ctrl+Alt+F2 and put in the sudo jockey-text -l and it said searching for drivers and it didn't display anything. It just went back to the normal Ubuntu command line. I didn't know what to do so I put "sudo jockey-text -e ubuntu" without quotations and the text ran off the end of the screen and I couldn't pan down or anything or get out of the screen I was on so I just hard-booted my computer. I started it back up to repeat the process so I'd have room but when I booted Linux back up I think it is asking for my password. I see my username but when I try and type in my password it doesn't go. I can't really see what it says because it is cut off. This is a pain in the ***. >.< ... Can anyone help, please?

---

### Post by Kaladin72 on 2011-05-01
Bump action!

---

### Post by Hedgehog1 on 2011-05-02
I have never used the 'jockey-text' set of commands directly myself, so solving issues caused by them is a little out of my league.

I am hoping other forum members will see this post and suggest a working soluton.

---

### Post by nothingspecial on 2011-05-02
> **Kaladin72 said:**
>  so I put "sudo jockey-text -e ubuntu"   :shock:

You didn't want to do that.

Explain exactly where you are up to. Do you get to the login screen or are you just getting text. Did you enable automatic login when you installed?

---

