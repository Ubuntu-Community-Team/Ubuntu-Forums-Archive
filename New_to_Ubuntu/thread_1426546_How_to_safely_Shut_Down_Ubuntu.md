---
title: "How to safely Shut Down Ubuntu?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-10
I used to enter **init 0** in terminal to shutdown my system..Is this safe?

---

### Post by Tikkyca on 2010-03-10
Dont know i just click on the username and click on shut down.

---

### Post by llawwehttam on 2010-03-10
I have used ```
init 0
``` for ages and see no problem with that.

If your very worried and paranoid then use ```
shutdown -h now
``` but I don't think it makes too much difference.

---

### Post by doas777 on 2010-03-10
I use:
```

sudo reboot
sudo shutdown 1
sudo halt

```
the first 2 are safe, the last may not be.

or just shutdown from the gui.

if the system is locked up, I hold Alt + Prntscrn (hold it for the entire command sequence), and slowly type 
```

reisub

```

---

### Post by llawwehttam on 2010-03-10
> **doas777 said:**
> I use:
if the system is locked up, I hold Alt + Prntscrn (hold it for the entire command sequence), and slowly type 
```

reisub

```

That is one of the most horrible ways to shutdown, almost like a hard restart.
I would not recommend it especially with ext4.

I have had to use it in the past but I avoid it at all costs.

---

### Post by undecim on 2010-03-10
> **llawwehttam said:**
> That is one of the most horrible ways to shutdown, almost like a hard restart.
I would not recommend it especially with ext4.

I have had to use it in the past but I avoid it at all costs.

It's MUCH safer than a hard restart. But it's still no alternative to a proper shutdown.

the s part syncs all your filesystems, and u unmounts them (this is equivilent to using the "safely remove" feature from the GUI).

Just make sure you wait for your hard drive light to turn off after each command.

When I want to reboot, I usually press Ctrl+Alt+F1 and Ctrl+Alt+Del - quick and easy.

I also have sudoers set up to let me use poweroff and reboot with no password, and have aliases in my bash to make "poweroff become" "sudo poweroff" and "reboot" to become "sudo reboot"

---

### Post by doas777 on 2010-03-10
> **llawwehttam said:**
> That is one of the most horrible ways to shutdown, almost like a hard restart.
I would not recommend it especially with ext4.

I have had to use it in the past but I avoid it at all costs.

that is not congruent with my understanding of the operation.
[http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html](http://www.junauza.com/2009/01/linux-keyboard-shortcuts-to-exit-safely.html)

---

### Post by denver on 2010-03-10
I'm even lazier then that. I only use:

S - sync
U - remount as RO
B - reset

:)).

It even works remotely, through SSH by echoing the letters one by one to /proc/sysrq-trigger :

```
echo s > /proc/sysrq-trigger
```

Will sync all filesystems for example.

---

### Post by undecim on 2010-03-10
> **denver said:**
> I'm even lazier then that. I only use:

S - sync
U - remount as RO
B - reset

:)).

It even works remotely, through SSH by echoing the letters one by one to /proc/sysrq-trigger :

```
echo s > /proc/sysrq-trigger
```

Will sync all filesystems for example.

You need to be root for that trick. You could instead do this:
```
echo s | sudo tee /proc/sysrq-trigger
```

or, if you want to do it all automatically,
```
sudo nohup bash -c "for key \"in r e i s u b\"; do echo $key > /proc/sysrq-trigger; sleep 8; done"

```

After about 8 seconds, your shell will disappear, and after about 40 seconds, your computer will reboot.

---

### Post by denver on 2010-03-10
Yup, you do need root. Most servers have the root account active :) (i rarely if ever have to do it on a desktop). If you have physical access to a computer you don't need the sysrq-trigger trick, but if you don't, and reboot does not work for some reason, its a life saver.

---

### Post by undecim on 2010-03-10
Someone should build a keyboard with just the Alt, SysRq, and R E I S U B keys that you can plug into a server and use.

---

### Post by denver on 2010-03-10
> **undecim said:**
> Someone should build a keyboard with just the Alt, SysRq, and R E I S U B keys that you can plug into a server and use.

You mean something along the lines of what MS already has?

[http://www.arcadeathome.com/images/news/new_microsoft_keyboard.jpg](http://www.arcadeathome.com/images/news/new_microsoft_keyboard.jpg)

:))

---

### Post by doas777 on 2010-03-10
one of my keyboards has put alt and sysreq so far apart that i can;t get them both with one hand.... it's like playing twister with your keyboard.

---

