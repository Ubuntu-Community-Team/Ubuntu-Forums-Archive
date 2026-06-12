---
title: "how to enable a modem in notebook"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by vinthund on 2005-08-02
hello,

I am trying to use a modem in a laptop (hp compaq nx7000). HP web site says it is "Agere Systems AC'97 Modem". I used a tool called scanModem but it produced a result shown below and that did not help me much as I do not what to do now. Anyone can give me a hint? Is it a winmodem or not?

```

marek@ubuntu:~$ ./scanModem

UPDATE=2005_July_21
ONLY use scanModem downloaded as: http://linmodems.technion.ac.il/packages/scanModem.gz

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.

./scanModem: line 258: gcc: command not found
PCIBUS=0000:00:1f.6

Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
            ----:----
Class 0703: 8086:24c6   Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 0e11:0860   Compaq Computer Corporation: Unknown device 0860
0000:00:1f.6 0703: 8086:24c6 (rev 01)
        Flags: medium devsel, IRQ 10

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:24c6 0e11:0860 debian 2.6.10-5-686  3.3.5 none    i686


 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:
        Broadcom
        AgereSystems
        Conexant
        Intel
        Smartlink

 To enable capture of codec information, please briefly login as Root:
         su - root
  Load snd-intel8x0m with:
         modprobe snd-intel8x0m
  Exit Root status
         exit
  and rerun
        ./scanModem

marek@ubuntu:~$ sudo modprobe snd-intel18x0m
FATAL: Module snd_intel18x0m not found.
marek@ubuntu:~$

```

---

### Post by vinthund on 2005-08-02
[QUOTE=vinthund]

```


         modprobe snd-intel8x0m
  Exit Root status
         exit
  and rerun
        ./scanModem

marek@ubuntu:~$ sudo modprobe snd-intel18x0m
FATAL: Module snd_intel18x0m not found.
marek@ubuntu:~$

```[/QUOTE]

sorry, I made a typo error in my command. now I'll go on the correct way and we'll see...

marek

---

### Post by autocrosser on 2005-08-02
In case it is not posted elsewhere--start your search here--

[http://www.linmodems.org/](http://www.linmodems.org/)

also look at--

[http://www.linuxhardware.net/](http://www.linuxhardware.net/)

Both have great information-- ;-)

---

