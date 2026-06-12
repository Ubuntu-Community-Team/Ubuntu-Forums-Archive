---
title: "Open firefox from terminal"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-04
Hello all,

I am very new to Linux and Terminal  and am running Unbuntu 9.10 Server. I have the intention of creating a home server I can muck around with web access such as webmin that I have already installed. I was wondering if it is possible and if someone could help me throught the following:

I want to install firefox 3.5 which I think I have already done. 
I then want to then open it from terminal as a browser. I don't know if I am using the right command to do this. Tried a number of variatons but comes back as Error: no display sepcified. 
I don't have a GUI. Would I need one to open firefox properly? 
Your help with any programs I need to install and troubleshooting would be appreciated. I can provide any info needed to answer que.

As I said previously got webmin installed and this is what I want to access with FF.

Regards,

Revo

A KEEN NEW LINUX LEARNER

---

### Post by Apollo87 on 2010-03-04
You need an X server (gui) if you're going to run firefox:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
startx
```

---

### Post by Revo99 on 2010-03-04
> **Apollo87 said:**
> You need an X server (gui) if you're going to run firefox:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
startx
```

So once I install my GUI it will always boot up like an OS correct?
If so. There is no way to open webmin interface without doing the above?

Thank you for your Apollo87

---

### Post by Vegan on 2010-03-04
The GUI is not configured to run on demand, its either CLI or GUI not both.

---

### Post by dfreer on 2010-03-04
You could very well just install the xserver, and start firefox alone in it. There's really no need to install the entire gnome desktop. IIRC, all you would need to install is xorg. Then use startx and launch firefox within it, or at least an xterm. 

EDIT: This is a script I used to use when already in GUI to launch a new separate X windows session, it might also be helpful:

```
#!/bin/sh
##uncomment if launching from console session
##not needed if gnome/kde login managers are not installed
#sudo /etc/init.d/gdm stop
##KDE use this instead
#sudo /etc/init.d/kdm stop


## Launches a new X session on display 3. If you don't have an Nvidia card
## take out the "& nvidia-settings --load-config-only" part
## Switch between sessions using <Ctrl>+<Alt>+F# keys.
## F7 is generally the first X session and 1-6 are virtual terminals.
## F8 or F9 should be display 3.
sudo X :3 -ac & nvidia-settings --load-config-only

## Goto game dir (modify as needed)
#cd "$HOME/.wine/drive_c/Program Files/Steam/"

## Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

### Launches game or program (modify as needed)
## Launches the metacity window manager. Useful if you are going to be running
## more than one x application and you want to be able to move/resize the windows.
## Will need metacity installed of course (part of gnome desktop)
#DISPLAY=:3 metacity --replace &
#sleep 2

## The "DISPLAY=:3" command simply states which window to launch the following program into.
## If you omit it, it will try to launch in the current session which may or may not have
## x windows running on it.
DISPLAY=:3 xterm &
#DISPLAY=:3 WINEDEBUG=-all wine "C:\Program Files\Steam\steam.exe" &
```

In your case, I think you can simply do the following:
```
sudo aptitude install xorg
startx && firefox
```

---

### Post by evo9 on 2010-03-04
> **Revo99 said:**
> 

I then want to then open it from terminal as a browser. I don't know if I am using the right command to do this. Tried a number of variatons but comes back as Error: no display sepcified. 




type 'firefox' (no quotes) into your terminal window and it should open

---

### Post by Revo99 on 2010-03-04
> **dfreer said:**
> You could very well just install the xserver, and start firefox alone in it. There's really no need to install the entire gnome desktop.

THANKS! this sounds like it. What are the commands just to install x server?

Cheers,

---

### Post by Revo99 on 2010-03-04
> **evo9 said:**
> type 'firefox' (no quotes) into your terminal window and it should open

Thanks! This is when I get "error: no display spcecified" back. However this
must be because I haven't installed the X server.

Cheers,

Revo

---

### Post by sisco311 on 2010-03-04
> **Revo99 said:**
> So once I install my GUI it will always boot up like an OS correct?
If so. There is no way to open webmin interface without doing the above?

Thank you for your Apollo87

By default it will boot in the GUI, but you can set it to boot in the CLI.

I don't know much about webmin, but can't you just use a CLI web browser (w3m, links...) or a web browser which can use framebuffer like links2?

[thread=882596]HOWTO: Ubuntu CLI versions & Framebuffer Programs[/thread]

> **dfreer said:**
> You could very well just install the xserver, and start firefox alone in it. There's really no need to install the entire gnome desktop.


+1 or a lighter window manager or a minimal gnome environment (gnome-core).

[uhelp]community/Installation/LowMemorySystems#Adding%20a%20Window%20Manager[/uhelp]

---

### Post by dfreer on 2010-03-04
> **Revo99 said:**
> THANKS! this sounds like it. What are the commands just to install x server?

Cheers,

See my edit in my previous post. Also, there exists several very good CLI browsers that do not require you to install an X windows server, if you feel comfortable with browsing the web using text only. My favorite is lynx, usage is simple:

```
sudo aptitude install lynx
lynx http://www.google.com
```

Screenshot: [http://upload.wikimedia.org/wikipedia/commons/e/ed/Lynx_%28web_browser%29.png](http://upload.wikimedia.org/wikipedia/commons/e/ed/Lynx_%28web_browser%29.png)

---

### Post by HermanAB on 2010-03-05
Hmm, on a real server, you should use 'lynx' (OK) or 'links' (better).

On a desktop machine with keyboard and screen attached, you should use regular Ubuntu, since installing the server version and then installing all the desktop schtuff is a waste of time.

---

### Post by Revo99 on 2010-03-05
.

---

### Post by Revo99 on 2010-03-05
I used Command 

startx && Firefox or
startx
my screen looks like it wants to boot then returns the following:

R****@E****:~$ with a little rectangular symbol after the $ sign. Plus the * I have added just for security.

I have an ATI 5770 card. Could this be the problem here?

Help appreciated 

Cheers

---

### Post by Revo99 on 2010-03-05
Finally found the correct symbol. This is exactly what I am getting in tiny text in the top left hand corner of the screen after typing startx.

reece@EVANS~$: &#58748;

Not much to go on sorry. :(

---

### Post by dfreer on 2010-03-05
Perhaps xorg needs to be configured for first time run? I think you would use the dpkg-reconfigure xorg command:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

---

### Post by Revo99 on 2010-03-07
Hey everyone,

Thanks for your help on this one. I have resolved the issue. Had to install x which I used xorg. Then needed a window manager and used fvmm.

Cheers,

revo99

---

