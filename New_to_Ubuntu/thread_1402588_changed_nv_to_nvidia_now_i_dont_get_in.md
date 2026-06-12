---
title: "changed nv to nvidia now i dont get in"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by F21 on 2010-02-09
Hey there,

i have got a nice two screens card in my computer. I have installed ubuntu 6.10 and i wanted to get two screens working.
I googled and found a command:
sudo gedit /etc/X11/xorg.conf

there it said to change nv to nvidia and so id did.
After that i did
Read #How to restart GNOME without rebooting computer

But after the reboot my whole system doesnt work no more. It launches, with a whole lot error codes, then it loads the ubuntu start up page but just before it goes to the login it goes back to loeding lots of lines. Then i get a announcement saying the X ... is not working. Whit the question if i wanne see the report. I press yes and get more details, i press yes read the stuff. Then announcement about something being turned down, reboot? yes. Then i get into a outside commandscreen. So i tried the command again where i hoped to change the nvidia back to nv so can get in again.
But when trying it, i get the announcement:
cannot open display.
Has anyone got any suggestions???

---

### Post by F21 on 2010-02-09
add on: I cannot log in because before i get to the logon screen it goes into loading different stuff and goes directly to the announcement about x.. not working.

Is there a way to reset the system to default setting or latest working configuration? like you can do in windows?

---

### Post by Sceiron on 2010-02-09
In the commandline move to /etc/X11 and use the command
```
 ls

```

check if there is a backup of your old xorg.conf file.
If so, then you can replace the "broken" one with the backup like this:
```

sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```

---

### Post by philinux on 2010-02-09
> **F21 said:**
> Hey there,

i have got a nice two screens card in my computer. I have installed ubuntu 6.10 and i wanted to get two screens working.
I googled and found a command:
sudo gedit /etc/X11/xorg.conf

there it said to change nv to nvidia and so id did.
After that i did
Read #How to restart GNOME without rebooting computer

But after the reboot my whole system doesnt work no more. It launches, with a whole lot error codes, then it loads the ubuntu start up page but just before it goes to the login it goes back to loeding lots of lines. Then i get a announcement saying the X ... is not working. Whit the question if i wanne see the report. I press yes and get more details, i press yes read the stuff. Then announcement about something being turned down, reboot? yes. Then i get into a outside commandscreen. So i tried the command again where i hoped to change the nvidia back to nv so can get in again.
But when trying it, i get the announcement:
cannot open display.
Has anyone got any suggestions???

Are you certain your version is 6.10

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history)

---

### Post by sandyd on 2010-02-09
> **F21 said:**
> add on: I cannot log in because before i get to the logon screen it goes into loading different stuff and goes directly to the announcement about x.. not working.

Is there a way to reset the system to default setting or latest working configuration? like you can do in windows?

sure.
if your using anything 9.04 and newer, you do not require a xorg.conf to run Xserver.so
Start up in recovery mode and rum
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

or,
You can also run
```

sudo nano /etc/X11/xorg.conf

```
and change nvidia back to nv instead.

---

### Post by Sceiron on 2010-02-09
> **carlee said:**
> sure.
if your using anything 9.04 and newer, you do not require a xorg.conf to run Xserver.so
Start up in recovery mode and rum
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
You can also run
```

sudo nano /etc/X11/xorg.conf

```
and change nvidia back to nv.

Wouldn't this replace the backup with the broken config file?

---

### Post by F21 on 2010-02-09
at the moment i am in the screen where i can do commandlines. This where the line:
sudo gedit /etc/X11/xorg.conf
doesnt work because cannot open display.

i did do command -help and there is says something about gnome version 2.18.0

i am pretty sure it is ubuntu 6.10/ it is an old installation...

---

### Post by Greenwidth on 2010-02-09
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

renames xorg.conf - xorg.conf.bak

so that it not loaded. The file is still there so you can replace it if you need to.


If it is 6.10, don't do this, you need to edit it like carlee said:

sudo nano /etc/X11/xorg.conf

---

### Post by F21 on 2010-02-09
The command:
sudo nano /etc/X11/xorg.conf

did work and got me into a new info screen where i can change stuff.. But i cannot find the line about nv or nvidia...

there is something about getting it automatically updated again with:
sudo dkpg-reconfigure -phigh xserver-xorg

The rest of the document is about fontpath stuff like:
/usr/share/fonts/X11/misc

then EndSection.

Nothing about nv or nvidia

---

### Post by F21 on 2010-02-09
excuse me. I was wrong with my last post.
I just had to go down lots more...

I am trying as i type!

Thumbs crost!

Thanks a lot in advance!!

I will let youu know if it worked out!!!

---

### Post by F21 on 2010-02-09
I did as carlee said:

or,
You can also run
Code:
sudo nano /etc/X11/xorg.conf

So i safed the changes and it says [ Wrote 138 lines]

Under this i come back to the command line. SO how do i have to reboot my system now??

---

### Post by F21 on 2010-02-09
And then i will still have the problem i cannot use two screens... = (

And i have got this brilliant little asus wireless AP WL-330g thing for getting internet acces. But it doesnt work.

Any tips??

---

### Post by F21 on 2010-02-09
Thanks a lott!!

I am in to my system now. Only thing thats left is how can i get two screens without changing nv into nvidia??

---

### Post by a2z on 2010-02-09
you should upgrade to at least intrepid. Or Jaunty. I don't know anything about earlier versions. Nvidia dual monitors have worked for me with bother.

---

### Post by sandyd on 2010-02-09
> **a2z said:**
> you should upgrade to at least intrepid. Or Jaunty. I don't know anything about earlier versions. Nvidia dual monitors have worked for me with bother.

you cant do a 6.xx -> 9.xx upgrade. becasue you must upgrade one version at a time.
advice: download ubuntu 9.10 [here]("http://ubuntu.com") and reinstall using that.
then, do this BEFORE clicking anything (including the hardware drivers dialog/window)
visit the link below to download the nvidia drivers.
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)
Download them to the desktop. 
You wont be using the nvidia drivers, youll be using vesa cause thats the default graphics driver. Therefore, there is no need to kill xserver first, or go to init 3 (lower runlevel)
run this.
```

sudo chmod 777 ~/Desktop/nvidia*
sudo sh ~/Desktop/nvidia*

```

---

### Post by markp1989 on 2010-02-09
> **F21 said:**
>  I have installed ubuntu 6.10 

is that a typo? if it isnt you should upgrade :)

---

### Post by celthunder on 2010-02-09
Which nvidia drivers are you running? 

The dual screen stuff should be supported as long as you're graphics drivers are somewhat up to date (nvidia has them on there site).

You should probably update everything though if you are really on 6.1

---

### Post by a2z on 2010-02-10
> **carlee said:**
> you cant do a 6.xx -> 9.xx upgrade. becasue you must upgrade one version at a time.



Well yes. Thanks for expanding. 
One should never assume ;)

---

### Post by F21 on 2010-02-12
hey there,

well i did already update my system to ubuntu 9.10.
And it seems stuff is working better already.

Now i again did like carlee said. Well, i still have to go and install the nvidia driver and run the command but i think that will halp me out on the two screen thing.

Another thing im still busy with is getting my asus wireles ap wl-330g to work. I reaaaally need this so i can get updates and some software i need for work. Anybody got tips which software to down for music editing, recording and stuff??? 

Thanks in advance!

---

### Post by F21 on 2010-02-12
> **carlee said:**
> you cant do a 6.xx -> 9.xx upgrade. becasue you must upgrade one version at a time.
advice: download ubuntu 9.10 [here]("http://ubuntu.com") and reinstall using that.
then, do this BEFORE clicking anything (including the hardware drivers dialog/window)
visit the link below to download the nvidia drivers.
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)
Download them to the desktop. 
You wont be using the nvidia drivers, youll be using vesa cause thats the default graphics driver. Therefore, there is no need to kill xserver first, or go to init 3 (lower runlevel)
run this.
```

sudo chmod 777 ~/Desktop/nvidia*
sudo sh ~/Desktop/nvidia*

```

I am puzzled.... I downloaded the nvidia driver, copy/paste via usb to my desktop and did the codes you said. But i just get back:
sudo chmod 777 ~/Desktop/nvidia*
cannot acces /home/f1/Desktop/nvidia*: no such file or directory
and
sudo sh ~/Desktop/nvidia*
cant open /home/f1/desktop/nvidia*

I already changed the name of the driver and that didnt help. Keeps saying it cant open ish.... = (

---

