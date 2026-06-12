---
title: "Compiling lm-sensors in 2.6.31-19-generic kernel"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-20
The instructions for compiling an lm-sensors module into the kernel are

Copy the two files from:
[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)
to a temporary directory, then run:
$ make
then as root:
# insmod k10temp.ko

I made a temporary folder: makelm. In it are the two files: one I named Makefile and the other k10temp.c.

Running make gave:

mark@Lexington-19-Karmic:~/Desktop/makelm$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/mark/Desktop/makelm/k10temp.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mark/Desktop/makelm/k10temp.mod.o
  LD [M]  /home/mark/Desktop/makelm/k10temp.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'

Then I did:

mark@Lexington-19-Karmic:~/Desktop/makelm$ sudo su

**root**@Lexington-19-Karmic:/home/mark/Desktop/makelm# insmod k10temp.ko

but when that ran, the terminal returned only:

root@Lexington-19-Karmic:/home/mark/Desktop/makelm# 

The make lm now has 7 more files in it, but what do I do to complete the installation and get readings on my panel?





I have linux-headers and I believe all the other compiling software alrady installed.

---

### Post by mcduck on 2010-02-20
Is there any specific reason why you want to compile lm-sensors? If not, just install it from Ubuntu's repositories... ;)

install:
```
sudo apt-get install lm-sensors
```

configure:
```
sudo sensors-detect
```

...and test:
```
sensors
```

if the results seem strange, then edit /etc/sensors.conf to attach correct sensors for correct values, and if necessary, calculate the correct multipliers for readings and set sane min/max values.

What coems to the original problem, successfull commands usually don't give any response, errors do. So check if the module is already succesfully loaded by running "lsmod".

---

### Post by Bachstelze on 2010-02-20
> **mcduck said:**
> Is there any specific reason why you want to compile lm-sensors?

Read more carefully. He doesn't want to compile lm-sensors itself, but a sensors driver that is not shipped with the kernel in the repos.

---

### Post by mcduck on 2010-02-20
> **Bachstelze said:**
> Read more carefully. He doesn't want to compile lm-sensors itself, but a sensors driver that is not shipped with the kernel in the repos.

good point, lucky thing I also answered to the module loading problem... :)

...and to continue that answer, if the module actually was succesfully loaded then just add it to /etc/modules to load it automatically on boot. You'll of course have to do sensors-detect and other configuration part to get lm-sensors to work correctly.

---

### Post by Mark_in_Hollywood on 2010-02-20
I"m confused by the output of sudo sensors-detect:

AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)n
mark@Lexington-19-Karmic:~$ 

If lm-sensors detects the K10 module, what do I have to write to /etc/modules to get it up & running?

---

### Post by Bachstelze on 2010-02-20
The command

```
lsmod
```

will output a list of all loaded modules. In k10temp is in there, you can run

```
sensors
```

and you should see your sensors data.

---

### Post by Mark_in_Hollywood on 2010-02-20
mark@Lexington-19-Karmic:~$ lsmod
Module                  Size  Used by

k10temp                 3680  0 

but when I 

mark@Lexington-19-Karmic:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

Any ideas about this?

---

### Post by mcduck on 2010-02-20
> **Mark_in_Hollywood said:**
> I"m confused by the output of sudo sensors-detect:

AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Chip `AMD K10 thermal sensors' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

Do you want to add these lines automatically? (yes/NO)n
mark@Lexington-19-Karmic:~$ 

If lm-sensors detects the K10 module, what do I have to write to /etc/modules to get it up & running?
Did you test with the "lsmod" comamnd if your module loaded correctly when you ran the "insmod" command? If it did load, just add the name of the module to /etc/modules.

---

### Post by Mark_in_Hollywood on 2010-02-20
Did you test with the "lsmod" comamnd if your module loaded correctly when you ran the "insmod" command? If it did load, just add the name of the module to /etc/modules.

No, I had no sense that testing was needed. My problem is I have no idea of what the name of the module is. I have several files in my temporary directory where the compiling took place. Currently in /etc/modules the only driver is:

powernow-k8

the compiling only gave names like:

k10temp.ko
k10temp.c
k10temp.mod.c
k10temp.mod.o
k10temp.o

and

Makefile
Module.markers
Module.symvers
modules.order

that's all there is, so I have no file named:

powernow-k10 or similar.

---

