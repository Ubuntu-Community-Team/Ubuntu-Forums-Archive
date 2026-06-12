---
title: "Nvidia GeForce 2 Resolution problem"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by GSI on 2009-01-05
Hi its me again. I have Nvidia GeForce 2 and my resolution is 640x480 and my desktop space is VERY small can you please help me.I cant run games and I have to use an weaker ATI video card

---

### Post by sadaruwan12 on 2009-01-05
> **GSI said:**
> Hi its me again. I have Nvidia GeForce 2 and my resolution is 640x480 and my desktop space is VERY small can you please help me.I cant run games and I have to use an weaker ATI video card

Do you have your nvidia card installed in your computer if it is then go to System -> Administration -> Hardware Drivers see whether Ubuntu have recognized your Nvidia card and listed under device driver then check on the check box in front of it to enable the driver and thats it.
\\:D/

---

### Post by achase79 on 2009-01-05
I had this problem too, You have to go to the system-> administration -> nvidia x config (something or other) and set the resolution there.  For some reason it doesn't give a good one automatically and this program will put the correct entry into the xorg.conf file

---

### Post by northern lights on 2009-01-05
> **GSI said:**
> Hi its me again. I have Nvidia GeForce 2 and my resolution is 640x480 and my desktop space is VERY small can you please help me.
Presumably you're on Intrepid. Have you installed all available updates?
Intrepid wouldn't recognize the GeForce 2 MX on my backup workstation either in early October. Manual driver install changed nothing either. Now it does flawlessly.

Please run```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx-96
```Reboot. Check again in "System > Administration > Hardware Drivers" as well as "System > Administration > NVIDIA X Server Settings".

---

### Post by GSI on 2009-01-15
Seems I told you about the wrong problem :(

See this is the problem 

Without drivers : Resolution 800x600 and no effects
With drivers : Resolution 500x300 and no effects 

Please help! I really like Ubuntu but I cant use it right now bcz my problem.

And when I install drivers on top right corner of the screen says : In order your graphics card to work properly Ubuntu is using drivers with which Ubuntu CANT handle. :( :( :(

---

### Post by mayooresan on 2009-01-15
I had this same problem with my Nvidia card, but Ubuntu 8.10 requested me to update the driver online. 

I did that and afterwards, it worked like magic on my machine. Now I have higer resolution and dazzling effects on my Ubuntu desktop :)

---

### Post by GSI on 2009-01-15
I don't have ubuntu 8.10 :( :( :(




Ubuntu 8.10 downloading..... :) :) 

I hope I will fix the problem in two or three hours :)

---

### Post by GSI on 2009-01-15
Ok. So now I have the newest ubuntu but it dosent offers me any driver download now resolution is prefect but still no effects and no games.
Please send me the driver 

Skype : crazyracer1
MSN : [email]hristianp@hotmail.com[/email]

---

### Post by Terl on 2009-01-15
> **GSI said:**
> Ok. So now I have the newest ubuntu but it dosent offers me any driver download now resolution is prefect but still no effects and no games.
Please send me the driver 

Skype : crazyracer1
MSN : [email]hristianp@hotmail.com[/email]

Did you go to the system-administration-hardware drivers selection?  If not try that and you should see a listing for your graphics card.

---

### Post by GSI on 2009-01-15
No properitary drivers are used in this system.

HELP! :(

---

### Post by GSI on 2009-01-15
> **northern lights said:**
> Presumably you're on Intrepid. Have you installed all available updates?
Intrepid wouldn't recognize the GeForce 2 MX on my backup workstation either in early October. Manual driver install changed nothing either. Now it does flawlessly.

Please run```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install nvidia-glx-96
```Reboot. Check again in "System > Administration > Hardware Drivers" as well as "System > Administration > NVIDIA X Server Settings".


No Such thing as Nvidia X server Settings

---

### Post by GSI on 2009-01-15
Its Working!!!!!!!! Thank you guys.

---

### Post by northern lights on 2009-01-15
> **GSI said:**
> Its Working!!!!!!!! Thank you guys.
Sorted then. Welcome.

For future reference:

- the graphics device (GeForce 2 MX) should have worked under previous releases also

- If earlier you were not offered the driver and/or couldn't find the package manually, you probably did not have the required repositories enabled

Anyhow, enjoy your system!

---

### Post by GSI on 2009-01-18
But why i cant save into X server Config and i have to correct the resolution every time i start ubuntu.....

---

### Post by GSI on 2010-01-06
......

---

### Post by jnmjr on 2010-01-06
> **GSI said:**
> But why i cant save into X server Config and i have to correct the resolution every time i start ubuntu.....


Try This, it worked for me...
[http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html](http://johnnydopefish.blogspot.com/2009/05/ubuntu-904-nvidia-failed-to-parse.html)

---

### Post by GSI on 2010-01-07
It's fixed. I'm on the newest version of ubuntu now

---

