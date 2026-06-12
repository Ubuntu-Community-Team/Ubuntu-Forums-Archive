---
title: "Crazy Mouse"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by burg1n on 2010-10-15
I just installed Ubuntu 10.10 on my Dell Inspiron 1520 laptop. I have a SteelSeries World of Warcraft Gaming mouse. The mouse moves across the screen very fast and is extremely sensitive. When I try to turn down the Sensitivity and Speed settings it seems to have no effect. Usually I can install the steelseries program for my mouse which has all of my settings but I can not get it to work with wine. I am new to Ubuntu and am not sure why it's not running with wine.

I don't think it's a problem with not having my mouse software though, I have seen many other people with this problem on other forums but I have not found any good answers.

The mouse is also very shaky, even when I am not touching the mouse at ALL the cursor is shaking. Also, it's doing this weird thing where it "double clicks" even when I'm only clicking it once. My mouse is very clean and clicks well and everything works fine with Windows so I'm not sure what the problem is.

A lot of forums are saying it's a problem with nvidia drivers, I do not remember if i had this problem before I installed my new drivers and I'm not sure how I should go about diagnosing a possible driver problem with this.

Please help! :)

---

### Post by burg1n on 2010-10-15
If it helps at all, I unplugged my mouse and it wasn't shaking anymore, and it seems fine if I use my touch pad on my laptop.

---

### Post by burg1n on 2010-10-15
I have tried:
xset m X/X X (tried many different suggested combinations)

xinput --set-prop "SteelSeries World of Warcraft MMO Gaming Mouse" "Device Accel Constant Deceleration" X
xinput --set-prop "Razer DeathAdder" "SteelSeries World of Warcraft MMO Gaming Mouse" X
(also tried many different combinations

Another site I came across was talking about creating some fdi policy for it but...I am new to linux/ubuntu and had no idea what the site was explaining.

I tried editing the xorg.conf file as well
:confused:

---

### Post by jtarin on 2010-10-15
The suggestion above about unplugging the mouse usually works in most cases.

---

### Post by burg1n on 2010-10-15
> **jtarin said:**
> The suggestion above about unplugging the mouse usually works in most cases.

Ya, but then I don't have a mouse, no way I'm using my touchpad for gaming! lol. 

Can anyone recommend a good gaming mouse that actually has real linux support?

---

### Post by burg1n on 2010-10-15
some people are suggesting to add this section into your xorg.conf:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Lachesis Optical Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "11"
    Option         "Resolution" "4000"
    Option         "ZAxisMapping" "4 5"
EndSection

I believe this is because I'm using a high dpi mouse but I could be wrong. But in this example, what is my "identifier"? is this what shows up for my mouse when I type "xinput list" ("SteelSeries World of Warcraft MMO Gaming Mouse"? Because some other sites say to write mouse, mouse0, mouse 1, etc into identifier.

I also finally managed to install my mouse's program/drivers with wine but they were useless, none of the settings changed anything.

---

### Post by jtarin on 2010-10-15
> **burg1n said:**
> Ya, but then I don't have a mouse, no way I'm using my touchpad for gaming! lol. 

Can anyone recommend a good gaming mouse that actually has real linux support?You don't understand....let me clarify. Unplug for a few moments then plug back in.

---

### Post by jtarin on 2010-10-15
> **burg1n said:**
> some people are suggesting to add this section into your xorg.conf:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Lachesis Optical Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "11"
    Option         "Resolution" "4000"
    Option         "ZAxisMapping" "4 5"
EndSection

I believe this is because I'm using a high dpi mouse but I could be wrong. But in this example, what is my "identifier"? is this what shows up for my mouse when I type "xinput list" ("SteelSeries World of Warcraft MMO Gaming Mouse"? Because some other sites say to write mouse, mouse0, mouse 1, etc into identifier.
Try adding. If they have experience with that mouse...use the example as a place to begin.

---

### Post by burg1n on 2010-10-15
Ok, I have tried leaving it unplugged for a while and it seems to have no effect when I plug it back in.

And making those changes to xorg.conf seemed to do nothing at all, so I figured it was because of the identifier. I did not find any examples with this specific mouse, only other high-dpi mice.

---

### Post by kroq-gar78 on 2010-10-15
restart x server after editing xorg.conf by hitting Ctrl-K-Print Screen
or just reboot and it will automatically restart x server

---

### Post by burg1n on 2010-10-15
Is anyone using the Saitek/mad catz cyborg rat 5/7/9 mice? I am looking at purchasing one of these and am wondering how it's working with Ubuntu and what kind of problems you've ran into.

---

### Post by TheMadEngineer on 2010-10-21
Here's the current discussion on the Cyborg R.A.T. series -- they require a little fix to work properly...

[Madcatz Cyborg R.A.T. 7 Gaming Mouse]("http://ubuntuforums.org/showthread.php?p=10008257#post10008257")

---

