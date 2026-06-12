---
title: "Dedicate X Session"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by Feyerbrand on 2010-07-30
I have been working with some scripts to run games faster on my HP mini 311  and I stumbled on dedicated X sessions that can be used from a launcher in terminal that logs you out and runs the service.  Now every time I run the script it doesn't do anything.   It turns the screen black and makes me restart to get back into my regular session.  I will paste what I have found and I hope that some of you super users could help me out : )

**Use launch scripts**

   *PERFORMANCE TWEAK*- 
Wine games will often perform  their best when they are launched in a separate X server. Wine doesn't  require a window manager (Gnome, KDE, XFCE, etc.) to run properly, so if  you launch a game in a separate X server, you can get a significant  performance boost. You can get an even bigger boost by stopping the  GDM/KDM before you launch the game (only to be done from the console). 
[LIST=1]
[*]First you need to create the script. From the terminal, do the following:```
nano launcher.sh
```
[*]Copy the text below and paste it into  the terminal with either the middle mouse button or by clicking on  Edit&#8594;Paste. Take out the nVidia settings portion if you don't have an  nVidia card and modify the application paths to match your game.```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac -terminate & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/game.exe"
```
[*]Save the file in your home directory by pressing CTRL-O, hit enter then CTRL-X to exit.
[*]Next, make your script executable with this command:```
chmod +x ~/launcher.sh
```
[*]Launch the game by doing this from a terminal:```
sh launcher.sh
``` OR```
./ launcher.sh
```
[/LIST]
***Reference website*** 

[http://gwos.org/doku.php/wine:winestuff](http://gwos.org/doku.php/wine:winestuff)

---

