---
title: "Error in my ear or ubuntu!!!"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by mountdiat on 2010-09-21
Hi all I recently install abuntu 10.4 ....and  not use liunx befor 
I donot hear any sound .....how can i solve this 
my mother board is gigabit g41 
pleas step by step .....iam recently biggner
thanx all ........sorry for my english

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> Hi all I recently install abuntu 10.4 ....and  not use liunx befor 
I donot hear any sound .....how can i solve this 
my mother board is gigabit g41 
pleas step by step .....iam recently biggner
thanx all ........sorry for my english
Welcome to Ubuntu Forums!
First, go outside and check if you can hear.
Then, if you can, follow Fix your sound! in my signature.

---

### Post by mountdiat on 2010-09-21
thanks ......but arts system notfound   what i do ????/

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> thanks ......but arts system notfound   what i do ????/
Don't worry about aRts.
Go on with the tutorial.

---

### Post by mountdiat on 2010-09-21
ok

---

### Post by JBAlaska on 2010-09-21
Your board seems to use a Realtek ALC888B sound chipset. Are you trying to use HDMI or analog sound output?

---

### Post by mountdiat on 2010-09-21
iam sorry for lateing ......i was praying
after installing oss
ido this 
sudo apt-get install -y gstreamer0.10-plugins-bad

now downloading.....what after that???

oh' sound icon disapeared

---

### Post by bradleypariah on 2010-09-21
> **lkjoel said:**
> 
First, go outside and check if you can hear.

lmfao :lol:

---

### Post by mountdiat on 2010-09-21
> **bradleypariah said:**
> lmfao :lol:

pleas help ........at one day you waseas me:mad:

---

### Post by mountdiat on 2010-09-21
where is **bradleypariah or  **[lkjoel]("http://ubuntuforums.org/member.php?u=1072696")

---

### Post by mountdiat on 2010-09-21
> **mountdiat said:**
> iam sorry for lateing ......i was praying
after installing oss
ido this 
sudo apt-get install -y gstreamer0.10-plugins-bad

now downloading.....what after that???

oh' sound icon disapeared
why not help:confused:

---

### Post by mountdiat on 2010-09-21
sound icon not appeared and device not detec

---

### Post by bradleypariah on 2010-09-21
Right-click on your panel.
Choose "Add to Panel..."
In the new window, choose "Notification Area".
This should show your Sound Icon.
If it doesn't, just go to System > Preferences > Sound.
Ensure you have chosen the correct outputs and that you do not have the sound muted.
If these things are not your problem, consider using Pulse Audio instead of ALSA, or vice-versa.
There are great tutorials out there on how to replace your audio drivers.

---

### Post by bradleypariah on 2010-09-21
Another option would be to go to Applications > Ubuntu Software Center 
Then download the GNOME ALSA Mixer.
This GUI is a great way to look for random outputs that may be turned down/off.

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> why not help:confused:
Type in a Terminal:
```
osstest
```
Do you hear sound?

---

### Post by mountdiat on 2010-09-21
yes

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> yes
Good.
Now follow the instructions here:[http://ubuntuforums.org/showpost.php?p=9872284&postcount=4]("http://ubuntuforums.org/showpost.php?p=9872284&postcount=4")

---

### Post by mountdiat on 2010-09-21
see this 
OSS not installed properly.
Please run ./CPanel.sh -1, reboot, and run ./CPanel.sh -2

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> see this 
OSS not installed properly.
Please run ./CPanel.sh -1, reboot, and run ./CPanel.sh -2
Is that the only thing you see?
If not, please tell us what it also shows.
If so, then run the commands shown.

---

### Post by mountdiat on 2010-09-21
whe run ...................

besmellah@besmellah-desktop:~$ cd
besmellah@besmellah-desktop:~$ ./CPanel.sh -r
This script comes with NO waranty.
Using Ubuntu 10.04 is strongly recommended.

Press ENTER to continue, or CTRL-C to exit.

Audio currently set to 
[sudo] password for besmellah: 
OSS is already loaded.
Audio is muted

Unmuting audio...
Press ENTER to continue, or CTRL-C to exit.


OSS not installed properly.
Please run ./CPanel.sh -1, reboot, and run ./CPanel.sh -2
besmellah@besmellah-desktop:~$

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> whe run ...................

besmellah@besmellah-desktop:~$ cd
besmellah@besmellah-desktop:~$ ./CPanel.sh -r
This script comes with NO waranty.
Using Ubuntu 10.04 is strongly recommended.

Press ENTER to continue, or CTRL-C to exit.

Audio currently set to 
[sudo] password for besmellah: 
OSS is already loaded.
Audio is muted

Unmuting audio...
Press ENTER to continue, or CTRL-C to exit.


OSS not installed properly.
Please run ./CPanel.sh -1, reboot, and run ./CPanel.sh -2
besmellah@besmellah-desktop:~$
Then run:
```
./CPanel.sh osspart1
#REBOOT COMPUTER
./CPanel.sh osspart2

```

---

### Post by mountdiat on 2010-09-21
oh. another download         what after that

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> oh. another download         what after that
Its already done?

---

### Post by mountdiat on 2010-09-21
see....in sound panel ......hardware not fond 
and sound not appear in add topanle
sorry for your time !!

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> see....in sound panel ......hardware not fond 
and sound not appear in add topanle
sorry for your time !!
So is the command finished?
If so, then type in:
```
./CPanel.sh -r
```

---

### Post by mountdiat on 2010-09-21
what after download ?
every time i install abuntu must do all these steps?
sorry again for ur losing time

---

### Post by mountdiat on 2010-09-21
> **lkjoel said:**
> So is the command finished?
If so, then type in:
```
./CPanel.sh -r
```
download time about 2h!!

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> download time about 2h!!
On what package?

---

### Post by mountdiat on 2010-09-21
i dont know  but about 62 upgraded

---

### Post by lkjoel on 2010-09-21
It's updating the entire system.
Just wait until it is finished.

---

### Post by lkjoel on 2010-09-21
Remember to always check the Terminal window.
It might be finished, so you must do what it tells you to do.

---

### Post by mountdiat on 2010-09-21
> **lkjoel said:**
> Remember to always check the Terminal window.
It might be finished, so you must do what it tells you to do.
thanks lkjoel  problem solved :KS
when i install new abuntu ...must i make these steps again??

---

### Post by aktiwers on 2010-09-21
> **mountdiat said:**
> thanks lkjoel  problem solved :KS
when i install new abuntu ...must i make these steps again??

Only if they did not fix this in the new version of Ubuntu :)

---

### Post by lkjoel on 2010-09-21
> **mountdiat said:**
> thanks lkjoel  problem solved :KS
when i install new abuntu ...must i make these steps again??
If the sound doesn't work... yes.

---

### Post by mountdiat on 2010-09-22
> **lkjoel said:**
> If the sound doesn't work... yes.
 i install abuntu again......and  install sound in about 2 minutes :)
=========================================================
But another question :confused::-
when i was install abuntu i make root partition and home partition and swap area .....ok
now .........if  i install abuntu again(10.10):popcorn:  and select root partition ....are all my saved data in home partition well removed???????????

---

### Post by lkjoel on 2010-09-22
> **mountdiat said:**
> i install abuntu again......and  install sound in about 2 minutes :)
=========================================================
But another question :confused::-
when i was install abuntu i make root partition and home partition and swap area .....ok
now .........if  i install abuntu again(10.10):popcorn:  and select root partition ....are all my saved data in home partition well removed???????????
Yes.

---

### Post by mountdiat on 2010-09-22
> **lkjoel said:**
> Yes.
yes!!!
so. how can i save my data?...and when i make other partitions with extention ext4 i cant mange them (copy and past)

---

### Post by mountdiat on 2010-09-22
please how make partitions and control them (copy past )

---

### Post by lkjoel on 2010-09-23
> **mountdiat said:**
> yes!!!
so. how can i save my data?...and when i make other partitions with extention ext4 i cant mange them (copy and past)
You take a USB Flash Drive, and copy all your data into it.

---

