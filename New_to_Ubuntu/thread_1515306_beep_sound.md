---
title: "beep sound"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by maroofi on 2010-06-22
[SIZE=3]hello
i m reading "the linux command line by William E. Shotts, Jr." and it says using [/SIZE]
[SIZE=5]echo "Time's up " $'\a'[/SIZE]   or[SIZE=5]
echo -e "Time's up\a"[/SIZE]
[SIZE=3]will print "time's up" and make a beep sound. and when i type it in bash the output is "Time's up" but it doesnt make beep or any sound at all.
is it my hardware or what?(i know the internal speaker works fine and i test it in windows and make beep sound using this \a but i dont know y it doesnt work in ubuntu.)
i use ubuntu 10.04 and HP Compaq nc6000.
thx in advance
[/SIZE]

---

### Post by bruno9779 on 2010-06-22
After reading your post I realized that it is not working here either.

I have been googling wide and far, and I have come up with this:

```
modprobe -l pcspkr
sudo modprobe pcspkr
```

Now it works fine

I am going to post back after rebooting to see if the change persists

---

### Post by maroofi on 2010-06-22
i read help for modprobe and i guess it adds or remove modules from linux kernel ... right?
but there is a problem here: what is modules or what is linux kernel...what are these things guys....:confused:
and i did what you said but it didnt work for me....

---

### Post by bruno9779 on 2010-06-22
pcspkr, as the name suggests is the module for the PC speaker.

Explaining the linux kernel, its history and such is an huge task.

Read wiki's entry for "linux kernel", that will give you a better idea that I ever could

---

### Post by maroofi on 2010-06-22
thx for the help but still got problem with this beep sound.i think it's not that important.but i realy like to solve it instead of ignoring it.
(see my new avatar? isnt it beautiful?)


i searched the forum and find this :

lsmod | grep pcspkr

and the result is :
pcspkr                  1518      0 
what does it means? and the speaker still doesnt work.

---

### Post by bruno9779 on 2010-06-22
```
lsmod | grep pcspkr
```

is to confirm that the pcspkr module is loaded. And it looks like it is

---

### Post by maroofi on 2010-06-22
i dont know how to test it in ubuntu but i have tested it in windows before.and it works fine.

---

### Post by philinux on 2010-06-22
@maroofi,

pcspkr is blacklisted. You'll have to comment out the relevant line in this file to get it to load on startup.

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by maroofi on 2010-06-22
i found this line  ("blacklist pcspkr") at the blacklist.conf file and put # before it then save it and restart my computer.it still doesnt work.:confused:

---

### Post by philinux on 2010-06-22
> **maroofi said:**
> i found this line  ("blacklist pcspkr") at the blacklist.conf file and put # before it then save it and restart my computer.it still doesnt work.:confused:

```
lsmod | grep pcspkr
```

Does the above show the module loaded?

You might have to un-blacklist snd_pcsp as well, not sure. Worth a go, you can always revert these changes easily.

---

### Post by maroofi on 2010-06-22
i did unblacklist both pcspkr and snd_pcsb by putting # before them.but it didnt work.

```

sourena@sourena-laptop:/$ lsmod | grep pcspkr
pcspkr                  1518  0 
sourena@sourena-laptop:/$ 

```

---

### Post by phr0ze on 2010-06-22
Perhaps it's easier to find a way to script a beep through the sound card instead if that's a solution that will work for you.

---

### Post by philinux on 2010-06-22
> **phr0ze said:**
> Perhaps it's easier to find a way to script a beep through the sound card instead if that's a solution that will work for you.

He could use this. Need to install mplayer from repo.

```
mplayer /usr/share/sounds/ubuntu/stereo/dialog-information.ogg
```

Works a treat.

---

### Post by maroofi on 2010-06-22
yea it works but i have to install mplayer first.but i played it with movie player.

---

### Post by philinux on 2010-06-22
> **maroofi said:**
> yea it works but i have to install mplayer first.but i played it with movie player.

Yes it will but if you use mplayer it is command line based so no distracting gui appears.

---

### Post by maroofi on 2010-06-22
it is 9MB and i installed it using
sudo apt-get install mplayer
and it works through command line.
thanks.

---

### Post by Lampi on 2010-06-22
just some thoughts:

```
groups <your username>
```
make sure the user is part of group audio and video, if not:

```
sudo adduser <your username> audio
sudo adduser <your username> video
```

now let's install a small tool called beep - this just does what it says:
```
sudo aptitude install beep
```
Now, test it in terminal, run:
```
beep
```
If it still does *NOT* work and you really commented out the blacklist thingy in modprobe.d + had a reboot then I'd seriously consider checking the hardware :lolflag: maybe the speaker is not connected then ...

---

### Post by maroofi on 2010-06-22
using 
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
i did blacklist pcspkr and snd_pcsd
and as you said :
```

sourena@sourena-laptop:~$ groups sourena
sourena : sourena adm dialout cdrom plugdev lpadmin admin sambashare
sourena@sourena-laptop:~$ sudo adduser sourena audio
Adding user `sourena' to group `audio' ...
Adding user sourena to group audio
Done.
sourena@sourena-laptop:~$ sudo adduser sourena video
Adding user `sourena' to group `video' ...
Adding user sourena to group video
Done.

```
and then :
```

sourena@sourena-laptop:~$ sudo aptitude install beep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  beep 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.1kB of archives. After unpacking 106kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  beep 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes            
Writing extended state information... Done
Get:1 http://ir.archive.ubuntu.com/ubuntu/ lucid/universe beep 1.2.2-24 [25.1kB]
Fetched 25.1kB in 1s (15.1kB/s)
Preconfiguring packages ...
Selecting previously deselected package beep.
(Reading database ... 128887 files and directories currently installed.)
Unpacking beep (from .../beep_1.2.2-24_i386.deb) ...
Processing triggers for man-db ...
Setting up beep (1.2.2-24) ...

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


```
and then when i type beep nothing happen.and i am realy sure that my internal speaker works fine.
but thanks for the help...we realy tried but it didnt work maybe mplayer is the best solution as philinux said.

---

### Post by Lampi on 2010-06-22
> **maroofi said:**
> using 
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
i did blacklist pcspkr and snd_pcsd
and as you said :
I said COMMENT OUT this means make it look like this:
```
# blacklist pcspkr
```
then reboot

now beep works or your speaker is out of order today ;)

---

