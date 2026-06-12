---
title: "Cannot get sound working(no internet)"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by ho0ola on 2010-03-10
Hello hello !

        Im havin a prob w/ sound... 

   [FONT=Book Antiqua][SIZE=2]After typing: sudo lshw -C snd[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]*-multimedia:0 UNCLAIMED[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       description: Multimedia audio controller[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       product: nForce Audio Processing Unit[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       vendor: nVidia Corporation[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       physical id: 5[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       bus info: pci@0000:00:05.0[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       version: a2[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       width: 32 bits[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       clock: 66MHz[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       capabilities: pm bus_master cap_list[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       configuration: latency=0 maxlatency=12 mingnt=1[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       resources: memory:e5000000-e507ffff[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]  *-multimedia:1[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       description: Multimedia audio controller[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       product: nForce2 AC97 Audio Controler (MCP)[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       vendor: nVidia Corporation[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       physical id: 6[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       bus info: pci@0000:00:06.0[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       version: a1[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       width: 32 bits[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       clock: 66MHz[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       capabilities: pm bus_master cap_list[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2[/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2] [/SIZE][/FONT]
  [FONT=Book Antiqua][SIZE=2]       resources: irq:21 ioport:d800(size=256) ioport:dc00(size=128) memory:e5081000-e5081fff[/SIZE][/FONT]
  

          - This tells me my system recognizes my audio driver and it is installed correct? 
I cant figure out how to open ALSA, do i need to? I didnt know if maybe that app would allow me to tinker w/ audio settings. 
         When I go to system>preferences>sound>hardware tab i dont know which one to select or really how to use any of this stuff. I have tried playing a CD and selecting EVERY possible option but nothing would work. 

I have my headphones plugged into the line in, which i know is the right one...

I have an nforce2 chipset 
AMD Athlon XP 2800+
Nvidia Geforce4 MX integrated GPU
2MB 3200 RAM
And Linux Ubuntu 9.10 Karmic Koala
120 GB HDD

NO INTERNET!!!! But im so happy ubuntu detected my linksys card!! and it is working, only all the signals i get are WEP protected. 

If this isnt enough info, please tell me what to tell you :)

Thanks guys
~KAcy

---

### Post by undecim on 2010-03-10
Can you get an ethernet cable and connect directly to your router? Then check System -> Administration -> Hardware Drivers

---

### Post by ho0ola on 2010-03-11
No i cant, I will be getting the internet soon, hopefully by the weekend. So, i guess ill just do it then :)

---

### Post by chaanakya_chiraag on 2010-03-11
Try doing this:
```
sudo killall pulseaudio
sudo pulseaudio --system --daemon
```
That should do it.  If it says pulseaudio isn't found, then this workaround isn't for you.

---

