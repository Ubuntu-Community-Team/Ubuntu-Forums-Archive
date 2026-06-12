---
title: "Maximize battery performance by terminal"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-16
Hello Guys every where 
I am searching the internet to maximize my hp mini battery performance, I found a blog describing how to do that through terminal but an error came what to do please ?
this is the pase of what I did and what the bash told me 
help please 
> fatharrahman@fatharrahman-HP-Mini-110-1100:~$ /etc/init.d/acpi restart
bash: /etc/init.d/acpi: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ cat/etc/init.d/acpi restart
bash: cat/etc/init.d/acpi: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ acpi 
The program 'acpi' is currently not installed.  You can install it by typing:
sudo apt-get install acpi
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ sudo apt-get install acpi
[sudo] password for fatharrahman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-utidylib libtidy-0.99-0 python-feedparser python-rsvg
  python-evolution python-chardet
Use 'apt-get autoremove' to remove them.


---

### Post by fatharraxman on 2010-11-16
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ cat/proc/acpi/battery/BAT/state
bash: cat/proc/acpi/battery/BAT/state: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$

---

### Post by deconstrained on 2010-11-16
When starting the acpi daemon, use 'acpid' in place of 'acpi' (the file names of daemon init scripts differ between Linux distros, mind you). Now that you've installed it, however, it's enabled by default and should be running, so you don't have to start it manually anyways.

The acpi daemon does stuff like automatically dimming/shutting off your monitor, arranging suspend when you close your laptop lid and other nice things. I'm surprised it wasn't installed by default on your system.

Along the lines of getting better battery performance, you could go a step further and disable services or [startup applications](https://help.ubuntu.com/community/AddingProgramToSessionStartup) that you don't need.

Edit: also,
> cat/proc/acpi/battery/BAT/state: No such file or directory
Put a space between 'cat' and the leading slash.:p

---

### Post by fatharraxman on 2010-11-17
Dear/deconstrained
Hello
thank you very much for your kind care
I just want to note that am novice in linux and really wanna know more concerning my problem
> **deconstrained said:**
> When starting the acpi daemon, use 'acpid' in place of 'acpi' (the file names of daemon init scripts differ between Linux distros, mind you).
still I can not use terminal to see battery state as you can see
> fatharrahman@fatharrahman-HP-Mini-110-1100:~$ cat /proc/acpi/BAT/state
cat: /proc/acpi/BAT/state: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ cat /acpi/BAT0/state
cat: /acpi/BAT0/state: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ cat /acpid/BAT/state
cat: /acpid/BAT/state: No such file or directory
fatharrahman@fatharrahman-HP-Mini-110-1100:~$ 

> Now that you've installed it, however, it's enabled by default and should be running, so you don't have to start it manually anyways.
does you mean it is working now ? but my battery still less than 2 hours while in windows it was more than 4 hours how to fix that?

> Put a space between 'cat' and the leading slash.:p

thank you again very much for your kind note i liked it really
have a good time

---

### Post by matt_symes on 2010-11-17
Did not read above post correctly... Sorry. Removed my entry

---

