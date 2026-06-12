---
title: "disable temporarily WLAN and Bluetooth"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by sm0011 on 2009-02-11
how do i temporarily disable WLAN and Bluetooth at startup...??? i use ubuntu 8.1 on Acer extensa 4620 laptop. although there are two seperate switches to disable them after startup, is there anyway to do so with startup only....:confused:

---

### Post by sleepyjon on 2009-02-13
Many laptops have a switch for the wireless. If you don't have that, you could try:

```

ifconfig wlan0 down
[/clode]

place that in /etc/init.d/

run
[code]
sudo update-rc.d default 19

```

I'm not positive that will work, but according to this:

[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

> 
11.6 It looks as if Debian does not use rc.local to customize the boot process; what facilities are provided?

Suppose a system needs to execute script foo on start-up, or on entry to a particular (System V) runlevel. Then the system administrator should: 

Enter the script foo into the directory /etc/init.d/. 

Run the Debian command update-rc.d with appropriate arguments, to specify which runlevels should start the service, and which runlevels should stop the service. 

Consider rebooting the system to check that the service starts correctly (assuming that you've asked for it to be started in the default runlevel). Otherwise, manually start it by running `/etc/init.d/foo start'. 

One might, for example, cause the script foo to execute at boot-up, by putting it in /etc/init.d/ and running update-rc.d foo defaults 19. The argument `defaults' refers to the default runlevels, which means (at least in absence of any LSB comment block to the contrary) to start the service in runlevels 2 through 5, and to stop the service in runlevels 0, 1 and 6. (Any LSB Default-Start and Default-Stop directives in foo take precedence when using the sysv-rc version of update-rc.d, but are ignored by the current (v0.8.10) file-rc version of update-rc.d.) The argument `19' ensures that foo is called after all scripts whose number is less than 19 have completed, and before all scripts whose number is 20 or greater.


---

### Post by Kain000 on 2009-02-13
> **sm0011 said:**
> how do i temporarily disable WLAN and Bluetooth at startup...??? i use ubuntu 8.1 on Acer extensa 4620 laptop. although there are two seperate switches to disable them after startup, is there anyway to do so with startup only....:confused:


I'm not sure I undersand what your ultimate goal is here.

You just want to disable the WiFi and bluetooth for the boot process and have them ready once the system is loaded?

Or do you want to physically switch them off only to have to switch them on when you want them, 

or is it that you want to have them auto activate a certian ammount of time after boot?


if it's the physical switches those need to be configured in your laptop's BIOS screens.

there will be a tab someplace in the bios menus that has to do with the wifi bluetooth switches. 


On my dell it allows you to select what device the switch controls either the wifi or bluetooth or both.

if you need further help in the bios process just post back.

---

### Post by sm0011 on 2009-02-13
thank u so much for the reply.. 
i want wifi and bluetooth to be physically off when i boot and get enabled only when i switch them "on" from the two seperate switches i have on the laptop,one for bluetooth and other for wifi.

---

### Post by Kain000 on 2009-02-14
ahh alright, 

what you are looking for is in the BIOS menus.

If youve never entered the BIOS before you will need to be on the ball as with some systems they dont give you very long to decide lol.

so when you first boot your laptop there will tipically be a screen with the logo of what ever company made the motherboard.  it's at this screen that (again tipically) there is a diolouge that tells you to press (usually esc or F1 or delete) some key to enter the BIOS or sometiems it is called "setup"

this may take a boot or 3 to get right, (as you only have a few secs and cant try more than one key usually)

once in your BIOS menu you will see a lot of "sections"  each with sub menus dealing with their main menu.  ie: you would find the options for your battery and screen brightness under power mangement.

so check arround I have a dell laptop and I believe the options for my wifi/bluetooth switch were found under power mangement>extras or somthing like that.  I'll reboot in a min and tell you for sure.


somewhere in your BIOS you will find the section you are looking for and be able to set what will happen when you switch them on or off.


then save and reboot (usually F10) sometimes just esc and it should work like you want.

While you are in the menus tho, take a look arround, you can change alot about your system from these screens and it is a good thing to know what you can and cannot configure from inside your BIOS.

---

### Post by Kain000 on 2009-02-14
Alright, in my BIOS it is F2 to enter into it, and the wireless switch was under the main menu called "wireless"

---

