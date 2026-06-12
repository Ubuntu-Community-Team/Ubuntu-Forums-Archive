---
title: "Good tool for learning command line"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by kamaboko on 2010-09-16
[https://launchpad.net/clicompanion/](https://launchpad.net/clicompanion/)

---

### Post by barney385 on 2010-09-16
Looks interesting. It's not in Synaptic as far as I can see.

Is there a repo for it?

---

### Post by skyjacker on 2010-09-16
Tried it......Like it. Thanks!

---

### Post by kamaboko on 2010-09-16
> **barney385 said:**
> Looks interesting. It's not in Synaptic as far as I can see.

Is there a repo for it?

No, I do not believe so.

---

### Post by jtarin on 2010-09-16
I like > Experienced users can use CLIcompanion to store their extensive list of commands in a searchable listI have always got a collection of obscure commands that I like to use occasionally.

---

### Post by JamButty on 2010-09-17
Great. Will save me a lot of time searching in obscure manpages for simple things. The constantly evolving environment (commands going in and out of fashion, advice on different pages conflicting etc.) is a challenge for n00bs.
Thanks.

---

### Post by zer010 on 2010-09-17
Definitely looks interesting...might have to try it out. Thanks!

---

### Post by JamButty on 2010-09-22
One problem though is a very small amount of display memory, I mean how much of the terminal display output is scrollable/savable. This is often vital when I am in unknown territory (which is most of the time with Ubuntu). The amount scrollable with Gnome terminal seems about 5 times that of Clicompanion, so now I jump back to Gnome terminal anytime I expect more than a screen of output that I might need to check.

---

### Post by duanedesign on 2010-09-27
> **JamButty said:**
> One problem though is a very small amount of display memory, I mean how much of the terminal display output is scrollable/savable. This is often vital when I am in unknown territory (which is most of the time with Ubuntu). The amount scrollable with Gnome terminal seems about 5 times that of Clicompanion, so now I jump back to Gnome terminal anytime I expect more than a screen of output that I might need to check.

This is a good point.

I have made some changes in CLI Companion to allow you to collapse/expand the command list. This will make the application more like Gnome-Terminal when the command list is collapsed. Hopefully this will make CLI Companion more useful as a daily Terminal.

Also in the next release I have redone the .clicompanion file format. This new format will allow for a broader range of commands to be stored in the command dictionary.

An example showing the difference between the old and new formats

NEW
> dpkg -l @: package : Find version of a package

OLD
> dpkg -l : package : Find version of a package

This new format will allow a user to add commands that can require arguments at run time anywhere in the command. It does this by using the @ symbol to act as a placeholder. The old format only allowed input at the end of the command. Which worked for a lot of commands, but not all. An example of a command that would not have worked with the old format:

> cat @ @ | sort | uniq > @ : file1, file2, file3 : combine, sort and remove duplicates


> Looks interesting. It's not in Synaptic as far as I can see.
Is there a repo for it?

Hopefully the application will make it into Debian by the end of the year and be in Universe for Natty Narwhal. Currently there are two options for installing CLI Companion. You can visit [the Launchpad page ]("https://launchpad.net/clicompanion")and download the .deb there. Additionally you can add the PPA and receive the updates automatically. To add the PPA use the following Terminal commands:

```
sudo add-apt-repository ppa:clicompanion-devs/clicompanion-nightlies
```
then to install CLI Companion run this command:
```
sudo apt-get install clicompanion
```
This PPA is fairly innocent. The only thing in it is CLI Companion. Nothing that will break your computer. The PPA is called nightlies, but until we get a stable PPA we will be very mindful not to push any broken code (on purpose). We are human and bugs happen. If you do notice a bug, or just have a Wishlist item please [file a bug.]("https://bugs.launchpad.net/clicompanion/+filebug")

thank you,
duanedesign

---

