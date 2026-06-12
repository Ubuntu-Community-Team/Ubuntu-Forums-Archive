---
title: "Jaunty - video drivers, mouse configuration"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by MaxVK on 2009-05-11
Hi, I'm having a few problems with Jaunty.

1)
I have an NVIDIA GFX card, but for some reason something called 'Jockey' keeps crashing when I try to enable the restricted drivers. Iv read a bunch of posts about rebooting and giving the servers time etc, but Iv been rebooting and giving them time for about 4 hours and I'm concerned because my router lights don't even flash when this is supposed to be trying to contact the servers. 
Is there any update on this situation (assuming that it *is* the servers)?
NOTE: I tried this while I was typing, and Jockey has just crashed for something like the 30th time since I installed this morning. What is Jockey, and why does it crash all the time?

2)
I have a Logitech Marble Mouse (Its a trackball). It has four buttons that used to be configured in the xorg.conf. Apparently this is no longer the case, and xorg.conf is ignored while something called 'Hal' has taken control.
Iv followed a bunch of tutorials to get my mouse working properly with Jaunty and 'Hal', but so far none of the files I have edited have done anything at all.
Iv used 'xinput' and my mouse shows in there as "ImExPS/2 Logitech Explorer Mouse", so Iv tried using that ID as well, but to no avail.

3)
I have a Microsoft Natural Ergonomic Keyboard 4000. It was working pretty well before, but in Jaunty I cant find anywhere to edit the control keys that cover the top of the keyboard - Most of these used to work according to my own configuration. Apparently 'Hal' cant handle this, and xinput says that there are two of these keyboards present.
Any ideas about setting up the control keys on the keyboard and/or sorting out 'Hal' so that it knows that there is only one keyboard?

4)
For reasons that escape me entirely (this is a fresh install after all), the CTRL + ALT + Backspace keys no longer log me out. Is this by design or is something else likely to be wrong?

As it stands right now the machine is all but unusable. The graphics are insanely slow without the restricted drivers, and doing almost anything with the mouse or keyboard (outside of simply right/left clicking or standard typing) is impossible.

I am at the point where I should be installing some apps, but I'm not going to bother if I'm going to have to re-install another version of Ubuntu to make things work properly.

Anyone have any idea (about any of this!)

Cheers

Max

---

### Post by Didius Falco on 2009-05-11
> **MaxVK said:**
> Hi, I'm having a few problems with Jaunty.

1)
I have an NVIDIA GFX card, but for some reason something called 'Jockey' keeps crashing when I try to enable the restricted drivers. Iv read a bunch of posts about rebooting and giving the servers time etc, but Iv been rebooting and giving them time for about 4 hours and I'm concerned because my router lights don't even flash when this is supposed to be trying to contact the servers. 
Is there any update on this situation (assuming that it *is* the servers)?
NOTE: I tried this while I was typing, and Jockey has just crashed for something like the 30th time since I installed this morning. What is Jockey, and why does it crash all the time?

2)
I have a Logitech Marble Mouse (Its a trackball). It has four buttons that used to be configured in the xorg.conf. Apparently this is no longer the case, and xorg.conf is ignored while something called 'Hal' has taken control.
Iv followed a bunch of tutorials to get my mouse working properly with Jaunty and 'Hal', but so far none of the files I have edited have done anything at all.
Iv used 'xinput' and my mouse shows in there as "ImExPS/2 Logitech Explorer Mouse", so Iv tried using that ID as well, but to no avail.

3)
I have a Microsoft Natural Ergonomic Keyboard 4000. It was working pretty well before, but in Jaunty I cant find anywhere to edit the control keys that cover the top of the keyboard - Most of these used to work according to my own configuration. Apparently 'Hal' cant handle this, and xinput says that there are two of these keyboards present.
Any ideas about setting up the control keys on the keyboard and/or sorting out 'Hal' so that it knows that there is only one keyboard?

4)
For reasons that escape me entirely (this is a fresh install after all), the CTRL + ALT + Backspace keys no longer log me out. Is this by design or is something else likely to be wrong?

As it stands right now the machine is all but unusable. The graphics are insanely slow without the restricted drivers, and doing almost anything with the mouse or keyboard (outside of simply right/left clicking or standard typing) is impossible.

I am at the point where I should be installing some apps, but I'm not going to bother if I'm going to have to re-install another version of Ubuntu to make things work properly.

Anyone have any idea (about any of this!)

Cheers

Max

Greetings!

I see you've already taken care of #1.

2. Have a read through this for possible solutions: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/313148](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/313148)

3. *Possible* solution. I don't know, I use a 3$ keyboard. <G>

[http://ubuntuforums.org/showpost.php?p=6753327&postcount=164](http://ubuntuforums.org/showpost.php?p=6753327&postcount=164)

4. Canonical took it out on purpose, but there are two ways to restore it. You can go to **Synaptic** and install the **DontZap** package, or you can add the following to you xorg.conf file, located at /**etc/X11/xorg.conf** - you have to do it as root.

```
Section “ServerFlags”
Option “DontZap” “false”
EndSection
```

Regards,

Didius

---

### Post by MaxVK on 2009-05-11
Ah, now its good to know that I can do that as a last resort, but Id like to try and get both the mouse (trackball) and the keyboard working with the Hal thing before I go that far.

I'm thinking (hoping) that either I'll come up with something myself, or someone else will.

Anyway, cheers for that info - I'll log it for use later on if I cant get this sorted out by myself.

cheers

Max

---

### Post by MaxVK on 2009-05-13
Just an update:

**Problem one - Restricted drivers manager never installs NVIDIA drivers**
I fixed this by accident and made a post about it: [Jaunty NVIDIA driver install error - Fixed?]("http://ubuntuforums.org/showthread.php?p=7258123")
Basically it happened like this: I was installing some bits and bobs and one of the things made the system ask for the CD. I put this in the drive and things were installed, but before I removed it I tried the restricted drivers manager again.

Usually I just get a progress bar that sits at zero until an error about Jockey crashing pops up and thats the end of it all. This time however, the CD spun up and the drivers were installed with no problem.

I'm thinking that perhaps the drivers installer forgets to ask for the CD and then just sits there until there is a time out. Anyway, it worked for me!

**Problem two: Logitech Marble Mouse**
Iv used this for ages in Ubuntu and I always have the buttons set in a specific way so that the smaller left button, when held, allows scrolling the page. By default this was set to Web page back.

Apparently editing xorg.conf does not work (I can confirm that) because Ubuntu is now using HAL instead.

I followed instructions to create the following file:
```
/etc/hal/fdi/policy/mouse-wheel.fdi
```
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="ImExPS/2 Logitech Explorer Mouse">
      <merge key="input.x11_options.Buttons" type="string">5</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```

Note that I got the name "ImExPS/2 Logitech Explorer Mouse" from typing:
xinput list
For some reason my mouse is not found by its correct name, but the button configuration seems to work fine. Perhaps this is of use to someone else too.

**Problem three remains a problem**
**Problem four** was answered by Didius previously:
> Canonical took it out on purpose, but there are two ways to restore it....

Thats it. Once the keyboard is setup as I like it Ill post information about that too.

Max

---

