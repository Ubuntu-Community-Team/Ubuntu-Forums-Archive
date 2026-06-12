---
title: "HELP! corrupt video after reboot.!"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by agent8 on 2009-12-19
I don't know what I was doing and I tried to get an ati driver to run dual monitors. I can't remember the program/driver. It was some program that gave me a choice of installing nvidea OR ati drivers. All I know is after boot up, I see 2 ubuntu logos on the top half and the bottom half is all corrupted/weird colors. I reboot, hit escape in panic till I get to the root with networking thing and tried.
sudo dpkg-reconfigure xserver-xorg

No options come up, it just says that I may be changing a customized setting or something and it gives me a conf. of where the new backup(?) is located. I type reboot but it's no go. Still same results.

If I could even get in in some kind of safe mode and back up some videos/music, I would be happy and I would re install. PLEASE, PLEASE help me! I am a linux/ubunto NOOB so take it easy on me. 

This is an old Sony vaio that I ruined and turned into a htpc. The ati card is a x300 and it is a 3.2 cpu if that helps and I think I am on the second newest ubuntu... 9. something.

Maybe by coincidence the video card failed upon reboot? HELP!

---

### Post by agent8 on 2009-12-19
Or what about  usb live cd. Or better yet, If I find the install disk I made will that help me in a way to get my info off or roll back whatever I did? [SIZE=5]HELP PLEASE!!![/SIZE]

---

### Post by marshmallow1304 on 2009-12-19
Someone may be able to help you fix this without a reinstall, but you can boot up with the CD you used to install and select "Try Ubuntu without any change to your computer".  From there, you can find your hard drive in the Places menu and copy out all your files.

---

### Post by RedSingularity on 2009-12-19
Can you post the contents of your xorg.conf file

Preferably the section where it says "Device"

---

### Post by agent8 on 2009-12-19
I am not sure how to get the .conf file to display. I can hit escape a bunch till it asks me a few  different ubuntus and the second one from the top says ubuntu with a bunch of numbers and in parentheses I think it says safe mode or something, I hit escape a bunch again like a nub and then I get to root or root with networking.
I type sudo like I know what I am doing:lolflag: and that's about as far as I go.

I think there is a new release of ubuntu and I totally don't mind burning a cd and using my external hd to get my stuff out if that would work. I have a feeling that the conf. file would be pretty large and my working pc is in another room. I am literally brand new at linux/ubuntu sorry.

---

### Post by RedSingularity on 2009-12-19
Display it like this.........

cat /etc/X11/xorg.conf

Then look at the Device section.

---

### Post by agent8 on 2009-12-19
bash: cat /etc/X11/xorg.conf no such file or directory found

do I type sudo before stuff ALL the time?

sudo cat /etc/X11/xorg.conf command not found

I am supposed to be in root from ubuntu recovery correct?

---

### Post by RedSingularity on 2009-12-20
You sure you are typing it exactly that way?  You should have an xorg.conf file.

---

### Post by agent8 on 2009-12-20
cat /etc/X11/xorg.conf but I might be doing it in the wrong location... Tried with space after sudo, space after cat, no spaces and all with the same result. all within recovery blue/grey box- root-black screen/white text

---

### Post by RedSingularity on 2009-12-20
And when you run  sudo dpkg-reconfigure xserver-xorg does it create a new file?

---

### Post by agent8 on 2009-12-20
this time when I did dpkg-reconfigure xserver-xorg it took me through a bunch of new blue screens and options about my keyboard layout and said that it made a new conf file with a long number after it.
After that I re-tried cat /etc/X11/xorg.conf and even cat /etc/X11/xorg.conf with the long number after it typed just as where it said it was but the same thing. bash: no such file


The fact that it created a new conf file.... is this good?

---

### Post by RedSingularity on 2009-12-20
Yeah thats what we want.  Does it say where it saved the new file?

---

### Post by agent8 on 2009-12-20
"overwritting possibly customized configuration file;
 /etc/X11/xorg.conf.20091219211723"

---

### Post by RedSingularity on 2009-12-20
Ok now do this command

sudo mv /etc/X11/xorg.conf.20091219211723 /etc/X11/xorg.conf

---

### Post by agent8 on 2009-12-20
mv cannot stat ' /etc/x11/xorg.conf.20091219211723' no such file or directory

---

### Post by RedSingularity on 2009-12-20
Make sure you have entered that long number correctly, even one missing or wrong digit will mess it up like that.

---

### Post by agent8 on 2009-12-20
sudo mv /etc/X11/xorg.conf.20091219211723 /etc/X11/xorg.conf with a space before and after "mv" and a space after the numbers right?

I redid the first step, got a new set of file numbers just in case and double, triple checked it all with the same results "cannot stat.............. no such file or directory". I am sure I am getting the numbers right. Not positive about the spacing and such but I have tried it over 50 times different ways. seriously. LoL. I think I really messed something up!

---

### Post by RedSingularity on 2009-12-20
Hmmmm if you do 

ls /etc/X11

Does it show the files you just created?

---

### Post by agent8 on 2009-12-20
cannot access /etc/x11 no such file or directory

---

### Post by RedSingularity on 2009-12-20
Have you been using a Capital X in X11?

---

### Post by agent8 on 2009-12-20
nope. everything in lower case just as you have listed it.

Fearing the worst, I have begun the download of the latest iso. ubuntu.:cry:

From the sounds of it, I must have screwed up something really bad

---

### Post by RedSingularity on 2009-12-20
Do it in upper case.


sudo mv /etc/X11/xorg.conf.20091219211723 /etc/X11/xorg.conf

---

### Post by agent8 on 2009-12-20
cap X's

 "try mv--help for more information"


and another time I got "missing destination file operand after /ect/X11/xorg.20091219211723/ect/X11/xorg.conf

---

### Post by RedSingularity on 2009-12-20
Can you post the "Device" Section of the xorg file yet?  

cat /etc/X11/xorg.conf

The device section has the driver info we need.

---

### Post by agent8 on 2009-12-20
Identifier "configured Video device"
Option "Use FBDev" "true"

Ah ha

---

### Post by RedSingularity on 2009-12-20
Is there a section just named "Device"?

---

### Post by agent8 on 2009-12-20
bunch of stuff on top about changing file (don't know how to scroll up to read it all.) then 

Section "device" with what I listed

Section "monitor" and then

Section "screen"
Device "configured video device"

---

### Post by RedSingularity on 2009-12-20
Ok and what is your brand video card?

---

### Post by agent8 on 2009-12-20
ati x300. It's an old system

---

### Post by RedSingularity on 2009-12-20
Ok make the device section look like this...........

```
Section "Device"
                Identifier        "ATI"
                Driver            "ati"
EndSection
```

Then reboot.

---

### Post by agent8 on 2009-12-20
you lost me... How do I "make it look" like anything? I guess I want to edit the xisting conf file? I don't know how to do that.

---

### Post by RedSingularity on 2009-12-20
sudo vi /etc/X11/xorg.conf

VI editor commands found here: [http://www.cs.rit.edu/~cslab/vi.html](http://www.cs.rit.edu/~cslab/vi.html)

Make sure you save when done editing.

---

### Post by agent8 on 2009-12-20
changed  Identifier to "ATI"
hit return and added the line  Driver "ati"

ZZ to save. Rebooted and still same artifacts/lockup after ubuntu logo loads:(

I really appreciated all your help on this. I am going to call it a night for now

---

