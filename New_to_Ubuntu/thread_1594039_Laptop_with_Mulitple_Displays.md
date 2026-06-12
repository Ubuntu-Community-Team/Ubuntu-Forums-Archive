---
title: "Laptop with Mulitple Displays"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by jojarth on 2010-10-11
Hello all,

After years and years of being a Windows user, my company wants to start exploring Linux. My job is to figure out if we can implement it. A buddy of mine who's company runs on Linux pointed me to Ubuntu as a great starting point. 

Using Virtual Box inside Windows 7, I found that most of the apps that I use can work with little or no configuration, either natively in Ubuntu, or with some WINE configuration. So, I backed up my hard drive and decided to give it a run my only OS (so I can't go running back to Windows if things don't work out).

The biggest problem I ran into is my monitors. I can't seem to figure out how to get them to detect the way I do in Windows. Please bear in mind that pretty much all I have done was install a VM of Ubuntu 10.04 (64bit), install the guest additions, install WINE, and start testing apps. I have very little configuration experience. Here is a break down of the day, maybe you can help me?

Laptop - Elitebook 8740W with the Quadro 3800M. Using the current Version (not beta) of the NVIDIA accelerated graphics driver. Although I did all my testing in 10.04, I am running the 64 bit version of 10.10. I am only worried about my monitors, as all my other peripherals work fine. 

My monitor at home is an ACER  LCD that does 1920x1080.
My monitors at work are 1 ACER and 1 ASUS that both do 1920x1080.
My laptops display pushes 1920x1200.

I am using the NVIDIA X Server settings to change my displays around. With the exception of travelling, I keep my laptop lid closed. 

Work - Docking station with 2 displays attached. My laptop lid is shut, my laptop is docked. The power button on the dock is pressed. In windows, the monitors come right up, in the configuration I used with them last.  In Ubuntu, blank. I have to open the laptop lid and manually configure them. Hopefully when I left home, I remembered to switch back to my laptop display, otherwise I need to hard boot my laptop to get the displays to kick in.

Home - Small setup that includes 1 external monitor, The laptop lid is closed, and I work off just the external monitor. In windows, I tapped the power button before shutting the lid, then the monitor would switch over to the external. In Ubuntu, I again have to configure it. Oh, hopefully I remembered to switch back to the laptop display before I left work, otherwise I have to hard power the computer to get the displays.

Travel - Use the laptop display, only hopefully I remembered to switch to it before I left home or work, otherwise I have to power cycle to get it back to the main display. 

Like I said, in Windows 7, all I did was plug\unplug\dock\undock and it detected my monitors just fine, and the right resolutions and where they where when I last used them. I understand that Ubuntu probably won't handle switching monitors as slick as Windows does, and I am not adverse to a few extra key-clicks. However, I can't figure it out. Please help? Thanks!

---

### Post by HermanAB on 2010-10-12
Howdy,

Modern displays use Plus and Pray technology.  The Xorg windowing system exchanges PnP messages with the screen just before you log in.  So to get the external screens to work right, you either need to plug them in before you power up or you may need to press ctrl-alt-backspace to restart Xorg say a prayer to the computer gods and and log in again.

Linux also supports 3 methods of handling multiple screens:
Clone (The default)
Twinview (Nvidia)
Xinerama (extended desktop)

Getting all methods to work may also be a bit of an adventure.

Finally, bear in mind that a virtual machine uses the display system of the host machine, so if you haven't got it configured and working in the host, then it is not going to work in the VM.

---

