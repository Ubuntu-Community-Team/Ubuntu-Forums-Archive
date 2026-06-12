---
title: "Wired connection problems"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-21
It was working fine last night...

Im trying to conneft to internet with a wired (ethernet) connection... My modem and all that says its all good but when i stick the cable in the laptop i dont get a connection... What is the problem?  When i go to settings for internet stuff, im lost as i dont know anythinf... Please help

---

### Post by lisati on 2009-03-21
Does starting Ubuntu after you have connected your cable make any different?

---

### Post by Skol312000 on 2009-03-21
No....

I have dsl and i dont know if i need to set it up weirdly

---

### Post by lisati on 2009-03-21
Next suggestion: does your wired network show up when you click on the networking icon (it looks like two little computers) on the top panel?

---

### Post by Skol312000 on 2009-03-21
It shows two littlencompters but im disconnedted!!!

Omg... This makes me mad... And i fully switched to Ubuntu...

What setting shoukd i do for dsl or for wired?!?

---

### Post by Skol312000 on 2009-03-21
Whats VPN?!? I havent even configured yet.. Should i?  How? And what settings?

---

### Post by Skol312000 on 2009-03-21
I even reset my 2wire gateway and still nothing...

The gateway modem shows that ethernet /internet/dsl is on and i just cant connect though Ubuntu...

This is the only thing i dont. Like about ubuntu... Spending a saturday for internet..

---

### Post by lisati on 2009-03-21
> **Skol312000 said:**
> It shows two littlencompters but im disconnedted!!!

Omg... This makes me mad... And i fully switched to Ubuntu...

What setting shoukd i do for dsl or for wired?!?

If you click on the two computers and all is well, you should get a list of networks that you can connect to. On my machine, the wired connection is listed as "Auto eth0"

---

### Post by Skol312000 on 2009-03-21
The little computers have an X on the corner.. I clicked once and it pulled a windows saying "wired Networks" but u can click it... I got aauto eth0  to choose... I did and nothing happened... I didnt set anything up yesterday and it still worked... What am igonna do?

---

### Post by Skol312000 on 2009-03-21
I finallywas able to cennect wirelessly but i want via ethernet!!!

Another problem is when i got on the internet "i have att service"
It told me sticknin backup cd and follow instructions... I guess it was only meant for qindows... I have to go back to windows... This is rodiculous... Wasted mt morning...

---

### Post by presence1960 on 2009-03-21
> **Skol312000 said:**
> I finallywas able to cennect wirelessly but i want via ethernet!!!

Another problem is when i got on the internet "i have att service"
It told me sticknin backup cd and follow instructions... I guess it was only meant for qindows... I have to go back to windows... This is rodiculous... Wasted mt morning...

I think you are getting way ahead of yourself. I don't know why you can't connect with a hard-wired connection BUT I can tell you this: I ran Linux with windows in Sun Virtual Box. My DSL went bad. When I called for service I was told they don't work on Linux boxes. So I had to set up a dual boot with Windows because the techs either didn't want or didn't know how to work with Linux. That is not Ubuntu's fault! Of course the disk they gave you probably only works with Windows and Mac. **SLOW DOWN now partner! And wait till someone more experienced in setting up networks comes along to help.**

---

### Post by presence1960 on 2009-03-21
> **Skol312000 said:**
> I even reset my 2wire gateway and still nothing...

The gateway modem shows that ethernet /internet/dsl is on and i just cant connect though Ubuntu...

This is the only thing i dont. Like about ubuntu... Spending a saturday for internet..

I seriously doubt this is Ubuntu's fault! It was working last night, right?

You have asked for help now it is a waiting game until someone who can help you comes along. The other option is to panic and do all sorts of goofy things and mess up your system. Sit tight someone will come along to help you.

Did you think you were going to switch to something new and not have issues that can be worked thru? Remember why you left Windows? This is probably nothing compared to the problems you experienced with Windows. Patience is a virtue.

---

### Post by Skol312000 on 2009-03-21
Im just now installing windows again because i reset thr damned att device and now i have to reconfigure... Everythingscool guys thanks.... Its a temporary switch

---

### Post by presence1960 on 2009-03-21
> **Skol312000 said:**
> Im just now installing windows again because i reset thr damned att device and now i have to reconfigure... Everythingscool guys thanks.... Its a temporary switch

Hopefully you will partition your hard disk and set up a dual boot. Windows will wipe GRUB. If you do this you can reinstall GRUB by this :

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition nr is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.
```

---

### Post by linux6994 on 2009-03-21
A couple of things concerning DSL

DSL uses PPPoe for logging in. Either you have a router that stores your user name and password and handles the protocol and all devices just connect DHCP to it or you use a PC via directly to your DSL modem and use the PPPoe setting to log in directly.

DSL modem > router > PCs
The router maintains your connection and everything connects via router. 

DSL modem > PC
You will need to install the PPPoe service on Ubuntu, this will allow you to login for your pppoe service.

sudo apt-get install pppoe

Good Luck

---

### Post by Skol312000 on 2009-03-21
thank you all verry much.. its up and running now

---

