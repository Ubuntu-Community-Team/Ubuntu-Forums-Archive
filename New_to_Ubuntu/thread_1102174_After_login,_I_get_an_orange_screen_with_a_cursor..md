---
title: "After login, I get an orange screen with a cursor......."
date: 2009-03-21
forum: New to Ubuntu
---

### Post by blandman3 on 2009-03-21
Hey guys, I have my LIVE CD in working condition, tried to install it - it was successful.  The only thing?..........

I put in my username and password, and just get an orange screen, the desktop isn't there, and I only have a cursor, what do I do?

I am new to ubuntu.

Also, how do you access the grub?  It won't let me do this, and what commands do I input so that I would be able to input and save the new boot parameters I need?

---

### Post by blandman3 on 2009-03-21
I can't access the failsafe modes either

---

### Post by blandman3 on 2009-03-21
Well, I finally was able to access GRUB and all, but I don't know what string of commands to use....

I have tried a combination of these (with or without some components):

noapic nolapic acpi=off pci=noacpi hw-detect/start_pcmcia=false netcfg/disable_dhcp=true xforcevesa

One time I got close with the following string:

hw-detect/start_pcmcia=false netcfg/disable_dhcp=true xforcevesa and i think with noapic at the end

it broke away from the orange screen, but just turned black with a cursor

Someone please help me!:guitar:

---

### Post by abn91c on 2009-03-21
```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by blandman3 on 2009-03-22
ok, where do I input those commands...literally?

I know how to get into nano by hitting ctrl alt F1, but is that where I input those commands-after I input my username and password?

---

### Post by blandman3 on 2009-03-22
what do these commands do if you don't mind me asking--I can clearly see they remove compiz, but will that mess ubuntu up?

---

### Post by Ms_Angel_D on 2009-03-22
> **blandman3 said:**
> ok, where do I input those commands...literally?

I know how to get into nano by hitting ctrl alt F1, but is that where I input those commands-after I input my username and password?

those commands will remove compiz, no it will not mess up ubuntu, but if  you wish to reinstall later you can.

You want just want to type those commands there after logging in then after entering them type exit to logout and use Ctrl+Alt+F7 to get to the desktop.

---

### Post by blandman3 on 2009-03-22
Thank you very much for the help.  I will check to see if it works, then I will update you.

Will I have to type this in everytime I want to run ubuntu?  probably not if I am saving it, huh?

---

### Post by Ms_Angel_D on 2009-03-22
> **blandman3 said:**
> Thank you very much for the help.  I will check to see if it works, then I will update you.

Will I have to type this in everytime I want to run ubuntu?  probably not if I am saving it, huh?

No you should only need to perform these steps once.

---

### Post by blandman3 on 2009-03-22
alrighty, that step worked!

I finally can access ubuntu after the login, the only problem is.........

there is nothing on my desktop,

is that normal?  I have the menu bars on top and the bottom.  I have the ability to put things on there, but I remember when running the live cd there were two shortcuts on my desktop.

---

### Post by Sef on 2009-03-22
First,  what is your video card, system specs, and make/model?

Second, was there any problems with the live cd?

Third, don't remove compiz-fusion yet; it may not be the problem.

Fifth, what version of Ubuntu are you using?

---

### Post by blandman3 on 2009-03-22
I don't know my video card, is that my graphics card?

I have a:

Compaq Presario SR1210NX
512 MB ram
80 GB HDD
Windows XP
intel celeron D 2.66 GHz 256 KB L2 CAche

In order to run the Live CD, I had to change a few boot commands by pressing F6 at the menu, twice and chose these options:

acpi=off noapic nolapic

after those options I hit esc, then typed:

hw-detect/start_pcmcia=false netcfg/disable_dhcp=true xforcevesa

although, I am pretty sure I didn't need xforcevesa

I hit enter, and was able to boot the CD, and it didn't give me a password screen.  This has worked everytime for the LIVE CD.

I have it installed also, but it wasn't getting past the login screen-just orange screen, so I pressed:

ctrl alt F1, got to GRUB, and input the login info then:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

and it worked!  now my system is updating, but isn't that just reinstalling everything I just deleted?

my graphics is intel(R)

---

### Post by blandman3 on 2009-03-22
ubuntu 8.10 intrepid ibex is what version I am using also

---

### Post by blandman3 on 2009-03-22
how do I mark a thread that I started solved?

---

