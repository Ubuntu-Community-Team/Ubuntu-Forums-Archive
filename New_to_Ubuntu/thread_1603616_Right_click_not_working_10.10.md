---
title: "Right click not working 10.10"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by AuroraDizon on 2010-10-22
Hey guys.  Since I upgraded from 10.04 to 10.10 right click will click something as if I left clicked something.  

10.10 netbook remix
HP mini netbook 210-1018CL

If anyone knows how to fix this let me know. Thanks :)

---

### Post by SpockVulcan on 2010-10-24
Check System> Preferences > Mouse and make sure the orientation is correct

---

### Post by psycho5 on 2010-10-24
I've got the exact same problem, also on HP mini, the mouse preferences doesn't have any option that can help enable right click.

*edit* except for trigger secondary click, but still, why isn't the right click working..?

---

### Post by psycho5 on 2010-10-25
*bump* help please, is this a bug? any possible solution? help really appreciated!!!

---

### Post by Verbeck on 2010-10-25
open gconf-editor then go to
/desktop/gnome/peripherals/mouse
see whether left_handed is checked or not

p.s.its actually the same thing as mouse preferences but still worth a check

---

### Post by psycho5 on 2010-10-25
should it be checked? right now as I can recall it isn't checked. I'm not near my laptop now, so I can't confirm. But, as a side note, doesn't that refer to if you're left or right handed?

---

### Post by kp0ccobep on 2010-10-28
Same on my HP Mini 210

---

### Post by psycho5 on 2010-10-28
checking the left handed box also doesn't work.

---

### Post by migs73 on 2010-10-28
Try downloading a CLI app called 'xev'.

This will open a box on the screen and when you use a mouse function whilst cursor is in the box the perceived output is diplayed in terminal. This will determine if your right click is seen at all.

---

### Post by Zzl1xndd on 2010-10-28
I think this might be related to Unity (as these folks are using the Netbook remix). I noticed while using Unity on my desktop that there doesn't appear to be any option to right click.

Not sure if this is a bug or working as intended.

---

### Post by psycho5 on 2010-10-28
> **tweakedenigma said:**
> I think this might be related to Unity (as these folks are using the Netbook remix). I noticed while using Unity on my desktop that there doesn't appear to be any option to right click.

Not sure if this is a bug or working as intended.

There is option to right click in Unity bro, I used a usb mouse and u can right click on the unity menu to add running items to the launcher, you can basically right click anywhere.. otherwise browsing the web without being able to right click to open in new tab or to "save as..." would have been a huge oversight if they forgot about it.

---

### Post by migs73 on 2010-10-28
> **tweakedenigma said:**
> I think this might be related to Unity (as these folks are using the Netbook remix). I noticed while using Unity on my desktop that there doesn't appear to be any option to right click.

Not sure if this is a bug or working as intended.

Hmmm, maybe a nod towards tablet pc's?

---

### Post by bluedalek on 2010-10-29
A friend has a new HP mini, model 210-1190ca.  Using the touch pad, the left button seems to work, but there is no response when trying to use the right button.

Plugging in a USB mouse allows both left & right clicking.

Another issue that I have come across, is that it is impossible to l.click and drag the mouse around.  The cursor seems to jump around, instead of being able to drag a box around the icons.

Anyone have any thoughts?

The more I read, the more it's looking like a switch over to 'regular' Ubuntu is in the cards!

---

### Post by Zzl1xndd on 2010-10-29
> **psycho5 said:**
> There is option to right click in Unity bro, I used a usb mouse and u can right click on the unity menu to add running items to the launcher, you can basically right click anywhere.. otherwise browsing the web without being able to right click to open in new tab or to "save as..." would have been a huge oversight if they forgot about it.

Well it wouldn't let me right click on anything. Not the launcher, desktop, etc.

---

### Post by CarlGWatts on 2010-11-05
The solution to this problem was provided way back in February in the posting titled "HP Mini 210 touchpad right click not working".

---

### Post by psycho5 on 2010-11-07
The solution was on that post here: 
> 
To get the trackpad working correctly you need to use the terminal and enter in the below commands. Make sure you press enter after each command:

```

sudo su

```
```

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

```
```

reboot

```
Once the computer reboots your trackpad will be able to do left click and drag and right clicking.
Last edited by Sabot; February 12th, 2010 at 03:09 PM..
  

---

### Post by Torero on 2010-11-24
Hi,

i had a left-klick problem with my Touchpad.

this workaround is also working for my Lenovo S10-3s with Kubuntu 10.10


great

Marcel

---

### Post by DieseL1988 on 2011-01-05
I can also confirm this worked on a Lenovo S10-3s running 10.10

However, the track-pad no longer edge scrolls and it did beforehand. Not a massive issue as right click is more important but it would be nice to have both features.

It seems the Ubuntu install just didn't detect the hardware correctly, I hope this is all corrected in the next release.

---

### Post by hansolo4949 on 2011-01-05
Yes, it does seen that you have a problem with the driver for your trackpad. You said that a usb mouse worked, right? This may be a long shot, but try it. Go to system>administration>hardware drivers and see if it has a driver for your trackpad. You should also download the gnome desktop if you want to, and see if the right click function works on gnome.


Hope that helps!

 hansolo4949

---

### Post by windozh8ter on 2011-03-13
This solution worked for me (HP Pavilion dv6).

---

