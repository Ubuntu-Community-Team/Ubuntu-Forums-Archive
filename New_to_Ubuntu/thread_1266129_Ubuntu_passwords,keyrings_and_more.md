---
title: "Ubuntu passwords,keyrings and more"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by Fatalrewind on 2009-09-14
Hello

I have been using Ubuntu for around 7 months and have found some areas
of Ubuntu that really annoy me but i have no idea of how to remove disable
these features and so i am here to ask for some help.

Ubuntu asks for a password for everything ,well just about everything
every time i perform system functions - this reminds me of windows vista
and how i hated vista , i think these system password security settings
should be removed as they only annoy everyone that uses Ubuntu and i simply 
don't need to be asked for a system password even after i have logged in
using my password ,if someone offers advice / fix to this please understand
that it should be easy to understand as i am not a power user or very good
at messing around with Ubuntu.

Default Keyring Password ,this has became more and more of a problem
for me as i have updated from 8.04 to 9.04 then onto notebook remix 9.10
and there doesn't seem to be a correct way of stopping this from appearing
after bootup ,after user password entry and after system sleep,logout
or standby ,i feel that the keyring is completely pointless in Ubuntu
and would like to see it removed ,why cant Ubuntu after all this time 
in constant development be fast easy and secure without going over
the tops of the regular users head ? i would love some help on removing
or disabling both these features of Ubuntu.

So these are the most annoying things that i would like to clear up
in Ubuntu as i feel they distract the user from general use but
there is one more thing i want to ask about and that would be the
way Ubuntu Boots up ,is it necessary for code and system calls
to be displayed when Booting up and shutting down in Ubuntu ?
would it be possible to have all that background stuff hidden as
this would make Ubuntu look cleaner and more user friendly right
at the beginning maybe its just me but i just want an easy to use
system without the reminders that theres alot of stuff happening
in the background ,it would make Ubuntu look more Professional to 
the new user and would Give Ubuntu a more easy on the eye appeal
for new users and people who would wish to use Ubuntu as family
home computer.

Thanks for taking the time to read everything ,im sure this stuff
has been asked before but i have only asked as i do like Ubuntu
and would love to see it become even more polished than it is
currently ,good work to all involved with Ubuntu and kind regards.

Paddy

---

### Post by LowSky on 2009-09-14
First off asking  for your password everytime you do a system administrative thing, isn't bad. I would understand if it asked for your password when you use firefox or open office, that would be insane, but to change admin stuff, come on how often do you realy feel the need to change a system setting or install something?

Secondly you can turned it off, its against the Ubuntu way to do so, but it possible. one way is to activate the root account and use that to do admin stuff, which is realy not a good idea, or use your account with no password, again very bad idea.

As for the keyring I totally agree with you. its annoying, doens't always work correctly and no reaosn why it should pop up for wireless access. and there is a way to have it stop appearing and that is to have never allowed it to activate in the first place. you can reset it from the *~/.gnome2/keyring* file I belive.

And what stuff at boot up? My screen shows the BIOS boot and then the Ubuntu logo then the desktop, at close its the logo then its off. If your seeing text there has to be a reason, as its not the default

---

### Post by Wim Sturkenboom on 2009-09-14
> **Fatalrewind said:**
> Ubuntu asks for a password for everything ,well just about everything every time i perform system functions - this reminds me of windows vista and how i hated vista , i think these system password security settings should be removed as they only annoy everyone that uses Ubuntu and i simply don't need to be asked for a system password even after i have logged in using my password ,if someone offers advice / fix to this please understand that it should be easy to understand as i am not a power user or very good at messing around with Ubuntu.
It does not annoy me as I can see the benefits of the security model. And I have not heard many others complaining about it. Further my experience is that I only need it at a maximum of once a day (for updates or installs). 

> **Fatalrewind said:**
> ... but there is one more thing i want to ask about and that would be the way Ubuntu Boots up ,is it necessary for code and system calls to be displayed when Booting up and shutting down in Ubuntu ?
would it be possible to have all that background stuff hidden as this would make Ubuntu look cleaner and more user friendly right at the beginning maybe its just me but i just want an easy to use system without the reminders that theres alot of stuff happening in the background ,it would make Ubuntu look more Professional to the new user and would Give Ubuntu a more easy on the eye appeal for new users and people who would wish to use Ubuntu as family home computer.

Below part of my grub configuration on an aao running UNR9.04 (file /boot/grub/menu.lst). It shows two menu entries, the first one is the default one used when the system boots. To suppress the messages that you see, the bold part (it's at the end of the first kernel line) can be added using your favourite editor (and you need sudo for that ;) ) 
```

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            580b247f-4b71-4370-8c00-c3b32f87168f
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=580b247f-4b71-4370-8c00-c3b32f87168f ro **quiet splash**
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            580b247f-4b71-4370-8c00-c3b32f87168f
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=580b247f-4b71-4370-8c00-c3b32f87168f ro  single
initrd          /boot/initrd.img-2.6.28-15-generic

```

---

### Post by drs305 on 2009-09-14
The default keyring issue is easily resolved. The method depends on whether you use autologin or enter the password during boot. Post #5 by mcduck explains how to change the keyring password behavior:
[http://ubuntuforums.org/showthread.php?t=1264954#5]("http://ubuntuforums.org/showthread.php?t=1264954#5")

---

### Post by Fatalrewind on 2009-09-14
Hi and thanks to everyone for the replys

Wim Sturkenboom ,is it this line that i add to the cfg ?

uuid 580b247f-4b71-4370-8c00-c3b32f87168f


again i am not very good at command line stuff or editing the main
Ubuntu cfg so could someone please give full details of what i do
to edit in the uuid that disables the text that appears at the boot
and shutdown.

in regards to the password protection that Ubuntu asks for ,how
would i go about logging in as the root as default so i don't have
to enter a password every time i want to install software,updates
or configure my desktop/system ,as i find my self doing nothing
but installing/uninstalling and configuring my Ubuntu ,it is after all
one of the best things Ubuntu has to offer the user and i love it
please bare in mind that im no good at all this so some step by step
instructions would be very welcome.

Hello and thanks LowSky
could you please describe exactly what i do to remove the keyring ?

LowSky
(As for the keyring I totally agree with you. its annoying, doens't always work correctly and no reaosn why it should pop up for wireless access. and there is a way to have it stop appearing and that is to have never allowed it to activate in the first place. you can reset it from the ~/.gnome2/keyring file I belive.)

also thanks to drs305 ,i will check out that link 

thanks to everyone

Paddy

---

### Post by Wim Sturkenboom on 2009-09-15
No, the next one starting with kernel.

```

kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=580b247f-4b71-4370-8c00-c3b32f87168f ro **quiet splash**

```At the end I've marked in bold what usually is there.

I think that the easiest way to edit the file is to run *gksudo gedit /boot/grub/menu.lst* in a terminal. I have however never used gksudo so not sure if the command will work. If that command works, just search for lines with kernel. The first one you find should look similar to what I've posted. Please note that the numbers that you will see are more than likely different; don't bother about them, just check if *quiet splash* is there or not.

If it's not there, add it. If it's there, post the content of the file here so we can check it.

---

