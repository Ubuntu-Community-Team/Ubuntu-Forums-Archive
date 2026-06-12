---
title: "Stuck with a &quot;Low Graphics&quot; warning pop-up"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by manilaph on 2010-05-27
Everytime I boot my Ubuntu 10.04 AMD64, I get a warning Pop-up that I am running on Low Graphics mode.

I have not installed the NVIDIA drivers yet because the last time I installed it, I got a blank black screen. This is my 2nd Fresh install of 10.04. I did all the steps upto the "nomodeset".

```
sgo@sgo-laptop:~$ lspci |grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)

```

Should I just live with this warning pop-up regarding low graphics? Everything seems to be working fine and I have the correct resolution and can play youtube etc.

The warning pop-up is just a few additional clicks before getting a working desktop.

I cannot seem to find a compatible nvidia driver right now.

---

### Post by cariboo on 2010-05-27
I would suggest you install the restricted drivers for your video card, then before you reboot, open a terminal and type:

```
sudo nvidia-xconfig
```

then reboot. You should be taken to the desktop, without the low graphics warning.

---

### Post by jmarz on 2010-05-27
[FONT="Verdana"][SIZE="4"]another poster told of using nomodeset at grub screen[/SIZE][/FONT]

thanks to those that posted about it - I finally got my set up fixed so I don't have to mess with the low graphics notice

one member posted this-
[1) Hold down Shift while booting to get to grub.
2) Press 'e'. Replace "quiet splash" with "nomodeset".
3) Ctrl+x to boot.
]]

I just let it go to grub and then hit the  e key

 use the dn arrow to get to the line that has the quiet splash
 use arrow key to get to the words quiet splash and delete them and type in  nomodeset
then do #3

after the reboot I still did have the low graph notice.

 so i went to synaptic and removed all nvidia drivers -
 used the search there to find it fast
did a reboot  and still had the notice.

 went back into synap and reloaded all nvidia stuff- clicked to sort by newest

and reinstalled a lot of the nv stuff from the top of that list - unless the description made me think it wasn't what i needed

did a reboot then - and finally it all worked and no stupid notice.


 good luck I hope it works for you- I've been messing with trying to fix mine on & off for a month or so

 Dual boot Ub 10+ with XP

---

### Post by manilaph on 2010-05-27
Thank you for all the replies. 

I did edit the grub and removed quite splash and replaced it with "nomodeset".

The "low graphics" warning is gone but I now have a wrong resolution.

The correct resolution for my 13.3-inch screen should be 1280x800.

I have not yet installed any NVIDIA drivers because I had a bad experience with it the last time around.

The resolution when I had "quite splash" and the low graphics warning is better with the original 1280x800.

I think the solution is to remove the low graphics warning or just to live with it because I believe that the warning is wrong.

Now that I do not have the warning, ... the graphics is actually in low graphics mode. When I have the warning... it is not really in low graphics mode.

Any other suggestions?

I have a feeling that the "low graphics warning" is actually a bug because I do not have "low graphics" when I have the warning. I have the correct graphics and resolution when I have the warning.

---

### Post by manilaph on 2010-05-27
> **cariboo907 said:**
> I would suggest you install the restricted drivers for your video card, then before you reboot, open a terminal and type:

```
sudo nvidia-xconfig
```

then reboot. You should be taken to the desktop, without the low graphics warning.

Thank you for the suggestion. Which NVIDIA driver should I use? I checked the list and it does not cater to my NVIDIA GeForce Go 6100.

---

### Post by manilaph on 2010-05-29
Here is an update:

1) I tried the nomodeset and install Nvidia-current.... I get a blank black screen.

2) After purging the Nvidia-current... I tried the Nvidia-173... still I get a blank black screen.

3) I remove all nvidia and still use the nomodeset.... i get bad resoultion (not the perfect resolution for my 13.3inch screen).

4) I go back to quite splash and without nvidia... I get pefect resolution but I get the "low graphics" notification. Please note that having the "low graphics" notification is still better-off than having bad resolution or a blank screen. And also, even with this low graphics notification... I can watch videos... youtube etc.

So is this "low graphics" notification a bug?

---

