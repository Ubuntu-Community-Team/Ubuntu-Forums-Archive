---
title: "Some weird black command screen..."
date: 2011-01-09
forum: New to Ubuntu
---

### Post by bradenmast on 2011-01-09
Hello all, i am pretty new to the linux community and i set up a dual boot on my laptop with vista, and ubuntu 10.10. My first problem last night was setting up dual monitors i finally somehow got that to work and turned my computer off last night. I went to get back on and they wernt working again! So i trolled around the internets and found someones gnome terminal solution and typed it in, then i rebooted to see the changes, and it boots into a black screen with my computer name on it and prompts me to enter my username and password and then it does nothing :confused:. I have absolutely no idea what this is, or how to fix it. I am currently on my vista (thank god this one works). Any ideas would be excellent thanks all.

---

### Post by andymorton on 2011-01-09
> **bradenmast said:**
> Hello all, i am pretty new to the linux community and i set up a dual boot on my laptop with vista, and ubuntu 10.10. My first problem last night was setting up dual monitors i finally somehow got that to work and turned my computer off last night. I went to get back on and they wernt working again! So i trolled around the internets and found someones gnome terminal solution and typed it in, then i rebooted to see the changes, and it boots into a black screen with my computer name on it and prompts me to enter my username and password and then it does nothing :confused:. I have absolutely no idea what this is, or how to fix it. I am currently on my vista (thank god this one works). Any ideas would be excellent thanks all.

After you've entered your username and password try typing startx

andy:)

---

### Post by Eternal_Light on 2011-01-09
This is quite simple :) It took me 2 or 3 days to sort that out as well when i first met ubuntu a couple of months ago. First of all you have to login to your account when the computer asks you to. In the command line. Keep in mind that when you type your password it doesn't show on screen at all. Not even as ***** marks.

After you do that if you dont get a new command prompt and cant type anything you have to press Alt+F1. It might ask you to relogin. You will want to do that.

Then you type in 
cd /etc/X11
sudo nano xorg.conf

this will open up the xorg.conf document on the nano text editor that can launch in a non-graphical environment. There you will have to tweak the xorg.conf based a lil bit on your instincts. Find the screen resolutions and lower them, maybe set it back to single screen view instead of duals /This way you might be able to get the graphical environment working again so you can at least browse the web and tweak at the same time. If you manage to get graphics going on, even on a single screen you will have to open a terminal and type in
cd /etc/X11
sudo gedit xorg.conf

If you have an nvidia card you might want to find and download the drivers that are released on their website as they come with a handy tool for managing your screen(s).
Good luck on your quest mate :)

---

### Post by bradenmast on 2011-01-09
Andy: I tried the startx command and it gave me an error and told me to go to the x.orgfoundation page or something. I would have screenshotted if i could. 
Eternal: Thanks bro I'm pulling up your reply on my phone as we speak to see if it works, ill be back in a bit LOL

---

### Post by bradenmast on 2011-01-09
I tried messing with that conf no deal any way to delete and reload a default? open to ideas lol

---

### Post by Eternal_Light on 2011-01-09
could you give me some specs? what graphics card u got? drivers? And most important of all what resolution do your screens have? I might be able to give u mine or at least tell you what mine looks like

---

### Post by bradenmast on 2011-01-09
Sure thing man, I am running a Nvidia geforce 8600 with the recommended proprietary driver (installed 2 days ago) also downloaded proprietary driver for my wireless card but that shouldnt have any affect. I have no clue the resolution for my laptop screen or my lcd monitor that i was attempting to run on. I'm in vista right now and have it set to 800x600 i think just so i can sit back a ways and use it. ummmm i have 4 gigs of ram and a 250 gb hard drive that i partitioned for vista, and ubuntu. hmmm.....

---

### Post by Vi3GameHkr on 2011-01-09
Will it boot normally in Ubuntu when the second monitor is disabled?  If you can somehow get into the xorg.conf and paste its contents in here, someone might be able to sort that out for you (I get the idea that it is corrupt, which basically means there's probably a syntax error somewhere)

Also, do you know what the max resolution you can get in Vista is?

---

### Post by Eternal_Light on 2011-01-09
ok. I also need to know if your linux is x64 or x32 and if your 8600M is GS GT or GTS. Depending on those 2 things ill tell u what to download and how to deal with it step by step, turns out we had the exact same problem so i can guide you eyes-closed :D

---

### Post by bradenmast on 2011-01-09
If you mean by disabled not connected then no. Max resolution is 1280x800 in vista. And i can get into the file using the GNU nano but i am not sure how to copy and paste it from there. Im such a noob sorry

---

### Post by bradenmast on 2011-01-09
eternal, i think its 32 bit? I would have known if i installed the 64 right and 64 isnt common, and how do i look up graphics card

---

### Post by bradenmast on 2011-01-09
Ah-ha! It is indeed a GT. Lawlz

---

### Post by Eternal_Light on 2011-01-09
umm nevermind, you said you installed the proprietary driver so we are fine i think...
Lets see.

access the xorg.conf again by 
cd /etc/X11
sudo nano xorg.conf

and then find in the file at a Section "Device" 
places where it says 
driver      "something"
first make sure its not talking about a mouse (driver    "mouse")
and then replace whatever is in the brackets with nvidia so it will look like
driver     "nvidia"
you might need to do this in two different Device sections coz it might have created one for the external monitor as well.



Section screen will have to look something like (NOTE: there might be 2 section screens, like below, one for each monitor, but there might be only one section screen).

Section "Screen"

# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0; DFP: 1280x800 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "CRT: 1680x1050_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050_60 +1280+0, DFP: 1280x800 +0+125"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

save it and reboot. If that doesnt work either then go again at xorg.conf and delete the LAST section.
This one:
Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Delete it.


Then go in the above one and at

    Option         "TwinView" "1"

replace it with a 0.


Post results here hopefully from ur working ubuntu :)
ps sorry for shyty english :(

---

### Post by Eternal_Light on 2011-01-09
If the above is too boring you can copypaste my xorg.conf. It will take only 3 or 4 commands in the command line, nothing more but there is a small chance that it will not work without tweaking either.
If we are lucky and it doesn't then your problem will have been dealt with in 3 minutes. :)

---

### Post by bradenmast on 2011-01-09
Wow, i thought that was going to fix it, but it is still a no go. Its exactly like what you gave me. Should i just do a clean install?

---

### Post by Eternal_Light on 2011-01-09
ffs i just found it. ok sec. Ill edit this post with more info in 5 mins or so


Here it is. 
Login normally.
sudo service gdm stop

Here is a slightly tricky part:

You will have to remove the proprietary driver you installed. To do so first you have to find the name of the package.
apt-cache search nvidia           or other similar keywords such as nv   etc.   It won't be hard to locate the name of the package that is the driver. Might be more than one packages but not too many. Note them down somewhere.
sudo apt-get remove packagename                  separately every time for each package you noted

maybe do a reboot
sudo service gdm stop

wget [http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/NVIDIA-Linux-x86-260.19.29.run)
cd ~/
sudo sh NVIDIA-Linux-x86-260.19.29.run

Follow the on-screen instructions
The program will ask u to reboot at least once before the installation is complete.
If it says anything about disabling nouveau choose yes!
If it says anything about autoconfiguring your xorg.conf say YES!

Do a reboot and you are ready!   99% guarantee this will work. if not then you might have a x64 system and do the same things again but with a different download url.

After that thing is complete you will have access to nvidia's options editor and set all options normally almost as easily as if u were in windows.
Gl man. This is going to work!

---

### Post by bradenmast on 2011-01-09
ran the search one is specified a the driver but up have 10 other nividia packages. so just the driver?

---

### Post by Eternal_Light on 2011-01-09
yea i guess. Just do the driver, and if any problems arise go back and do all others as well. But for now it should be fine.

---

### Post by bradenmast on 2011-01-09
I'm sorry for being such a pain and I appreciate all your help, but it doesn't like the  url gah this is a pain

---

### Post by Eternal_Light on 2011-01-09
haha no worries mate :/ now lets see.... what kind of error do u get?

if u got no problem with it i can download it and provide u with a dropbox url to get it from there.

Uhh also if you could do that for me:

Go to

cd /etc/X11
and then do
ls

and tell me if there is any xorg.conf.backup or something like that
maybe the OS has kept a backup...

---

### Post by bradenmast on 2011-01-09
I'm going to take a quick break mate dont want to leave you hanging ll be back in like 30

---

### Post by Eternal_Light on 2011-01-09
> **bradenmast said:**
> I'm going to take a quick break mate dont want to leave you hanging ll be back in like 30
ahh nevermind it. i gotta drop it for today. It's getting late over here :P
Anyways.


Few final tips for u to check out:
>Be connected to the internet through a wire. Wireless doesn't autoconnect when on command line. Maybe thats why your pc couldn't handle the url.

>run a
sudo apt-get update
sudo apt-get upgrade
sudo reboot
maybe they have given out a patch/fix that you haven't downloaded yet. Again you need to be connected to the net thru cable.

>If you get too tired of all that stuff (but only after you have tried the above with the internet cable on) do a clean install and do NOT load the proprietary drivers. Download them from nvidia's site instead. And don't worry. I did 4 clean reinstalls of my kubuntu before sticking to the one i got now :P   Several things can cause bugs that are too hard for a newb to fix. Give it some time and you will start "feeling" what you should tamper with and what not.


>And finally, always keep backups of files you edit. I dont remember the command atm but if you search for it you will find a "copy and rename" function or something so you can make a clean copy of a file you are going to do surgery on incase something bad happens.

With that I'm out! I'll check in tommorow again :)
Good luck and have fun.

---

### Post by bradenmast on 2011-01-09
Eternal_Light i freaking love you man! I didnt realize i needed to be hard wired, so i plugged her in and redid the download it worked, used the utility like you said and rebooted, and it went straight into the desktop! I'm not sure if i want to set up my external monitor now! lol but i am so happy for your help! If you ever need anything hit me up! Oh wow thanks again man the community help was definately a positive experience! Wow thanks again!

---

### Post by Eternal_Light on 2011-01-09
Haha no prob man don't even mention it :P
I got out of bed to use the restroom and couldnt resist a peek at the forums. Im very happy it all worked out. 

Now quickly do a copy paste of your xorg.conf to your documents folder :P
then run thru a terminal
sudo nvidia-settings     and go setup that dualscreen :P  It's the twinview option.
DO A BACKUP before you tamper with anything at all coz its almost certain you are going to crash x a couple of times till you get the screens up and running. I had dedicated a whole day to the cause!

Have fun with ur new os :) GN

---

### Post by bradenmast on 2011-01-09
I backed up and also finally got the twinview to work too! Oh man i have the largest grin plastered to my face right now :D you are definatly a :KS not in a weird way! I dont know if i can thank you enough! YAY!

---

### Post by Eternal_Light on 2011-01-10
Just make sure you backup the working dualscreen xorg.conf as well so you can fallback directly to it if a problem arises. :)

---

