---
title: "oh why does ubuntu hate my resolution"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by akiratheoni on 2009-04-24
I'm sort of frustrated... so if my posts sound condescending, I don't mean to. It's just that ever since I got this graphics card, 8.10 and 9.04 decide to hate me and never give me the resolution I want. And when they do give me the resolution I want, they always throw a fit and give me problems.

I'm sorry for not doing a comprehensive search on this. The whole nvidia thing has changed since 8.04 especially with the emphasis on the new xservers to not rely on the xorg.conf. I don't want to do any outdated fixes for my problem.

Details:
Video card: nVidia GeForce 9500GT
Resolution desired: 1680x1050
Version of Ubuntu: 9.04 32-bit
nVidia driver installed: 180.44
Problem: I can get 1360x768 (very distorted), 1152x864 (workable, this is the resolution I'm using), 1024x768, and other resolutions that are irrelevant. I can't find a way to manually tell Ubuntu that I want a resolution of 1680x1050; I edited the xorg.conf, but the usual Ctrl+Alt+Backspace to kill the xserver and restart it didn't work.

Help?

Thanks.

---

### Post by Peter09 on 2009-04-24
Xorg is now sort of redundant.

It sounds like it does not identify your screen as a wide screen and so is applying the wrong format.

---

### Post by Peter09 on 2009-04-24
In System->administration do you see the nvidia setting application.

If not try installing it (use synaptic)

---

### Post by akiratheoni on 2009-04-24
Yeah I think you're right. Unfortunately I'm looking around and I don't see a solution. I was really looking forward to Ubuntu too... oh well.

---

### Post by Zimmer on 2009-04-24
[http://ubuntuforums.org/showthread.php?t=977798](http://ubuntuforums.org/showthread.php?t=977798)
post 5 might help.
Is your nvidia driver being 'used' ?
Have you read the xorg log to see what is happening ?

Is the card supported by the driver you are using?

---

### Post by presence1960 on 2009-04-24
> **akiratheoni said:**
> Yeah I think you're right. Unfortunately I'm looking around and I don't see a solution. I was really looking forward to Ubuntu too... oh well.

Do as peter09 said. Use Synaptic to install nividia-settings. I had the same problem when I got my new Acer widescreen. Ubuntu didn't recognize it, but once I installed the above all was fine. Sounds like a trivial reason to give up on Ubuntu, especially if you don't try the solution suggested. Unless you already have your mind made up!

---

### Post by akiratheoni on 2009-04-24
@Peter09: I didn't see your post, I guess we posted at the same time. The nVidia settings is in System -> Administration. The problem is that while I can choose different resolutions, widescreen resolutions don't appear.

I also added the thing to the xorg.conf... but the traditional Ctrl+Alt+Backspace to kill the xserver isn't working. How do I restart the xserver?

---

### Post by CatKiller on 2009-04-24
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.


> **akiratheoni said:**
> I edited the xorg.conf, but the usual Ctrl+Alt+Backspace to kill the xserver and restart it didn't work.

They disabled Ctrl-Alt-Backspace, because apparently new users kept pressing it by accident. It's pretty easy to turn it back on, but logging into a virtual console and running ```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```will probably do.

---

### Post by Melk79 on 2009-04-24
The Ctrl+Alt+Backspace combo has been disabled in [Jaunty]("http://www.ubuntu.com/getubuntu/releasenotes/904#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg"), if that's what you're using now (sidebar still says Hardy).

You can logout and login in to restart x as well.

---

### Post by BarryM on 2009-04-25
Hello there, I hope I am not offending protocol by putting this here. I have been trying to get twinview configured, and, looking at this thread thought I had the answer. I found and installed the Nvidia X server settings tool and installed it, and got twinview working - sort of - but when I selected the Save to X configuration file I get an error message "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'

I created the backup file in an ill advised attempt at setting up twinview using nvidia.config, from the root terminal.

Can anyone tell me what to do?

Do I need to log on as root or administrator or whatever, and if so, how do I do that?

Any advice would be very welcome!

Barry

---

### Post by Wamellx on 2009-04-25
For the first question i had close to the same problem, instead of having the 180 driver for nvidia use the second highest under the recommended(for me the recommended was 180 the second best 177). I started using 177 and its been working ever since.

---

### Post by akiratheoni on 2009-04-25
> **Wamellx said:**
> For the first question i had close to the same problem, instead of having the 180 driver for nvidia use the second highest under the recommended(for me the recommended was 180 the second best 177). I started using 177 and its been working ever since.
I tried 177 but I could only get a 800x600 or 640x480 resolution.

---

