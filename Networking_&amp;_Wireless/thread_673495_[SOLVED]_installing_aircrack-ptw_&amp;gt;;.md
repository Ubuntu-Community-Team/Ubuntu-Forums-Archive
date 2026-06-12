---
title: "[SOLVED] installing aircrack-ptw &amp;gt;;\"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by thefatmoop on 2008-01-20
this is a complete noob question but i can't get the dumb thing to install

sudo apt-get install libpcap0.8-dev

sudo apt-get install build-essential


```
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ ls
aircrack-ptw    aircrack-ptw-lib.c  attacksim.c  README
aircrack-ptw.c  aircrack-ptw-lib.h  Makefile
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ make 
make: `aircrack-ptw' is up to date.
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ make install
make: *** No rule to make target `install'.  Stop.
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ 
```

---

### Post by kevdog on 2008-01-20
Read the README file.

Then try again with

make clean
make
sudo make install

---

### Post by thefatmoop on 2008-01-20
euphoria@Euphoria:~/Desktop$ cd aircrack-ptw-1.0.0
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ make clean
rm -f aircrack-ptw attacksim
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ make
gcc -o aircrack-ptw -Wall -fomit-frame-pointer -O3 -lpcap aircrack-ptw.c aircrack-ptw-lib.c
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$ sudo make install
[sudo] password for euphoria:
make: *** No rule to make target `install'.  Stop.
euphoria@Euphoria:~/Desktop/aircrack-ptw-1.0.0$

---

### Post by kevdog on 2008-01-20
What's the README file state??  Maybe its meant to be installed manually or by hand.

---

### Post by thefatmoop on 2008-01-20
not alot, i had no problems installing it at all in backtrack 


This is aircrack-ptw, an advanced wep cracking tool.

aircrack-ptw has been written by Erik Tews, Andrei Pychkine and Ralf-Philipp Weinmann.

This software is provided for education only. Only use it against your
owne networks.

Contents:
 - attacksim
     * Simulation of our attack, not usefull for wep-cracking,
       just for education.
 
 - aircrack-ptw
     * The actual attack tool.


For more informations see:

[http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/](http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/)

---

### Post by thefatmoop on 2008-01-20
here's the instructions for backtrack (which i didn't need before... owell) i didn't notice that i'm using aircrack-ng version .0.9.1 and according to backtrack "Note : This is no longer needed since Aircrack-ng 0.9+ includes PTW."

```
 cd /tmp
 wget http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/download/aircrack-ptw-1.0.0.tar.gz
 tar -xzvf aircrack-ptw-1.0.0.tar.gz
 cd aircrack-ptw-1.0.0
 sed -e "s/-O3 -lpcap/-O3/" -e "s/\(gcc.*b.c\)/\1 -lpcap/" Makefile > Makefile.new
 cp Makefile Makefile.old; mv Makefile.new Makefile
 make
```
(didn't work)

guess i'm fine. i'm so used to backtrack 2 and installing those required packs

i'm a moron who is rushing through the install too fast to read this lol
```
 Static WEP cracking options:

      -c         : search alpha-numeric characters only
      -t         : search binary coded decimal chr only
      -h         : search the numeric key for Fritz!BOX
      -d <mask>  : debug - specify mask of the key (A1:XX:CF:YY)
      -m <maddr> : MAC address to filter usable packets
      -n <nbits> : WEP key length :  64/128/152/256/512
      -i <index> : WEP key index (1 to 4), default: any
      -f <fudge> : bruteforce fudge factor,  default: 2
      -k <korek> : disable one attack method  (1 to 17)
      -x or -x0  : disable last keybytes bruteforce
      -x1        : enable last keybyte bruteforcing (default)
      -x2        : enable last two keybytes bruteforcing
      -X         : disable bruteforce multithreading (SMP only)
      -y         : experimental single bruteforce mode
  **_    -z         : PTW attack_**
      -s         : show ASCII version o
```

---

### Post by kevdog on 2008-01-20
What's the difference between aircrack-ng and aircrack-ptw by the way.  Ive only used the ng version.

---

### Post by thefatmoop on 2008-01-20
ohh gosh you haven't cracked wep if you haven't used ptw. Well they're now one program, but let me explain the old version

aircrack logs/tracks the data.cap files and it would require like what 1million packets to crack a 128bit wep? well aircrack-ptw is just a cracking program (so it just breaks down the .cap file) and requires about 1/5th the packet samples so you can crack a 64bit wep with around 30,000-60,000 packet samples. and compared to aircrack-ng for example it can take 20+ minutes to crack wep, well ptw takes about 1 minute max

in other words an absolute must have when cracking wep

---

### Post by kevdog on 2008-01-20
I take it that the ptw requires packet injection -- so patched drivers are necessary!  Where do I get this ptw program.  It sounds like a winner to me!  (I thought with packet injection with the ng program it cut the collection time down to 1/5 the time compared to conventional cracking

---

### Post by thefatmoop on 2008-01-20
if you have an older version of aircrack-ng you should need to use this 

```
 cd /tmp
 wget http://www.cdc.informatik.tu-darmstadt.de/aircrack-ptw/download/aircrack-ptw-1.0.0.tar.gz
 tar -xzvf aircrack-ptw-1.0.0.tar.gz
 cd aircrack-ptw-1.0.0
 sed -e "s/-O3 -lpcap/-O3/" -e "s/\(gcc.*b.c\)/\1 -lpcap/" Makefile > Makefile.new
 cp Makefile Makefile.old; mv Makefile.new Makefile
 make
```
and the wget is the tar obviously 

i would suggest updating to the newer version of the aircrack-ng suite since Aircrack-ng 0.9+ includes the PTW .cap interpretator

here's the site for aircrack-ng 
[http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php)

i just saw this 
New tools: airtun-ng, packetforge-ng (improved arpforge), wesside-ng, easside-ng, airserv-ng, airolib-ng and airdriver-ng

the wesside-ng attack is supposed to be AMAZING as seen on the backtrack 3 trailer

---

### Post by kevdog on 2008-01-20
Ok, noob here when it comes to aircrack, I installed the latest aircrack version, and then just tried the basic attack as explained in the beginner tutuorial.  I read the roadmap about different attacks, but it didnt seem to make a lot of sense to me.  I dont know when to use what attack and in what situation as they seems to become increasingly more complex.  The tutorials describe the different attacks, but dont do a real good job explaining when and why you would want to use each attack.

---

