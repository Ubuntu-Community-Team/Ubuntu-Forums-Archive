---
title: "Laptop Brightness at Maximum!"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Fawk3s on 2011-07-10
Hi! Just installed a 10.10 on my laptop! All excited! Its an amazing feeling! :)

But the laptop brightness is at the maximum and I feel like I'm staring at a tubelight! The brightness increase / decrease function keys behave as if it is increasing / decreasing the brightness, but nothing happens!

( Its a Lenovo T510 laptop, in case any of you guys are also using! )

Thanks in advance!

---

### Post by Jacobonbuntu on 2011-07-10
Hi Fawk3s!
and welcome!

I have two laptops; in one case the function buttons do work, on another one they don't.....

If you use 10.10 you can use the brightnes-panel in the gnome-panel (right-click on one of the panels and choose "add") In Unity you can set the brightness by the energy- settings.

hope it works!!

have a good time,
Jacob

---

### Post by Fawk3s on 2011-07-10
Thank you Jacob! I found brightness applet in the place where you asked me to look! However, when I tried to use the same, it went to the left hand top corner of the screen and got stuck! :) Can't even close it!

By the way, I also found this place, System -> Preferences -> Power Management. There is an option, 'Set display brightness to' along with a scroll bar. I set it to 50% (initially it was 100%) hoping for some results... But unfortunately, nothing happened again! 

Guess, I'll've to live with this.. :) No issues...

Thanks for the reply again though!

---

### Post by Jacobonbuntu on 2011-07-10
ah, terrible, and strange. You might want to buy sun glasses...8-)

---

### Post by mikewhatever on 2011-07-10
Here is a search result
[http://ubuntuforums.org/showthread.php?p=8826832](http://ubuntuforums.org/showthread.php?p=8826832)

> To be able to use the IBM FN keys to change the brightness, you need to add /etc/modprobe.d/thinkpad-acpi file with below content.
options thinkpad-acpi brightness-enable=1 experimental=1 hotkey=enable,0xffffff

---

### Post by Fawk3s on 2011-07-11
> **mikewhatever said:**
> Here is a search result
[http://ubuntuforums.org/showthread.php?p=8826832](http://ubuntuforums.org/showthread.php?p=8826832)

Thanks Mike! That looked like some real stuff there. I'd however bug you with a couple of more questions here. (please answer keeping in mind that a noob is asking them)

1) First of all, all the files present in /etc/modprobe.d were of type .conf type. So I presumed that the hinkpad-acpi should also be of the same type. Am I mistaken?

2) Secondly, I was unable to create the file directly in the /etc/modprobe.d (it was write protected) even though I used the sudo command before trying to create it. So I had to create the file in another directory and move it here using the sudo. Is there no way of creating the file directly? Please tell me.

3) Thirdy, since even after all this it did not solve the problem, my another noob question would be, do we ever have to restart the system like in windows?! :P

Appreciate all the responses (as well as the patience involved :) in answering! )

---

### Post by scrooge_74 on 2011-07-11
> **Fawk3s said:**
> Thanks Mike! That looked like some real stuff there. I'd however bug you with a couple of more questions here. (please answer keeping in mind that a noob is asking them)

1) First of all, all the files present in /etc/modprobe.d were of type .conf type. So I presumed that the hinkpad-acpi should also be of the same type. Am I mistaken?

2) Secondly, I was unable to create the file directly in the /etc/modprobe.d (it was write protected) even though I used the sudo command before trying to create it. So I had to create the file in another directory and move it here using the sudo. Is there no way of creating the file directly? Please tell me.

3) Thirdy, since even after all this it did not solve the problem, my another noob question would be, do we ever have to restart the system like in windows?! :P

Appreciate all the responses (as well as the patience involved :) in answering! )

Hi,

1)Didnt read the thread from where the info came, but if the info didnt put a .conf at the end then dont.

2) you can type first sudo su and you gain root privileges and then you can make the file directly there

3) You dont usually need to, but in this case you need to load the module in order for it to work

modprobe module is the command, being module the name of the module , or reboot see if it loads

---

### Post by Fawk3s on 2011-07-11
> **scrooge_74 said:**
> Hi,

1)Didnt read the thread from where the info came, but if the info didnt put a .conf at the end then dont.

2) you can type first sudo su and you gain root privileges and then you can make the file directly there

3) You dont usually need to, but in this case you need to load the module in order for it to work

modprobe module is the command, being module the name of the module , or reboot see if it loads

Thank you Scoorge! Although it did not solve the issue, at least I got to learn about what the modules are and how to load them /view the already loaded ones! (I was successfully able to load thinkpad_acpi.ko! )

---

### Post by mikewhatever on 2011-07-11
> **Fawk3s said:**
> ...

1) First of all, all the files present in /etc/modprobe.d were of type .conf type. So I presumed that the hinkpad-acpi should also be of the same type. Am I mistaken?

You are probably right. I think the .conf is the new convention, so if you are on 11.04, add it.

> 2) Secondly, I was unable to create the file directly in the /etc/modprobe.d (it was write protected) even though I used the sudo command before trying to create it. So I had to create the file in another directory and move it here using the sudo. Is there no way of creating the file directly? Please tell me.

Use the following command to open the file for editing (if not present, it will be created), save and exit when done:

```
gksudo gedit /etc/modprobe.d/thinkpad-acpi.conf
```
> 
3) Thirdy, since even after all this it did not solve the problem, my another noob question would be, do we ever have to restart the system like in windows?! :P

You might need to reboot in this particular case. I am not sure you can reload the module.

---

### Post by Fawk3s on 2011-07-11
> **mikewhatever said:**
> You are probably right. I think the .conf is the new convention, so if you are on 11.04, add it.



Use the following command to open the file for editing (if not present, it will be created), save and exit when done:

```
gksudo gedit /etc/modprobe.d/thinkpad-acpi.conf
```
You might need to reboot in this particular case. I am not sure you can reload the module.

Hey, all of you guys are absolutely amazing! Thanks so much!

---

### Post by s1baker on 2011-07-12
If all else fails, you may want to see if you can use the terminal to adjust the brightness.

Check out post #9 in this link about using the xgamma command in the terminal:

[http://ubuntuforums.org/showthread.php?t=1283622](http://ubuntuforums.org/showthread.php?t=1283622)

---

