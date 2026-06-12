---
title: "a question about gparted"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by beew on 2010-07-25
I am experiencing a strange problem.

I have Ubuntu 10.04 installed in a Dell laptop, a 8 G usb thumb drive and a 40G hard disk from an old computer which I now use as an external hard drive.

I installed gparted in all of them. I also have a live usb with 3 G persistence which comes with gparted preinstalled.

I can start gparted in both the Dell (internal hard disk) and the live USB but it just wouldn't start in the 8G usb and the external hard disk.  Moreover, in the live usb and the internal installation gparted shows up in system > administration whereas in the external hard drive and the 8 G usb it shows up in applications > system tools.

I am not sure if this is a bug, it may just be the way it should be even though I don't understand the logic behind it.

I would appreciate it if someone can explain to me what is going on. I am in the process of learning and experimenting. Thanks

---

### Post by Anuovis on 2010-07-25
From what I understand, I do not think you have any OS installed on that external 40GB  HDD or 8GB flash drive. It is natural that not only gparted but no other software can be launched from there, there is no OS to begin with. 

However, you do not need gparted on those two devices. Why would you? They are external, mountable storages. Once you have a working OS you can always plug them in and format in any file format you wish. 

Gparted is mainly for setting up/managing partitions for your main HDD (e.g. before installing or when you want to resize/create new partitions).

Does that answer your questions?

---

### Post by beew on 2010-07-25
> **Anuovis said:**
> From what I understand, I do not think you have any OS installed on that external 40GB  HDD or 8GB flash drive. It is natural that not only gparted but no other software can be launched from there, there is no OS to begin with. 


Of course they are installed. I am running all kinds of softwares and doing system and kernel updates on them. You plug them in any working computer with compatible hardware and they work like "real" installations except the 8 G one is a bit slow as you would expect.

My question is not what you think I should use gparted for, but whether it is expected to behave in certain way. I could have used my external installation to manage the internal hard drive of a computer that I plug it into like you would use a live usb for. Why not?

---

### Post by crutch on 2010-07-25
Hi,
I'm not sure that I understand. You are saying that you have ubuntu installed on the external devices, and you boot into these installations (I take it the external drive is eSata or something like this?), but you cannot get gparted to start - is this correct? have you tried starting gparted from an termional, to see what responce you get when it doesn't start?

---

### Post by Anuovis on 2010-07-25
I see. I have no experience with this so probably will not be able to help you much. I only used gparted from Ubuntu CD with no issues.

Maybe somebody else could help you with this.

---

### Post by beew on 2010-07-25
> **crutch said:**
> Hi,
I'm not sure that I understand. You are saying that you have ubuntu installed on the external devices, and you boot into these installations (I take it the external drive is eSata or something like this?), but you cannot get gparted to start - is this correct? have you tried starting gparted from an termional, to see what responce you get when it doesn't start?

One external drive (40G) is the hard drive of a dead computer. I took it out, reformatted it and use it as an external drive. Another one, the 8g one, is a kingston usb pendrive.

I made a full installation of Ubuntu in both of them and they become kind of portable computers. You can plug them in any desktop or laptop computer that supports booting from usb (and have the right hardware drivers) and start a Ubuntu session. I have done this with several laptops and desktops. I can get on the internet, do system updates and play 3d games (in the 40G installation, the other one is too slow)

I can also install softwares through synaptic or apt-get and I installed a lot of them!:D  I installed gparted in them this way. The curious thing is in both cases gparted somehow appears to be in the wrong place (applications > system tools instead of System > administration) and it wouldn't start.

BTW, just to be clear, I made a full installation of Ubuntu on these devices, they are not live usbs with persistence. You can't do system level updates in live usbs with persistence without breaking them, you can only update applications. But with full installations you can.

Hope I have explained it clearly.

---

### Post by crutch on 2010-07-25
Sounds cool. I take that nothing happens when you try to open gparted. Could you check if you are trying to open gparted as a normal user or as root. - System>Preferences>Main menu, select gparted and click properties. check if the command is gksu /usr/sbin/gparted or something else.

---

### Post by beew on 2010-07-25
Hi, Crutch,

The command is /usr/sbin/gparted %f

Yeah, it is kind of cool, you can never do such a thing with Windows, they want you to pay for every installation. I heard that you can install windows
7 with a usb, but only for upgrading and only on the Vista/XP machine that creates it! :)

---

### Post by crutch on 2010-07-25
I'm not quite sure what the %f does in this but gparted will normally only run as root as it needs root permissions in order to make changes to the way the disks are formatted. could you try typing 'gksu /usr/sbin/gparted' in the terminal, and if this works replace the command in the menu properties.

---

### Post by beew on 2010-07-25
Crutch,

You are a genius! It works!! Problem solved, though still don't know how the command mixed up happened. 

Thanks a million!!

---

### Post by crutch on 2010-07-25
It does seem a bit odd doesn't it. Glad I was able to help.

---

