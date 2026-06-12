---
title: "Ubuntu Studio Nvidia driver activated but not currently in use"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Moxid on 2011-05-14
So first time installing Ubuntu, I loaded it up wubi style in windows, standard amd64 version.  Had the same problem and installed via Additional Drivers, rebooted and Unity was working and my 2nd monitor was also working with Twinview.

Then I said ok, I'll install Ubuntu Studio 11.04 as I wanted the audio software all bundled in.  Now this time I installed the Nvidia binary X.org driver v 185 via the Ubuntu Software center.  Prior to installing this I did have mirrored monitors and did not have Unity running.  After installing I'm stuck down to 1 monitor and in additional drivers it states that Nvidia accelerated graphics driver is active but not in use.  I have googled the problem and also searched the forums and have not found a solution.  From the xorg.0.log it seems that the Nvidia driver did install properly, granted I couldn't say that for sure just because I'm new to linux.  

Any suggestions would be helpfull.  

I've tried removing and reinstalling from the Additional Drivers unsuccessfully.

---

### Post by wildmanne39 on 2011-05-14
> **Moxid said:**
> So first time installing Ubuntu, I loaded it up wubi style in windows, standard amd64 version.  Had the same problem and installed via Additional Drivers, rebooted and Unity was working and my 2nd monitor was also working with Twinview.

Then I said ok, I'll install Ubuntu Studio 11.04 as I wanted the audio software all bundled in.  Now this time I installed the Nvidia binary X.org driver v 185 via the Ubuntu Software center.  Prior to installing this I did have mirrored monitors and did not have Unity running.  After installing I'm stuck down to 1 monitor and in additional drivers it states that Nvidia accelerated graphics driver is active but not in use.  I have googled the problem and also searched the forums and have not found a solution.  From the xorg.0.log it seems that the Nvidia driver did install properly, granted I couldn't say that for sure just because I'm new to linux.  

Any suggestions would be helpfull.  

I've tried removing and reinstalling from the Additional Drivers unsuccessfully.
Hi, I read that this is a bug in natty and it is being worked on if I find more information I will post it here.

---

### Post by Moxid on 2011-05-15
So I take it that it might be better to install the 10.04 versioN?

---

### Post by wildmanne39 on 2011-05-15
> **Moxid said:**
> So I take it that it might be better to install the 10.04 versioN?

Hi, maybe, was it working in the last ubuntu version? With unity mine says the same thing as yours but I do not think it makes any difference sense the cube does not work in natty. However if you are having other problems like I was with my nvidia card driver, I had to go into additional drivers and choose the 173 driver the newer one created a lot of problems with unity.:)

---

### Post by wildmanne39 on 2011-05-15
> **Moxid said:**
> So I take it that it might be better to install the 10.04 versioN?

Hi, you can also log out and click on your name then at the bottom you will see a menu of what desktop you are logging into,switch to ubuntu classic and see if that helps.):P

---

### Post by Hedgehog1 on 2011-05-15
I also have this same message about my nvidia driver - but if Unity works, then Compiz works because Unity uses Compiz.

The bug that is reported is 'is says it is not being used, but it really is being used'.

If you look at the pictures here: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

There are all from my desktop with the cube and wobbly windows running in 'Ubuntu Classic' - and all while that silly error messages tells me it isn't being used.

Ahh... The joys of a new release with radical UI changes...

***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-15
> **Hedgehog1 said:**
> I also have this same message about my nvidia driver - but if Unity works, then Compiz works because Unity uses Compiz.

The bug that is reported is 'is says it is not being used, but it really is being used'.

If you look at the pictures here: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")

There are all from my desktop with the cube and wobbly windows running in 'Ubuntu Classic' - and all while that silly error messages tells me it isn't being used.

Ahh... The joys of a new release with radical UI changes...

***The Hedge***

:KS
Hi, thats what I thought to but I did not want to say that until I was sure.

---

### Post by wildmanne39 on 2011-05-16
> **Moxid said:**
> So first time installing Ubuntu, I loaded it up wubi style in windows, standard amd64 version.  Had the same problem and installed via Additional Drivers, rebooted and Unity was working and my 2nd monitor was also working with Twinview.

Then I said ok, I'll install Ubuntu Studio 11.04 as I wanted the audio software all bundled in.  Now this time I installed the Nvidia binary X.org driver v 185 via the Ubuntu Software center.  Prior to installing this I did have mirrored monitors and did not have Unity running.  After installing I'm stuck down to 1 monitor and in additional drivers it states that Nvidia accelerated graphics driver is active but not in use.  I have googled the problem and also searched the forums and have not found a solution.  From the xorg.0.log it seems that the Nvidia driver did install properly, granted I couldn't say that for sure just because I'm new to linux.  

Any suggestions would be helpfull.  

I've tried removing and reinstalling from the Additional Drivers unsuccessfully.

Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:)

---

### Post by muscule_boy on 2011-09-17
I am using Ubuntu 11.04 and prefer using the classic desktop with effects.  I have effects turned on such as wobbly windows and the desktop cube... and they seem to work fine.

I am confused because of the activated but not currently in use message on my Ubuntu 11.04 amd64 (Intel) desktop system.

The problem I see, is that the "Additional Drivers" window, opened from "System->Administration->Additional Drivers" menu option, shows two selections in the top box:

[COLOR="Blue"]   NVIDIA accelerated graphics driver (version 173)
 * NVIDIA accelerated graphics driver (version current) [Recommended][/COLOR]

When the second choice is selected the send box shows driver information such as "3D-accelerated proprietary graphics driver for NVIDIA cards, Required if you want to run Unity.  This driver...

At the bottom of the window (along with a "Remove" button:

 * This driver is activated but not currently in use    

So, I think the driver is being used since the NVIDIA X Server settings show (GPU = NVIDIA GeForce 9400 GT):

[INDENT]Operating System:       Linux-x86_64
NVIDIA Driver Version:  270.41.06[/INDENT]

I just wished the "Additional Drivers" window should show the actual version not just "version current", so I can confirm that the version shown on the "NVIDIA X Server Settings" window matches. 

It would also be nice if the "Additional Drivers" window actually indicated that the driver was in use rather than just "This driver is activated but not currently in use.".

Hopefully, the Ubuntu team can figure these minor problems out, but I think my driver is working. I do find it strange that I can not see the 270 version in the Synaptic Package Manager.

Oh, btw... I went to nvidia.com and tried to see what version of the driver it would suggest I install for my graphics card.. it indicated:

    **NVIDIA-Linux-x86_64-280.13.run**

So, I am a little confused by the message in my "Additional Drivers" window but assume that Ubuntu will soon get things fixed up for us NVIDIA users.  ;)

---

