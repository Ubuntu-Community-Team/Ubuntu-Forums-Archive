---
title: "How do I switch to GNOME using live USB Ubuntu Netbook Edition 10.04"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by mr.xulu on 2010-09-07
Hi! I'm a one-week old ubuntu user. I have an ubuntu netbook 10.04 installed in a live usb drive.

when i'm booted to UNE 10.04 using live usb and try to switch to GNOME environment i'm asked for a password but it fails to enter since i don't have an account made yet. I try to enter the keyring password that i set upon opening UNE 10.04 but that doesn't work either. How do i switch to GNOME in live usb?

Thanks :)

---

### Post by gauravj on 2010-09-07
You will have to download netbook remix iso.
Burn it to usb using startup disk creator from some other ubuntu system.
Or you can make a live cd from iso and create a usb startup disk.
You have to select boot from usb drive in bios.

All this done, the booting of usb do not ask for password.
Password is required when you install the system to hard disk
creating an account.

---

### Post by coffeecat on 2010-09-07
> **gauravj said:**
> All this done, the booting of usb do not ask for password.

Yes it does, if you log out and login again in during the live session - which is what the OP seems to be doing to get gnome.

@mr.xulu, the live session ubuntu name and password *should* be:

username = ubuntu
password = blank (that is, simply press enter without typing anything in.)

I say *should* because that is what it should be, but sometimes this doesn't work. I don't know why.

---

### Post by candtalan on 2010-09-07
Another possibility is to just use a 'Desktop' version in a live USB stick.

Although a desktop version will need 4 GB hard drive space, it will run as a live system with no problem. In my asus eeepc 9000, I have unr 10.04 installed, and I also run Ubuntu 10.04.1 as a live session from a usb stick in demonstrations, it is no problem.

---

### Post by C.S.Cameron on 2010-09-07
With a 10.04 Live USB you can go to System/Administration/Users and Groups and create a new user with it's own password.
You can go to System/Administration/Login Screen to select log in options.

---

### Post by mr.xulu on 2010-09-07
Thanks to everyone for your help!

To cofffeecat and c.s. cameron your suggestions worked! As a week-old user of ubuntu I have to say i'm amazed at all the help from the community!

I installed lucid desktop in my netbook as i prefer gnome interface. I like how all the menus are just concentrated in one corner of the screen unlike une where my eyes have to go all around the screen looking at different icons. une seems to tire my eyes more if i'm working on the computer for a long time. 

But I still installed netbook 10.04 on live usb coz i'm trying to get my family to start using ubuntu on their netbooks and laptops and i'd like them to get a feel of both une and gnome while trying it out.

Thanks again everyone :)

---

