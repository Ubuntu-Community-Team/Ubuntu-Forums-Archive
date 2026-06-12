---
title: "Scroll Lock at Boot or Login Screen"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Raynman37 on 2009-09-16
Hi Everyone,

I have an illuminated keyboard that is turned on by the scroll lock key, and at this point I got it to enable scroll lock by running:

```
xmodmap -pm
```

and then doing the whole

```
xmodmap -e &#8216;add mod3 = Scroll_Lock&#8217;
```

thing and creating an /etc/X11/Xmodmap file like I found in a few tutorials.

What I was wondering is, what is the earliest point in the boot process can I enable the scroll lock. Ideally, I would like to make it so that I can do it when GRUB first opens with the boot selector, but I'm not sure how to reference either the Xmodmap or if there is another way to do it?  

I have my boot sectors password protected, so it would be nice if I could see my keys when I'm typing that in.  If I can't do it then, is there a way to have the boot sequence enable scroll lock at any time before it gets to the GDM login screen?

Thanks!

---

### Post by Mike_IronFist on 2009-09-16
I assume it would involve editing your xorg config file, but anything like that is beyond the scope of my knowledge.

---

### Post by Raynman37 on 2009-09-17
Ok, here were a few things I read when I was poking around google looking for some answers:

GuestToo on linuxquestions.org said:
> you can enable the scroll lock key by typing:

xmodmap -pm

to find an unused modifier ... on my machine, mod3 is free
to set up the scroll lock key on mod3, you can type:

xmodmap -e 'add mod3 = Scroll_Lock'

now the scroll lock key should work
but i don't know if Gnumeric will ignore it or not

you can put this line in the hidden file /root/.Xmodmap (create the file if it does not exist) to enable the scroll lock key every time X starts:

add mod3 = Scroll_Lock

achim 59 replied:
> The stated command does indeed work (thanks for the tip!) but the addition of a hidden /root/.Xmodmap doesn't work in Ubuntu 8.10. I'm guessing that is because there is no root user as such, since root privileges can only be accessed through "sudo" (or "su" if you've set up a root password), i.e. one cannot login as root directly.

Until I've located an appropriate place for the command, I'm keeping it in a bash script in my ~/bin.

It seems like GuestToo was on to something by having a command that would be read every time X started.  Does anyone know how to make this command work?

I also found an interesting post here: [http://www.nabble.com/Scroll-Lock-led-td13413113.html](http://www.nabble.com/Scroll-Lock-led-td13413113.html)

Maybe someone will recognize what they were doing there :)

---

### Post by Raynman37 on 2009-09-28
Bump, hoping for an answer :)

---

### Post by Darkwing-Duck on 2009-09-28
If you wanted to make this work when you stared Xserver then create a bash script with the commands that you wanted in it and add it to the startup scripts.

That would be the simple way around it. If you need help with making a script let me know!

---

### Post by Raynman37 on 2009-09-30
I like the sound of that, but yeah, I would need help writing the script because I really havent dont much scripting at all...

If you want to pm me I can tell you my email or aim or whatever chat client you want and we can talk about it!

Edit: Or just click on the aim link under my info in the sidebar (which I forgot was even there) <---

---

### Post by CaptainMark on 2009-09-30
Have you checked your bios options, a lot of them have scroll/num lock status on/off at boot up

---

### Post by Raynman37 on 2009-09-30
I just checked the BIOS and the only option it gave me in there was to turn the Num Lock key on or off.

---

