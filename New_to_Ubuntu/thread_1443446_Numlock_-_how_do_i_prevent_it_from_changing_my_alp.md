---
title: "Numlock - how do i prevent it from changing my alphanumeric keys into numbers?"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Xendric on 2010-03-31
I have an HP Pavillion laptop with an embedded number pad.
When I press numlock in Ubuntu, it allows me to use the number pad numbers (when numlock is off, the keys on the number pad act as arrow keys), but it also changes some of my keys (such as K,L,I,O) into numbers.

I understand that this is useful on laptops that dont have a separate number pad, but is there any way to disable this feature and only make Numlock activate my number pad?

---

### Post by johngreth on 2010-03-31
It is most likely a hardware thing that Ubuntu can't change.

---

### Post by undecim on 2010-03-31
> **johngreth said:**
> It is most likely a hardware thing that Ubuntu can't change.

It is.

Just take a look at the output from xev when you press the buttons. The computer can't tell the difference between the real numpad and the fn key numpad

---

### Post by Xendric on 2010-04-01
> **undecim said:**
> Just take a look at the output from xev when you press the buttons. 

Sorry, I'm a complete noob as far as Linux and Ubuntu go - what is xev and what exactly are you suggesting me to do?

---

### Post by johngreth on 2010-04-01
what undecim is trying to say is that it can't be fixed, and you can prove that to your self by opening a terminal and running:
```
xev
```
then type the numbers with the function keys and with the num lock.

The important thing to notice is that the output is the same regardless of which way you enter the numbers, so it is impossible for the computer to tell the difference and therefor your problem can't be solved. I bought a wireless keyboard for my laptop because I got too fed up with it. You should be able to get one cheep ($15). It's a worthwhile investment.

---

### Post by Xendric on 2010-04-01
Ah ok, I get it now.

If it's a hardware issue though, how come Windows would only type letters, no matter whether my Numlock was on or off?

---

### Post by johngreth on 2010-04-01
Maybe windows disallowed the keyboard from actually using numlock. I'm not really sure...

---

### Post by gaaslight on 2010-06-28
Hi Xendric, 

I don't have a blog like these other bozos, but I have keyboard like yours. 

```
sudo gedit
```

open /etc/gdm/Init/Default

Find the line

exit 0

Add the following code above that line

```
if [ -x /usr/bin/numlockx ]; then
        /usr/bin/numlockx off
      fi
```

---

### Post by johngreth on 2010-06-28
> I don't have a blog like these other bozos
nice.

Anyway, wouldn't that also affect the numbers that are over the arrow keys? I'm not saying your solution is wrong. I just want to understand it in case it ever comes up again.

---

### Post by gaaslight on 2010-06-28
The keyboards that Xendric and I use, type the letter on the key with numlock off. With numlock on, we have to hold down the FN key to type the letter on the key. These keyboards don't have 10-key numeric pads on the right side of the board as a size consideration. The numbers at the top (2nd row) of the board work normally with numlock off.

---

### Post by gaaslight on 2010-06-28
The keyboards that Xendric and I use, type the letter on the key with numlock off. With numlock on, we have to hold down the FN key to type the letter on the key. These keyboards don't have 10-key numeric pads on the right side of the board as a size consideration. The numbers at the top (2nd row) of the board work normally with numlock off.

---

### Post by itkeepsrepeating on 2010-09-02
> **gaaslight said:**
> The keyboards that Xendric and I use, type the letter on the key with numlock off. With numlock on, we have to hold down the FN key to type the letter on the key. These keyboards don't have 10-key numeric pads on the right side of the board as a size consideration. The numbers at the top (2nd row) of the board work normally with numlock off.

@gaaslight:
I'm using Fedora13 now, but I still use Gnome, and am having this problem. I copy/pasted your suggestion into the aforementioned file, but I didn't get a result, even after logging out/in. I have that exact behavior described in the above quote. 

I'm fairly certain this is a Gnome thing, due to the path to the file we're editing here. 

An aside: I'd like to fire up Ubuntu to check the issue there, but haven't gotten around to fixing grub after Fedora/anaconda borked it up.

EDIT: I noticed there is no /usr/bin/numlockx file in my system. A clue, perhaps? Can I maybe just copy/paste your numlockx, or maybe a different version of the added goodness to /etc/gdm/Init/Default?

---

### Post by gaaslight on 2010-09-03
> **itkeepsrepeating said:**
> @gaaslight:
I'm using Fedora13 now, but I still use Gnome, and am having this problem. I copy/pasted your suggestion into the aforementioned file, but I didn't get a result, even after logging out/in. I have that exact behavior described in the above quote. 

I'm fairly certain this is a Gnome thing, due to the path to the file we're editing here. 

An aside: I'd like to fire up Ubuntu to check the issue there, but haven't gotten around to fixing grub after Fedora/anaconda borked it up.

EDIT: I noticed there is no /usr/bin/numlockx file in my system. A clue, perhaps? Can I maybe just copy/paste your numlockx, or maybe a different version of the added goodness to /etc/gdm/Init/Default?

[http://wiki.archlinux.org/index.php/Activating_Numlock_on_Bootup]("http://wiki.archlinux.org/index.php/Activating_Numlock_on_Bootup")

---

### Post by itkeepsrepeating on 2010-09-03
Thanks, gaaslight, that link pointed me right where I needed to go. Your instructions were there, but since I had already done that with no effect, I loosely followed the KDE instructions. To be more explicit, I created a file "numlockx" in my home directory, made it executable, and entered into it:
```
#!/bin/sh
numlockx on
```

Then, in Gnome, I went to System>Preferences>Startup Applications, and created a new entry, named it "numlockx", and pointed it to the file I just created. Restarted and found success.

Thanks go out to gaaslight, and fedoraforums as well for both of your snappy responses. 

I'm still kind of wondering why the original fix posted here by gaaslight didn't work, when the same thing was posted as a suggestion in the fedora forums. Maybe it's something I did, maybe they changed how Gnome works, maybe I'm just an idiot or have magical powers. Whatever, it works now. THANKS!!

---

