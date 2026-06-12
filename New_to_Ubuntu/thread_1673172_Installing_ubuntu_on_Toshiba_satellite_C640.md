---
title: "Installing ubuntu on Toshiba satellite C640"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by nafi27 on 2011-01-22
Hi all :)
I'm totally new to the world of linux..
my problem is i got new toshiba satellite c640 with windows 7 installed on it..
i wanted to install ubuntu 10.10 on this machine but it looks like the kerenl got stuck in this line[COLOR=Blue]
[/COLOR][COLOR=Blue]Kernel_thread_helper+0x6/0x10[/COLOR]
i did some googling around to find out what is this problem .. but i couldn't find any solution that work's for me..
pls guys any help will be much appreciated

---

### Post by zeroseven0183 on 2011-01-22
I've looked into the web for information about your laptop and it seems that it's 64-bit. Can you confirm if this is correct?

You probably installed the 32-bit Ubuntu. You can download the 64-bit version.

---

### Post by nafi27 on 2011-01-22
hi there ..
thanks for the quick reply :)..
yup i downloaded the 32 ubuntu version ..but i don't know if my machine is 64 or 32 bit .. i hope if you can show me a way so i can figure that out ...
in addition the windows 7 that i have is 32 bit O/S
so what do you advise me to do ?

---

### Post by nafi27 on 2011-01-22
i'm downloading ubuntu 64 bit version now..once i try it i will let you know the results ..thanks

---

### Post by nafi27 on 2011-01-23
> **zeroseven0183 said:**
> I've looked into the web for information about your laptop and it seems that it's 64-bit. Can you confirm if this is correct?

You probably installed the 32-bit Ubuntu. You can download the 64-bit version.

dear sir .. i have downloaded the 64 version .. and try to install it ..it's still the same..the same area got stuck in ..[COLOR=Blue]Kernel_thread_helper+0x0/0x10[/COLOR]
any suggestions ?

---

### Post by Quackers on 2011-01-23
There are some things you can try.
Have you checked the MD5SUM of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that checks out, whilst booting from the cd, press the Esc key. This should bring up a different screen. Choose the Language then ok that screen. On the next screen you should see some options. Choose the one that checks the cd for errors.

It seems that your problem can be caused by a hardware issue. On that same screen (after the cd check has been run) press F6 and you should see some options appear.
Try any that mention acpi or apic (like acpi=off, or noapic) if they exist (not too sure). 
The thread below may give you some ideas
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by nafi27 on 2011-01-23
thanks a lot .. i will try it and let you know

---

### Post by HermanAB on 2011-01-23
Toshibas usually require these kernel parameters:
nomodeset nolapic acpi="Linux"

---

### Post by nafi27 on 2011-01-23
hi again..
ive tried your suggestions..and i was able to do two things.
first .. i was able to run ubuntu from the CD ..browse the files ..using internet .. listen to songs.
secondly .. i installed ubuntu successfully on my machine using the options in the F6 configuration menu..
but after i finished the installation .. im not able to boot to the  system from my harddisk..when it start booting.. it get stuck with the  same message i showed you guys in the previous replies..
did i do anything wrong ??.
and thanks alot for the feedback friends

---

### Post by nafi27 on 2011-01-23
hi guys ..one more thing..
when i try to edit the boot command ..adding the extension acpi="off"..i'm able to access the system but not in the graphic mode..only the console mode...
and when i try to add acpi="Linux".. the booting get stuck with [COLOR=Blue]Kernel_thread_helper+0x0/0x10[/COLOR]
any hint ??
cheers :)

---

### Post by Quackers on 2011-01-23
Did you write down the boot arguments you use to install the system?
Those boot arguments need to used on boot until you edit a file in the system. To get the system to boot, hold down the shift key whilst booting. This will give you the grub menu, in which your Ubuntu choice will be highlighted. When the menu appears press the "e" key and a new screen will appear. Using the up/down arrows on your keyboard, navigate to the end of the line which says "quiet splash".
Then type a space and then add nolapic nomodeset etc etc - changing those for the ones you used. Put a space in between multiple entries.
Then press ctrl + X to reboot.
You should then get to your desktop. Then you can edit /etc/default/grub file with your changes.
Have a look at the thread below and scroll to the heading
"How to permanently set kernel boot options on an installed OS (not wubi)"
and follow those instructions to edit that file for a normal boot.
[http://http://ubuntuforums.org/showthread.php?t=1613132](http://http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by nafi27 on 2011-01-24
hi again..
i've tried the same options to boot when i installed ubuntu .. apci=off..all what i can get to is the console mode not the graphic mode..so i can't see my desktop ..but i can login from the console and browse through the directories ..using different commands like cd ..ls ..
but still not able to get to the GUI..
any suggestion ??
thanks

---

### Post by Quackers on 2011-01-24
try startx

---

### Post by nafi27 on 2011-01-24
i just tries the startx ..the screen just blackedout...i think i have a long way to learn about linux ...lool :D
..so what do  you think friend ?

---

### Post by nafi27 on 2011-01-24
dude .. i entered the console ..then i gave the command startx ... but the screen just blacked out ...nothing is there just a black screen..
i think i ill need to learn a lot before i enter into the linux world..looll
so what should i do next my friend..appreciate your significant help in this matter.. :)

---

### Post by Quackers on 2011-01-24
Does ctrl+Alt+F7 do anything?

---

### Post by gandaran on 2011-01-24
update the bios, most of the times this fixes the toshiba issues with linux.

---

### Post by nafi27 on 2011-01-24
the ctl+alt+f7 doesn't do anything...
i'm able to run ubuntu from the cd ..so that means there are some configuration can make the ubuntu on cd communicate well with the MBR ? right ?? so how come updating the BIOS solve the issue ??

---

### Post by Quackers on 2011-01-24
Updating the bios (if an update is available) could conceivably fix any acpi issues.
It's definitely worth seeing if an update is available.

---

### Post by nafi27 on 2011-01-24
ok ..updating the will be my last solution to try.. i will raise this issue in the toshiba forums...then i will let you know the results..thanks a alot friends :)

---

### Post by Quackers on 2011-01-24
You're welcome :-)
Good luck over there!

---

