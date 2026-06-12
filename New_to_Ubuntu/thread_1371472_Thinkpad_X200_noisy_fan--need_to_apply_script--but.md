---
title: "Thinkpad X200: noisy fan--need to apply script--but do not not know how to."
date: 2010-01-03
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2010-01-03
There is an excellent link [here]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts") with suggestion to get the fan noise under control. the problem is I do not understand the sequence to follow. 

I am running Karmic 32-bit on X200 Thinkpad.

Here is my output for ```
$ cat /proc/acpi/ibm/fan
status:		enabled
speed:		3762
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))
```

The thing is I want the fan to quieten down when tempt are low and fireup when tempt crosses a threshold.

Thanks--I have been struggling with this for 3 days non stop now. Can someone help me decipher the codes in that link for Karmic with a simple step by step instruction?

---

### Post by shuttleworthwannabe on 2010-01-04
Hi there, can anyone please guide me on this. Thanks

---

### Post by blazemore on 2010-01-04
Please open a terminal (Applications -> Accessories -> Terminal)
and type the following commands, pressing the Enter key after each one:

1. Download the script
```
wget http://www.thinkwiki.org/index.php?title=Code/tp-fancontrol&action=raw&ctype=application/octet-stream tp-fancontrol
```2. Move the script to the correct location
```
sudo mv tp-fancontrol /usr/bin/tp-fancontrol
```At this point you'll have to enter your password. No visual feedback will be given as you do so. Enter your password and press Enter.

3. Make the script executable, so your computer can run it
```
sudo chmod +x /usr/bin/tp-fancontrol
```4. Run this (required by the script according to the wiki) (separate commands)
```
sudo su
echo thinkpad-acpi /etc/modules
touch /etc/modprobe.d/thinkpad-acpi.conf
echo options thinkpad-acpi experimental=1 fan_control=1 /etc/modprobe.d/thinkpad-acpi.conf
exit

```5. Reboot now, or you can do this to load it straight away
```
sudo modprobe thinkpad-acpi experimental=1  fan_control=1
```Any errors, let me know.
Hope this helps!

---

### Post by shuttleworthwannabe on 2010-01-04
[CODE/] $ sudo modprobe thinkpad-acpi experimental=1  fan_control=1
[sudo] password for user: 
WARNING: All config files need .conf: /etc/modprobe.d/thinkpad-acpi, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.[/CODE]

Thanks for the help; all except the last step went well. I am not sure what the issue right now?

Appreciate the help!
S

---

### Post by blazemore on 2010-01-04
Sorry, please run this command and I'll fix the first post as well...
```
sudo mv /etc/modprobe.d/thinkpad-acpi /etc/modprobe.d/thinkpad-acpi.conf
```

---

### Post by shuttleworthwannabe on 2010-01-04
> **blazemore said:**
> Sorry, please run this command and I'll fix the first post as well...
```
sudo mv /etc/modprobe.d/thinkpad-acpi /etc/modprobe.d/thinkpad-acpi.conf
```

Hi sorry at what step should I run this? after chmod?

---

### Post by blazemore on 2010-01-04
just run it now.
I've fixed the guide so other people will do it right the first time; that fix there is just for you now.

---

### Post by shuttleworthwannabe on 2010-01-04
Blazemore,

this is the error I get when I run the last command:```
$ sudo mv /etc/modprobe.d/thinkpad-acpi /etc/modprobe.d/thinkpad-acpi.conf
mv: cannot stat `/etc/modprobe.d/thinkpad-acpi': No such file or directory
```

---

### Post by shuttleworthwannabe on 2010-01-05
Just checking if you are still around.

---

### Post by audiomick on 2010-01-05
Hi.
Because you're looking for blazemore.
If you go to the first page of the forum
[http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)
there is a list at the bottom of who is logged in. He's not there at the moment, but he'll be back. I see him a lot.

---

