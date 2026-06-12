---
title: "Which file loads wifi module?"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by lfys on 2007-09-13
My wifi card with chipset acx111 from TI doesn't work with "default" version of module..

With the console I do this to bring up network connection: 

sudo rmmod acx
sudo modprobe acx firmware_ver=1.2.0.30

So where do I have to add "firmware_ver=1.2.0.30" in order to  load the right version at startup?

---

### Post by spd106 on 2007-09-14
Create a file in the /etc/modprobe.d/ directory and add the line as an option.
i.e.
```
echo "options acx firmware_ver=1.2.0.30" | sudo tee /etc/modprobe.d/acx

```

---

### Post by lfys on 2007-09-18
Tried it:

[INDENT][I]dirk@elvis3:~$ sudo rmmod acx
Password:
dirk@elvis3:~$ sudo modprobe acx
WARNING: /etc/modprobe.d/acx line 1: ignoring bad line starting with 'echo'[/I][/INDENT]

Something is wrong.

---

### Post by walkerk on 2007-09-18
> **spd106 said:**
> Create a file in the /etc/modprobe.d/ directory and add the line as an option.
i.e.
```
echo "options acx firmware_ver=1.2.0.30" | sudo tee /etc/modprobe.d/acx

```

```
echo 'options acx firmware_ver=1.2.0.30' | sudo tee /etc/modprobe.d/acx
```

how about that?

or just use gedit :/
```
gksu gedit /etc/modprobe.d/acx
```

now add the line and save..

---

### Post by spd106 on 2007-09-18
Sorry, I wasn't very clear. The code I provided was a one line shell script to create the file. Just copy + paste into a terminal, then enter your password.
i.e.
```
spd106@ubuntu:~$ echo "options acx firmware_ver=1.2.0.30" | sudo tee /etc/modprobe.d/acx
Password:
options acx firmware_ver=1.2.0.30

```

What you should see in the acx file is just the part between the double quotes.

---

### Post by lfys on 2007-09-19
Oh. I'm sorry. I misunderstood.
The line of code you gave me does make the file needed and puts the required option there.

What I did was making the file and then copying your code into is. Stupid!

---

