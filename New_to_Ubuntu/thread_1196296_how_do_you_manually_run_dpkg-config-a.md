---
title: "how do you manually run dpkg-config-a"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by roberttye on 2009-06-24
I have been trying to run dpkg-configure-a' manually but am having trouble with it
if anybody can help me with this it would be appreciated
I am unable to use use add/remove or my synaptic package manager without it telling me that I have a fatal error and must run manually
Thanks roberttye

---

### Post by bodhi.zazen on 2009-06-24
close synaptic

open a terminal

at the command line enter :

```
sudo dpkg-reconfigure -a
```

---

### Post by Celauran on 2009-06-24
Open a terminal and type

```
sudo dpkg --config -a
```

---

### Post by abn91c on 2009-06-24
**[COLOR="Blue"]sudo dpkg --configure -a[/COLOR]** is the correct syntax

---

### Post by lisati on 2009-06-24
As has already been suggested, go to the command line (applications->accessories->terminal) and type it in. ```
sudo dpkg --configure -a
```
 You will be asked for your password. Don't worry if it doesn't show, this is a normal Ubuntu security precaution (in case someone sneaky is looking over your shoulder) - just type it in as normal.

---

### Post by Miljet on 2009-06-24
Also note that "configure" has two dashes in front, the "a" only has one. And there are spaces before the dashes.

Just thought I would point that out after looking at the title of your post.

---

### Post by kansasnoob on 2009-06-25
When I've been playing and really hosed things I like to run:

```
sudo dpkg-reconfigure -phigh -a
```

---

### Post by wcutrombonekid on 2009-06-25
i've gotten this warning too, when i type this code in the terminal, what is it doing?

---

### Post by kansasnoob on 2009-06-25
> **wcutrombonekid said:**
> i've gotten this warning too, when i type this code in the terminal, what is it doing?

Well, quite simply, something interrupted the installation process. Many things could do that.

It's important to read the full output from the terminal when that occurs.

I've been playing with Enlightenment 17 a lot on Jaunty and sometimes some package changes I've made interfere with updates.

Generally the terminal will tell you what's up. You might want to run:

```
sudo apt-get -f install
```

Which may render a recommendation to auto-remove something or other, or somehow to cure some unmet dependency. Just don't go hog wild!

Pay attention to the changes you make, take notes!

Oh, and running that command reconfigures all installed packages.

---

### Post by -kg- on 2009-06-26
> **kansasnoob said:**
> 
Oh, and running that command reconfigures all installed packages.

From the "apt-get" manual:

> -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.  This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. Any Package that are specified must completely correct the problem. The option is sometimes necessary when running APT for the first time; APT itself
does not allow broken package dependencies to exist on a system. It
is possible that a system´s dependency structure can be so corrupt as to require manual intervention (which usually means using dselect( 8 ) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. 
Configuration Item: APT::Get::Fix-Broken.


If ever you are unsure what a command and it's options do, you can pull up it's manual page (if it exists) by typing:

```
man command
```

(Substituting the command, such as apt-get, in place of "command" above) which will display the command, what it does, and it's list of options and what they do.  The manuals are real handy to have as a reference to ensure you know what these commands do.

---

