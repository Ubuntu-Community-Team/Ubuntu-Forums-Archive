---
title: "Which support area do I post to for setting up Graphics Card?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by WolfRage on 2009-10-23
Which main support area should I posty in to get help setting up my ATI Radeon 9600x card in Ubuntu 9.10? I recently read a great article in the media section, but it was targetd towards intel graphics drivers.

---

### Post by squaregoldfish on 2009-10-23
Hardware & Laptops would be your best bet.

Steve.

---

### Post by WolfRage on 2009-10-23
Thanks! I think I may have found a fix. The open source ATI drivers. I will post in hardware for further support.

---

### Post by overdrank on 2009-10-23
> **WolfRage said:**
> Thanks! I think I may have found a fix. The open source ATI drivers. I will post in hardware for further support.

Also :)
Multimedia & Video
Have multimedia question? ATI, Nvidia, Sound cards. Just ask here.

---

### Post by 3rdalbum on 2009-10-23
> **WolfRage said:**
> Which main support area should I posty in to get help setting up my ATI Radeon 9600x card in Ubuntu 9.10? I recently read a great article in the media section, but it was targetd towards intel graphics drivers.

Ubuntu 9.10 already comes with the only driver available for the ATI Radeon 9600x, so congratulations - it's already set up.

---

### Post by WolfRage on 2009-10-23
Then why is it not working? The graphics even for native linux games are horrible and my frame rate is way behind? There must be a better way and I will fix it.

---

### Post by 3rdalbum on 2009-10-23
ATI doesn't support those graphics cards anymore on Linux, leaving you with only the open-source driver. The best solution would be to upgrade your card to something that is supported; if you have PCI-E you should get a recent Nvidia graphics card, if you only have AGP then you can get recent ATI cards in AGP from PowerColor.

---

### Post by WolfRage on 2009-10-23
I understand what you are saying. Bu I just moved overseas and so I do not have the cash to upgrade this spare computer right now. So until then I am going to have to make it work. My wife has the main computer and I do not want to kick her off every time I want to do something graphic intensive.

---

### Post by Mark Phelps on 2009-10-23
> **WolfRage said:**
> I understand what you are saying. Bu I just moved overseas and so I do not have the cash to upgrade this spare computer right now. So until then I am going to have to make it work. My wife has the main computer and I do not want to kick her off every time I want to do something graphic intensive.

I sympathize with you, really!  I'm one of the folks who's graphics card is no longer supported by ATI, too.  

But the unfortunate situation, as others have already told you, is that ATI dropped support for these cards in Linux some time back.  So, basically, apart from some tweaking (which you can do by typing "man radeon" in a terminal and seeing the great long list of parameters), and some minor 3D acceleration, like me, you're stuck with the open source drivers.

You can also go to the Phoronix forums and read the threads there about tweaks folks have done using the open source drivers.

---

### Post by WolfRage on 2009-10-23
Thanks for the advice I will have to find the Phoronix forum.

---

### Post by WolfRage on 2009-10-27
For any one searching for Information relating to a ATI 9600 XT All-In-Wonder I found that your options are as follows: The current best solution is Envy which is aviable in the Ubuntu repositores, this appplication will match up the propritary drivers with your version of Ubuntu, your Kernel and the x-org-server version. 
The next reall good option is to regress to Ubuntu 8.04 Hardy Herron or 8.10 Intrepid.
Although the regression is not ideal it offered me the best solution when coupled with Envy to support the legacy hardware of my older desktop, with out breaking the system with future updates.
Best pages to help you:
This page will give you help with installing drivers on versions of Ubuntu 8.10 and older.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 
This page will tell you how to regress your version of Ubuntu with out reinistalling an older version of Ubuntu.
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)
This is the Envy NG home page, which will help to automagicly update your propritary drivers to your system.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

