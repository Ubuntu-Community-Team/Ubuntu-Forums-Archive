---
title: "confused about unity on 11.04"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by marinara on 2011-08-30
hi.  I've been loving ubuntu 11.04 since april.  
I installed it on VMware.

I'm wondering if I have unity or not.
I can turn unity off, with the ccsm, (compiz settings manager)
but when I turn it on, I dont have the launcher, panel, manager.

so I guess, i'm in like "no man's land" unity is neither completely installed or completely uninstalled?

All i know is it looks like unity.  please inform me if I'm running unity or not.
Thanks,
karl

---

### Post by Andrethe7th on 2011-08-30
My phsycic powers detect pain and suffering... you are running unity.  Unless of course you selected the something else from the drop down menu there before you logged in.  In which case you would be running the classic gnome desktop or whatever you selected.

---

### Post by BlinkinCat on 2011-08-30
Why would you turn it off if you want it?

Posting a screen shot could help -

---

### Post by jtarin on 2011-08-30
> **BlinkinCat said:**
> Why would you turn it off if you want it?

Posting a screen shot could help -
11.04....one of those love/hate things.:lolflag:

---

### Post by anewguy on 2011-08-30
Move your mouse to the far left - do some options "scroll in" from the left when you do so?  Does anything show on your screen?  Note that things like the Applications/Places/System menu won't show in Unity by default.  

Dave ;)

---

### Post by marinara on 2011-08-30
There is no launcher when i move my mouse to the left screen edge.  I'm sure there never was.  

I think it might be classic gnome, but then why does "compizconfig settings manager" say the Unity plugin is enabled?  Since I'm running in VMware, i'm sure it's not using the unity 3d.

It's heartening to see that i've confused more people. :)

[IMG]http://img6.imagebanana.com/img/nf20jnoi/Workspace1_001.png[/IMG]

---

### Post by BlinkinCat on 2011-08-30
Sure looks like "classic" - maybe in VM graphics not recognized as suitable for Unity - maybe?

---

### Post by BlacqWolf on 2011-08-30
My guess would be that VMware isn't virtualising a suitable video card, or for Unity to recognize it as a suitable card, you need to install VMware Tools (a set of drivers and such to improve support for the virtual hardware) for the Unity environment to work.
 
[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)
 
If you install VMware Tools, it should work as normal. Install VMware Tools, reboot, make sure Unity (or the option may be 'Ubuntu,' as BlinkinCat said) is selected from the dropdown menu on the login screen, and it should log you into Unity.
 
If it doesn't work, try tinkering with VMware's graphics settings, such as raising video memory, enabling 3D accelleration (3D accelleration is required for Unity), etc. I've never used VMware, so I don't know what options it provides.

---

### Post by BlinkinCat on 2011-08-30
> **BlacqWolf said:**
> make sure Unity is selected from the dropdown menu on the login screen, and it should log you into Unity.

I believe it is called Ubuntu in drop down menu - I think! - ;)

---

### Post by BlacqWolf on 2011-08-30
> **BlinkinCat said:**
> I believe it is called Ubuntu in drop down menu - I think! - ;)
 
It's been a while since I looked, but I think it is. Thank you for that, I've edited my post.

---

### Post by anewguy on 2011-08-31
Definitely Ubuntu Classic (Gnome).  As others have suggested, it appears VMWare didn't set up a suitable pseudo video adapter.  I know the VirtualBox has the "extras" you install that included updated video - does VMWare have anything like that?  If not, perhaps you should give VirtualBox a try in the case, install the additions, and see if it makes any difference.

Dave ;)

---

### Post by marinara on 2011-09-01
> **anewguy said:**
> Definitely Ubuntu Classic (Gnome).  As others have suggested, it appears VMWare didn't set up a suitable pseudo video adapter.  I know the VirtualBox has the "extras" you install that included updated video - does VMWare have anything like that?  If not, perhaps you should give VirtualBox a try in the case, install the additions, and see if it makes any difference.

Dave ;)
thank you dave.  I think you're right, my ubuntu is classic.

i've installed VMware tools into VMWare player, and the video seems to work (i can switch resolutions for the vm in VMware player)  but it doesn't seem to give me 3d acceleration, and I suppose that's why I don't have the option to run Ubuntu unity.

thanks again

---

### Post by coffeecat on 2011-09-01
> **marinara said:**
> i've installed VMware tools into VMWare player, and the video seems to work (i can switch resolutions for the vm in VMware player)  but it doesn't seem to give me 3d acceleration, and I suppose that's why I don't have the option to run Ubuntu unity.

I have only a little experience of VMWare Player, but when I tried it I couldn't get the 3d acceleration needed for Unity even with VMWare Tools added. As others have suggested, try VirtualBox. With the guest addons installed in the guest machine you should be able to run the Unity desktop.

---

### Post by narasi on 2011-09-01
I dont think you will be needing 3d acceleration to run Unity... Did you try choosing the version "unity 2d" from the login page?

---

### Post by coffeecat on 2011-09-01
> **narasi said:**
> I dont think you will be needing 3d acceleration to run Unity... Did you try choosing the version "unity 2d" from the login page?

You need 3d acceleration to run Unity - it's a compiz plugin. And the OP will need to install the unity-2d package before they can run Unity 2d from the log in.

---

