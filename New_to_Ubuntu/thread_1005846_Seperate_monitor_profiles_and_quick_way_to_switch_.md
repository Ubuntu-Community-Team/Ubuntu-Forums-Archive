---
title: "Seperate monitor profiles and quick way to switch between them..."
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-08
I researched this and didn't see anyone else that was doing what I'm trying to do. I have a Nvidia GeForce 8600GS with an lcd monitor plugged into the DVI port and a crt television plugged in via svideo on the other side of my room.

When I'm at the computer, I use the monitor and for watching movies or playing games I use the tv. I know how to switch between them using the nvidia control panel, but is there a way to creata profiles for both devices that could be switched with a key press or command and auto adjust the resolution on both devices and such?

---

### Post by taseedorf on 2008-12-10
okay man.
this is what i would do

it is kind of dumb, but you can write a script to do it for you each time

first set your settings how u want for your first monitor
then
save /etc/X11/xorg.conf as xorg.conf.V1
do the same for the second monitor and save it as xorg.xonf.V2

load each one when you want to switch by typing

sudo cp /etc/X11/xorg.conf.V1 /etc/X11/xorg.conf
sudo dpkg-reconfigure -phigh xserver-xorg

you can try making a script with a text editor

echo "Pick which you want to use"
echo "1 or 2"
read Choice
if [ $Choice = "1" ]
then
gksu cp /etc/X11/xorg.conf.V1 /etc/X11/xorg.conf
gksu dpkg-reconfigure -phigh xserver-xorg
    else
    if [ $Choice = "2" ]
    gksu cp /etc/X11/xorg.conf.V2 /etc/X11/xorg.conf
    gksu dpkg-reconfigure -phigh xserver-xorg
        else
        echo "error!"
    fi
fi


than save the text file as whatever and save it in your home dir
and do
chmod +x <scriptname>
and whalla...
run your script by
./scriptname

---

### Post by taseedorf on 2008-12-10
in not on my linux box now, but i believe there are profiles, but they are in the profile manager...

OR, just create a new account called "Crt" and use that with your monitor... i dunno

---

