---
title: "How Do I Completely Remove A Program?"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-10-10
I used 

```
apt-get --purge remove amarok
```
to try to completely remove amarok, but when I search for "amarok," there are still files in /usr/share. I want to remove it so when I reinstall it, it's as if I had never installed it before. Is there a command besides  "purge" that I can use to completely remove a program, or do I have to manually go in and delete the stuff in /usr/share myself?

---

### Post by Gannon8 on 2009-10-10
Well, you could remove the amarok folder in /usr/bin (just make sure you know what your doing).
BTW, isn't it "apt-get purge <whatever>"? I rarely use it :P

---

### Post by Sup3r3g0 on 2009-10-10
I don't think I know exactly what to do. I vaguely believe that it has something to do with rm -rf and then the location of the file. Is that right?

---

### Post by rippin on 2009-10-10
> **Sup3r3g0 said:**
> I used 

```
apt-get --purge remove amarok
```to try to completely remove amarok, but when I search for "amarok," there are still files in /usr/share. I want to remove it so when I reinstall it, it's as if I had never installed it before. Is there a command besides  "purge" that I can use to completely remove a program, or do I have to manually go in and delete the stuff in /usr/share myself?

sudo rm -r (use FULL path here so as NOT to wipe out EVERYTHING!!!)
[INDENT]OR

[/INDENT]sudo <file manger>, go to directory in question and delete
[INDENT]OR

[/INDENT]use synaptic

---

### Post by 3rdalbum on 2009-10-10
> **Sup3r3g0 said:**
> I want to remove it so when I reinstall it, it's as if I had never installed it before.

When you reinstall Amarok, it will overwrite the old files from the old package, if any exist. It will not overwrite per-user settings, so you'd best remove them from the hidden folder in your home directory. Without an existing settings file, Amarok will behave like it has just been installed.

If you want to remove and reinstall Amarok because it's not behaving as expected, then be aware that removing and reinstalling software doesn't generally solve problems on Linux, because program binaries don't get corrupted. The best procedure to try is to remove the per-user settings as I mentioned above.

---

### Post by sandyd on 2009-10-10
here you go.
```

rm ~/.kde/share/config/amarok*

```that will reset all of amarok's settings.

---

### Post by Sup3r3g0 on 2009-10-10
thanks i got it

---

### Post by grakhul on 2009-10-11
Very helpful. I also used aptitude purge <programname>, which is supposed to removed all traces of the program, configuration files and your personal settings.  I have noticed that this is not always the case. 

Best to use 'find' or 'locate' afterwards and manually remove any trace files.

Too bad there isn't a way to completely remove everything.

---

### Post by Elludium_Q-36 on 2010-01-04
I'm having similar problems with barry.

Seems complete removal and reinstallation is of no avail and perhaps the installation files are corrupted but synaptic does not download a thing after complete removal.

---

