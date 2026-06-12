---
title: "Will 12.xx have unity?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by rez182 on 2011-05-19
will 12.xx have unity? im not able to use it in 11.04 since its not compatible with my graphics card, and i think it will never be unless ubuntu developers make a fix for my graphics. i really need this cuz my 10.10 does not work with wifi when in battery mode. and 11.04 seems to work in battery mode as long as the graphics driver is NOT installed. so i was wondering. will 12.xx have unity or not. or can some1 suggest me some other solution.

thanks alot.

Asus K40IE
Nvidia Gforce 310M - 512MB

---

### Post by compmodder26 on 2011-05-19
Yes it will. But you should be able to install unity-2d from the repositories.  You can log in to Classic mode and then install it from there.  That should allow you to use Unity with your graphics card.

---

### Post by dwhite on 2011-05-19
> **compmodder26 said:**
> yes it will. But you should be able to install unity-2d from the repositories.  You can log in to classic mode and then install it from there.  That should allow you to use unity with your graphics card.

+1

---

### Post by ghostcatzero on 2011-05-19
You can also stay in Classic display mode and avoid using Unity entirely, though I don't know how far into the future Ubuntu will support Classic. Just select it from Login Screen settings ([http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/)) or at the bottom of the screen at the password prompt when you login.

---

### Post by compmodder26 on 2011-05-19
> **ghostcatzero said:**
> You can also stay in Classic display mode and avoid using Unity entirely, though I don't know how far into the future Ubuntu will support Classic. Just select it from Login Screen settings ([http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/05/enable-ubuntu-classic-desktop-in-ubuntu-11-04-natty-narwhal/)) or at the bottom of the screen at the password prompt when you login.

Future versions of Ubuntu will be based on Gnome 3.  While the gnome 3 shell will not be installed by default, it should be available for download through the repositories.  Gnome 3 shell has what is called "fallback mode" which is essentially gnome panels like Gnome 2 has.  So, in a round-about way, you should still be able to get your "Classic" interface should you choose to.

---

### Post by kaldor on 2011-05-19
11.10 will be entirely Unity-only. But, there will be improvements by then.

Option 1: Use default, 3d-accelerated Unity

Option 2: If not compatible, you will default to the 2d version of Unity.

Option 3: Install GNOME 3 stuff from the repos and use the "Fallback Mode" which is just a fancy name for the "classic" panel setup.

While Ubuntu will be much different, it won't matter if you don't have the needed hardware; you'll have options.

---

### Post by rez182 on 2011-05-19
thanks everyone for the replies, but the problem i am facing with 11.04 is that i cant install the graphics card driver 260.x.x.x (default version for nvidia) at all, cuz then i cant even view the login screen where i can select the classic.

if my graphics card is not supported by ubuntus latest unity, does it mean i cant use future releases ever?

btw im using the same 260.x.x. nvidia driver in my 10.10, and its works fine, but for some reason it conflicts with unity. i installed 11.04 10-12 times trying to solve this problem, but i forgot if i tried making classic login the default and then installing the driver. ill need to do it again. but im afraid to screw up all my files again. so ill need to try in in my pen drive. is it possible? please leave an answer to that in here [http://ubuntuforums.org/showthread.php?p=10837017#post10837017](http://ubuntuforums.org/showthread.php?p=10837017#post10837017)

thanks for the trouble...

EDIT: one thing i noticed in LiveUSB session, in the synaptic manager, the latest 270.x.x.x is available, but when i boot in from HDD ubuntu (10.10 or 11.04) i see only 260.x.x.x of the nvidia driver.

---

### Post by compmodder26 on 2011-05-19
You will be able to use unity-2d.  It doesn't require 3D graphics.

BTW, what is your nvidia card?

---

### Post by rez182 on 2011-05-19
> **compmodder26 said:**
> You will be able to use unity-2d.  It doesn't require 3D graphics.

BTW, what is your nvidia card?

my graphics card is nvidia gforce 310M - 512 mb

but i need graphics card driver to play games or for better performing desktop right...

---

### Post by compmodder26 on 2011-05-19
Sorry for asking about it, should have re-read your original post.  Anyway, here is a [thread]("http://ubuntuforums.org/showthread.php?t=1392766") detailing a fix for that card.  Have you tried that yet?

---

### Post by rez182 on 2011-05-19
> **compmodder26 said:**
> Sorry for asking about it, should have re-read your original post.  Anyway, here is a [thread]("http://ubuntuforums.org/showthread.php?t=1392766") detailing a fix for that card.  Have you tried that yet?

no i didnt see that thread before. im goin through it now...so far didnt find any..they are talkin about past ubuntu releases...
EDIT: btw thanks for this info...

---

### Post by wildmanne39 on 2011-05-19
> **rez182 said:**
> thanks everyone for the replies, but the problem i am facing with 11.04 is that i cant install the graphics card driver 260.x.x.x (default version for nvidia) at all, cuz then i cant even view the login screen where i can select the classic.

if my graphics card is not supported by ubuntus latest unity, does it mean i cant use future releases ever?

btw im using the same 260.x.x. nvidia driver in my 10.10, and its works fine, but for some reason it conflicts with unity. i installed 11.04 10-12 times trying to solve this problem, but i forgot if i tried making classic login the default and then installing the driver. ill need to do it again. but im afraid to screw up all my files again. so ill need to try in in my pen drive. is it possible? please leave an answer to that in here [http://ubuntuforums.org/showthread.php?p=10837017#post10837017](http://ubuntuforums.org/showthread.php?p=10837017#post10837017)

thanks for the trouble...

EDIT: one thing i noticed in LiveUSB session, in the synaptic manager, the latest 270.x.x.x is available, but when i boot in from HDD ubuntu (10.10 or 11.04) i see only 260.x.x.x of the nvidia driver.Hi which nvidia card do you have?

---

### Post by jakupl on 2011-05-19
> **rez182 said:**
> 

Asus K40IE
Nvidia Gforce 310M - 512MB

:)

---

### Post by beew on 2011-05-19
That is a pretty good machine and it is ridiculous to say that OP should  use a fall back DE like Unity 2d or classical desktop (which will not be  around for 12.XX anyway) which are meant for old hardware. If OP cannot run Unity on such a machine without going to fall back mode then maybe you shouldn't use Ubuntu on it, period.

---

### Post by jerome1232 on 2011-05-19
> **beew said:**
> That is a pretty good machine and it is ridiculous to say that OP should  use a fall back DE like Unity 2d or classical desktop (which will not be  around for 12.XX anyway) which are meant for old hardware. If OP cannot run Unity on such a machine without going to fall back mode then maybe you shouldn't use Ubuntu on it, period.

Ubuntu will move to gnome3, which has a gnome2-esk fallback mode. The issue at hand is not the hardware itself, but the driver. I would try to install nvidia-current, if it screws up your display you should be able to boot into recovery mode and reconfigure xorg to not use the nvidia driver.

Also try running "nvidia-xconfig" from a virtual terminal after a failed driver attempt, then rebooting.

Is this a fresh install or an upgrade? (from the info thus far I infer that it's a fresh install but I wanted to be sure)

---

