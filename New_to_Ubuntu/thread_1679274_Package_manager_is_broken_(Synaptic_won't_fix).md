---
title: "Package manager is broken (Synaptic won't fix)"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by woodge on 2011-01-31
I'm running 10.04 LTS. The Ubuntu software center either freezes and quits or tells me my "package system is broken" when I try to install anything. 

As prompted by the software center, I tried:
```
apt-get install -f
```I got this error:

E: Read error - read (5: Input/output error)
E: The packge lists or status file could not be parsed or opened.

I went to the synaptic package manager and immediately got this error:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.#

Synaptic then quits.
What can I do?

---

### Post by pastalavista on 2011-01-31
You need to use 'sudo' when using any apt-get command, to gain administrative (root) privileges. Try these commands one at a time```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f
```

---

### Post by khamil8686 on 2011-01-31
i did some googling to see if i could find anything and i found a couple things you could try

0. i always jump to complex solutions before i think of simple ones, make sure that youre using sudo like pastalavista said :)

1.
```
sudo apt-get -f install
```
you said you tried this one however you didnt list that you had the install part of the command, possibly try the install?

2. to reinstall synaptic try running the command
```
sudo apt-get install synaptic
```

3. you might be out of disk space on your partition possibly? try this command
```
df -h
```
and see if you have any free space on your partition

4. something messed up your sources.list file possibly
A. Check /etc/apt directory and see if there is a original or old backup of your sources.list file and run
```
cp /etc/apt/*name of backup here like sources.list.backup* /etc/apt/sources.list
```
to replace the current sources.list with the original or old backup one
B. Fire up a live cd of your current version 10.04 and then mount your system partition and copy the /etc/apt/sources.list file from the live cd session to /etc/apt/sources.list in your system on your hard drive
C. Find online somewhere where someone has a copy of 10.04's original sources.list file and replace the contents of your current one with the sources.list that you found (make sure to backup your current one first)

run this code to make a backup of your current sources.list just in case before you make any changes to it
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

post back if you have troubles :)

---

### Post by sandyd on 2011-01-31
> **woodge said:**
> I'm running 10.04 LTS. The Ubuntu software center either freezes and quits or tells me my "package system is broken" when I try to install anything. 

As prompted by the software center, I tried:
```
apt-get install -f
```I got this error:

E: Read error - read (5: Input/output error)
E: The packge lists or status file could not be parsed or opened.

I went to the synaptic package manager and immediately got this error:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.#

Synaptic then quits.
What can I do?
package lists are corrupt
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

```

---

### Post by matt_symes on 2011-01-31
Hi

I would run fsck on the partition as well.

Kind regards

---

### Post by makeos on 2011-04-19
> **sandyd said:**
> package lists are corrupt
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

```
i tried this and got 
```
E: Lists directory /var/lib/apt/lists/partial is missing.
```

---

### Post by sandyd on 2011-04-19
> **makeos said:**
> i tried this and got 
```
E: Lists directory /var/lib/apt/lists/partial is missing.
```
```

sudo mkdir /var/lib/apt/lists/partial
```

---

### Post by makeos on 2011-04-20
> **sandyd said:**
> ```

sudo mkdir /var/lib/apt/lists/partial
```

Thank you..works like a charm now.

---

