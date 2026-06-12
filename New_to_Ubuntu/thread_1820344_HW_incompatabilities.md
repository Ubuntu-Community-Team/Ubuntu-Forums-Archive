---
title: "HW incompatabilities?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by nnjond on 2011-08-07
Hi,

I've had problems with every os I've tried on my pc; including distros, (such as my present Ubuntu 11.04), that work fine on my Laptop. So Now I think I should investigate the possoibility of hw incompatabilities. Please could you advice me on what pc info I should collect, and how.

Thanks for your time.

-This i must establish with the live cd

---

### Post by haqking on 2011-08-07
> **nnjond said:**
> Hi,

I've had problems with every os I've tried on my pc; including distros, (such as my present Ubuntu 11.04), that work fine on my Laptop. So Now I think I should investigate the possoibility of hw incompatabilities. Please could you advice me on what pc info I should collect, and how.

Thanks for your time.

-This i must establish with the live cd


depends what hardware you are having issues with.

check your hardare is supported under linux here [http://linuxhcl.com/](http://linuxhcl.com/)

if it is then it might be faulty.

be more specific about what hardware you are having incompatabilitied with.
version numbers.
firmware
drivers
error messages

etc etc

---

### Post by Old_Grey_Wolf on 2011-08-07
I have had problems with wireless NICs and Graphics cards/chipsets. If you have the live CD you can type a command in the terminal to list the hardware.
```
lshw

```
or you may need to use
```
sudo lshw
```
I can't remember if the live CD requires sudo; however, I don't think it does since you don't need a password to log in.

Then research the devices to determine if they are compatible with the OS you want to try.

---

### Post by nnjond on 2011-08-07
I thought there were some Bash commands that would reveal all the relevant.

I don't want to take my pc apart and examine it's innards unless I have to.

---

### Post by Daveth on 2011-08-07
or load up Sysinfo from the software centre which displays the innards for you!

---

### Post by haqking on 2011-08-07
> **nnjond said:**
> I thought there were some Bash commands that would reveal all the relevant.

I don't want to take my pc apart and examine it's innards unless I have to.

so you want to know what hardware you have you mean ?

[FONT=Verdana]sudo apt-get install hardinfo

this should give you everythign you need, it is like device manager in windows, should install then give you menu option under system tools
[/FONT]

---

