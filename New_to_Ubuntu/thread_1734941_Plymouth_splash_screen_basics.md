---
title: "Plymouth splash screen basics"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by dredmal on 2011-04-20
I am trying to learn how to change the splash screen when my pc boots. I am using Ubuntu 10.10 with Nvidia graphics. I am a linux noob but I do have a strong computer background

So far the best link I found was [_here_]("http://crashsystems.net/2010/04/changing-plymouth-themes/") for customizing the splash screen. Although it is for v10.04 not 10.10

I began to follow the steps on the site in my terminal attempting to install the same theme presented in the guide (plymouth-theme-solar) but I get an error because the 'solar' directory does not exist. 

I found the theme listed in the default repositories using the command provided on the site. I don't know how to turn that repository into the /lib/plymouth/themes/solar folder in order to continue with the guide.

Can anyone point me in the right direction to help me understand? The less reading the better, I've spent hours doing customizations I thought would take a few minutes.

Any help is greatly appreciated

---

### Post by LOIREE on 2011-04-20
Maybe this?
[http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/](http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/)

---

### Post by dredmal on 2011-04-20
Sorry that does not help me. Could you take another look at my issue and try again?

---

### Post by Jechem on 2011-04-20
You can install the plymouth-theme-solar from synaptic package manager(screenshot). Then do:

```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/solar/solar.plymouth 100
```

```
sudo update-alternatives --config default.plymouth
```

choose solar

or simply install the Plymouth Manager:

[http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812).

---

### Post by dredmal on 2011-04-20
Before I try the plymouth manager. Is it compatible with Ubuntu 10.10? The last customization software I installed did not work and I'm not aware of a way to check software compatibility specific to my distro.

Thanks for the clear and simple support. Your post is exactly what I was looking for I believe

---

### Post by Jechem on 2011-04-20
Yes it is compatible with 10.10. I've tried it the first time Mefrio released it. He has done more enhancements to it since. Read through the forum thread to know if some people had problems with it.

---

### Post by dredmal on 2011-04-20
I followed the instructions you provided and got the package installed and configured with no errors.

I rebooted my machine but nothing changed. I checked the config to make sure the solar theme was selected and it was. This is actually the second time I've tried to do this today and had no change in my splash screen.

It seems I'm doing everything correctly but nothing is changing. Do you have any more advice by chance?

I will try the plymouth manager application in the meantime to see if i have any luck with that.

Thanks for your help so far, your help was very clear and understandable.

---

### Post by dredmal on 2011-04-20
I downloaded the plymouth manager and installed it using my ubuntu software center and it placed a shortcut in my applications menu.

When I click on the plymouth manager menu item nothing happens.

I would like to avoid installing software at this point because everytime I install something it doesn't work and I end up needing support all over again.

thanks

---

### Post by Krytarik on 2011-04-20
You need to run
```
sudo update-initramfs -u
```
after choosing another splash.

You can find some more splashs at gnome-look.org, my favorite is this one:
[http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696](http://gnome-look.org/content/show.php/Ubuntu+sunrise+plymouth?content=129696)

I tried Plymouth Manager, but it didn't work for whatever reason.

Greetings.

---

### Post by dredmal on 2011-04-20
Thank you! I think that is going to solve my problem. I saw that command a few minutes ago and almost ran it on my own but was worried it would mess something up. I believe I will be marking this post as solved in a few minutes.

thanks again

---

### Post by dredmal on 2011-04-20
Still no change :(

I followed your instructions and rebooted and everything was the same.

I ran the config command again to triple check that 'solar' was selected. I then ran the command you suggested for a second time just in case and waited for the command to complete. I then did a full shutdown and turned my computer on again but it was still the same.

:( Is there anything I can do?

Thanks for the helpful and quick replies

---

### Post by Krytarik on 2011-04-20
Do you really see *a* Plymouth boot splash, usually the default purple one with the Ubuntu logo and white/red dots below it?

---

### Post by dredmal on 2011-04-20
Yes that is exactly what I see but I was considering it more pink than purple.

---

### Post by Krytarik on 2011-04-20
Like this?:
[http://i1-news.softpedia-static.com/images/news2/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-2.jpg](http://i1-news.softpedia-static.com/images/news2/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-2.jpg)

---

### Post by dredmal on 2011-04-20
yes exactly like that except mine seems to be brighter. same logo, same dots, same gradient

---

### Post by Krytarik on 2011-04-21
Yeah, depends on the chosen brightness of the monitor, obviously, mine is a bit brighter, too.

Try installing/choosing the one I linked to, of those at least I know that it works. But choose "100" instead of "200", and make sure to have "manual" selected, also with Solar.

---

### Post by dredmal on 2011-04-21
I followed your link and the instructions associated with it and had no problems but my splash screen is still the same.

A few details that may help:

I have the #4 theme selected (sunrise) and it is set to manual with a priority of 200.

My #1 theme also shows 'sunrise' but is set to auto and a priority of 200

The #2 and #3 themes are set to manual with a priority of 100

---

### Post by Krytarik on 2011-04-21
That's why I said "100", lower number means higher priority. But if you choose "manual" that shouldn't really matter.

Please post the output when you run:
```
sudo update-alternatives --config default.plymouth
```
In code-tags please, use the #-button in the editor therefore.

---

### Post by dredmal on 2011-04-21
oops i misread and thought you wanted me to set it to 200, i will fix that

---

### Post by dredmal on 2011-04-21
I changed it to 100 and ran the update-initramfs -u command but it still did not change

here is the output from my config:
 
```
There are 4 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                         Priority   Status
------------------------------------------------------------
  0            /lib/plymouth/themes/simple/simple.plymouth                   100       auto mode
  1            /lib/plymouth/themes/simple/simple.plymouth                   100       manual mode
  2            /lib/plymouth/themes/solar/solar.plymouth                     100       manual mode
  3            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth         100       manual mode
* 4            /lib/plymouth/themes/ubuntu-sunrise/ubuntu-sunrise.plymouth   100       manual mode

Press enter to keep the current choice[*], or type selection number: 

```

the simple.plymouth theme is a theme i created using a guide earlier today where i had the same result of no viewable changes

---

### Post by Krytarik on 2011-04-21
> **dredmal said:**
> oops i misread and thought you wanted me to set it to 200, i will fix that
I just noted it because the install instructions of it states "200".
> **dredmal said:**
> the simple.plymouth theme is a theme i created using a guide earlier today where i had the same result of no viewable changes
Please remove those, reselect one of the last installed splashs, and run "update-initramfs -u" again.

---

### Post by dredmal on 2011-04-21
how do i remove them? 

I will look for the solution to that myself to try and save you some time.

---

### Post by Krytarik on 2011-04-21
> **dredmal said:**
> how do i remove them? 

Oh, I thought you had to figure that already, in order to change the priority.

I guess this command will do, I didn't use it for a while:
```
sudo update-alternatives --remove default.plymouth /lib/plymouth/themes/simple/simple.plymouth
```

---

### Post by dredmal on 2011-04-21
sorry i am a linux noob, although i do understand computers very well and i'm comfortable with command line interfaces

when i changed the priority i simply reentered the same commands again and used 100 instead of 200

i ran the remove command you provided and it did not work 

here is my output:

```
update-alternatives: error: unknown argument `/lib/plymouth/themes/simple/simple.plymouth'

```

---

### Post by dredmal on 2011-04-21
i managed to remove the simple theme by running the command 'sudo nautilus' and navigating to the 'simple' folder and removing it.

i then ran the config command and selected 'sunrise'
next i ran the command sudo update-initramfs -u and rebooted
still no change

one thing i forgot to mention that i just remembered is:
At one point yesterday i had no splash screen and i found some webpage that instructed me on how to get it back. When I installed ubuntu it had the splash screen then i noticed it was missing one day.

---

### Post by Krytarik on 2011-04-21
I just tested the stated command, and it works. Usually, I would run this before removing the splash theme's directory, maybe that was the reason? Is it still listed there?

What guide did you follow then?

---

### Post by dredmal on 2011-04-21
I copied the remove command you provided and pasted it into my terminal and got the output shown above, i tried to get creative and modify it myself but that gave me the same error shown above.

After I removed the 'simple' folder it was not listed as an option when I ran the config.

When I noticed I had no splash screen, i found [_this link_]("http://ubuntuforums.org/showthread.php?t=1470876") and followed the instructions by the original poster and it fixed my problem.

I followed [_this link_]("http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html") to install the 'simple' theme.

Both of these events happened before I began this original post.

If you think it will be helpful I will gladly put the 'simple' folder back in it's original place and try the command you provided again. Just let me know. I fear it will not work however because I copied exactly what you posted the first time and got the error message that I provided above.

Thanks for all of your help so far, if you get tired of helping and decide to quit, i would appreciate it if you let me know so that i am not left hanging

---

### Post by Krytarik on 2011-04-21
Try this, to re-create the alternatives list:```

sudo rm /var/lib/dpkg/alternatives/default.plymouth
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth 100
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/solar/solar.plymouth 100
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-sunrise/ubuntu-sunrise.plymouth 100
```Then choose "ubuntu-sunrise" or "solar" again, run "update-initramfs -u", and reboot.

---

### Post by Jechem on 2011-04-21
> **dredmal said:**
> 
I followed [_this link_]("http://jechem.blogspot.com/2010/10/how-to-change-splash-screen-in-ubuntu.html") to install the 'simple' theme.

That was from my blog. Sorry it didn't work out right for you.:(

There are other themes that don't run right with some video cards.

edit: I'm just curious, are you using grub only or burg? Have you changed the config of grub/burg?

---

### Post by dredmal on 2011-04-21
I fell asleep in the middle of this last night, spent most of my day on it and wore out i guess.

I followed the most recent instructions from Krytarik but still no change. I am making sure to let the update-initramfs -u command finish before I close my terminal.

@Jechem I am using grub2. I modified it's background image, font and removed the memtest entry from the menu. I had no problems getting those changes to work.

I understand that nvidia video cards can cause issues and that is what i'm using. Do you think that is my problem? Wouldn't the 'simple' theme work even if it was? Is there something I can do to eliminate video as the possible culprit?

From my perspective, it seems as if nothing is happening. Although I do understand it could be rejecting my changes and reverting back to the default splash theme.

Could I install a super simple theme (since simple didn't work haha) just to prove or disprove video as my problem?

---

### Post by Jechem on 2011-04-21
If the plymouth is not accepted it defaults into a blank screen. 

Just choose the default ubuntu logo plymouth for now see if it works. 

Most of the fixes require setting a different resolution based on the big and ugly ubuntu plymouth(link on my signature). 

Usually my simple plymouth script works with nvidia graphics cards. That's the simplest I could make.  Sorry.:(

---

### Post by dredmal on 2011-04-21
The default plymouth ubuntu logo is working and has been showing since I resolved my black screen issue at first.

I followed the link in your signature but it doesn't seem to match my issue. My resolution seems fine, but I can't change the image.

Are you suggesting that I try to change the resolution anyway?

---

### Post by Jechem on 2011-04-21
no don't change the resolution if it is working properly for you.

---

### Post by Jechem on 2011-04-21
you can give this a try:

[http://internauta2000.deviantart.com/art/Ubuntu-10-10-Plymouth-Splash-174707078]("http://internauta2000.deviantart.com/art/Ubuntu-10-10-Plymouth-Splash-174707078")

it's a nice plymouth theme i use.

---

### Post by Krytarik on 2011-04-21
Actually, even if there were issues with your video card, with the splash theme set to "manual", there were either (a) graphical glitches, (b) the splash wouldn't load at all, or (c) Plymouth crashes while trying to do so.

To really rule out the video, install the splash "ubuntu-text" and try it:
```
sudo apt-get install plymouth-theme-ubuntu-text
```And, more importantly, please post the outputs of these commands, after selecting anything else than "ubuntu-logo":
```
ls -al /lib/plymouth/themes/default.plymouth
ls -al /etc/alternatives/default.plymouth
```Also, you could try reinstalling "plymouth":
```
sudo apt-get install --reinstall plymouth
```

---

### Post by dredmal on 2011-04-21
> **Jechem said:**
> you can give this a try:

[http://internauta2000.deviantart.com/art/Ubuntu-10-10-Plymouth-Splash-174707078]("http://internauta2000.deviantart.com/art/Ubuntu-10-10-Plymouth-Splash-174707078")


i personally don't see how trying this theme will help me when i've tried 3 other themes, i'm going to avoid this suggestion without understanding how it can help me solve and understand my problem

@krytarik how will installing a text theme rule out video? i'm fine with doing this but i'd like to understand what i'm doing before i do it.
after i install the text theme how do i go back to the way it was before?

what do the ls -al commands do?

also, can reinstalling plymouth put me at risk of not being able to boot? what are the risks of reinstalling?

sorry i'm not trying to be hard headed i am simply afraid of blindly entering these commands with no idea of what the outcome could be. i've had alot of problems just trying to accomplish a simple task and i'm trying to take caution and learn more in the process

---

### Post by Krytarik on 2011-04-21
> **dredmal said:**
> i personally don't see how trying this theme will help me when i've tried 3 other themes, i'm going to avoid this suggestion without understanding how it can help me solve and understand my problemI wouldn't do that either.
> **dredmal said:**
> 
@krytarik how will installing a text theme rule out video? i'm fine with doing this but i'd like to understand what i'm doing before i do it.*Jechem* pointed to the possibility of insufficient driver combatibility. But we know that the default splash runs just fine (with the framebuffer workaround). So, to be sure that its really not related to a driver issue, we need to try one splash theme that is either comparable with the default splash, or is even more simple, in terms of graphics.
> **dredmal said:**
> after i install the text theme how do i go back to the way it was before?Just by running the commands you already know too good.
> **dredmal said:**
> 
what do the ls -al commands do?They just list the specified files, with all details, in our case the interesting part is their symlink target. At my system the output is this:
```
krytarik@krytarik-desktop:~$ ls -al /lib/plymouth/themes/default.plymouth
lrwxrwxrwx 1 root root 34 2011-04-04 16:27 /lib/plymouth/themes/default.plymouth -> /etc/alternatives/default.plymouth
krytarik@krytarik-desktop:~$ ls -al /etc/alternatives/default.plymouth
lrwxrwxrwx 1 root root 53 2011-04-04 16:27 /etc/alternatives/default.plymouth -> /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
```
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
> **dredmal said:**
> 
also, can reinstalling plymouth put me at risk of not being able to boot? what are the risks of reinstalling?No, not really. Plymouth is really just the boot splash, one could even disable/remove it at all without affecting the wider system.
> **dredmal said:**
> 
sorry i'm not trying to be hard headed i am simply afraid of blindly entering these commands with no idea of what the outcome could be. i've had alot of problems just trying to accomplish a simple task and i'm trying to take caution and learn more in the processI do understand this, and I'm perfectly fine with it. A lot of people are spewing out commands here without even knowing for theirselves what they do, obviously.

---

### Post by dredmal on 2011-04-21
i ran the provided command to install the text theme and then ran 
sudo update-alternatives --config default.plymouth in order to select it as my theme but it is not listed as an option

do i have to use another method to use this theme?

---

### Post by Krytarik on 2011-04-21
> **dredmal said:**
> i ran the provided command to install the text theme and then ran 
sudo update-alternatives --config default.plymouth in order to select it as my theme but it is not listed as an option
I was thinking -based on some guides about package based install- that it runs the install command itself, apparently not. And I didn't remember what I needed to do to install it. So, just install it manually as an alternative, like the others:
```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth 100
```
It seems like it's because it usually serves as fallback option, and is installed to another alternative list, "text.plymouth".

---

### Post by dredmal on 2011-04-21
I got the text theme installed ran the config to select it and ran the initramfs command and rebooted. it still looks the same 

But i did notice one piece of information that I incorrectly stated before. What I was calling the ubuntu logo was actually just the text 'ubuntu 10.10' I'm rather embarrassed that I didn't notice that before. It still has the pink background and the red/white dots but the logo itself is plain text, not an image. I'm terribly sorry for any time this oversight may have wasted.

Does this mean I have been using a text theme the entire time? Does this point to the resolution issue? Should I reinstall plymouth?

Sorry once again for making such a silly mistake in my observation. I expect more from myself and I believe I have simply been glazing over when I see that pink color everytime I think I fixed it.

---

### Post by Krytarik on 2011-04-21
> **dredmal said:**
> 
Does this mean I have been using a text theme the entire time?Yes it does, apparently. That's why I even posted a screenshot, there is indeed a markedly difference between the graphical splash and the text splash, I know since I tested it once. Anyway.
> **dredmal said:**
> 
Does this point to the resolution issue? Should I reinstall plymouth?
It does point to a well-known driver issue that may occur with proprietary drivers. Reinstalling "plymouth" wouldn't help here. Try these workarounds:

1.) Readme of the Plymouth boot splash (/usr/share/doc/plymouth/README.Debian):
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

For nVidia and ATI users, the default "nouveau" and "radeon"
drivers are Kernel Mode Setting enabled, but do not always
provide 3D capability at the current time. By switching to
using the restricted/non-free nvidia-glx or fglrx drivers,
you will gain 3D capability at the loss of a high-color
splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
/etc/default/grub
sudo update-grub

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u2.) [http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/](http://mikebeach.org/2010/06/nvidia-proprietary-drivers-and-low-resolution-plymouth-splash-screen/)

---

### Post by Learning Linux 2011 on 2011-04-22
> **Krytarik said:**
> [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
No, not really. Plymouth is really just the boot splash, one could even disable/remove it at all without affecting the wider system.



How can I disable it?

I'm just jumping into this thread and I have been trying to change the plymouth boot/splash screen as well, and I can't seem to figure it out either.  

I basically just wanted to change the color from purple to something else, but I can't seem to do it.

I edited the ubuntu-logo.script file to change the colors, saved it and tried running some of the commands listed here, but nothing sticks.

This seems unreasonably complicated just trying to change the boot screen.  Maybe disabling it would be better.

---

### Post by Claus7 on 2011-04-22
Hello,

I just jump in to this very interesting discussion to say that:
if you get the "textish" ubuntu logo screen while booting, then in order to change that, whatever you might try, won't work, except if you try to fix the resolution of the plymouth logo. Only then you will be able to see a change on the theme while booting.

There are many scripts on the net (I suppose that someone has posted here some links on the very first posts), which will do such a work and will make that plymouth theme look very nice.

Since the OP found out that the case was different than first thought, I think that the OP has a lot of things to reconsider and test again. 

Regards!

---

### Post by Learning Linux 2011 on 2011-04-22
Anybody know what those *.so files in /lib/plymouth are?  Can they be edited?  I think *.so files are "shared object" DLL type files.  They look important and maybe they need to be changed somehow.

Or maybe I am barking up the wrong tree and the startup logo can't be edited by hand.

---

### Post by Krytarik on 2011-04-22
@Learning Linux 2011: Are you, too, getting the text splash, the OP is getting, and *Claus7* is referring to?

See here on how to manually change the background colors of the graphical (!) Plymouth boot splash, I tested it, and it works:
[http://ubuntuforums.org/showthread.php?p=10561873#post10561873](http://ubuntuforums.org/showthread.php?p=10561873#post10561873)

To disable the Plymouth boot splash at all:
1.) modify the options of "GRUB_CMDLINE_LINUX_DEFAULT" in the file "/etc/default/grub":

[LIST]
[*]remove the option "splash" to only disable the splash
[*]remove the option "quiet" to also enable the output during the boot process
[/LIST]
 2.) run:
```
sudo update-grub
```[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20(file)]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")

---

### Post by Krytarik on 2011-04-22
> **Learning Linux 2011 said:**
> Anybody know what those *.so files in /lib/plymouth are?  Can they be edited?  I think *.so files are "shared object" DLL type files.  They look important and maybe they need to be changed somehow.

Or maybe I am barking up the wrong tree and the startup logo can't be edited by hand.
Leave those alone! They are part of the Plymouth app, and not of any theme.

---

### Post by Krytarik on 2011-04-22
This is another guide, on how to set only a background image as the Plymouth boot splash:
[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by Claus7 on 2011-04-23
Hello,

> **Krytarik said:**
> @Learning Linux 2011: Are you, too, getting the text splash, the OP is getting, and *Claus7* is referring to?...


Just to make the thinks a little bit clearer:
when I'm reffering to "textish" splash ubuntu logo I'm referring to the one named:
textish_ubuntu_splash.png
which is just text!

On the other hand exists the text based splash which is way more polished than the first one:
ubuntu-lucid-splash.png

And the magnificent ubuntu sunrise sunset which is among the best looking as *Krytarik* proposes as well.

Regards!

---

### Post by Krytarik on 2011-04-23
@Claus7: Thanks for the direct comparison, that illustrates it quite well!

In fact, I'm back now at the default splash, because "Ubuntu Sunrise" takes sometimes too long to show up at all at boot (actually it is because the splash newly is getting aborted by an error message about the firmware of my TV-card). As an interim I used the default splash with a black background, like described by the other post I linked to. Not bad, too, but a bit boring. =)

---

### Post by Learning Linux 2011 on 2011-04-23
> **Claus7 said:**
> Hello,



Just to make the thinks a little bit clearer:
when I'm reffering to "textish" splash ubuntu logo I'm referring to the one named:
textish_ubuntu_splash.png
which is just text!

On the other hand exists the text based splash which is way more polished than the first one:
ubuntu-lucid-splash.png

And the magnificent ubuntu sunrise sunset which is among the best looking as *Krytarik* proposes as well.

Regards!

Yes, I am referring to the "textish" looking one.  The first one out of the three that Claus7 posted there.


I have gone in to edit the ubuntu-logo.script and change the colors, but that didn't seem to actually do anything.

I'm beginning to think that the "textish" boot splash isn't plymouth at all. Maybe it is part of something else?  Is there a way to edit the purple text-ish looking splash?  Like change the color or change the word "Ubuntu" to something else?  Is the textish-looking still called "Plymouth", or is it called something else?  
Is that in the /lib/plymouth folder, or somewhere else?  Because I have edited some of the things in the Plymouth folder and nothing changes.

---

### Post by Krytarik on 2011-04-23
The text splash is, too, handled by Plymouth, and it seems like it's just controlled by the file "/lib/plymouth/ubuntu-text.so", so no, it doesn't seem like one can modify the text splash.

---

### Post by Claus7 on 2011-04-23
Hello,

> **Krytarik said:**
> @Claus7: Thanks for the direct comparison, that illustrates it quite well!

In fact, I'm back now at the default splash, because "Ubuntu Sunrise" takes sometimes too long to show up at all at boot (actually it is because the splash newly is getting aborted by an error message about the firmware of my TV-card). As an interim I used the default splash with a black background, like described by the other post I linked to. Not bad, too, but a bit boring. =)

there is some time now that I had fixed plymouth as I did not like this textish ubu logo. Unfortunately, I cannot provide any help about the tv-card issue I'm afraid..

> **Learning Linux 2011 said:**
> Yes, I am referring to the "textish" looking one.  The first one out of the three that Claus7 posted there.


I have gone in to edit the ubuntu-logo.script and change the colors, but that didn't seem to actually do anything.

I'm beginning to think that the "textish" boot splash isn't plymouth at all. Maybe it is part of something else?  Is there a way to edit the purple text-ish looking splash?  Like change the color or change the word "Ubuntu" to something else?  Is the textish-looking still called "Plymouth", or is it called something else?  
Is that in the /lib/plymouth folder, or somewhere else?  Because I have edited some of the things in the Plymouth folder and nothing changes.

Now, since you have that textish looking ubuntu logo, that means that no matter what you do, you won't be able to see any descent ubuntu plymouth logo, unless you fix the resolution problem of plymouth. Even if you do not notice it, plymouth uses a resolution for displaying the logo. If you have different resolutions for your Desktop and grub and so on, the boot-up process delays a lot (this might be a fix for *Krytarik* too, yet I'm not so sure), and in the end results in this low quality logo.

For this to be polished, these links I provide give a lot of info on how to fix this issue and at least to be able to see the more polished ubuntu logo. If you are able to do so, then you can proceed in installing and enjoying a different one. It has been a way to long, and I do not remember exactly the steps I had followed to solve my issue. Most of them were taken from those two links I provide though.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Hope this helped,
Regards!

---

### Post by Claus7 on 2011-04-23
Hello,

> **Krytarik said:**
> The text splash is, too, handled by Plymouth, and it seems like it's just controlled by the file "/lib/plymouth/ubuntu-text.so", so no, it doesn't seem like one can modify the text splash.

I would not try to mess with this one as well...

Also, one other thing: since the OP has messed with plymouth, a nice thing would be, before trying anything else, just to reinstall any plymouth libraries, so as whatever the OP tries from now on to avoid messing with any tweaks that might still exist.

Regards!

---

### Post by Krytarik on 2011-04-23
> **Claus7 said:**
> 
Also, one other thing: since the OP has messed with plymouth, a nice thing would be, before trying anything else, just to reinstall any plymouth libraries, so as whatever the OP tries from now on to avoid messing with any tweaks that might still exist.

As I understand it, the OP has only fixed the non-existent splash by applying the 'FRAMEBUFFER=y' workaround, so that didn't touch the Plymouth files at all.

---

### Post by Learning Linux 2011 on 2011-04-23
> **Krytarik said:**
> The text splash is, too, handled by Plymouth, and it seems like it's just controlled by the file "/lib/plymouth/ubuntu-text.so", so no, it doesn't seem like one can modify the text splash.

Ahh, ok, well that explains alot, thanks.  At least that explains why nothing I was trying was working.

I suppose I could get the source code, edit it and recompile it.

---

