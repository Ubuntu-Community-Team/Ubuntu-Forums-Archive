---
title: "ubuntu freezing"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by supapandadeanna on 2010-12-28
i just installed ubuntu 10.10 three days ago on my laptop.  everything was working great until today when i accidentally forgot to plug my charger in before my laptop died, which i do from time to time.  so now everytime i boot up ubuntu it the ubuntu logo that was all cool looking before and just said ubuntu now has that ugly text :[FONT="Courier New"]Ubuntu 10.10[/FONT] in courier and then it goes to the administer login thing where you would normally enter a pw and it just freezes, it says log in as supapandadeanna like if my mouse were hovering over the word administer or whatever and the mouse doesnt move and the screen doesnt change to anything, eventually the laptop goes to sleep mode and doesnt go out so i have to hit the power button. my computer still runs windows vista fine which is what im using now, but i really want to use my ubuntu :( i had it exactly how i wanted it and everything. somebody help me, im not a computer wiz or anything like that, thanks

panda

---

### Post by kroq-gar78 on 2010-12-28
that happened with me on one of my Compaq/HP laptops. I just did Ctrl-Alt-Delete to shutdown. It works when I boot it back up.

Also, did sleep mode work before all of this happened, or did sleep (and/or hibernate) never work?

EDIT: select your user with ENTER and then type in your password, then Enter, and then to Ctr-Alt-Delete and wait for 1 minute

---

### Post by supapandadeanna on 2010-12-28
everything has always been functional the sleep, the hibernate etc. and its still functional on windows os, i didnt try ctrl alt dlt but i will, however, even when i turned it off and back on it didnt work... thank you for the reply. :(

---

### Post by Rubi1200 on 2010-12-28
Hi and welcome to the forums :)

Please post the _full_ specifications for the computer.

Also, do you have or can you get an Ubuntu LiveCD?

Thanks.

---

### Post by supapandadeanna on 2010-12-28
it is a gateway laptop says model NX570X pretty old, but very reliable. dont know anything too technical, so if theres anymore info you need please help me explain it to you.

and no i dont have the cd and i used a usb to install it because my cd drive doesnt work anymore

---

### Post by kroq-gar78 on 2010-12-28
Do you still have access to the flash drive? The work just as well as LiveCDs and are faster replacements. When people say "LiveCD", LiveUSB generally works too. If you boot up your flash drive, run this code in a terminal (Applications -> Accessories -> Terminal):

```
sudo lshw
```

and post the output.

---

### Post by supapandadeanna on 2010-12-28
i will tomorrow.  but i dont really know how to do what youre telling me, i dont know much about computers at all :(
could you give me a run through on what to do from when i turn my computer on to that point?

---

### Post by Rubi1200 on 2010-12-28
Hi,
you can use a LiveUSB just as well.
This link is to download Ubuntu and also explains how to make a LiveUSB:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Once you have it ready, you need to change the setting in BIOS to allow booting from the flash drive.

Depending on the make and model it is usually accessed using something like F2, F12, Del, Esc.

As the computer boots and you see the POST screen (the one which tells you the name of the manufacturer) look at what it says in terms of the key to use.

Once in BIOS go to the menu which will say something like Boot or Boot Priority.

There, you can change the options using the cursor to boot from the flash drive. It needs to be set as the first priority.

It will say something like USB drive, removable media etc.

Once you have done this you can boot the USB and choose to try NOT install Ubuntu.

At the live desktop, go to Applications > Accessories > Terminal and run the commands already asked for.

If you run into difficulties, ask please.

---

### Post by supapandadeanna on 2010-12-28
can i run it without the usb in after that though?

---

### Post by Rubi1200 on 2010-12-28
> **supapandadeanna said:**
> can i run it without the usb in after that though?
What do you mean exactly?

If you are using a LiveUSB then it needs to remain plugged in for the time you use it. The information is being read directly from the files on the USB stick, so it needs to be there while you are doing anything.

Once finished, tell Ubuntu to restart and remove the USB after it confirms you can do so.

This will not affect Windows while you are using it.

---

### Post by supapandadeanna on 2010-12-28
oh, well i thought once you installed it you didnt need the usb or cd anymore?

---

### Post by Rubi1200 on 2010-12-28
> **supapandadeanna said:**
> oh, well i thought once you installed it you didnt need the usb or cd anymore?
Once Ubuntu is installed you remove the flash drive and boot normally.

I thought you just wanted to try first to save your data etc.?

---

### Post by supapandadeanna on 2010-12-28
no, i had already installed it and this happened.

---

### Post by Rubi1200 on 2010-12-28
> **supapandadeanna said:**
> no, i had already installed it and this happened.
I understood that from your first post.

But, if you want to get Ubuntu up and running again there is certain information we need that is best accessed from within Ubuntu.

That is why we wanted you to boot the computer with a LiveCD/USB.

If we need to help you make repairs to the system this is also done from the live environment.

---

### Post by supapandadeanna on 2010-12-28
ooh sorry, okay well i dont have the usb with me right now but when  i do ill get back to you
thanks for everything

---

### Post by supapandadeanna on 2010-12-28
i finally have my usb. now what do i need to do

---

### Post by Rubi1200 on 2010-12-29
> **supapandadeanna said:**
> i finally have my usb. now what do i need to do
Hi,
great news.

Follow the instructions I posted earlier in the thread regarding booting the computer from the flash drive.

Choose to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post.

There are instructions included.

Post the results back here in a new post and we can take it from there.

---

