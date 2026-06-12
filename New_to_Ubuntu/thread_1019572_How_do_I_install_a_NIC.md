---
title: "How do I install a NIC"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Douglas G. on 2008-12-23
Trying to help out my neighbor, old 1.3 ghz P3, with a older 3com 3c905b Network card and ubuntu will not see it, or load the driver automatically. I need to find a driver and load it, and being a linux/ubuntu newbie, I have NO IDEA how to make this happen..

Ubuntu is loaded and running fine. NIC was tested in a (dare I say it?) Windows system and works great.

---

### Post by northern lights on 2008-12-23
Can you please run```
sudo lshw -C network
```on your neighbor's machine and post the output here?

USB flashdrive for transfer might be the easiest, rather than manual typing...

---

### Post by halitech on 2008-12-23
do you know if the NIC is a PCI or ISA card?

ISA is harder to set up and configure.

---

### Post by Douglas G. on 2008-12-23
It's PCI. Ubuntu also says there is no network

---

### Post by northern lights on 2008-12-23
Where does it say that? Can you please verify that there is not output for the above? Thank you.

---

### Post by halitech on 2008-12-23
ok, in addition to the output from Northern lights, can you also post the output of
```
sudo ifconfig
```

---

### Post by Douglas G. on 2008-12-23
I will be able to get to computer in about an hour. 

Remember I am a linux newbie, how do I transfer the information from the commands to a flash drive.

---

### Post by hyper_ch on 2008-12-23
please run

```

lspci

```
and post the output here embraced in [noparse]```

```[/noparse] brackets

---

### Post by halitech on 2008-12-23
since you will need to transfer from 1 system to another, run the commands like this
```
sudo lshw -C network > network.txt
```
```
sudo ifconfig > ifconfig.txt
```

you will then find 2 txt files in the /home folder that you can copy to the thumb drive

the > tells the system to pipe the output to a text file instead of displaying them on the screen

---

