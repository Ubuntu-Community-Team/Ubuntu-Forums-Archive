---
title: "Ubuntu Installs but does not work"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-03-31
Hi all

I installed Ubuntu on my computer...

It boots fine... But does not show the Ubuntu Logo and progress bar... Just Black screen...

Then it asks for username password... But after that desktop does not load.. Only black screen... Keyboard does not respond but mouse does... the screen remains black.... but mouse pointer is seen... the screen remains like this for hours....

I reinstalled UBUNTU several times... But no success...

---

### Post by carml on 2009-03-31
Which version you installed and with which cd,alternate or live?

---

### Post by PukingPenguin on 2009-03-31
Which Ubuntu version?
What kind of video card? Using the livecd post the output of ```
lspci | grep -i vga
```

---

### Post by RedSingularity on 2009-03-31
If you could post the specifications of your computer we could get a better idea of whats happening.

---

### Post by Guruprasad on 2009-04-01
I installed UBUNTU 8.10 using live USB. I checked the USB for errors, it is fine. I sucessfully installed UBUNTU on another system using same USB.

I tried running UBUNTU from USB with the same live USB. But the GDM did not start.

My system config is
P4 2.4GHZ
1GB RAM
Onboard Intel Display Card.

---

### Post by Guruprasad on 2009-04-01
UBUNTU 8.10

lspci | grep -i vga

> 00:02.0 VGA compatible controller: Intel corporation 82545G/GL[Brookdale-G]/GE chipset integrated graphics device (rev01)

---

### Post by hyper_ch on 2009-04-01
strange, intel video cards should work...

---

### Post by RedSingularity on 2009-04-01
I would think the intel video card would work but it looks as if thats your problem because everything else is fine.  Can you boot into the terminal prompt?

---

### Post by Guruprasad on 2009-04-02
How to boot into terminal prompt?

---

### Post by jagnikam on 2009-04-02
Follow these steps 
ALT + F2
type xterm
sudo vim /etc/inittab 
Press [COLOR="Red"]i[/COLOR]
id:5:initdefault:
change above line to 
id:3:initdefault:
then press [COLOR="Red"]Esc[/COLOR] and type [COLOR="Red"]:wq[/COLOR]
sudo reboot 


thats it. From next time it will always start into terminal prompt.


> **Guruprasad said:**
> How to boot into terminal prompt?

---

### Post by kevmitch on 2009-04-02
You can get to a terminal with Alt-Ctrl-F1. 

Once there there are a couple things you can do:

Search your Xorg logs for errors

```
grep EE /var/log/Xorg.0.log
```
```
grep EE /var/log/Xorg.20.log
```

Search your xsession log for errors

```
cat ~/.xsession-errors
```

See what processes are actually running

```
ps aux
```

or search them for ones of interest

```
ps aux | grep gdm
```
```
ps aux | grep X
```
```
ps aux | grep gnome
```

You could also try restarting gdm

```
/etc/init.d/gdm restart
```

This doesn't sound like the usual graphics problem. You DO see the pointer so there is graphics output, there's just not much of it. Is it an actual pointer or is it just an "X"?

Could you clarify what happens when you're asked for user/pass? Does it show the graphical login screen or is it just text-based console?

---

### Post by Guruprasad on 2009-04-02
I tried pressing Alt + F2 during boot to enter terminal prompt but it did not work...

---

### Post by Guruprasad on 2009-04-02
I will try the commands you mentioned.

I can see my mouse pointer (similar to the one in windows), not the default X pointer.

The graphical login screen (brown colour) asks for username and then password. After giving password it shows brown screen with mouse pointer. At this stage mouse and keyboard both are responding. After sometime the keybord stops responding while mouse is still responding and the screen stays the same endlessly.

---

### Post by jagnikam on 2009-04-02
try booting in runlevel 3 by editing the boot on grub by deleting the splash screen and adding either a 3 or an init 3 in the end.

when you start pc on OS selection press [COLOR="Magenta"]escape[/COLOR] and press [COLOR="Magenta"]e[/COLOR] for edit and add 3 or init 3 in the end. press enter.

---

### Post by kevmitch on 2009-04-02
Sorry, just to clarify. You should be able to get to a terminal by hitting Alt-Ctrl-F1 any time after the login screen has appeared. 

> 
try booting in runlevel 3 by editing the boot on grub by deleting the splash screen and adding either a 3 or an init 3 in the end.

If that doesn't work, then try booting into **runlevel 1**. This is single user mode where you are brought directly to the text only console. 
As far as I can tell runlevel 3 is the same as the default runlevel 2 so you'll probably see the same behaviour. It's also possible you won't even have to do the whole "e" thing if you have a (recovery mode) option in the boot menu. If you do just select that.

---

### Post by anewguy on 2009-04-02
As already stated, wait until you get the black screen after you log on.  Then hold down Ctrl Alt and press F1, then release all three keys.  This should bring you to a log on prompt.  Use your normal userid and password, and then should bring you to a command prompt.  Once you are at that prompt do the following:

sudo apt-get remove compiz <press enter>
sudo apt-get remove compiz-core <press enter>

You will be prompted for a password again because of the sudo - just use your normal password.

Once the above completes and you are returned to the command prompt, type:

sudo shutdown -r now <press enter>

This will cause your system to shutdown and reboot, which is what we want (it's the simplest).  When it reboots check to see if you still have the same error or not and post back here.

Dave :)

---

### Post by Guruprasad on 2009-04-03
Dear anewguy

You solution was perfect...

Ubuntu started perfectly...

Thank you very much....


> As already stated, wait until you get the black screen after you log on. Then hold down Ctrl Alt and press F1, then release all three keys. This should bring you to a log on prompt. Use your normal userid and password, and then should bring you to a command prompt. Once you are at that prompt do the following:

sudo apt-get remove compiz <press enter>
sudo apt-get remove compiz-core <press enter>

You will be prompted for a password again because of the sudo - just use your normal password.

Once the above completes and you are returned to the command prompt, type:

sudo shutdown -r now <press enter>

This will cause your system to shutdown and reboot, which is what we want (it's the simplest). When it reboots check to see if you still have the same error or not and post back here.


---

### Post by tkearn5000 on 2009-04-03
Anewguy,
I tried your fix and had success with it as well. I was wondering what exactly it did that fixed the problem. I am assuming that it removed some of the visual effects. Is this right?
Thanks for the help
-TK

---

### Post by kevmitch on 2009-04-03
> **tkearn5000 said:**
> Anewguy,
 I am assuming that it removed some of the visual effects. Is this right?
Thanks for the help
-TK
Bingo. For whatever reason, compiz isn't cooperating with your video card. If you're interested in why, you might try 
```

compiz --replace

```
In the terminal (though of course you would have to reinstall those packages).

---

### Post by tedw on 2009-04-03
Thank you Anewguy

I have been battling for ages just to get Intrepid to work. 

Some small variations I had to use were:

At the black screen with mouse pointer, Ctrl-Alt-F2 does not work for me.  The only thing that does work at that stage is the power button ! 

OK, I effectively went back a step and before logging in, I selected Options (lower left) Failsafe Terminal, change session and then logged in.  
This gave me a terminal screen on which I could apply your fix. 

Typing exit got me back to the login screen and logging in worked fine without rebooting.  My thanks to you. 

I did try Ctrl-Alt-F2 at the login screen and this gave a very raw text screen 40 columns by about 25 lines which is very unfriendly because you cannot see where you are typing. 

Next question.  Is this a known issue with compiz or does it have to be reported as a bug ?

thanks again,  tedw

---

### Post by tkearn5000 on 2009-04-04
After deleting the compiz files, getting ubuntu up and running, and learning more about how it works, I am interested in attempting to get the 3D graphics to work. 

My video card is: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device. It is from Intel. 

If I reinstall the compiz files that I deleted, would I be able to restart in low graphics mode, and see if the proprietary drivers for my card are available on the hardware drivers menu. I found a site that offers open source drivers for people running linux with this card, but I think installing that way might be over my head.

If anyone has experience with this, I would appreciate the help.
Thanks,
-TK

---

### Post by kevmitch on 2009-04-05
If you reinstall compiz, turn off "visual effects" in System->Prefrences->Appearance. That will prevent it from starting automatically until you can make sure things are working ok.

To test it out run the replace command in the terminal. This will give you some debugging info. I believe that that is an older intel chip. I wouldn't be surprised if it simply couldn't handle compiz.

---

### Post by tkearn5000 on 2009-04-05
Thanks for the reply Kevmitch. I found out that my card is blacklisted by compiz, so it looks like I'll be living without the desktop effects while. Maybe I'll pick up a new one eventually.
-Thanks,
-TK

---

### Post by kevmitch on 2009-04-05
It might be an idea to file a bug report on this. The goal of Ubuntu is to eliminate these kinds of headaches. Things would probably have been a lot easier if the desktop just worked the first time around. In particular, it would be nice if it would automatically fall back to metacity (no visual effects) if your graphics card was blacklisted. 

If you do file a bug report, use the ubuntu-bug utility:

```

aptitude install reportbug
ubuntu-bug compiz

```

That will include all your system info. Then describe exactly what happened in as much detail as possible.

---

### Post by WinterMadness on 2009-04-05
theres a possibility that your disc isnt in such good shape, you might want to try and reburn it going as slow as possible.

---

### Post by kevmitch on 2009-04-05
> **WinterMadness said:**
> theres a possibility that your disc isnt in such good shape, you might want to try and reburn it going as slow as possible.

All the packages have md5sums for their contents so if you got through the install stage, this is probably not the problem.

---

