---
title: "Noob stuff. Mythtv"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by xeticus on 2009-05-08
I just installed 9.04 under my xp partition using Wubi and I love it. So much easier to use than the previous versions I gave a try in years past. I do have a couple questions though.

Mythtv? I have it installed I think but when I try to run it I get either I have to join a community which i thought I had or when I active the Mythtv front end I get a black box that shows up and nothing happens. Compared to Kaffeine or VLC why is Mythtv such a bitch to use?

I have Pinnacle Pro Stick USB Tuner the 800E. I've been trying to get it to work with either Kaffeine or Mythtv. I've read some instructions here and there but they seem to be for earlier verions of Ubuntu and they aren't the most noob friendly instructions. Does anyone have any suggestions about what is the **easiest** way to get this card working in ubuntu. I have managed to get Kaffeine to the point that i see a DVB listing but I have no clue how to get it to work after that.

Anyway I want to thank everyone who helped make Ubuntu and especially 9.04 so great. The Synaptic package manager is freaking awesome!!!

---

### Post by xeticus on 2009-05-10
Bumpage. Help a noob please.

---

### Post by pauna on 2009-05-10
> **xeticus said:**
> 
Mythtv? I have it installed I think but when I try to run it I get either I have to join a community which i thought I had or when I active the Mythtv front end I get a black box that shows up and nothing happens. Compared to Kaffeine or VLC why is Mythtv such a bitch to use?


Mythtv is not really a simple desktop program like Kaffeine or VLC, it's a total TV set top box infrastructure. 

To set up Mythtv properly you need two separate systems: a frontend (which displays your TV/video recordings) and backend (which handles your TV tuner cards and recording). You can of course run those in the same physical box, like I do. The point is, Mythtv requires a lot of tweaking and configuring.

So unless you are trying to build a dedicated TV set top box, forget about MythTV, Kaffeine should be ok for casual TV viewing.

I have no experience with the Pinnacle USB stick, but the key thing is that the kernel needs to recognize it. Could you please dump the relevant parts of the "dmesg" command and the "lsusb" command here after you have inserted the stick?

---

### Post by xeticus on 2009-05-11
> **pauna said:**
> Mythtv is not really a simple desktop program like Kaffeine or VLC, it's a total TV set top box infrastructure. 

To set up Mythtv properly you need two separate systems: a frontend (which displays your TV/video recordings) and backend (which handles your TV tuner cards and recording). You can of course run those in the same physical box, like I do. The point is, Mythtv requires a lot of tweaking and configuring.

So unless you are trying to build a dedicated TV set top box, forget about MythTV, Kaffeine should be ok for casual TV viewing.

I have no experience with the Pinnacle USB stick, but the key thing is that the kernel needs to recognize it. Could you please dump the relevant parts of the "dmesg" command and the "lsusb" command here after you have inserted the stick?Okay I'm going to check out what those commands are and get back to you.

---

### Post by blazemore on 2009-05-11
MythTV is notoriously difficult to install.

Google MythBuntu

---

### Post by xeticus on 2009-05-29
> **blazemore said:**
> MythTV is notoriously difficult to install.

Google MythBuntuI gave up on MythTV. I did manage to get my Pinnacle tv tuner working under Kaffeine. I'm not sure how. it works better under Kaffeine than it ever did under the Pinnacle software.

---

### Post by LowSky on 2009-05-29
I hope these links help

[http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick](http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick)

[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)

---

### Post by xeticus on 2009-05-30
> **LowSky said:**
> I hope these links help

[http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick](http://www.mythtv.org/wiki/Pinnacle_PCTV_HD_Pro_USB_Stick)

[http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)I'm good thanks. Ive been enjoying Kaffeine, VLC and Dragon Player. Much easier to install and configure than Mythtv.

---

