---
title: "I couldn't login after reinstalling(rescuing) Grub2"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by neiu bee on 2011-06-13
Hi.. i upgraded to 10.10 from 10.04 which is other OS with xp, both on different drives. My xp got struck so i installed it again without knowledge of grub2 overwritten.But my entire crucial data is under ubuntu. So i tried to get out of it using "ubuntu alternate 10.10". I did not follow every step of the installation, but i choose only "Grub installation" for first time and "software and other packages installation"[ i couldn't remember properly]
for the second time.I could rescue my grub2 but my problem is with the login.. i can't move a bit after that

Ubuntu 10.10 Machine ttyl
Machine login:rouster-[my previous one]
password:             [my previous one]
login failed 

This is the message i'm getting... i have to get that data for my report please help me to get out of this.

---

### Post by Irihapeti on 2011-06-13
I can't quite tell from your message whether you've overwritten your installation or not. However, it seems that getting your documents is the most important thing at the moment.

Do you have a liveCD or liveUSB? It doesn't have to be Ubuntu, BTW.

If you need to download a liveCD, I suggest [parted magic]("http://partedmagic.com/doku.php?id=start"). It has a number of rescue tools on it, including Photorec (see below).

If you boot with a liveCD (or liveUSB), you should be able to mount your Ubuntu partition and get access to your documents if they are still there.

If it turns out that they are overwritten, Photorec *might* be able to help you recover your documents.

---

### Post by garvinrick4 on 2011-06-13
If you have an install cd you can boot from it and use Try Ubuntu and look and see if your install is still there. If the /home is still there we can copy that to an external? You can even
drag and drop to external if that is easier for you. I do not know what version Install Cd you have handy to use as a live cd 11.04 is a bit different from 10.10 and below but pretty easy
to see if your install is still there.
## I see post 2 has recommended about the same. I will bow out.

---

### Post by Irihapeti on 2011-06-13
gavinrick4, given your number of beans, you probably know more about it than I do. Feel free to continue.

---

### Post by beelzebufo on 2011-06-13
I have had that happen to me several times, your data is probably not lost.  search these forums for a post about reinstalling grub2, it will talk about sudo apt-get purging and reinstalling from a live cd, sorry I don't have time to look it up for you, the hard part is just mounting the drive from the live cd, usually takes me about 10 minutes when I have that tutorial open

good luck

---

### Post by garvinrick4 on 2011-06-13
@neiu bee
If you need more help just say so.

---

### Post by jtarin on 2011-06-13
I would agree with garvinrick4 and might add you could use the CHROOT method to access your files to move them.

---

### Post by neiu bee on 2011-06-14
hey irihapeti.. thanks for ua repli... 
1. I didn't over write my installation b'coz both OSes installed are in different drives.Its only MBR that is overwritten 
2. I recently upgraded 10.04 to 10.10. I have 10.04 live cd.. also 10.10 netbook line cd, and 10.10 alternate cd
3.I tried a lot but could not mount my "/" partition.. but when i installed GRUB2 using 10.10 alternate cd its not displaying any thing... but here i have a problem.. my / partition was cleared totally and new things were installed after i tried using alternate cd [ initially partition was 14GB/23Gb after GRUB2 installation it is 1.36GB/23GB].
Even then i'm not able to login...i think the GUI might not have installed
So tell me  way to install GUI or login through commnands.
I have not given any login name, password during GRUB2 installation. But its asking when i'm about to login. I tried old one.. but couldn't not do it.

---

### Post by neiu bee on 2011-06-14
ya i thought of copying.. but its going to clear the partition and copy...

---

### Post by wildmanne39 on 2011-06-14
> **neiu bee said:**
> hey irihapeti.. thanks for ua repli... 
1. I didn't over write my installation b'coz both OSes installed are in different drives.Its only MBR that is overwritten 
2. I recently upgraded 10.04 to 10.10. I have 10.04 live cd.. also 10.10 netbook line cd, and 10.10 alternate cd
3.I tried a lot but could not mount my "/" partition.. but when i installed GRUB2 using 10.10 alternate cd its not displaying any thing... but here i have a problem.. my / partition was cleared totally and new things were installed after i tried using alternate cd [ initially partition was 14GB/23Gb after GRUB2 installation it is 1.36GB/23GB].
Even then i'm not able to login...i think the GUI might not have installed
So tell me  way to install GUI or login through commnands.
I have not given any login name, password during GRUB2 installation. But its asking when i'm about to login. I tried old one.. but couldn't not do it.
Hi,I also suspect since you did an alternate install that it did not install GUI, so try this
```
sudo apt-get install gdm
```

---

### Post by neiu bee on 2011-06-15
> **wildmanne39 said:**
> Hi,I also suspect since you did an alternate install that it did not install GUI, so try this
```
sudo apt-get install gdm
```


Heyy thats fine but.. i've got another problem... after giving this command, it is asking to update a few files. But i'm not able to connect to internet as i have to login using a user name and password to it. But when i used alternate CD.. it connected automatically using DHCP [i'm not sure but it dispalyed a msg- succesfully connected using DHCP]. So now how do i connect to internet. I have tried "startx" sudo apt-get update.... and a few after trying "gdm" but i struck at connecting to internet. So plz link

---

### Post by neiu bee on 2011-06-15
> **wildmanne39 said:**
> Hi,I also suspect since you did an alternate install that it did not install GUI, so try this
```
sudo apt-get install gdm
```

hey buddy... i did with "gdm". I could connect to net..and i updated my sys. But now there is another problem in the form of "plymouth"
Mountall:Plymouth command failed
Mountall:disconnected from plymouth

It is following einstein's law
"Energy[problem] can neither be created nor be destroyed it[problem] only converts from one [problem] to another"

---

