---
title: "need help to install iso to a clean hard drive"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by aparolin on 2009-07-31
thanx for your help; 
i am new to linux and ubuntu...  very green.  
i probably have a stupid question, but i must be missing something simple.
i am stuck.  
i have downloaded to a harddrive to a (friend's computer) the ubuntu 9.04 desktop i386 iso.  it is 699 mb.  i have extracted numerous folders (8), but to burn the iso and installation folders to a cd would be nearly 1400mb.  if i only burn the iso to the cd, i dont think my (new to me) computer would be able to open the program and install.  should i have not extracted these files???

i acquired a used hp computer with 1gb ram, 250mb hd, pentium d processor.  but the hdd was wiped clean. it has only one file on the harddrive (command), only 94kb.  i have changed bios to boot from the cd rom, so i think i the pc is ready for installation once i burn an installation cd.  
are there commands to install an iso???

i would appreciate you directing me to the light:P
i am sure i can convert my friend; he uses winme, ugh:(
again; thanx for your help,

alan

---

### Post by lykwydchykyn on 2009-07-31
The iso is a CD image file  --it is basically a "snapshot" of a CD.  You don't extract anything from it, you burn it directly to a CD.

Depending on what CD burning software your friend has, this function might be named various things.  If nothing else, infrarecorder (which is free and open source) is a windows CD recording software which can burn an iso to CD.

[http://infrarecorder.org/](http://infrarecorder.org/)

Hope that makes it clear.

This might make them clearer:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by gettinoriginal on 2009-07-31
There is no extraction necessary.  Burn the entire .iso to disk using your friends computer, then insert the disk into your computer, and it will install from the disk.  I would like to suggest though that the disk should be burned at the slowest speed possible to avoid errors. Good luck, and welcome to Ubuntu.  :)

---

### Post by aparolin on 2009-07-31
thanx to lykwydchykyn and gettinoriginal for your replys.  
so you say the iso will load onto the hdd using the cd drive as the boot drive.

ok

i will give it a try.:D

---

### Post by Liolikas on 2009-07-31
> **aparolin said:**
> thanx to lykwydchykyn and gettinoriginal for your replys.  
so you say the iso will load onto the hdd using the cd drive as the boot drive.

ok

i will give it a try.:D
Not exactly this will happen if you burn iso file correctly you will see many flies and folders in cd and Ubuntu will boot and work from cd and on desktop you will see icon install to hdd. After install to hdd you can forget cd.

---

### Post by aparolin on 2009-08-01
thanx all for your help:D

i made the mistake of cd-burning the downloaded program as a data file; which would not work,
then i burned it as an image file (which it is) and all went well.

now my ubuntu education begins:D

again thanx,
alan

---

### Post by lkraemer on 2009-08-01
You will probably want to install the following via Synaptics Pagkage
Manager:

1.  K3B - CD/DVD Burning Software
2.  VLC - Media Player
3. Amarok - Music Player
4. File Roller - Archive Manager
5. Keepassx - Password manager
6. PDF Editor - PDF Editor
7. VirtualBox - Runs XP as Guest OS.
8. pysdm - manager for adding fstab entries for Windows drive/partition support.
9. Wine or Crossover (Allows some Windows software to run in Linux.)
10. Pidgin or PSI (IM/Chat Software that works good)

lkraemer

---

