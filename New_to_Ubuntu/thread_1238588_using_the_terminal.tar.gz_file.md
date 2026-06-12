---
title: "using the terminal/.tar.gz file"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Ditas on 2009-08-12
alright, i've read a few guides on how to do this, and i'm still lost; probably missing something blindingly obvious...

i downloaded the vpn software that my university offers to connect to wireless; unfortunately they don't support linux/ubuntu beyond that, and i'm at a loss as for how to decompress/compile/run a .tar.gz file

i believe i've "unzipped" it using a gui (right click, uncompress file), as its now a folder, and i can view the readme (which is also no help)

right now, i'm trying to go through the steps offered in some of the guides i've seen, most are like this:
[INDENT] 
[LIST=1]
[*]For a GZipped tarball: tar –zxvf filename.tar.gz (or filename.tgz)
[*]For a BZipped tarball: tar jzvf filename.tar.bz (or filename.tbz)
[*]./configure
[*]make
[*](as root) make install
[/LIST]

Unfortunately, i keep getting a message that says "this is not a directory" and i am not sure how to make the terminal work, in the broadest explanation 

i'm somewhat versed in using terminals on DOS/Windows, and have even fooled around with them on a mac, but this whole deal is beyond me. if it helps, i'm using the updated ubuntu that came with my dell mini 9 netbook; not completely sure if they have something proprietary going on, but i wouldn't be surprised..

anyway, i'm sure this answer is out there, but at this point (i'm about 3 or 4 hours into working with ubuntu) i'm not even sure how to sift out the information i need in a search, so i'm throwing myself on your mercy, as it were.

thanks for any help you can offer, and again my apologies, i'm sure this question has been asked a million and a half times.

TLDR: how in hell do i install a .tar.gz file
[/INDENT]

---

### Post by Ditas on 2009-08-12
also, specifically; my prompt looks like this:

kris@kris :~$

i'm not sure where in the file system the cash sign puts me, or how i change that

---

### Post by Ditas on 2009-08-12
sigh, ignore that last one; i'm learning as i post apparently alot of these answers are as blindingly obvious as i had thought they were

---

### Post by vegesm on 2009-08-12
The first two steps is unzipping the tar.gz file. You already do that so skip those two steps. Then change to the directory where you unzipped the file with:
cd <dirname>
It's the same as in Windows.
Then type ./configure and make. For the last step type
```
sudo make install
```
It'll ask for your password. type it and you should be ready

---

### Post by Ditas on 2009-08-12
thank you for the help so far; i believe i've made it to the directory, but when i type in ./configure my message is "no such file or directory"

currently my prompt is at: kris@kris:~/Desktop/vpnclient$

which is the folder that all of the files are in

---

### Post by vegesm on 2009-08-12
Do you have a file called configure in that directory? If not just skip that step. Usually you only need make.

BTW if that VPN software isn't something unique you could install it via Synaptic. Go to System -> Administration->Synaptic and search for the name of the VPN software. If it finds it you can easily install it by double-clicking on it

---

### Post by Ditas on 2009-08-12
there is no configure file; there is a config.h file but i'm not sure if thats similar

when i type in make, the terminal does this:

kris@kris:~/Desktop/vpnclient$ make
make -C /lib/modules/2.6.24- lpia/build SUBDIRS=/home/kris/Desktop/vpnclient modules
*** /lib/modules/2.6.24-24- lpia/build: No such file or directory.  Stop.
*** [default] Error 2

then returns me to promps

---

### Post by Ditas on 2009-08-12
i should probably also mention that the source code was provided by the university for linux, rather than specifically for ubuntu, but i'm not sure how that would affect the install

---

### Post by vegesm on 2009-08-12
Type make -C /lib/modules/2.6.xx.xxx/build. In the place of "2.6.xx.xxx" write your kernel version. The easiest way to find that out is to go /lib/modules in the file manager. The folder which is there has the same name as your kernel.

---

### Post by unutbu on 2009-08-12
Ditas, have you installed the build-essential package?
If not, try that.

---

### Post by Ditas on 2009-08-12
i do not think i have build-essential; in my add/remove list it is not listed, i looked on google on the computer i'm using for a .deb version, but could not find a link to download from

i also was not able to get make -C /lib/modules/2.6.xx.xxx/build. to work; in my /lib/modules/ directory, there are three folders; the most recent of which is 2.6.24-24-lpia

---

### Post by unutbu on 2009-08-12
Click System>Admin>Synaptic and select and install build-essential via the GUI, or In a terminal run```

sudo apt-get install build-essential
```

I'm not sure about the rest of the compiling problem, but I think build-essential is essential for compiling.

---

