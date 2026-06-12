---
title: "List of Beginner Questions"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by italianoman421 on 2009-05-03
List of Beginner Qs

 I have a Dell Inspiron 9300 that I have not put Ubuntu on yet and I do not have a windows XP disc for it since this model uses the F11 key to reinstall the XP OS. If I partition my disc and load Ubuntu 9.04, will the F11 key still be an option to restore the computer to factory settings if needed?

These Qs are about a Dell Inspiron 8200 running Ubuntu 9.04

How do I check to see how much of my CPU is being used on Ubuntu 9.04? I’m afraid the computer itself may be overheating.

I have a netgear wireless card that is about 7 years old, and it barely picks up a wireless signal. Is there a program or something I need to execute or do I need a new card supported by Linux?

Thanks

---

### Post by pbpersson on 2009-05-03
You can see how much CPU is being used by using System Monitor

The F11 key might rely upon a small disk partition being left untouched - at least that how it was in the old days with Compaq computers.

I know nothing about wireless cards

---

### Post by Dex73 on 2009-05-03
To check usage go to System/Administration/System Monitor on Hardy Heron. Could be the same.

---

### Post by Elfy on 2009-05-03
I would use a terminal and run top to find out cpu usage - the system monitor uses more than the terminal.

People will need more information about the wireless card - try running 

```
lspci
```in a terminal, look for the netwrok card and give us that.

---

### Post by blackened on 2009-05-03
> **italianoman421 said:**
> ...How do I check to see how much of my CPU is being used on Ubuntu 9.04? I’m afraid the computer itself may be overheating...

Install and use sensors panel applet (or the full lm-sensors, or even gkrellm) so that you can monitor the system's actual temperatures.

```
sudo apt-get install sensors-applet
```
or
```
sudo apt-get install lm-sensors
```
or
```
sudo apt-get install gkrellm
```

---

### Post by Old_Grey_Wolf on 2009-05-03
> **italianoman421 said:**
> I have a Dell Inspiron 9300 that I have not put Ubuntu on yet and I do not have a windows XP disc for it since this model uses the F11 key to reinstall the XP OS. If I partition my disc and load Ubuntu 9.04, will the F11 key still be an option to restore the computer to factory settings if needed?

Just in case something goes wrong when you install Ubuntu, call Dell, and ask for a recovery CD. They will want the service tag number found on the bottom of the laptop.

---

### Post by Spiritous on 2009-05-03
> **pbpersson said:**
> You can see how much CPU is being used by using System Monitor

The F11 key might rely upon a small disk partition being left untouched - at least that how it was in the old days with Compaq computers.

I know nothing about wireless cards

No, the BIOS is built into the MainFrame now... In a battery

---

### Post by SentientFluid on 2009-05-03
When is the F11 key used?  If it's used during boot then it's controlled by the BIOS.  In that case it won't matter what you do so long as you don't touch the recovery partition.  I don't rmember, however, if using the recovery partition will affect any partitions you've changed to install Ubuntu.  Best bet is to ask Dell for the recovery disks as mentioned above.

---

### Post by arapa on 2009-05-03
> How do I check to see how much of my CPU is being used on Ubuntu 9.04? I’m afraid the computer itself may be overheating...

As stated above gkrellm is a great tool for monitoring temps.  

To quickly see what your system is doing as far as CPU% there is a GUI tool under SYSTEM>ADMINISTRATION>SYSTEM MONITOR that displays CPU/processes,memory etc.

Also there is a command using the terminal (APPLICATIONS>ACCESSORIES>TERMINAL) called top which gives you an overview.

---

### Post by blackened on 2009-05-03
> **arapa said:**
> ...Also there is a command using the terminal (APPLICATIONS>ACCESSORIES>TERMINAL) called top which gives you an overview.

And also, beloved by all for its color-coding and advanced sorting abilities, there is htop.

---

