---
title: "file browser crashes"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-02
when using the file browser it crashes (just closes doesn't freeze system or anything) when i try to look at the

user/bin files.

this has me worried that there is a problem with my system any ideas would be much appreciated.

doug

---

### Post by matt_symes on 2011-04-02
Hi

Have a look at the folder using the terminal ?

```
ls -al /usr/bin
```

(I assume you mean /usr/bin and not user/bin)

Kind regards

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi

Have a look at the folder using the terminal ?

```
ls -al /usr/bin
```

(I assume you mean /usr/bin and not user/bin)

Kind regards

Yes you are right i mean /usr/bin 

and using the terminal i am able to view all files, should i try to reinstall the file browser do you think?

---

### Post by matt_symes on 2011-04-02
Hi

> **dwhite said:**
> should i try to reinstall the file browser do you think?

Possibly. Is that the only folder that crashes nautilus ?

Have you installed any nautilus extensions ?

Kind regards

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi



Possibly. Is that the only folder that crashes nautilus ?

Kind regards

Hi, yes the only folder I have come across anyway.

I just went to synaptic package manager, deleted nautilus and then reinstalled, but same thing happens when opening usr/bin

oh, and also i didn't intentionally install any extensions, i'll check the list on synaptic to see if i can tell.
ps thanks for looking at this with me

??

---

### Post by dnairb on 2011-04-02
The /usr/bin folder can take a few seconds to open in nautilus - it contains over 1400 items on my laptop.

You could try in terminal:

```
nautilus /usr/bin
```

which will output error messages to the terminal. If there are any, you can post them here.

---

### Post by dwhite on 2011-04-02
> **dnairb said:**
> The /usr/bin folder can take a few seconds to open in nautilus - it contains over 1400 items on my laptop.

You could try in terminal:

```
nautilus /usr/bin
```

which will output error messages to the terminal. If there are any, you can post them here.

ok used terminal made the current directory /$ then typed 

nautilus /usr/bin


nautilus opened and then immediately quit
and no errors in terminal

---

### Post by dnairb on 2011-04-02
OK. You could try purging then reinstalling Nautilus and trying again:

```
sudo apt-get purge nautilus
```

then:

```
sudo apt-get install nautilus
```

---

### Post by dwhite on 2011-04-02
> **dnairb said:**
> Were any error messages reported in the terminal window?

sorry, no error messages


doug@dp-PT20:/$ nautilus usr/bin
doug@dp-PT20:/$ 

this is what i got

---

### Post by matt_symes on 2011-04-02
Hi

I seem the remember reading that certain file types could crash nautilus.

I cannot remember the exact types (think i read it after a couple of beers once) and i am trying to track it down.

Maybe you are being hit by that issue.

```
nautilus usr/bin
```

Unfortunately that will not work with nautilus. Good trick for most other software though.

Kind regards

---

### Post by dwhite on 2011-04-02
> **dnairb said:**
> OK. You could try purging then reinstalling Nautilus and trying again:

```
sudo apt-get purge nautilus
```

then:

```
sudo apt-get install nautilus
```

I tried this, everything seemed to work but then when i tried to open usr/bin in nautilus same result...crash

sorry to be a pain, but thanks for the help

---

### Post by matt_symes on 2011-04-02
Hi

Is anything being logged by nautilus in your ~/.xsession-errors file ?

Kind regards

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi

Is anything being logged by nautilus in your ~/.xsession-errors file ?

Kind regards


the most recent errors from nautilus in the ~/.xsession-errors file are:



(nautilus:2059): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2059): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): Gtk-CRITICAL **: IA__gtk_widget_is_toplevel: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:2059): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2059): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Initializing nautilus-gdu extension

(nautilus:2553): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2553): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2553): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Initializing nautilus-gdu extension

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:2571): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Initializing nautilus-gdu extension

---

### Post by dnairb on 2011-04-02
> **matt_symes said:**
> 

```
nautilus usr/bin
```

Unfortunately that will not work with nautilus. Good trick for most other software though.

Kind regards

The command was 

```
nautilus /usr/bin
```

note the leading "/" - this does work on my system - try it.

Nautilus itself seems to be OK. I agree that there may well be errors in other parts of the system.

---

### Post by dwhite on 2011-04-02
> **dnairb said:**
> The command was 

```
nautilus /usr/bin
```

note the leading "/" - this does work on my system - try it.

Nautilus itself seems to be OK. I agree that there may well be errors in other parts of the system.

tried it with the leading "/" but still no errors show up in the terminal.

---

### Post by dwhite on 2011-04-02
when in nautilus anytime i click on anything on the 

"Places" pane, an error is added to the .xsession-errors file

(nautilus:3768): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

is this normal?

not really a smile face in .xsession-errors the error is (nautilus:three seven six eight ):

---

### Post by matt_symes on 2011-04-02
Hi

> **dnairb said:**
> The command was 

```
nautilus /usr/bin
```

note the leading "/" - this does work on my system - try it.

Nautilus itself seems to be OK. I agree that there may well be errors in other parts of the system.

Yes that was my typo. I meant /usr/bin.

What output do you get on your system and what are you running ? I get no output either.

```
matthew@matthew-laptop:~$ nautilus /usr/bin
matthew@matthew-laptop:~$
```

Kind regards

---

### Post by matt_symes on 2011-04-02
Hi

> Nautilus itself seems to be OK. I agree that there may well be errors in other parts of the system.

@dnairb

Did you ever come across a bug that crashed nautilus when viewing certain file types. I am in agreement with you. I think the install is probably alright.

I seem to remember reading this but i can't track down info.

Kind regards

---

### Post by dnairb on 2011-04-02
> **dwhite said:**
> tried it with the leading "/" but still no errors show up in the terminal.

> **matt_symes said:**
> Hi



Yes that was my typo. I meant /usr/bin.

What output do you get on your system and what are you running ? I get no output either.

```
matthew@matthew-laptop:~$ nautilus /usr/bin
matthew@matthew-laptop:~$
```

Kind regards

@matt_symes:

When running the above command (in Lucid 10.04), nautilus opens at /usr/bin. If nautilus itself crashed, I would expect to see an error reported in terminal. As there is no further output in terminal, I believe that nautilus itself is not the problem.


@dwhite:

The .xsession-errors point to an error elsewhere in the system. 

I myself have not encountered this before; it's possibly due to nautilus extensions (but you don't have any installed) or Ubuntu One perhaps?

---

### Post by dnairb on 2011-04-02
> **matt_symes said:**
> Hi



@dnairb

Did you ever come across a bug that crashed nautilus when viewing certain file types. I am in agreement with you. I think the install is probably alright.

I seem to remember reading this but i can't track down info.

Kind regards

@matt_symes:
I've not encountered this before myself.

@dwhite:
Another thought: it may be a media-preview issue perhaps:

In Nautilus: Edit - Preferences - Previews tab and try changing settings there.

I may be clutching at straws here. If this doesn't work, then I am at a loss as what to do next. Sorry

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi



Yes that was my typo. I meant /usr/bin.

What output do you get on your system and what are you running ? I get no output either.

```
matthew@matthew-laptop:~$ nautilus /usr/bin
matthew@matthew-laptop:~$
```

Kind regards
i get

```
 doug@dp-PT20:~$ nautilus /usr/bin
doug@dp-PT20:~$ 

```

nautilus opens then immediately quits, lot of errors written to .xsession-errors

including an error saying that the "nautilus-gdu" extension failed to initialize

---

### Post by matt_symes on 2011-04-02
Hi

Try renaming this directory

```
~/.local/share/gvfs-metadata
```

Kind regards

---

### Post by dwhite on 2011-04-02
i can no longer start up computer, on restart i put in my password and it just goes to the startup page.....again

i have started in safe mode into the terminal

how can i save some of my files, that i can see in the terminal onto a usb drive

i don't know where the usb drive shows up

i want to write something like cp "folder name" to the usb i have inserted

---

### Post by matt_symes on 2011-04-02
Hi

> **dwhite said:**
> i can no longer start up computer, on restart i put in my password and it just goes to the startup page.....again

i have started in safe mode into the terminal

how can i save some of my files, that i can see in the terminal onto a usb drive

i don't know where the usb drive shows up

i want to write something like cp "folder name" to the usb i have inserted

Blimey. :( What happened ? 

Rename the folder back to see if that is causing the problem.

Kind regards

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi



Blimey. :( What happened ? 

Rename the folder back to see if that is causing the problem.

Kind regards


sorry this didn't happen with the rename, i never got to that

i deleted the contents of .xsession-error and after that problems, i really need to save some files to a usb before i do anything else

---

### Post by matt_symes on 2011-04-02
Hi

Insert the USB device and the mount it.

```
sudo mkdir /mnt/usb
sudo chown <your_user_name>:<your_user_name> /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```

Change <your_user_name> to your user name.

That assumes your device is sdb1. You can check this by typing

```
sudo fdisk -l
```

That is a small L above.

Then copy files.

```
sudo cp -R /source/path /mnt/usb
```

Good luck.

Kind regards

---

### Post by dwhite on 2011-04-02
> **matt_symes said:**
> Hi

Insert the USB device and the mount it.

```
sudo mkdir /mnt/usb
sudo chown <your_user_name>:<your_user_name> /mnt/usb
sudo mount /dev/sdb1 /mnt/usb
```Change <your_user_name> to your user name.

That assumes your device is sdb1. You can check this by typing

```
sudo fdisk -l
```That is a small L above.

Then copy files.

```
sudo cp -R /source/path /mnt/usb
```Good luck.

Kind regards


I have been able to save my documents to the usb thanks to your help

thanks very much!!!

i guess i will try to do a clean install, don't know what else to do

---

### Post by matt_symes on 2011-04-02
Hi

Check the disk for bad blocks using disk utility or smartrctl just to be sure. Do this from the liveCD.

Good luck :)

Kind regards

---

### Post by dwhite on 2011-04-03
was able to save all my files i needed to thanks to the help of matt_symes :), reinstalled system and now up and running like nothing happened.

Playing around got me in trouble #-o but all's well that ends well!!!

thanks everyone

---

