---
title: "Using my TV as a monitor"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by Antedeluvian on 2009-11-02
I am running Ubuntu 8.04 on an older Dell pc from Freegeek Vancouver. I had  installed an NVidia GeForce 6200 card. When I connect the computer to the TV using an S video connection, I get a signal on the tv.

 When I startup the tv and the computer,  the Dell screen and then the Ubuntu one show on the tv. But as soon as I try to login, the tv as monitor goes blank. When I then check the System>Preferences>Screen Resolution setting, I find that the setting for cloned monitors has reverted back to single monitor. 

So I think there is some process with NVidia that I am missing which causes it to recognize that I have connected to a TV as a monitor and locks in the connection. I don't know how to formulate the next question other than where should I be looking next? Is my hunch correct?

Definitely a Noobie. Please excuse the lack of correct vocabulary. Any help that you can give  to this young mind in an old corpus will be appreciated.

---

### Post by x C0MMAND0 x on 2009-11-02
On Dell systems, try holding FN and hitting F8.  This cylces between which monitor(s) get the display.  Try that first.

---

### Post by Antedeluvian on 2009-11-02
> **x C0MMAND0 x said:**
> On Dell systems, try holding FN and hitting F8.  This cylces between which monitor(s) get the display.  Try that first.

No luck with this suggested procedure. Perhaps because this computer may no longer be a true Dell as Freegeek rebuilds older computers and puts them out there for a second life.

---

### Post by sandyd on 2009-11-02
> **Antedeluvian said:**
> No luck with this suggested procedure. Perhaps because this computer may no longer be a true Dell as Freegeek rebuilds older computers and puts them out there for a second life.
are you using xinerama?

---

### Post by Antedeluvian on 2009-11-02
> **carlee said:**
> are you using xinerama?

No. I do not know about xinerama.

---

### Post by Bruce H on 2009-11-03
For Nvidia, use their TwinView settings. You can find this in nvidia-settings. You'll need to run it as root, so open a terminal and type:

```
sudo nvidia-settings
```

Standard definition televisions have a tiny native resolution: 320x280, if I remember correctly, though you should be able to use a virtual resolution. I wouldn't go higher than 800x600 because of pixelization issues. If your TV is a High Def TV, then you can go higher.

---

### Post by LowSky on 2009-11-03
> **Bruce H said:**
> 
Standard definition televisions have a tiny native resolution: 320x280, if I remember correctly, though you should be able to use a virtual resolution. I wouldn't go higher than 800x600 because of pixelization issues. If your TV is a High Def TV, then you can go higher.

If its a high def tv then you sohuld use component or hdmi or vga if available, s-video is not made for viewing a computer signal

---

### Post by Antedeluvian on 2009-11-03
> **Bruce H said:**
> For Nvidia, use their TwinView settings. You can find this in nvidia-settings. You'll need to run it as root, so open a terminal and type:

```
sudo nvidia-settings
```Standard definition televisions have a tiny native resolution: 320x280, if I remember correctly, though you should be able to use a virtual resolution. I wouldn't go higher than 800x600 because of pixelization issues. If your TV is a High Def TV, then you can go higher.

The response to entering "sudo nvidia-settings" is "command not found."  How do I correct this?`

---

### Post by Antedeluvian on 2009-11-03
> **LowSky said:**
> If its a high def tv then you sohuld use component or hdmi or vga if available, s-video is not made for viewing a computer signal 
 
I have a standard television about 5 years old. I had been previously recommended to use the setting 800-600. 

The s video cable is delivering the signal, but  the dual [cloned setting] is not holding. When I go to login, I lose it.

---

### Post by sandyd on 2009-11-04
> **Antedeluvian said:**
> The response to entering "sudo nvidia-settings" is "command not found."  How do I correct this?`
install the package "nvidia-settings"

---

### Post by perdo44 on 2009-11-06
> **carlee said:**
> install the package "nvidia-settings"
Thank you for your help and advice.
What a mess I have created for myself. I made the connection to the television, but managed to set an incorrect resolution. So this is the problem I have now.
I cannot reset the resolution because on my computer monitor, I can only see the login-rectangle, and cannot access the terminal as a result.
I cannot reset it on my television  [if I could use it as my primary monitor,] because I cannot see the top line tool bar of the image.
 I am now using another computer to send this plea for advice for this fine mess. I have not had so much fun since I managed to turn  my desktop image upside down by mistake a month ago.

---

### Post by sandyd on 2009-11-08
> **perdo44 said:**
> Thank you for your help and advice.
What a mess I have created for myself. I made the connection to the television, but managed to set an incorrect resolution. So this is the problem I have now.
I cannot reset the resolution because on my computer monitor, I can only see the login-rectangle, and cannot access the terminal as a result.
I cannot reset it on my television  [if I could use it as my primary monitor,] because I cannot see the top line tool bar of the image.
 I am now using another computer to send this plea for advice for this fine mess. I have not had so much fun since I managed to turn  my desktop image upside down by mistake a month ago.
unplug the computer from the tv
press ctrl+alt+f1

login

type in

sudo dpkg-reconfigure --pligh xserver-xorg

---

### Post by perdo44 on 2009-11-08
> **carlee said:**
> unplug the computer from the tv
press ctrl+alt+f1

login

type in

sudo dpkg-reconfigure --pligh xserver-xorg

When I press ctrl+alt+f1, I get the Ubuntu Help Center. Is this where you want me to go? Once again the resolution is so extreme it is difficult to read it or use it.

---

### Post by perdo44 on 2009-11-09
> **perdo44 said:**
> When I press ctrl+alt+f1, I get the Ubuntu Help Center. Is this where you want me to go? Once again the resolution is so extreme it is difficult to read it or use it.

I still need more help. The resolution is still too great for me  to use  the monitor. I have made some progress as I can now see "accessories" "places" and "system" in the toolbar. I have tried  with the NVidia settings to reset the resolution but it is not responding.

---

### Post by Antedeluvian on 2009-11-10
Thanks to all for help.

---

