---
title: "console-ation question!!!!!!!"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by vivek.pandey on 2011-02-26
hi everyone

i have ubuntu 10.10 and a 3g usb modem. my question is how can i connect to internet from the console window and not gui. for gui  i just  need to configure the modem by entering providers nsme and the plan. also /etc/init.d/start networking or simply start networking wont work. i guess it works for wired network
 thanx to all

---

### Post by vivek.pandey on 2011-02-26
any help?

---

### Post by vivek.pandey on 2011-02-26
????????/

---

### Post by realzippy on 2011-02-26
Configure:
```
sudo pppoeconf
```

Start
```
pon dsl-provider
```

---

### Post by vivek.pandey on 2011-02-26
> **realzippy said:**
> Configure:
```
sudo pppoeconf
```

Start
```
pon dsl-provider
```

sorry but it didnt work
when i typed sudo pppoeconf it started to scan devices found walan0 vboxnet and eth0 but after scanning it displayed message that it couldnot find the interface or something sorry i dont remember exact message

---

### Post by pi.boy.travis on 2011-02-26
I've looked everywhere, and I honestly don't think there's a TTY utility to configure 3G modems(without considerable difficulty). You can connect to the internet with the 3G modem with the GUI, then use Alt+F1 to switch to a TTY.

---

### Post by donkyhotay on 2011-02-26
Something in linux that can be done with a GUI but not in the CLI? I don't believe it (unless the software is proprietary). I'd check the man pages for the program you use to connect, it should have CLI switches in there for connecting without GUI. I'm not certain since I don't use a modem myself.

---

### Post by pi.boy.travis on 2011-02-26
> **donkyhotay said:**
> Something in linux that can be done with a GUI but not in the CLI? I don't believe it (unless the software is proprietary). I'd check the man pages for the program you use to connect, it should have CLI switches in there for connecting without GUI. I'm not certain since I don't use a modem myself.

I checked the man pages for the network-manager CLI interface, and there doesn't seem to be any way to access networ-manager's interfacing with PPPoE. There is a CLI interface for that, but the OP said they tried it and it didn't work for them. . . :confused:

---

### Post by vivek.pandey on 2011-02-26
well i guess there would be some way else how people using unix which is only cui get access to net?

---

### Post by pi.boy.travis on 2011-02-26
> **neo_aryan said:**
> well i guess there would be some way else how people using unix which is only cui get access to net?


Any other kind of interface can be brought up easily:

```
sudo service network start
```

It's the 3G modem that has me stumped. . . :/

---

### Post by vivek.pandey on 2011-02-26
> **pi.boy.travis said:**
> Any other kind of interface can be brought up easily:

```
sudo service network start
```

It's the 3G modem that has me stumped. . . :/

i guess sudo start networking also does same as the command you gave

---

### Post by pi.boy.travis on 2011-02-26
> **neo_aryan said:**
> i guess sudo start networking also does same as the command you gave

Yep, they're both interfaces to Upstart.

---

### Post by uRock on 2011-02-26
> **neo_aryan said:**
> any help?

> **neo_aryan said:**
> ????????/
Please wait 24 hours before bumping your thread.

Thank you for your kind consideration,
uRock

---

